---
layout: page
title: "Package"
category: ref
parent: "Shipment"
date: 2016-05-10 19:22:01
order: 27
---

#### Methods

 * [package.search](#package_search)
 
----

#### Entity Properties

 * [Package](#package_properties)

----

There may be multiple packages for one shipment. Each package may have multiple tracking numbers, most packages will have only one tracking number.

----

<h1 id="package_search">
package.search
<code>(null|object $filters, array $options = [], null|string|object $fields = [])</code>
</h1>

Retrieve list of packages by filters. Package data can be customized by specifying properties to retrieve.

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td><ul>
        <li>null - Retrieve list of all packages.</li>
        <li>object - Retrieve list of packages using specified <a href="/doc/search-filters.html" title="Search Filters">filters</a>.</li>
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
        <td>
            <ul>
                <li>null - Retrieve "shipment_id", "order_unique_id" and "order_ref".</li>
                <li>string '*' - Retrieve all properties excluding "items" and "tracking_numbers".</li>
                <li>object - List of properties to retrieve in addition to "shipment_id", "order_unique_id" and "order_ref". List may include '*'.</li>
            </ul>
            <p>
            See "<a href="#package_properties">Package Properties</a>". Example:
            <code>['*', 'package_status']</code>
            </p>
        </td>
    </tr>
</tbody>
</table>

## Entity Properties

<h3 id="package_properties">
    Package Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>package_id</th>
        <td>
            <pre><code>{ "package_id" : "123" }</code></pre>
            The internal package ID.
        </td>
    </tr>
    <tr>
        <th>shipment_id</th>
        <td>
            <pre><code>{ "shipment_id" : "100000005" }</code></pre>
            The "Shipment ID" property. This number may appear on the packing slip as the "Packing Slip #".
        </td>
    </tr>
    <tr>
        <th>order_unique_id</th>
        <td>
            <pre><code>{ "order_unique_id" : "100000010" }</code></pre>
            The "unique_id" property for the order associated with this shipment.
        </td>
    </tr>
    <tr>
        <th>order_ref</th>
        <td>
            <pre><code>{ "order_ref" : "ABC-54321" }</code></pre>
            The user-specified order "order_ref" field.
        </td>
    </tr>
    <tr>
        <th>package_status</th>
        <td>
            <pre><code>{ "package_status" : "not_on_manifest" }</code></pre>
            The "Status" property. Allowed values: not_on_manifest, on_manifest, on_truck.
        </td>
    </tr>
    <tr>
        <th>updated_at</th>
        <td>
            <pre><code>{ "updated_at" : "2016-05-11 18:51:18" }</code></pre>
            The "Updated At" property.
        </td>
    </tr>
    <tr>
        <th>items</th>
        <td>
            Array of <a href="#package_item_properties">Package Item</a> objects.
        </td>
    </tr>
    <tr>
        <th>tracking_numbers</th>
        <td>
            Array of <a href="#track_properties">Shipment Track</a> objects.
        </td>
    </tr>
</tbody>
</table>

<h3 id="package_item_properties">
    Package Item Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>sku</th>
        <td>
            <pre><code>{ "sku" : "product1" }</code></pre>
            The "SKU" property.
        </td>
    </tr>
    <tr>
        <th>name</th>
        <td>
            <pre><code>{ "name" : "product1" }</code></pre>
            The "Name" property.
        </td>
    </tr>
    <tr>
        <th>weight</th>
        <td>
            <pre><code>{ "weight" : 12 }</code></pre>
            The "Weight" property.
        </td>
    </tr>
    <tr>
        <th>weight_units</th>
        <td>
            <pre><code>{ "weight_units" : "POUND" }</code></pre>
            The "Weight Units" property. See: <a href="/doc/units-of-measure.html#weight" title="Weight Units">Weight Units</a>.
        </td>
    </tr>
    <tr>
        <th>qty</th>
        <td>
            <pre><code>{ "qty" : 1 }</code></pre>
            The "Quantity" property.
        </td>
    </tr>
    <tr>
        <th>order_item_id</th>
        <td>
            <pre><code>{ "order_item_id" : 2 }</code></pre>
            The internal order item ID.
        </td>
    </tr>
    <tr>
        <th>package_data</th>
        <td>
<pre><code>[
    {"label" : "Serial Number - 8 Characters", "value" : "55285368"},
    {"label" : "Serial Number - 8 Characters", "value" : "55285368"}
]</code></pre>
            The "Package Data" property.
        </td>
    </tr>
</tbody>
</table>

<h3 id="track_properties">
    Shipment Track Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>track_id</th>
        <td>
            <pre><code>{ "track_id" : 1 }</code></pre>
            The internal track ID.
        </td>
    </tr>
    <tr>
        <th>carrier</th>
        <td>
            <pre><code>{ "carrier" : "fedex" }</code></pre>
            The carrier code.
        </td>
    </tr>
    <tr>
        <th>carrier_name</th>
        <td>
            <pre><code>{ "carrier_name" : "Federal Express" }</code></pre>
            The carrier name.
        </td>
    </tr>
    <tr>
        <th>description</th>
        <td>
            <pre><code>{ "description" : "Express Saver" }</code></pre>
            The method description (without the carrier name).
        </td>
    </tr>
    <tr>
        <th>number</th>
        <td>
            <pre><code>{ "track_number" : "800027315160887" }</code></pre>
            The carrier's tracking number.
        </td>
    </tr>
    <tr>
        <th>date</th>
        <td>
            <pre><code>{ "created_at" : "2014-07-24T18:51:18+00:00" }</code></pre>
            The date and time the tracking number was created.
        </td>
    </tr>
</tbody>
</table>
