---
layout: page
title: "Third Party Billing"
category: ref
date: 2019-05-02 15:35:07
order: 36
---

#### Methods

 * [tpb_group.list](#tpb_group_list)

----

#### Entity Properties

 * [Third Party Billing Account Group](#tpb_group_properties)

----

A Third Party Billing Account Group represents a group of third party billing accounts.  Each group can have one account
per carrier/warehouse combination. Groups can be be assigned to an order using `order.options.tpb_group_id`.


<h1 id="tpb_group_list">
tpb_group.list
<code>()</code>
</h1>

Retrieve a list of Third Party Billing Groups. Use the `tpb_group_id` to instruct an order to be shipped on the appropriate
third party billing account within the group.

#### Parameters

The method is used without parameters.

#### Return Value

An array of objects. Each object will contain "<a href="#tpb_group_properties">Third Party Billing Group Properties</a>".

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "tpb_group.list",
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
            "tpb_group_id" : 73,
            "label" : "TPB Group A",
            "status" : "active"
        },
        {
            "tpb_group_id" : 74,
            "label" : "TPB Group B",
            "status" : "pending_approval"
        }
    ]
}
```

## Entity Properties

<h3 id="tpb_group_properties">
    Third Party Billing Account Group Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>tpb_group_id</th>
        <td>
            <pre><code>{ "tpb_group_id" : 71 }</code></pre>
            An automatically generated unique identifier for a Third Party Billing Account Group.
        </td>
    </tr>
    <tr>
        <th>label</th>
        <td>
            <pre><code>{ "name" : "TPB Group A" }</code></pre>
            A descriptive name to identify a Third Party Billing Account Group.
        </td>
    </tr>
    <tr>
        <th>status</th>
        <td>
            <pre><code>{ "status" : "active" }</code></pre>
            The status of the group. Possible values: <code>active</code>, <code>inactive</code>, <code>pending_approval</code> 
        </td>
    </tr>
</tbody>
</table>
