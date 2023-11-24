---
layout: page
title: "Search Filters"
category: doc
parent: "API Basics"
date: 2014-07-29 14:00:26
order: 220
---

#### Filters

Filters are provided as a list of keys and filter specifications. The keys are names of fields that can be returned
in the response. Not all fields support filtering.

Multiple filters are combined using "AND" logic. For example, to find orders that were created after 2023-01-01 and
are not completed the filters could be specified like so:

```json
{
  "created_at": {"from": "2023-01-01"},
  "status": {"neq": "complete"}
}
```

<table class="table-striped">
<tr>
  <th>eq</th>
  <td>
  	<pre><code>{ "status" : { "eq" : 1 } }</code></pre>
  	The value is equal to the given value.
  </td>	
</tr>
<tr>
  <th>neq</th>
  <td>
  	<pre><code>{ "sku" : { "neq" : "product1" } }</code></pre>
  	The value is not equal to the given value.
  </td>	
</tr>
<tr>
  <th>starts</th>
  <td>
  	<pre><code>{ "sku" : { "starts" : "abc-" } }</code></pre>
  	The value starts with the given value (prefix match).
  </td>	
</tr>
<tr>
  <th>gt</th>
  <td>
  	<pre><code>{ "order_id" : { "gt" : 5 } }</code></pre>
  	The value is greater than the given value.
  </td>	
</tr>
<tr>
  <th>lt</th>
  <td>
  	<pre><code>{ "order_id" : { "lt" : 5 } }</code></pre>
  	The value is less than the given value.
  </td>	
</tr>
<tr>
  <th>gteq</th>
  <td>
  	<pre><code>{ "order_id" : { "gteq" : 5 } }</code></pre>
  	The value is greater than or equal to the given value.
  </td>	
</tr>
<tr>
  <th>lteq</th>
  <td>
  	<pre><code>{ "order_id" : { "lteq" : 5 } }</code></pre>
  	The value is less than or equal to the given value.
  </td>	
</tr>
<tr>
  <th>from</th>
  <td>
  	<pre><code>{ "created_at" : { "from" : "2014-07-12 14:12:47", "datetime" : true } }</code></pre>
  	<pre><code>{ "created_at" : { "from" : "2014-07-12" } }</code></pre>
  	The value is greater than or equal to the given value. If the "datetime" flag is specified the value is compared
    with the exact timestamp given, otherwise the value is compared with the first second on the given date. The
    timezone is the merchant's configured timezone. 
  </td>	
</tr>
<tr>
  <th>to</th>
  <td>
  	<pre><code>{ "created_at" : { "to" : "2014-07-12 14:12:47", "datetime" : true } }</code></pre>
  	<pre><code>{ "created_at" : { "to" : "2014-07-12" } }</code></pre>
  	The value is less than or equal to the given value. If the "datetime" flag is specified the value is compared
    with the exact timestamp given, otherwise the value is compared with the last second on the given date. The
    timezone is the merchant's configured timezone.
  </td>	
</tr>
<tr>
  <th>in</th>
  <td>
  	<pre><code>{ "order_id" : { "in" : [ "114", "115" ] } }</code></pre>
  	The value is equal to one of the given values. This can be used to locate multiple records with one query.
  </td>	
</tr>
<tr>
  <th>nin</th>
  <td>
  	<pre><code>{ "status" : { "nin" : [ "new", "complete" ] } }</code></pre>
  	The value is not equal to any of the given values.
  </td>	
</tr>
<tr>
  <th>null</th>
  <td>
  	<pre><code>{ "target_ship_date" : { "null" : 1 } }</code></pre>
  	The field's value is null (has no value).
  </td>	
</tr>
<tr>
  <th>notnull</th>
  <td>
  	<pre><code>{ "target_ship_date" : { "notnull" : 1 } }</code></pre>
  	The field has a value that is not null.
  </td>	
</tr>
</table>
