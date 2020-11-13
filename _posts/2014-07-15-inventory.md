---
layout: page
title: "Inventory"
category: ref
date: 2014-07-15 17:27:49
order: 10
---

#### Methods

 * [inventory.list](#inventorylist)
 * [inventory.lots](#inventorylots)
 * [inventory.details](#inventorydetails)

----

#### Entity Properties

 * [Inventory Item](#inventory_item)
 * [Inventory Lot](#lot_properties)

----

ShipStream tracks each merchant's inventory at all times using the following statuses:

 * **Expected** - Listed on open ASNs, RMAs and Other Deliveries that have not yet been received.
 * **Processed** - Counted on an ASN, RMA or Other Delivery but not yet put-away.
 * **Put-Away** - Has been received on an ASN, RMA or Other Delivery that has not yet been committed to the inventory.
   If you have auto-commit enabled this should always be 0.
 * **Available** - Available for new orders. Backordered amounts are not reflected as a negative Available amount but are tracked separately as "Backordered".
 * **Allocated** - Allocated to existing orders but not yet Reserved.
 * **Reserved** - Reserved to a specific shelf location and waiting to be picked.
 * **Picked** - Picked from the shelves but not yet shipped.
 * **Backordered** - Reserved by existing orders but not in stock. Will be automatically converted to Reserved when stock is added. Backordered quantities are not reflected in the Available amount as a negative number.
 * **Advertised** - The "Available" quantity plus the virtual BOM quantity.  The virtual BOM quantity is controlled by a product's "Virtual Inventory" attribute.

Additionally, products have two flags that can be set which will affect whether or not they are retrieved in an inventory request.

 * **Status** - Enabled/Disabled - If "Disabled", the product is effectively deleted and will not appear in responses to inventory requests.
 * **Visibility** - Visible/Not Visible - If "Not Visible", the product will not appear in the inventory list but may still be ordered via the Merchant Panel.


inventory.list
==============

~~~ slim
inventory.list (string|array|null $skus, int|null $warehouseId, string|null $updatedSince)
~~~

Get inventory levels for one or more products by SKU. If a warehouse is not specified the sum of all warehouse inventories
will be returned, otherwise the inventory levels for the specified warehouse will be returned.

#### Parameters

0 _string|array|null_
: SKUs. If not specified then inventory for all SKUs will be returned.
  - string - Get inventory for a single product by SKU.
  - array - Get inventory for the specified products by SKU.
  - null - Get inventory for all products.

  
1 _int|null_
: Warehouse. If not specified, returned values represent sums of all warehouses.

2 _string|null_
: Updated Since.
{:.code-defs.wide}

#### Return Value

An array of [Inventory Items](#inventory_item) or an empty array if there were no matching SKUs.

#### Example Request

Get inventory for two SKUs:

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "inventory.list",
        [
            ["BlueWidget-1","BlueWidget-5"]
        ]
    ]
}
```

Get all inventory:

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "inventory.list"
    ]
}
```

Get all inventory for warehouse "2":

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "inventory.list",
        [
            null,
            2
        ]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "result" : [
        {
            "sku" : "BlueWidget-1",
            "qty_expected"    : 0,
            "qty_processed"   : 0,
            "qty_putaway"     : 50,
            "qty_available"   : 22,
            "qty_allocated"   : 5,
            "qty_reserved"    : 16,
            "qty_picked"      : 1,
            "qty_backordered" : 0,
            "qty_advertised"  : 22
        },
        {
            "sku" : "BlueWidget-5",
            "qty_expected"    : 40,
            "qty_processed"   : 0,
            "qty_putaway"     : 0,
            "qty_available"   : 0,
            "qty_allocated"   : 0,
            "qty_reserved"    : 2,
            "qty_picked"      : 0,
            "qty_backordered" : 5,
            "qty_advertised"  : 0
        }
    ]
}
```

inventory.lots
==============

~~~ slim
inventory.lots (null|object $filters, array $options = [])
~~~

Retrieve list of lots by filters.

#### Parameters

0 _null|object_
: Filters to apply for the search.

  * _null_ - Retrieve list of all orders.
  * _object_ - Retrieve list of orders using specified "[Search Filters](/doc/search-filters.html)".

1 _null|object_
: Options to apply for the search.

  * _null_ - No options will be applied.
  * _object_ - Apply specified "[Search Options](/doc/search-options.html)".

#### Return Value

An array of objects. Each object will contain 
"<a href="#lot_properties">Lot Properties</a>".

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "inventory.lots",
        [
            {
                "lot_id" : {
                    "in" : [1, 2]
                }
            },
            []
        ]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "result" : {
       "results": [
           {
               "lot_id": "1",
               "lot_number": "2018-07-09",
               "origination_date": "2018-07-09",
               "expiration_date": "2019-04-07",
               "is_active": "1",
               "group_value": "2018-07-09",
               "created_at": "2018-07-09T19:58:23+00:00",
               "sku": "product1",
               "name": "product 1",
               "locations": [
                   "location 1"
               ],
               "qty_putaway": "0.0000",
               "qty_available": "76.0000",
               "qty_reserved": "0.0000"
           },
           {
               "lot_id": "2",
               "lot_number": "2018-07-09",
               "origination_date": "2018-07-09",
               "expiration_date": "2019-04-11",
               "is_active": "1",
               "group_value": "2018-07-09",
               "created_at": "2018-07-09T19:59:03+00:00",
               "sku": "product2",
               "name": "product 2",
               "locations": [],
               "qty_putaway": "0.0000",
               "qty_available": "0.0000",
               "qty_reserved": "0.0000"
           }
       ],
       "totalCount": 2,
       "numPages": 1
   }
}
```

#### Error Codes

| code | message |
| ---- | ------- |
| 102 | Unexpected error applying filters. |

inventory.details
==============

~~~ slim
inventory.details (string|array|null $skus, string|null $updatedSince)
~~~

Get global and per-warehouse inventory levels for one or more products by SKU.

#### Parameters

0 _string|array|null_
: SKUs. If not specified then inventory for all SKUs will be returned.
  - string - Get inventory for a single product by SKU.
  - array - Get inventory for the specified products by SKU.
  - null - Get inventory for all products.
  
1 _string|null_
: Updated Since.
{:.code-defs.wide}

#### Return Value

An array of detailed items inventory, or an empty array if there were no matching SKUs.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "inventory.detailed",
        [
            ["BlueWidget-1","BlueWidget-5"],
            "2014-07-24T18:51:18+00:00"
        ]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "result" : [
        {
            "sku": "BlueWidget-1",
            "qty_expected": "0.0000",
            "qty_processed": "0.0000",
            "qty_putaway": "0.0000",
            "qty_available": "8.0000",
            "qty_allocated": "0.0000",
            "qty_reserved": "0.0000",
            "qty_picked": "2.0000",
            "qty_backordered": "0.0000",
            "qty_advertised": "8",
            "detailed": [
                {
                    "warehouse_id": "1",
                    "qty_expected": "0.0000",
                    "qty_processed": "0.0000",
                    "qty_putaway": "0.0000",
                    "qty_available": "8.0000",
                    "qty_allocated": "0.0000",
                    "qty_reserved": "0.0000",
                    "qty_picked": "2.0000",
                    "qty_advertised": "8"
                },
                {
                    "warehouse_id": "2",
                    "qty_expected": "0.0000",
                    "qty_processed": "0.0000",
                    "qty_putaway": "0.0000",
                    "qty_available": "0.0000",
                    "qty_allocated": "0.0000",
                    "qty_reserved": "0.0000",
                    "qty_picked": "0.0000",
                    "qty_advertised": "0"
                },
                {
                    "warehouse_id": "3",
                    "qty_expected": "0.0000",
                    "qty_processed": "0.0000",
                    "qty_putaway": "0.0000",
                    "qty_available": "0.0000",
                    "qty_allocated": "0.0000",
                    "qty_reserved": "0.0000",
                    "qty_picked": "0.0000",
                    "qty_advertised": "0"
                }
            ]
        },
        {
            "sku": "BlueWidget-5",
            "qty_expected": "0.0000",
            "qty_processed": "0.0000",
            "qty_putaway": "0.0000",
            "qty_available": "98.0000",
            "qty_allocated": "0.0000",
            "qty_reserved": "0.0000",
            "qty_picked": "1.0000",
            "qty_backordered": "0.0000",
            "qty_advertised": "98",
            "detailed": [
                {
                    "warehouse_id": "1",
                    "qty_expected": "0.0000",
                    "qty_processed": "0.0000",
                    "qty_putaway": "0.0000",
                    "qty_available": "98.0000",
                    "qty_allocated": "0.0000",
                    "qty_reserved": "0.0000",
                    "qty_picked": "1.0000",
                    "qty_advertised": "98"
                },
                {
                    "warehouse_id": "2",
                    "qty_expected": "0.0000",
                    "qty_processed": "0.0000",
                    "qty_putaway": "0.0000",
                    "qty_available": "0.0000",
                    "qty_allocated": "0.0000",
                    "qty_reserved": "0.0000",
                    "qty_picked": "0.0000",
                    "qty_advertised": "0"
                },
                {
                    "warehouse_id": "3",
                    "qty_expected": "0.0000",
                    "qty_processed": "0.0000",
                    "qty_putaway": "0.0000",
                    "qty_available": "0.0000",
                    "qty_allocated": "0.0000",
                    "qty_reserved": "0.0000",
                    "qty_picked": "0.0000",
                    "qty_advertised": "0"
                }
            ]
        }
    ]
}
```

#### Error Codes

| code | message |
| ---- | ------- |
| 102 | Unexpected error applying filters. |

## Entity Properties

<h3 id="inventory_item">
    Inventory Item
</h3>

<table class="table-striped">
<tr><th>sku</th>
<td>
	<pre><code>{ "sku" : "BlueWidget-1" }</code></pre>
	A unique identifier for a product. The SKU does appear on the packing slip. It is recommended that this be human-readable
	and end with a per-pack quantity to facilitate proper receiving. For example, a single blue widget may be "BlueWidget-1" and
	a pack of 5 blue widgets may be "BlueWidget-5". Maximum character length is 64.
</td></tr>
<tr><th>qty_expected</th>
<td>
	<pre><code>{ "qty_expected" : 1 }</code></pre>
	The "Expected" quantity.
</td></tr>
<tr><th>qty_processed</th>
<td>
	<pre><code>{ "qty_processed" : 1 }</code></pre>
	The "Processed" quantity.
</td></tr>
<tr><th>qty_putaway</th>
<td>
	<pre><code>{ "qty_putaway" : 1 }</code></pre>
	The "Put-Away" quantity.
</td></tr>
<tr><th>qty_available</th>
<td>
	<pre><code>{ "qty_available" : 1 }</code></pre>
	The "Available" quantity.
</td></tr>
<tr><th>qty_allocated</th>
<td>
	<pre><code>{ "qty_allocated" : 1 }</code></pre>
	The "Allocated" quantity.
</td></tr>
<tr><th>qty_reserved</th>
<td>
	<pre><code>{ "qty_reserved" : 1 }</code></pre>
	The "Reserved" quantity.
</td></tr>
<tr><th>qty_picked</th>
<td>
	<pre><code>{ "qty_picked" : 1 }</code></pre>
	The "Picked" quantity.
</td></tr>
<tr><th>qty_backordered</th>
<td>
	<pre><code>{ "qty_backordered" : 1 }</code></pre>
	The "Backordered" quantity. This quantity will not be present
	for single-warehouse requests since backordered amounts are not
	apportioned to specific warehouses.
</td></tr>
<tr><th>qty_advertised</th>
<td>
	<pre><code>{ "qty_advertised" : 1 }</code></pre>
	The "Advertised" quantity. This is the "Available" quantity plus
	the virtual BOM quantity.  The virtual BOM quantity is controlled by
	a product's "Virtual Inventory" attribute.
</td></tr>
</table>

<h3 id="lot_properties">
    Lot Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>lot_id</th>
        <td>
            <pre><code>{ "lot_id": 25 }</code></pre>
            The internal lot ID.
        </td>
    </tr>
    <tr>
        <th>is_active</th>
        <td>
            <pre><code>{ "is_active": 1 }</code></pre>
            Flag whether lot is active.
        </td>
    </tr>
    <tr>
        <th>sku</th>
        <td>
            <pre><code>{ "sku": "product1" }</code></pre>
            The "SKU" property.
        </td>
    </tr>
    <tr>
        <th>name</th>
        <td>
            <pre><code>{ "name": "product 1" }</code></pre>
            The "Name" property.
        </td>
    </tr>
    <tr>
        <th>lot_number</th>
        <td>
            <pre><code>{ "lot_number": "AB190405ZZ9Z" }</code></pre>
            The "Lot Number" property.
        </td>
    </tr>
    <tr>
        <th>expiration_date</th>
        <td>
            <pre><code>{ "expiration_date": "2019-04-07" }</code></pre>
            The "Expiration Date" property.
        </td>
    </tr>
    <tr>
        <th>origination_date</th>
        <td>
            <pre><code>{ "origination_date": "2018-07-09" }</code></pre>
            The "Origination Date" property.
        </td>
    </tr>
    <tr>
        <th>group_value</th>
        <td>
            <pre><code>{ "group_value": "2018-07-09" }</code></pre>
            The "Group Value" property.
        </td>
    </tr>
    <tr>
        <th>created_at</th>
        <td>
            <pre><code>{ "created_at": "2018-07-09T18:51:34+00:00" }</code></pre>
            The "Created At" property in ISO 8601 format.
        </td>
    </tr>
    <tr>
        <th>locations</th>
        <td>
            <pre><code>{ "locations": ["location A", "location B"] }</code></pre>
            A list of locations.
        </td>
    </tr>
    <tr>
        <th>qty_putaway</th>
        <td>
            <pre><code>{ "qty_putaway": "1.0000" }</code></pre>
            The "Put-Away" quantity.
        </td>
    </tr>
    <tr>
        <th>qty_available</th>
        <td>
            <pre><code>{ "qty_available": "55.0000" }</code></pre>
            The "Available" quantity.
        </td>
    </tr>
    <tr>
        <th>qty_reserved</th>
        <td>
            <pre><code>{ "qty_reserved": "1.0000" }</code></pre>
            The "Reserved" quantity.
        </td>
    </tr>
</tbody>
</table>
