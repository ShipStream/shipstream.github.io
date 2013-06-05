---
layout: page
title: "Search Options"
category: doc
parent: "API Basics"
date: 2014-07-29 13:24:56
order: 120
---

#### Options

Search options are optional and can be used for safe paging.

<table class="table-striped">
<tr>
  <th>sort_field</th>
  <td>
  	<pre><code>{ "sort_field" : "status" }</code></pre>
  	The "Sort Field" option. Default: "order_id".
  </td>	
</tr>
<tr>
  <th>sort_dir</th>
  <td>
  	<pre><code>{ "sort_dir" : "desc" }</code></pre>
  	The "Sort Direction" option. Allowed: "asc" or "desc". Default: "asc".
  </td>	
</tr>
<tr>
  <th>page</th>
  <td>
  	<pre><code>{ "page" : 5 }</code></pre>
  	The "Page" numeric option. Default: 1.
  </td>	
</tr>
<tr>
  <th>limit</th>
  <td>
  	<pre><code>{ "limit" : 100 }</code></pre>
  	The "Limit" numeric option. Default: 50.
  </td>	
</tr>
</table>
