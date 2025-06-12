---
published: true
layout: page
title: "Custom Fields"
category: ref
parent: "Shipment"
date: 2025-05-16 16:32:07
order: 145
---

#### Methods

 * [shipment_custom_field.list](#shipment_custom_field_list)

----

#### Entity Properties

 * [Shipment Custom Field](#field_properties)
 * [Shipment Custom Field Option](#option_properties)

----

#### Additional Resources

<ul>
    <li><a href="/ref/shipment.html#shipment_custom_field" title="Shipment Custom Fields">Shipment Custom Fields</a> — when updating Shipment info.</li>
</ul>

----

<h1 id="shipment_custom_field_list">
shipment_custom_field.list
</h1>

~~~ slim
shipment_custom_field.list ()
~~~

Retrieve list of shipment custom fields available for the calling merchant.

#### Return Value

An array of objects. Each object will contain [Shipment Custom Field](#field_properties) properties.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id"      : 1234,
    "method"  : "call",
    "params"  : [
        "34aa989befe360d67fe3f70b3517a1e5",
        "shipment_custom_field.list"
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

## Entity Properties

<h3 id="field_properties">
    Shipment Custom Field Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>custom_field_id</th>
        <td>
            <pre><code>{ "custom_field_id" : 1 }</code></pre>
            An automatically generated unique identifier for an Shipment Custom Field.
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
            Flag whether Shipment Custom Field is active.
        </td>
    </tr>
    <tr>
        <th>input_type</th>
        <td>
            <pre><code>{ "input_type" : "multiselect" }</code></pre>
            The "input_type" property. Allowed values: "text", "multiline-text", "number", "currency", "select", "multiselect", "boolean", "date", "client-user", "admin-user", "email", "url".
        </td>
    </tr>
    <tr>
        <th>is_required</th>
        <td>
            <pre><code>{ "is_required" : 1 }</code></pre>
            Flag whether Shipment Custom Field is required.
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
            Flag whether Shipment Custom Field is displayed in the client grid.
        </td>
    </tr>
    <tr>
        <th>is_display_client_form</th>
        <td>
            <pre><code>{ "is_display_client_form" : 1 }</code></pre>
            Flag whether Shipment Custom Field is displayed in the client form.
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
    Shipment Custom Field Option Properties
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
