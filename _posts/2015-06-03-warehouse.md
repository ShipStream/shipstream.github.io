---
layout: page
title: "Warehouse"
category: ref
date: 2015-06-03 17:48:21
order: 37
---

#### Methods

 * [warehouse.list](#warehouse_list)

----

#### Entity Properties

 * [Warehouse](#warehouse_properties)
 
----

ShipStream supports multiple warehouses. Use this API endpoint to retrieve your list of warehouses.

<h1 id="warehouse_list">
warehouse.list
<code>()</code>
</h1>
Retrieve warehouses list.

#### Parameters

The method is used without parameters.

#### Return Value

An array of objects with warehouse information.

#### Example Request

Retrieve warehouses information:

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "warehouse.list",
        []
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "error" : null,
    "result" : [
        {
            "warehouse_id" : 1,
            "name" : "Warehouse 1",
            "is_active" : 1
        },
        {
            "warehouse_id" : 2,
            "name" : "Warehouse 2",
            "is_active" : 1
        }
    ]
}
```

<h3 id="warehouse_properties">
    Warehouse Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>warehouse_id</th>
        <td>
            <pre><code>{ "warehouse_id" : 1 }</code></pre>
            The internal warehouse ID.
        </td>
    </tr>
    <tr>
        <th>name</th>
        <td>
            <pre><code>{ "name" : "Warehouse 1" }</code></pre>
            The "Name" property.
        </td>
    </tr>
    <tr>
        <th>is_active</th>
        <td>
            <pre><code>{ "is_active" : 1 }</code></pre>
            Flag whether warehouse is active.
        </td>
    </tr>
</tbody>
</table>
