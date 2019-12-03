---
layout: page
title: "Inventory"
category: ref
date: 2014-07-15 17:27:49
order: 10
---

#### Methods

 * [inventory.list](#inventory_list)

----

#### Entity Properties

 * [Inventory Item](#inventory_item)

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

Additionally, products have two flags that can be set which will affect whether or not they are retrieved in an inventory request.

 * **Status** - Enabled/Disabled - If "Disabled", the product is effectively deleted and will not appear in responses to inventory requests.
 * **Visibility** - Visible/Not Visible - If "Not Visible", the product will not appear in the inventory list but may still be ordered via the Merchant Panel.


inventory.list
==============

~~~ slim
inventory.list (string|array|null $skus, int|null $warehouseId)
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
            "qty_backordered" : 0
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
            "qty_backordered" : 5
        }
    ]
}
```

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
	a product's "Virtual Inventory" attribute.  This quantity will not 
	be present for single-warehouse requests since virtual amounts 
	are not apportioned to specific warehouses.
</td></tr>
</table>
