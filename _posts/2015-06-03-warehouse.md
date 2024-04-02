---
layout: page
title: "Warehouse"
category: ref
date: 2015-06-03 17:48:21
order: 180
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
            "is_active": 1,
            "address": {
                "street1": "4616 Crossroads Park Dr",
                "street2": "",
                "city": "Liverpool",
                "country": "US",
                "region": "NY",
                "postcode": "13088"
            }
        },
        {
            "warehouse_id" : 2,
            "name" : "Warehouse 2",
            "is_active": 1,
            "address": {
                "street1": "3900 Produce Rd",
                "street2": "",
                "city": "Louisville",
                "country": "US",
                "region": "KY",
                "postcode": "40218"
            }
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
    <tr>
        <th>address</th>
        <td>
            <pre><code>{ "address" : { "street1": "3900 Produce Rd", "street2": "", "city": "Louisville", "country": "US", "region": "KY", "postcode": "40218" }}</code></pre>
             The address of the warehouse. <a href="#warehouse_address_properties">Details</a>.
        </td>
    </tr>
</tbody>
</table>

<h3 id="warehouse_address_properties">
    Warehouse Address Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>street1</th>
        <td>
            <pre><code>{ "street1" : "3900 Produce Rd" }</code></pre>
            The street address. First Line
        </td>
    </tr>
    <tr>
        <th>street2</th>
        <td>
            <pre><code>{ "street2" : "# 61157" }</code></pre>
            The street address. Second Line
        </td>
    </tr>
    <tr>
        <th>city</th>
        <td>
            <pre><code>{ "city" : "Liverpool" }</code></pre>
            The city.
        </td>
    </tr>
    <tr>
        <th>country</th>
        <td>
            <pre><code>{ "country" : "GB" }</code></pre>
            The country code ISO 3166-1.
        </td>
    </tr>
    <tr>
        <th>region</th>
        <td>
            <pre><code>{ "region" : "KY" }</code></pre>
            The region code ISO 3166-2.
        </td>
    </tr>
    <tr>
        <th>postcode</th>
        <td>
            <pre><code>{ "postcode" : "40218" }</code></pre>
            The "Postal Code" property. Pass as a string to prevent leading 0s from being dropped.
        </td>
    </tr>
</tbody>
</table>
