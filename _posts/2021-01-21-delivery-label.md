---
published: true
layout: page
title: "Delivery Label"
category: ref
parent: "Delivery"
date: 2021-01-21 17:27:22
order: 30
---

#### Methods

 * [delivery_label.info](#delivery_label_info)
 * [delivery_label.search](#delivery_label_search)
 * [delivery_label.create](#delivery_label_create)
 * [delivery_label.void](#delivery_label_void)

----

#### Entity Properties

* [Delivery Label](#delivery_label_properties)
* [Delivery Label Package](#delivery_label_package_properties)
* [Delivery Label Address](#delivery_label_address_properties)

---

<h1 id="delivery_label_info">
delivery_label.info
<code>(int $labelId, array $fields = [])</code>
</h1>

Retrieve delivery label information.

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>Delivery label internal id</td>
    </tr>
    <tr>
        <td>1</td>
        <td><ul>
        <li>null - Basic label data.</li>
        <li>array - Array of fields. Allowed: "packages", "destination_address", "origin_address"</li>
        </ul></td>
    </tr>
</tbody>
</table>

#### Return Value

An object with <a href="#delivery_label_properties">Delivery Label Properties</a>.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "12e6f7398eb7a992219477aaa771725d",
        "delivery_label.info",
        [
            "2",
            [
                "packages",
                "destination_address",
                "origin_address"
            ]
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
    "result": [
        {
            "label_id": "8",
            "delivery_id": "26",
            "warehouse_id": "1",
            "status": "valid",
            "shipping_method": "ups_03",
            "created_at": "2021-01-20T10:03:55+00:00",
            "updated_at": "2021-01-20T10:04:01+00:00",
            "packages": [
                {
                    "warehouse_id": "1",
                    "label_id": "8",
                    "carrier": "ups",
                    "weight": "18.000",
                    "weight_unit": "lb",
                    "dimensions": {
                        "length": "10.000",
                        "width": "11.000",
                        "height": "12.000"
                    },
                    "dimension_unit": "in",
                    "tracking": [
                        {
                            "number": "1Z49R7V89024431506",
                            "description": "UPS Ground"
                        }
                    ],
                    "package_items": [
                        {
                            "delivery_item_id": 2,
                            "sku": "O-VS-Oregano-p3",
                            "quantity": "4.000"
                        },
                        {
                            "delivery_item_id": 3,
                            "sku": "O-VS-Mint-p2",
                            "quantity": "4.000"
                        },
                        {
                            "delivery_item_id": 5,
                            "sku": "VS-Bags-p1",
                            "quantity": "4.000"
                        }
                    ]
                }
            ],
            "destination_address": {
                "region": "New York",
                "postcode": "13088",
                "lastname": "Marquez",
                "street": "4616 Crossroads Park Dr",
                "city": "Liverpool",
                "email": null,
                "telephone": "865-971-4663",
                "firstname": "Sherlock",
                "company": null,
                "classification": "com",
                "is_valid": null,
                "country": "US"
            },
            "origin_address": {
                "region": "New York",
                "postcode": "10036",
                "lastname": "Gates",
                "street": "11 Times Square",
                "city": "New York",
                "email": null,
                "telephone": "212.245.2100",
                "firstname": "Bill",
                "company": "Microsoft",
                "classification": null,
                "is_valid": null,
                "country": "US"
            }
        }
    ]
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Requested delivery label does not exist. |

---

<h1 id="delivery_label_search">
delivery_label.search
<code>(object|null $filters = [], array|null $options = [], array|null $fields = [])</code>
</h1>

An array of objects. Each object will contain <a href="#delivery_label_properties">Delivery Label Properties</a>.

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td><ul>
        <li>null - Retrieve list of all delivery labels.</li>
        <li>object - Retrieve list of delivery labels using specified <a href="/doc/search-filters.html" title="Search Filters">filters</a>.</li>
        </ul></td>
    </tr>
    <tr>
        <td>1</td>
        <td><ul>
        <li>null - No options will be applied.</li>
        <li>object - Apply specified <a href="/doc/search-options.html" title="Search Options">options</a>.</li>
        </ul></td>
    </tr>
    <tr>
        <td>2</td>
        <td><ul>
        <li>null - Basic label data.</li>
        <li>array - Array of fields. Allowed: "packages", "destination_address", "origin_address"</li>
        </ul></td>
    </tr>
</tbody>
</table>

#### Return Value

An array of objects. Each object will contain "<a href="#delivery_label_properties">Delivery Label Properties</a>".

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "12e6f7398eb7a992219477aaa771725d",
        "delivery_label.search",
        [
            { "label_id": { "eq" : "2" } },
            {
                "limit": 100,
                "page": 1
            },
            [
                "packages",
                "destination_address",
                "origin_address"
            ]
        ]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "result": {
        "results": [
            {
                "label_id": "2",
                "delivery_id": "22",
                "warehouse_id": "1",
                "status": "valid",
                "shipping_method": "ups_03",
                "created_at": "2021-01-18T13:57:25+00:00",
                "updated_at": "2021-01-18T13:57:29+00:00",
                "packages": [
                    {
                        "warehouse_id": "1",
                        "label_id": "2",
                        "carrier": "ups",
                        "weight": "45.000",
                        "weight_unit": "lb",
                        "dimensions": {
                            "length": "10.000",
                            "width": "11.000",
                            "height": "12.000"
                        },
                        "dimension_unit": "in",
                        "tracking": [
                            {
                                "number": "1Z49R7V89024877071",
                                "description": "UPS Ground"
                            }
                        ],
                        "package_items": [
                            {
                                "delivery_item_id": "68",
                                "sku": "O-VS-Oregano-p3",
                                "quantity": "10.000"
                            },
                            {
                                "delivery_item_id": "69",
                                "sku": "O-VS-Mint-p2",
                                "quantity": "10.000"
                            },
                            {
                                "delivery_item_id": "70",
                                "sku": "VS-Bags-p1",
                                "quantity": "10.000"
                            }
                        ]
                    }
                ],
                "destination_address": {
                    "region": "New York",
                    "postcode": "13088",
                    "lastname": "Marquez",
                    "street": "4616 Crossroads Park Dr",
                    "city": "Liverpool",
                    "email": null,
                    "telephone": "865-971-4663",
                    "firstname": "Sherlock",
                    "company": null,
                    "classification": "com",
                    "is_valid": null,
                    "country": "US"
                },
                "origin_address": {
                    "region": "New York",
                    "postcode": "10036",
                    "lastname": "Gates",
                    "street": "11 Times Square",
                    "city": "New York",
                    "email": null,
                    "telephone": "212.245.2100",
                    "firstname": "Bill",
                    "company": "Microsoft",
                    "classification": null,
                    "is_valid": null,
                    "country": "US"
                }
            }
        ],
        "totalCount": 1,
        "numPages": 1
    }
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 101 | Invalid filters given. Details in error message. |

---

<h1 id="delivery_label_create">
delivery_label.create
<code>(string $deliveryId, object $address, array $packages, object $options)</code>
</h1>

Create a new delivery label.

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>Delivery internal id</td>
    </tr>
    <tr>
        <td>1</td>
        <td>Destination Address. See <a href="#delivery_label_address_properties">Delivery Label Address Properties</a>.</td>
    </tr>
    <tr>
        <td>2</td>
        <td>Array of delivery label packages. See <a href="#delivery_label_package_properties">Delivery Label Package Properties</a>.</td>
    </tr>
    <tr>
        <td>3</td>
        <td>Options. See <a href="#delivery_label_options">Delivery Label Options</a>.</td>
    </tr>
</tbody>
</table>

#### Return Value

An object with <a href="#delivery_label_properties">Delivery Label Properties</a>.

#### Example Request

```json
{
    "jsonrpc":2.0,
    "id":1234,
    "method":"call",
    "params":[
        "12e6f7398eb7a992219477aaa771725d",
        "delivery_label.create",
        [
            "11000022",
            {
                "firstname" : "Bill",
                "lastname" : "Gates",
                "company" : "Microsoft",
                "street" : "11 Times Square",
                "city" : "New York",
                "region" : "NY",
                "postcode" : "10036",
                "country" : "US",
                "telephone" : "212.245.2100"
            },
            [
                {
                    "weight": "45.000",
                    "weight_unit": "lb",
                    "dimensions": {
                        "length": "10.000",
                        "width": "11.000",
                        "height": "12.000"
                    },
                    "dimension_unit": "in",
                    "package_items": [
                        {
                            "sku": "O-VS-Oregano-p3",
                            "quantity": "10.000"
                        },
                        {
                            "sku": "O-VS-Mint-p2",
                            "quantity": "10.000"
                        },
                        {
                            "sku": "VS-Bags-p1",
                            "quantity": "10.000"
                        }
                    ]
                }
            ],
            {
                "shipping_method":"ups_03",
                "return_service_type":"print_or_download"
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
    "result": [
        {
            "label_id": "10",
            "delivery_id": "27",
            "warehouse_id": "1",
            "status": "valid",
            "shipping_method": "ups_03",
            "created_at": "2021-01-22T13:45:17+00:00",
            "updated_at": "2021-01-22T13:45:28+00:00",
            "packages": [
                {
                    "warehouse_id": "1",
                    "label_id": "10",
                    "carrier": "ups",
                    "weight": 45,
                    "weight_unit": "lb",
                    "dimensions": {
                        "length": 10,
                        "width": 11,
                        "height": 12
                    },
                    "dimension_unit": "in",
                    "tracking": [
                        {
                            "number": "1Z49R7V89013598741",
                            "description": "UPS Ground"
                        }
                    ],
                    "package_items": [
                        {
                            "delivery_item_id": "81",
                            "sku": "O-VS-Oregano-p3",
                            "quantity": 10
                        },
                        {
                            "delivery_item_id": "82",
                            "sku": "O-VS-Mint-p2",
                            "quantity": 10
                        },
                        {
                            "delivery_item_id": "83",
                            "sku": "VS-Bags-p1",
                            "quantity": 10
                        }
                    ]
                }
            ],
            "destination_address": {
                "firstname": "Sherlock",
                "lastname": "Marquez",
                "telephone": "865-971-4663",
                "street": "4616 Crossroads Park Dr",
                "city": "Liverpool",
                "postcode": "13088",
                "classification": "com",
                "region": "New York",
                "country": "US"
            },
            "origin_address": {
                "firstname": "Bill",
                "lastname": "Gates",
                "company": "Microsoft",
                "street": "11 Times Square",
                "city": "New York",
                "region": "New York",
                "postcode": "10036",
                "telephone": "212.245.2100",
                "email": null,
                "classification": null,
                "is_valid": null,
                "country": "US"
            }
        }
    ]
}
```

----

#### Error Codes

| code | message |
|------| ------- |
| 100  | Requested delivery label does not exist. |
| 101  | Invalid filters given. Details in error message. | 
| 102  | Invalid data given. Details in error message. |
| 103  | Cannot void the delivery label. Details in error message. |
| 104  | An unexpected error occurred while creating the delivery label. |
| 105  | Requested delivery does not exist. |

---

<h1 id="delivery_label_void">
delivery_label.void
<code>(int $labelId)</code>
</h1>

Void delivery label.

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>Delivery label internal id</td>
    </tr>
</tbody>
</table>

#### Return Value

<code>true</code> if the Delivery Label was voided.

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "12e6f7398eb7a992219477aaa771725d",
        "delivery_label.void",
        [
            "8"
        ]
    ]
}
```

#### Example Response

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "result": true
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 103 | Cannot void the delivery label. Details in error message. |


<h3 id="delivery_label_properties">
    Delivery Label Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>label_id</th>
        <td>
            <pre><code>{ "label_id" : 2 }</code></pre>
            The internal delivery label ID.
        </td>
    </tr>
    <tr>
        <th>delivery_id</th>
        <td>
            <pre><code>{ "delivery_id" : 22 }</code></pre>
            The internal delivery ID.
        </td>
    </tr>
    <tr>
        <th>warehouse_id</th>
        <td>
            <pre><code>{ "warehouse_id" : 1 }</code></pre>
            The internal warehouse ID.
        </td>
    </tr>
    <tr>
        <th>status</th>
        <td>
            <pre><code>{ "status" : "valid" }</code></pre>
            The "Status" property. Allowed: "valid", "void".
        </td>
    </tr>
    <tr>
        <th>shipping_method</th>
        <td>
            <pre><code>{ "shipping_method" : "ups_03" }</code></pre>
            See the <a href="/doc/shipping-methods.html">Shipping Methods</a> document for a reference. Is not optional.
        </td>
    </tr>
    <tr>
        <th>created_at</th>
        <td>
            <pre><code>{ "created_at" : "2021-01-18T13:57:25+00:00" }</code></pre>
            The "Created At" property in ISO 8601 format.
        </td>
    </tr>
    <tr>
        <th>updated_at</th>
        <td>
            <pre><code>{ "updated_at" : "2021-01-18T13:57:25+00:00" }</code></pre>
            The "Updated At" property in ISO 8601 format.
        </td>
    </tr>
    <tr>
        <th>packages</th>
        <td>
            Array of delivery label packages. See <a href="#delivery_label_package_properties">Delivery Label Package Properties</a>.
        </td>
    </tr>
    <tr>
        <th>destination_address</th>
        <td>
            Destination Address. See <a href="#delivery_label_address_properties">Delivery Label Address Properties</a>.
        </td>
    </tr>
    <tr>
        <th>origin_address</th>
        <td>
            Origination Address. See <a href="#delivery_label_address_properties">Delivery Label Address Properties</a>.
        </td>
    </tr>
</tbody>
</table>

<h3 id="delivery_label_package_properties">
    Delivery Label Package Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>warehouse_id</th>
        <td>
            <pre><code>{ "warehouse_id" : "1" }</code></pre>
            The ID of the warehouse associated with the package.
        </td>
    </tr>
    <tr>
        <th>label_id</th>
        <td>
            <pre><code>{ "label_id" : 2 }</code></pre>
            The internal delivery label ID.
        </td>
    </tr>
    <tr>
        <th>carrier</th>
        <td>
            <pre><code>{ "carrier" : "ups" }</code></pre>
            Carrier code.
        </td>
    </tr>
    <tr>
        <th>weight</th>
        <td>
            <pre><code>{ "weight" : "16.900" }</code></pre>
            The weight of the package.
        </td>
    </tr>
    <tr>
    <th>weight_unit</th>
        <td>
            <pre><code>{ "weight_unit" : "lb" }</code></pre>
            The unit of measure used for <code>weight</code>. See: <a href="/doc/units-of-measure.html#weight" title="Weight Units">Weight Units</a>.
        </td>
    </tr>
    <tr>
        <th>dimensions</th>
        <td>
            <pre><code>{
    "dimensions" : {
        "length": "16.000",
        "width": "12.000",
        "height": "8.000"
    }
}</code></pre>
            The <code>length</code>, <code>width</code>, and <code>height</code> of the package.
        </td>
    </tr>
    <tr>
        <th>dimension_unit</th>
        <td>
            <pre><code>{ "dimension_unit" : "in" }</code></pre>
            The unit of measure used for <code>length</code>, <code>width</code>, and <code>height</code> in <code>dimensions</code>. 
            See: <a href="/doc/units-of-measure.html#length" title="Length Units">Length Units</a>.
        </td>
    </tr>
    <tr>
        <th>tracking</th>
        <td>
            <pre><code>[
    {
        "number" : "1Z49R7V80308849438",
        "description" : "UPS Ground"
    }, {
        "number" : "1Z49R7V29475663003",
        "description" : "UPS Ground"
    }
]</code></pre>
            An array of tracking objects.<br>
            The "number" property contains the tracking number.<br>
            The "description" property contains the shipping method name.
        </td>
    </tr>
    <tr>
        <th>package_items</th>
        <td>
            <pre><code>[
    {
        "delivery_item_id": 1,
        "sku": "product1",
        "quantity": "2.0000"
    }, {
        "delivery_item_id": 3,
        "sku": "product2",
        "quantity": "2.0000"
    }
]</code></pre>
            An array of items contained in the package.
<pre><code>"delivery_item_id" is the unqiue identifier of the related delivery item.
"sku" is the package item's SKU.
"quantity" is the quantity of the item in the package.
</code></pre>
        </td>
    </tr>
</tbody>
</table>

<h3 id="delivery_label_address_properties">
    Delivery Label Address Properties
</h3>

<table class="table-striped">
<tbody>
<tr>
    <th>firstname</th>
    <td>
        <pre><code>{ "firstname" : "Gates" }</code></pre>
        The "First Name" property.
    </td>
</tr>
<tr>
    <th>lastname</th>
    <td>
        <pre><code>{ "lastname" : "Bill" }</code></pre>
        The "Last Name" property.
    </td>
</tr>
<tr>
    <th>company</th>
    <td>
        <pre><code>{ "company" : "Microsoft" }</code></pre>
        The "Company" property.
    </td>
</tr>
<tr>
    <th>street</th>
    <td>
        <pre><code>{ "street" : "11 Times Square\nc/oSteve Ballmer" }</code></pre>
        The street address. Multi-line street addresses will be separated by a newline ("\n") character. Only two address lines are supported.
    </td>
</tr>
<tr>
    <th>city</th>
    <td>
        <pre><code>{ "city" : "New York" }</code></pre>
        The "City" property.
    </td>
</tr>
<tr>
    <th>region</th>
    <td>
        <pre><code>{ "region" : "NY" }</code></pre>
        The "Region" property.
    </td>
</tr>
<tr>
    <th>postcode</th>
    <td>
        <pre><code>{ "postcode" : "10036" }</code></pre>
        The "Postal Code" property. Pass as a string to prevent leading 0s from being dropped.
    </td>
</tr>
<tr>
    <th>country</th>
    <td>
        <pre><code>{ "country" : "US" }</code></pre>
        The "Country" property.
    </td>
</tr>
<tr>
    <th>classification</th>
    <td>
        <pre><code>{ "classification" : "com" }</code></pre>
        The "Classification" property. Allowed: "res" - residential, "com" - commercial, "po" - post office, "mil" - military, "unk" - unknown.
    </td>
</tr>
<tr>
    <th>is_valid</th>
    <td>
        <pre><code>{ "is_valid" : 1 }</code></pre>
        Flag whether address is valid.
    </td>
</tr>
<tr>
    <th>telephone</th>
    <td>
        <pre><code>{ "telephone" : "212.245.2100" }</code></pre>
        The "Telephone" property.
    </td>
</tr>
<tr>
    <th>email</th>
    <td>
        <pre><code>{ "email" : "customer@example.com" }</code></pre>
        The "Email" property.
    </td>
</tr>
</tbody>
</table>

<h3 id="delivery_label_options">
    Delivery Label Options
</h3>

<table class="table-striped">
<tbody>
<tr>
    <th>shipping_method</th>
    <td>
        <pre><code>{ "shipping_method" : "ups_03" }</code></pre>
        See the <a href="/doc/shipping-methods.html">Shipping Methods</a> document for a reference. Is not optional.
    </td>
</tr>
<tr>
    <th>return_service_type</th>
    <td>
        <pre><code>{ "return_service_type" : "print_or_download" }</code></pre>
        The "Return Service Type" property. Allowed: "print_or_download", "email_label".
    </td>
</tr>
<tr>
    <th>copy_email_to</th>
    <td>
        <pre><code>{ "copy_email_to" : "customer@example.com" }</code></pre>
        The "Copy Email To" property. Comma separated emails. Only applicable to "email_label" Return Service Type.
    </td>
</tr>
<tr>
    <th>email_message</th>
    <td>
        <pre><code>{ "email_message" : "Email message here." }</code></pre>
        The "Email Notification Message" property. Only applicable to "email_label" Return Service Type.
    </td>
</tr>
<tr>
    <th>saturday_pickup</th>
    <td>
        <pre><code>{ "saturday_pickup" : 1 }</code></pre>
        The "Saturday Pickup" property.
    </td>
</tr>
<tr>
    <th>tpb_group_id</th>
    <td>
        <pre><code>{ "tpb_group_id" : 11 }</code></pre>
        The ID number of a <a href="/ref/third-party-billing-group.html">Third Party Billing Account Group</a>. If unset or <code>null</code>, and a default group is configured, the default group will be used.  Set to <code>0</code> to disable third party billing.
    </td>
</tr>
</tbody>
</table>
