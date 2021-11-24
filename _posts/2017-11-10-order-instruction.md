---
published: true
layout: page
title: "Instructions"
category: ref
parent: "Order"
date: 2017-11-10 14:42:47
order: 90
---

#### Methods

 * [order_instruction.create](#order_instruction_create)
 * [order_instruction.edit](#order_instruction_edit)
 * [order_instruction.list](#order_instruction_list)
 * [order_instruction.delete](#order_instruction_delete)

----

<h1 id="order_instruction_create">
order_instruction.create
</h1>

~~~ slim
order_instruction.create (string $orderUniqueId, string $note, object|null $options)
~~~

Create a new order instruction.

#### Parameters

0 _string_
: Order unique ID

1 _string_
: Note

2 _object|null_
: Additional Options (see "[Order Instruction](#order_instruction_properties)")
{:.code-defs.wide}

#### Return Value

An object with the new [Order Instruction](#order_instruction_properties). The "file_content" property is not returned. Use the [order_instruction.list](#order_instruction_list) method to retrieve it.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "order_instruction.create",
        [
            "100000309",
            "Place Amazon FBA Label in a pouch",
            {
                "file_name" : "amazon_fba_3425232.pdf",
                "file_content" : "base64 encoded file content",
                "presentation" : "once_per_shipment",
                "print_target" : "LASER"
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
        "instruction_id" : 1,
        "order_id" : 118,
        "unique_id" : "100000309",
        "note" : "Place Amazon FBA Label in a pouch",
        "file_name" : "amazon_fba_3425232.pdf",
        "presentation" : "once_per_shipment",
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

<h1 id="order_instruction_edit">
order_instruction.edit
</h1>

~~~ slim
order_instruction.edit (string $instructionId, string|null $note, object|null $options)
~~~

Modify the order instruction.

#### Parameters

0 _string|int_
: Instruction ID

1 _string|null_
: Note

2 _object|null_
: Additional Options (see "[Order Instruction](#order_instruction_properties)")
{:.code-defs.wide}

#### Return Value

An object with the updated [Order Instruction](#order_instruction_properties). The "file_content" property is not returned.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "order_instruction.edit",
        [
            123,
            null,
            {
                "presentation" : "once_per_order"
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
        "instruction_id" : 1,
        "order_id" : 118,
        "unique_id" : "100000309",
        "note" : "Place Amazon FBA Label in a pouch",
        "file_name" : "amazon_fba_3425232.pdf",
        "presentation" : "once_per_order",
        "print_target" : "LASER"
    }
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Invalid data given. Details in error message. |
| 101 | Requested order instruction does not exist. |

----

<h1 id="order_instruction_list">
order_instruction.list
</h1>

~~~ slim
order_instruction.list (string $orderUniqueId, array|null $fields = [])
~~~

Create a new order instruction.

#### Parameters

0 _string_
: Order unique ID

1 _array|null_
: Fields

#### Return Value

An array of objects. Each object will contain [Order Instruction](#order_instruction_properties) properties. Include "file_content" to the list of the fields to return the "file_content" property.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "order_instruction.list",
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
            "instruction_id" : 1,
            "order_id" : 118,
            "unique_id" : "100000309",
            "note" : "Place Amazon FBA Label in a pouch",
            "file_name" : "amazon_fba_3425232.pdf",
            "presentation" : "once_per_shipment",
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

<h1 id="order_instruction_delete">
order_instruction.delete
</h1>

~~~ slim
order_instruction.delete (string $instructionId)
~~~

Delete order instruction.

#### Parameters

0 _string|int_
: Instruction ID

#### Return Value

true if the order instruction was deleted.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "order_instruction.delete",
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

 * [Order Instruction](#order_instruction_properties)

----

## Entity Properties

<h3 id="order_instruction_properties">
    Order Instruction Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>note</th>
        <td>
            <pre><code>{ "note" : "Place Amazon FBA Label in a pouch" }</code></pre>
            Instruction to the packer. The note is required.
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
        <th>presentation</th>
        <td>
            <pre><code>{ "presentation" : "once_per_shipment" }</code></pre>
            The "presentation" property. Allowed values: "once_per_order", "once_per_shipment", "once_per_package".
        </td>
    </tr>
    <tr>
        <th>print_target</th>
        <td>
            <pre><code>{ "print_target" : "LASER" }</code></pre>
            The "print_target" property. Allowed values: "LABEL", "SMALL_LABEL", "LASER".
        </td>
    </tr>
</tbody>
</table>
