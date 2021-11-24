---
layout: page
title: "Search Filters"
category: doc
parent: "API Basics"
date: 2014-07-29 14:00:26
order: 220
---

#### Filters

It is required to always specify the filter type for the filters. Supported filter types are listed below. Others types are not supported.

<table class="table-striped">
<tr>
  <th>eq</th>
  <td>
  	<pre><code>{ "status" : { "eq" : 1 } }</code></pre>
  	The "Equals" filter.
  </td>	
</tr>
<tr>
  <th>neq</th>
  <td>
  	<pre><code>{ "sku" : { "neq" : "product1" } }</code></pre>
  	The "Not Equals" filter.
  </td>	
</tr>
<tr>
  <th>gt</th>
  <td>
  	<pre><code>{ "order_id" : { "gt" : 5 } }</code></pre>
  	The "Greater Than" filter.
  </td>	
</tr>
<tr>
  <th>lt</th>
  <td>
  	<pre><code>{ "order_id" : { "lt" : 5 } }</code></pre>
  	The "Less Than" filter.
  </td>	
</tr>
<tr>
  <th>gteq</th>
  <td>
  	<pre><code>{ "order_id" : { "gteq" : 5 } }</code></pre>
  	The "Greater Than or Equals" filter.
  </td>	
</tr>
<tr>
  <th>lteq</th>
  <td>
  	<pre><code>{ "order_id" : { "lteq" : 5 } }</code></pre>
  	The "Less Than or Equals" filter.
  </td>	
</tr>
<tr>
  <th>from</th>
  <td>
  	<pre><code>{ "created_at" : { "from" : "2014-07-12 14:12:47", "datetime" : true } }</code></pre>
  	<pre><code>{ "created_at" : { "from" : "2014-07-12" } }</code></pre>
  	The "From" date filter.
  </td>	
</tr>
<tr>
  <th>to</th>
  <td>
  	<pre><code>{ "created_at" : { "to" : "2014-07-12 14:12:47", "datetime" : true } }</code></pre>
  	<pre><code>{ "created_at" : { "to" : "2014-07-12" } }</code></pre>
  	The "To" date filter.
  </td>	
</tr>
<tr>
  <th>in</th>
  <td>
  	<pre><code>{ "order_id" : { "in" : [ 114, 115 ] } }</code></pre>
  	The "In" filter.
  </td>	
</tr>
<tr>
  <th>nin</th>
  <td>
  	<pre><code>{ "order_id" : { "nin" : [ 114, 115 ] } }</code></pre>
  	The "Not In" filter.
  </td>	
</tr>
<tr>
  <th>null</th>
  <td>
  	<pre><code>{ "target_ship_date" : { "null" : 1 } }</code></pre>
  	The "NULL" filter.
  </td>	
</tr>
<tr>
  <th>notnull</th>
  <td>
  	<pre><code>{ "target_ship_date" : { "notnull" : 1 } }</code></pre>
  	The "Not NULL" filter.
  </td>	
</tr>
</table>
