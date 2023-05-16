---
layout: page
title: "Enumerations"
category: ref
date: 2021-11-24 15:26:40
order: 40
---

#### Methods

 * [enumeration.list](#enumeration_list)
 * [enumeration.info](#enumeration_info)

*These methods were added in version 2021.6*

----

#### Entity Properties

 * [Enumeration](#enumeration_properties)

----

enumeration.list
==============

~~~ slim
enumeration.list (int|null $warehouseId)
~~~

Get all enumerations.

#### Parameters

0 _int|null_
: Warehouse.
{:.code-defs.wide}

#### Return Value

An array of [Enumerations](#enumeration_properties) or an empty array.

#### Example Request

Get all enumerations:

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "enumeration.list"
    ]
}
```

Get all enumerations for warehouse "2":

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "enumeration.list",
        [2]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "result" : {
        "catalog": {
            "goods_type": {
                "singular_name": "Goods Type",
                "plural_name": "Goods Types",
                "data": [
                    {
                        "key": "HAZMAT",
                        "label": "Regulated"
                    },
                    {
                        "key": "LIMITED_QUANTITIES_COMMODITIES",
                        "label": "Limited Quantities: Consumer Commodity"
                    },
                    {
                        "key": "NORMAL",
                        "label": "Not Regulated"
                    }
                ]
            }
        },
        "shipment": {
            "status": {
                "singular_name": "Status",
                "plural_name": "Statuses",
                "data": [
                    {
                        "key": "canceled",
                        "label": "Canceled"
                    },
                    {
                        "key": "shipped",
                        "label": "Shipped"
                    },
                    {
                        "key": "new",
                        "label": "New"
                    },
                    {
                        "key": "packed",
                        "label": "Packed"
                    },
                    {
                        "key": "packing",
                        "label": "Packing"
                    },
                    {
                        "key": "packing_exception",
                        "label": "Packing Exception"
                    },
                    {
                        "key": "picked",
                        "label": "Picked"
                    },
                    {
                        "key": "picking",
                        "label": "Picking"
                    },
                    {
                        "key": "voided",
                        "label": "Voided"
                    }
                ]
            }
        }
    }
}
```

enumeration.info
==============

~~~ slim
enumeration.info (string $path, int|null $warehouseId)
~~~

Get enumeration info.

#### Parameters

0 _string_
: Path.

1 _int|null_
: Warehouse.
{:.code-defs.wide}

#### Return Value

[Enumeration](#enumeration_properties).

#### Example Request

Get enumeration info:

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "enumeration.info",
        ["catalog/goods_type"]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "result" : {
        "singular_name": "Goods Type",
        "plural_name": "Goods Types",
        "data": [
            {
                "key": "HAZMAT",
                "label": "Regulated"
            },
            {
                "key": "LIMITED_QUANTITIES_COMMODITIES",
                "label": "Limited Quantities: Consumer Commodity"
            },
            {
                "key": "NORMAL",
                "label": "Not Regulated"
            }
        ]
    }
}
```

<h3 id="enumeration_properties">
    Enumeration Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>singular_name</th>
        <td>
            <pre><code>{ "singular_name" : "Lot Type" }</code></pre>
            The singular name.
        </td>
    </tr>
    <tr>
        <th>plural_name</th>
        <td>
            <pre><code>{ "plural_name" : "Lot Types" }</code></pre>
            The plural name.
        </td>
    </tr>
    <tr>
        <th>depends_on_merchant</th>
        <td>
            <pre><code>{ "depends_on_merchant" : true }</code></pre>
            Depends on merchant flag is only returned when the value is true.
        </td>
    </tr>
    <tr>
        <th>depends_on_warehouse</th>
        <td>
            <pre><code>{ "depends_on_warehouse" : true }</code></pre>
            Depends on warehouse flag is only returned when the value is true.
        </td>
    </tr>
    <tr>
        <th>data</th>
        <td>
            <pre><code>{ "data" : [{"key": "packed", "label": "Packed"}] }</code></pre>
            Enumeration data.
        </td>
    </tr>
</tbody>
</table>
