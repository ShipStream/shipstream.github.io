---
published: true
layout: page
title: "Delivery Label"
category: ref
parent: "Delivery"
date: 2021-01-21 17:27:22
order: 6
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
            "carrier": "ups",
            "created_at": "2021-01-20T10:03:55+00:00",
            "updated_at": "2021-01-20T10:04:01+00:00",
            "packages": [
                {
                    "warehouse_id": "1",
                    "label_id": "8",
                    "carrier": "ups",
                    "weight": "18.000",
                    "weight_units": "POUND",
                    "dimensions": {
                        "length": "10.000",
                        "width": "11.000",
                        "height": "12.000"
                    },
                    "dimension_units": "INCH",
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
        },
        {
            "label_id": "9",
            "delivery_id": "26",
            "warehouse_id": "1",
            "status": "valid",
            "carrier": "ups",
            "created_at": "2021-01-20T10:04:23+00:00",
            "updated_at": "2021-01-20T10:04:26+00:00",
            "packages": [
                {
                    "warehouse_id": "1",
                    "label_id": "9",
                    "carrier": "ups",
                    "weight": "27.000",
                    "weight_units": "POUND",
                    "dimensions": {
                        "length": "10.000",
                        "width": "11.000",
                        "height": "12.000"
                    },
                    "dimension_units": "INCH",
                    "tracking": [
                        {
                            "number": "1Z49R7V89021837511",
                            "description": "UPS Ground"
                        }
                    ],
                    "package_items": [
                        {
                            "delivery_item_id": 2,
                            "sku": "O-VS-Oregano-p3",
                            "quantity": "6.000"
                        },
                        {
                            "delivery_item_id": 3,
                            "sku": "O-VS-Mint-p2",
                            "quantity": "6.000"
                        },
                        {
                            "delivery_item_id": 5,
                            "sku": "VS-Bags-p1",
                            "quantity": "6.000"
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
                "carrier": "ups",
                "created_at": "2021-01-18T13:57:25+00:00",
                "updated_at": "2021-01-18T13:57:29+00:00",
                "packages": [
                    {
                        "warehouse_id": "1",
                        "label_id": "2",
                        "carrier": "ups",
                        "weight": "45.000",
                        "weight_units": "POUND",
                        "dimensions": {
                            "length": "10.000",
                            "width": "11.000",
                            "height": "12.000"
                        },
                        "dimension_units": "INCH",
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
        <th>carrier</th>
        <td>
            <pre><code>{ "carrier" : "ups" }</code></pre>
            Carrier code.
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
            Array of delivery label packages. See "<a href="#delivery_label_package_properties">Delivery Label Package Properties</a>".
        </td>
    </tr>
    <tr>
        <th>destination_address</th>
        <td>
            Destination Address. See "<a href="#delivery_label_address_properties">Delivery Label Address Properties</a>".
        </td>
    </tr>
    <tr>
        <th>origin_address</th>
        <td>
            Origination Address. See "<a href="#delivery_label_address_properties">Delivery Label Address Properties</a>".
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
    <th>weight_units</th>
        <td>
            <pre><code>{ "weight_units" : "POUND" }</code></pre>
            The unit of measure used for weight.
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
        <th>dimension_units</th>
        <td>
            <pre><code>{ "dimension_units" : "INCH" }</code></pre>
            The unit of measure used for dimensional measurement.
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
        The "Classification" property. Allowed: "res" - residential, "com" - commercial, "unk" - unknown.
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