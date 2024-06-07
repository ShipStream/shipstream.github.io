---
layout: page
title: "Stock Movements"
category: ref
date: 2024-04-16 13:01:39
order: 100
---

#### Methods

* [stock_movement.list](#stock_movement_list)

*These methods were added in version 2024.2*

----

#### Entity Properties

* [Stock Movement](#stock_movement_properties)

----

Stock Movements record every change to inventory items such as when an order is received and allocated to a warehouse or a shipment is picked from the shelf.

stock_movement.list
==============

~~~ slim
stock_movement.list (null|object $filters, null|object $options)
~~~

Retrieve list of stock movements.

#### Parameters

0 _object|null_
: [Filters](doc/search-filters.html) to apply to the request. Allowed properties for filtering: "id", "entity_type", "entity_action", "entity_id", 
"product_id", "sku", "created_at", "warehouse_id", "location"

1 _object|null_
: [Options]((doc/search-options.html)) to apply to the request.
{:.code-defs.wide}

#### Return Value

An array of [Stock Movements](#stock_movement_properties) or an empty array.

#### Example Request

Get all stock movements:

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "stock_movement.list"
    ]
}
```

Get all stock movements for warehouse "2":

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "stock_movement.list",
        [
            {
                "warehouse_id": {
                    "eq": "2"
                }
            }
        ]
    ]
}
```

#### Example Response

```json
{
    "result": {
        "results": [
            {
                "id": "12",
                "entity_type": "order",
                "entity_action": "create",
                "product_id": "4",
                "qty_expected": null,
                "qty_processed": null,
                "qty_putaway": null,
                "qty_available": "-1.0000",
                "qty_allocated": "1.0000",
                "qty_reserved": null,
                "qty_picked": null,
                "qty_backordered": null,
                "created_at": "2022-09-12T19:47:50+00:00",
                "sku": "12-345-6789",
                "comment": null,
                "warehouse_id": "2",
                "entity_id": "100000001",
                "location": ""
            }
        ],
        "totalCount": 1,
        "numPages": 1
    },
    "id": "1",
    "jsonrpc": "2.0"
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 101 | Invalid filters given. Details in error message. |

----

<h3 id="stock_movement_properties">
    Stock Movement Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>id</th>
        <td>
            <pre><code>{ "id" : "1" }</code></pre>
            The internal stock movement ID.
        </td>
    </tr>
    <tr>
        <th>entity_type</th>
        <td>
            <pre><code>{ "entity_type" : "order" }</code></pre>
            The "Type" property. Allowed values: "delivery", "order", "work_order", "stock", "relocation".
        </td>
    </tr>
    <tr>
        <th>entity_action</th>
        <td>
            <pre><code>{ "entity_action" : "pick" }</code></pre>
            The "Action" property. Allowed values: "create", "edit", "cancel", "void", "adjust", "process", "unprocess"
            "putaway", "commit", "transfer", "ship", "unship", "pick", "unpick", "relocate", "pull", "push", "convert", 
            "allocate", "deallocate", "correction", "assemble".
        </td>
    </tr>
    <tr>
        <th>entity_id</th>
        <td>
            <pre><code>{ "entity_id" : "100000001" }</code></pre>
            The "Entity ID" property.
        </td>
    </tr>
    <tr>
        <th>product_id</th>
        <td>
            <pre><code>{ "product_id" : "4" }</code></pre>
            The internal product ID.
        </td>
    </tr>
    <tr>
        <th>sku</th>
        <td>
            <pre><code>{ "sku" : "12-345-6789" }</code></pre>
            The "Product SKU" property.
        </td>
    </tr>
    <tr>
        <th>warehouse_id</th>
        <td>
            <pre><code>{ "warehouse_id" : "2" }</code></pre>
            The internal warehouse ID.
        </td>
    </tr>
    <tr>
        <th>qty_expected</th>
        <td>
            <pre><code>{ "qty_expected" : null }</code></pre>
            The "Expected" qty.
        </td>
    </tr>
    <tr>
        <th>qty_processed</th>
        <td>
            <pre><code>{ "qty_processed" : null }</code></pre>
            The "Processed" qty.
        </td>
    </tr>
    <tr>
        <th>qty_putaway</th>
        <td>
            <pre><code>{ "qty_putaway" : null }</code></pre>
            The "Put-Away" qty.
        </td>
    </tr>
    <tr>
        <th>qty_available</th>
        <td>
            <pre><code>{ "qty_available" : null }</code></pre>
            The "Available" qty.
        </td>
    </tr>
    <tr>
        <th>qty_allocated</th>
        <td>
            <pre><code>{ "qty_allocated" : null }</code></pre>
            The "Allocated" qty.
        </td>
    </tr>
    <tr>
        <th>qty_reserved</th>
        <td>
            <pre><code>{ "qty_reserved" : "-1.0000" }</code></pre>
            The "Reserved" qty.
        </td>
    </tr>
    <tr>
        <th>qty_picked</th>
        <td>
            <pre><code>{ "qty_picked" : un }</code></pre>
            The expected qty.
        </td>
    </tr>
    <tr>
        <th>qty_backordered</th>
        <td>
            <pre><code>{ "qty_backordered" : null }</code></pre>
            The "Backordered" qty.
        </td>
    </tr>
    <tr>
        <th>created_at</th>
        <td>
            <pre><code>{ "created_at" : "2020-10-26T16:42:03+00:00" }</code></pre>
            The "Timestamp" property.
        </td>
    </tr>
    <tr>
        <th>comment</th>
        <td>
            <pre><code>{ "comment" : "" }</code></pre>
            The "Comment" property.
        </td>
    </tr>
    <tr>
        <th>location</th>
        <td>
            <pre><code>{ "location" : "A01-W01-001" }</code></pre>
            The "Location" property.
        </td>
    </tr>
</tbody>
</table>
