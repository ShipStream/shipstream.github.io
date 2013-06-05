---
layout: page
title: "Packing"
category: ref
parent: "Order"
date: 2017-11-10 14:42:47
order: 17
---

#### Methods

 * [order_packing.create](#order_packing_create)
 * [order_packing.edit](#order_packing_edit)
 * [order_packing.info](#order_packing_info)
 * [order_packing.list](#order_packing_list)
 * [order_packing.delete](#order_packing_delete)
 
----

<h1 id="order_packing_create">
order_packing.create
</h1>

~~~ slim
order_packing.create (string $orderUniqueId, string $note, object|null $options)
~~~

Create a new order packing instruction.

#### Parameters

0 _string_
: Order unique ID

1 _string_
: Note

2 _object|null_
: Additional Options (see "[Order Packing](#order_packing_properties)") 
{:.code-defs.wide}

#### Return Value
 
An object with the new [Order Packing](#order_packing_properties). The "file_content" property is not returned. Use [order_packing.info](#order_packing_info) method to retrieve it.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "order_packing.create",
        [
            "100000309",
            "Place Amazon FBA Label in a pouch"
            {
                "file_name" : "amazon_fba_3425232.pdf",
                "file_content" : "base64 encoded file content",
                "print_copies" : "one_per_shipment",
                "print_target" : "LASER"
            },
        ]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "error" : null,
    "result" : {
        "packing_id" : 1,
        "order_id" : 118,
        "unique_id" : "100000309",
        "note" : "Place Amazon FBA Label in a pouch",
        "file_name" : "amazon_fba_3425232.pdf",
        "print_copies" : "one_per_shipment",
        "print_target" : "LASER"
    }
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Invalid data given. Details in error message. |
| 102 | Requested order does not exist. |

----

<h1 id="order_packing_edit">
order_packing.edit
</h1>

~~~ slim
order_packing.edit (string $packingId, string|null $note, object|null $options)
~~~

Modify the order packing instruction.

#### Parameters

0 _string|int_
: Packing ID

1 _string|null_
: Note

2 _object|null_
: Additional Options (see "[Order Packing](#order_packing_properties)") 
{:.code-defs.wide}

#### Return Value
 
An object with the updated [Order Packing](#order_packing_properties). The "file_content" property is not returned. Use [order_packing.info](#order_packing_info) method to retrieve it.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "order_packing.edit",
        [
            123,
            null,
            {
                "print_copies" : "one_per_order"
            }
        ]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "error" : null,
    "result" : {
        "packing_id" : 1,
        "order_id" : 118,
        "unique_id" : "100000309",
        "note" : "Place Amazon FBA Label in a pouch",
        "file_name" : "amazon_fba_3425232.pdf",
        "print_copies" : "one_per_order",
        "print_target" : "LASER"
    }
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Invalid data given. Details in error message. |
| 101 | Requested order packing does not exist. |

----

<h1 id="order_packing_info">
order_packing.info
</h1>

~~~ slim
order_packing.info (string $packingId, array|null $fields = [])
~~~

Retrieve full order packing information.

#### Parameters

0 _string|int_
: Packing ID

1 _array|null_
: Fields

#### Return Value

Object which contains [Order Packing](#order_packing_properties) properties. Include "file_content" to the list of the fields to return 
the "file_content" property.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "order_packing.info",
        [
            123,
            {
                "fields" : [ "file_content" ]
            }
        ]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "error" : null,
    "result" : {
        "packing_id" : 123,
        "order_id" : 118,
        "unique_id" : "100000309",
        "note" : "Place Amazon FBA Label in a pouch",
        "file_name" : "amazon_fba_3425232.pdf",
        "file_content" : "base64 encoded file content",
        "print_copies" : "one_per_order",
        "print_target" : "LASER"
    }
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Invalid data given. Details in error message. |
| 101 | Requested order packing does not exist. |

----

<h1 id="order_packing_list">
order_packing.list
</h1>

~~~ slim
order_packing.list (string $orderUniqueId, array|null $fields = [])
~~~

Create a new order packing instruction.

#### Parameters

0 _string_
: Order unique ID

1 _array|null_
: Fields

#### Return Value
 
An array of objects. Each object will contain [Order Packing](#order_packing_properties) properties. Include "file_content" to the list of the fields to return the "file_content" property.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "order_packing.list",
        [
            "100000309"
        ]
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
            "packing_id" : 1,
            "order_id" : 118,
            "unique_id" : "100000309",
            "note" : "Place Amazon FBA Label in a pouch",
            "file_name" : "amazon_fba_3425232.pdf",
            "print_copies" : "one_per_shipment",
            "print_target" : "LASER"
        },
        ...
    ]
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Invalid data given. Details in error message. |
| 102 | Requested order does not exist. |

----

<h1 id="order_packing_delete">
order_packing.delete
</h1>

~~~ slim
order_packing.delete (string $packingId)
~~~

Delete order packing.

#### Parameters

0 _string|int_
: Packing ID

#### Return Value

true if the order packing was deleted.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "order_packing.delete",
        [
            123
        ]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "error" : null,
    "result" : true
}
```
 
#### Entity Properties

 * [Order Packing](#order_packing_properties)
 
----

## Entity Properties

<h3 id="order_packing_properties">
    Order Packing Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>note</th>
        <td>
            <pre><code>{ "note" : "Place Amazon FBA Label in a pouch" }</code></pre>
            Instructions to the packer. The note is required.
        </td>
    </tr>
    <tr>
        <th>file_name</th>
        <td>
            <pre><code>{ "file_name" : "amazon_fba_3425232.pdf" }</code></pre>
            The "file_name" property.
        </td>
    </tr>
    <tr>
        <th>file_content</th>
        <td>
            <pre><code>{ "file_content" : "base64 encoded file content" }</code></pre>
            The "file_content" property. Must be base64 encoded.
        </td>
    </tr>
    <tr>
        <th>print_copies</th>
        <td>
            <pre><code>{ "print_copies" : "one_per_shipment" }</code></pre>
            The "print_copies" property. Allowed values: "one_per_order", "one_per_shipment", "one_per_package", "none".
        </td>
    </tr>
    <tr>
        <th>print_target</th>
        <td>
            <pre><code>{ "print_target" : "LASER" }</code></pre>
            The "print_target" property. Allowed values: "4X6_LABEL", "SMALL_LABEL", "LASER".
        </td>
    </tr>
</tbody>
</table>
