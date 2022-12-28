---
published: true
layout: page
title: "Custom Fields"
category: ref
parent: "Order"
date: 2022-12-15 12:22:45
order: 95
---

#### Methods

 * [order_custom_field.info](#order_custom_field_info)
 * [order_custom_field.list](#order_custom_field_list)
 * [order_custom_field.create](#order_custom_field_create)
 * [order_custom_field.update](#order_custom_field_update)
 * [order_custom_field.delete](#order_custom_field_delete)

----

#### Entity Properties

 * [Order Custom Field](#field_properties)
 * [Order Custom Field Option](#option_properties)

----

<h1 id="order_custom_field_info">
order_custom_field.info
</h1>

~~~ slim
order_custom_field.info (int $customFieldId)
~~~

Retrieve full order custom field information.

#### Parameters

0 _int_
: Order Custom Field ID
{:.code-defs.wide}

#### Return Value

An object with [Order Custom Field](#field_properties).

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id"      : 1234,
    "method"  : "call",
    "params"  : [
        "27a5c429525a85c9e02c91537874808e",
        "order_custom_field.info",
        [
            23
        ]
    ]
}
```

#### Example Response

```json
{
    "result": {
        "custom_field_id": "23",
        "name": "Colors",
        "code": "colors",
        "is_active": "1",
        "input_type": "multiselect",
        "is_required": "0",
        "client_note": null,
        "client_permissions": "unrestricted",
        "is_display_client_grid": "0",
        "is_display_client_form": "0",
        "sort_order": "0",
        "created_at": "2022-12-14T17:07:31+00:00",
        "updated_at": "2022-12-14T17:07:31+00:00",
        "options": [
            {
                "option_id": 12,
                "label": "Red",
                "is_default": false,
                "sort_order": 5
            }
        ]
    },
    "id": "1234",
    "jsonrpc": "2.0"
}
```

----

#### Error Codes

| code | message |
|------| ------- |
| 101    | Requested order custom field does not exist. |

----

<h1 id="order_custom_field_list">
order_custom_field.list
</h1>

~~~ slim
order_custom_field.list ()
~~~

Retrieve list of order custom fields.

#### Return Value

An array of objects. Each object will contain [Order Custom Field](#field_properties) properties.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id"      : 1234,
    "method"  : "call",
    "params"  : [
        "34aa989befe360d67fe3f70b3517a1e5",
        "order_custom_field.list"
    ]
}
```

#### Example Response

```json
{
    "result": [
        {
            "custom_field_id": "3",
            "name": "Original Purchase Date",
            "code": "purchase_date",
            "is_active": "1",
            "input_type": "date",
            "is_required": "0",
            "client_note": null,
            "client_permissions": "restricted",
            "is_display_client_grid": "1",
            "is_display_client_form": "0",
            "sort_order": "0",
            "created_at": "2022-07-01T10:46:16+00:00",
            "updated_at": "2022-07-01T10:46:16+00:00"
        },
        {
            "custom_field_id": "4",
            "name": "Main Item SKU",
            "code": "main_sku",
            "is_active": "1",
            "input_type": "text",
            "is_required": "0",
            "client_note": null,
            "client_permissions": "unrestricted",
            "is_display_client_grid": "0",
            "is_display_client_form": "1",
            "sort_order": "99",
            "created_at": "2022-07-01T11:43:28+00:00",
            "updated_at": "2022-07-01T11:43:28+00:00"
        }
    ],
    "id": "1234",
    "jsonrpc": "2.0"
}
```

----

<h1 id="order_custom_field_create">
order_custom_field.create
</h1>

~~~ slim
order_custom_field.create (object $data)
~~~

Create a new order custom field.

#### Parameters

0 _object_
: Order Custom Field data (see "[Order Custom Field](#field_properties)")
{:.code-defs.wide}

#### Return Value

An object with the new [Order Custom Field](#field_properties)").

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id"      : 1234,
    "method"  : "call",
    "params"  : [
        "27a5c429525a85c9e02c91537874808e",
        "order_custom_field.create",
        [
            {
                "name": "Colors",
                "code": "colors",
                "is_active": 1,
                "input_type" : "multiselect",
                "client_permissions" : "unrestricted",
                "is_display_client_grid": 1,
                "is_display_client_form": 1,
                "options" : 
                [
                    {
                        "label" : "Red",
                        "is_default": 0,
                        "sort_order": 5
                    }
                ]
            }
        ]    
    ]
}
```

#### Example Response

```json
{
    "result": {
        "custom_field_id": "30",
        "name": "Colors",
        "code": "colors",
        "is_active": "1",
        "input_type": "multiselect",
        "is_required": "0",
        "client_note": null,
        "client_permissions": "unrestricted",
        "is_display_client_grid": "1",
        "is_display_client_form": "1",
        "sort_order": "0",
        "created_at": "2022-12-15T16:57:15+00:00",
        "updated_at": "2022-12-15T16:57:15+00:00",
        "options": [
            {
                "option_id": 18,
                "label": "Red",
                "is_default": false,
                "sort_order": 5
            }
        ]
    },
    "id": "1234",
    "jsonrpc": "2.0"
}
```

----

#### Error Codes

| code | message |
|------| ------- |
| 100  | Invalid data given. Details in error message. |

----

<h1 id="order_custom_field_update">
order_custom_field.update
</h1>

~~~ slim
order_custom_field.update (string $customFieldId, object $data)
~~~

Modify the order custom field.

#### Parameters

0 _int_
: Custom Field ID

1 _object|null_
: Order Custom Field data (see "[Order Custom Field](#field_properties)")
{:.code-defs.wide}

#### Return Value

true if order custom field was successfully updated.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id"      : 1234,
    "method"  : "call",
    "params"  : [
        "27a5c429525a85c9e02c91537874808e",
        "order_custom_field.update",
        [
            23,
            {
                "name": "Colors"
            }
        ]    
    ]
}
```

#### Example Response

```json
{
    "result": true,
    "id": "1234",
    "jsonrpc": "2.0"
}
```

----

#### Error Codes

| code | message |
|------| ------- |
| 100  | Invalid data given. Details in error message. |
| 101  | Requested order custom field does not exist. |

----

<h1 id="order_custom_field_delete">
order_custom_field.delete
</h1>

~~~ slim
order_custom_field.delete (int $customFieldId)
~~~

Delete order custom field.

#### Parameters

0 _int_
: Custom Field ID

#### Return Value

true if the order custom field was deleted.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id"      : 1234,
    "method"  : "call",
    "params"  : [
        "27a5c429525a85c9e02c91537874808e",
        "order_custom_field.delete",
        [
            25
        ]
    ]
}
```

#### Example Response

```json
{
    "result": true,
    "id": "1234",
    "jsonrpc": "2.0"
}
```

----

#### Error Codes

| code | message |
|------| ------- |
| 100  | Invalid data given. Details in error message. |

----

## Entity Properties

<h3 id="field_properties">
    Order Custom Field Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>custom_field_id</th>
        <td>
            <pre><code>{ "custom_field_id" : 1 }</code></pre>
            An automatically generated unique identifier for an Order Custom Field.
        </td>
    </tr>
    <tr>
        <th>name</th>
        <td>
            <pre><code>{ "name" : "Main Item SKU" }</code></pre>
            The "name" property.
        </td>
    </tr>
    <tr>
        <th>code</th>
        <td>
            <pre><code>{ "code" : "main_sku" }</code></pre>
            The "code" property.
        </td>
    </tr>
    <tr>
        <th>is_active</th>
        <td>
            <pre><code>{ "is_active" : 1 }</code></pre>
            Flag whether Order Custom Field is active.
        </td>
    </tr>
    <tr>
        <th>input_type</th>
        <td>
            <pre><code>{ "input_type" : "multiselect" }</code></pre>
            The "input_type" property. Allowed values: "text", "multiline-text", "number", "currency", "select", "multiselect", "boolean", "date", "client-user", "email", "url".
        </td>
    </tr>
    <tr>
        <th>is_required</th>
        <td>
            <pre><code>{ "is_required" : 1 }</code></pre>
            Flag whether Order Custom Field is required.
        </td>
    </tr>
    <tr>
        <th>client_note</th>
        <td>
            <pre><code>{ "client_note" : "Warranty Claim Reason" }</code></pre>
            The "client_note" property.
        </td>
    </tr>
    <tr>
        <th>client_permissions</th>
        <td>
            <pre><code>{ "client_permissions" : "unrestricted" }</code></pre>
            The "unrestricted" property. Allowed values: "unrestricted", "restricted", "read-only", "hidden".
        </td>
    </tr>
    <tr>
        <th>is_display_client_grid</th>
        <td>
            <pre><code>{ "is_display_client_grid" : 1 }</code></pre>
            Flag whether Order Custom Field is displayed in the client grid.
        </td>
    </tr>
    <tr>
        <th>is_display_client_form</th>
        <td>
            <pre><code>{ "is_display_client_form" : 1 }</code></pre>
            Flag whether Order Custom Field is displayed in the client form.
        </td>
    </tr>
    <tr>
        <th>sort_order</th>
        <td>
            <pre><code>{ "sort_order" : 0 }</code></pre>
            The "sort_order" property.
        </td>
    </tr>
    <tr>
        <th>created_at</th>
        <td>
            <pre><code>{ "created_at" : "2022-12-15T13:47:47+00:00" }</code></pre>
            The "Created At" property.
        </td>
    </tr>
    <tr>
        <th>updated_at</th>
        <td>
            <pre><code>{ "updated_at" : "2022-12-15T13:47:47+00:00" }</code></pre>
            The "Updated At" property.
        </td>
    </tr>
    <tr>
        <th>options</th>
        <td>
            Array of options. See "<a href="#option_properties">Option Properties</a>".
        </td>
    </tr>
</tbody>
</table>

<h3 id="option_properties">
    Order Custom Field Option Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>option_id</th>
        <td>
            <pre><code>{ "option_id" : 2 }</code></pre>
            The internal option ID.
        </td>
    </tr>
    <tr>
        <th>label</th>
        <td>
            <pre><code>{ "label" : "Red" }</code></pre>
            The "Label" property.
        </td>
    </tr>
    <tr>
        <th>is_default</th>
        <td>
            <pre><code>{ "is_default" : 1 }</code></pre>
            Flag whether option is default.
        </td>
    </tr>
    <tr>
        <th>sort_order</th>
        <td>
            <pre><code>{ "sort_order" : 5 }</code></pre>
            The "Sort Order" property.
        </td>
    </tr>
</tbody>
</table>