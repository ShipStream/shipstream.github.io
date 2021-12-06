---
layout: page
title: "API Basics"
category: doc
date: 2021-01-12 19:39:09
order: 210
---

ShipStream exposes all of it's API endpoints via HTTP using the JSONRPC protocol. This page explains the general
method of authenticating and calling methods. Each method is documented in detail in the Reference section.

There are only two actual JSONRPC methods: `login` and `call`. The `login` procedure returns a session ID which
is then passed to subsequent requests to `call`. The `call` procedure takes the API method name and other request parameters.

### Authentication

The preferred authentication method is to use HTTP Basic Auth with the API key username and password in which case the
`session_id` parameter to the `call` method should be `null`.

You can also retrieve a session ID using the `login` method to be used for subsequent requests to `call` in which case
it is not necessary to use HTTP Basic Auth. 

#### HTTP Basic Auth Example

```
$ echo '{"jsonrpc":2.0,"id":1234,"method":"call","params":[null,"warehouse.list",[]]}' \
  | http POST https://apiuser:password@example.shipstream.app/api/jsonrpc
```

### Request Format

All requests must be POST requests with the request parameters given as a JSON-encoded string in the POST body.
The request parameters are as follows:

<dl class="dl-horizontal">
<dt>jsonrpc</dt>
<dd>The JSONRPC protocol version number. Must be "2.0".</dd>
<dt>id</dt>
<dd>A unique identifier for the request that will be included in the response.</dd>
<dt>method</dt>
<dd>The remote procedure to call. This should always be either `login` or `call`.</dd>
<dt>params</dt>
<dd>An array of request parameters specific to the remote procedure being called (see below for details).</dd>
</dl>

### Response Format

The response will be a JSON-encoded string with the following properties:

<dl class="dl-horizontal">
<dt>jsonrpc</dt>
<dd>The JSONRPC protocol version number ("2.0").</dd>
<dt>id</dt>
<dd>The unique identifier that matches the id given in the request.</dd>
<dt>error</dt>
<dd><em>If</em> there is an error, this will be an object with keys `code` and `message`. See "Error Codes" for a list
of general error codes.</dd>
<dt>result</dt>
<dd>If an error did not occur this will contain the appropriate response data, otherwise this will be empty.</dd>
</dl>

### Error Codes

<table class="table table-condensed">
<thead>
  <tr>
    <th>code</th>
    <th>message</th>
    <th>meaning</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>-32700</td>
    <td>Parse error</td>
    <td>Invalid JSON was received by the server.<br>An error occurred on the server while parsing the JSON text.</td>
  </tr>
  <tr>
    <td>-32600</td>
    <td>Invalid Request</td>
    <td>The JSON sent is not a valid Request object.</td>
  </tr>
  <tr>
    <td>-32601</td>
    <td>Method not found</td>
    <td>The method does not exist / is not available.</td>
  </tr>
  <tr>
    <td>-32602</td>
    <td>Invalid params</td>
    <td>Invalid method parameter(s).</td>
  </tr>
  <tr>
    <td>-32603</td>
    <td>Internal error</td>
    <td>Internal JSON-RPC error.</td>
  </tr>
</tbody>
</table>

The error codes are easier to read if you first multiply by -1 and then subtract 32000. From this point forward, all error
codes mentioned will have this formula already applied to them, but due to the requirement of hte JSONRPC protocol, they
will be reported via the API without the formula applied.

login `(username, api_key)`
=====

**If using HTTP Basic Auth described above you do not need to use a session ID!**

An API session is started by calling the `login` method to get a session ID. The session ID will expire after 24 hours
and can be used as the first method parameter for subsequent calls to `call`. If using HTTP Basic Auth then there is no
need for a session ID and this first parameter can be `null`.

#### Parameters

| order | type | description |
| ----- | ---- | ----------- |
| 0 | string | The API user's username. |
| 1 | string | The API user's API key (password). |

#### Return Value

Upon a successful login the result will be a session ID which is a 32-character hexadecimal string.

----

#### Example Request

<div class="api-endpoint-request">
    <pre><span class="api-endpoint-request-type">POST</span>/api/jsonrpc</pre>
</div>

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "login",
    "params" : [
        "username",
        "password"
    ]
}
```

#### Example Response

An example response for a successful login:

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "result" : "be1c13ed4e03f0ed7f1e4053dfff9658"
}
```

An example response for if the session is expired:

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "error" : {
        "code" : -32005,
        "message" : "Session expired. Try to relogin."
    }
}
```

#### Error Codes

| code | message |
| ---- | ------- |
| 2 | Access denied. |
| 6 | Required parameter is missing, for more details see "exception.log". |

call `(session_id, method, arguments)`
====

The 'call' method is used to call all other API endpoints which are detail in the pages under the "API Reference" heading in the sidebar.

#### Parameters

| order | type | description |
| ----- | ---- | ----------- |
| 0 | null,string | The session ID obtained from calling `login` or `null` if using HTTP Basic Auth. |
| 1 | string | The API method to call. This always takes the form of "`resource.method`". E.g. "`state.get`" |
| 2 | array | The arguments to the API method. If there are no additional arguments this parameter may be omitted. |

#### Return Value

The response may be any valid JSON type according to the method which was called.

----

#### Error Codes

| code | message |
| ---- | ------- |
| 2 | Access denied. |
| 3 | Invalid api path. |
| 4 | Resource path is not callable. |
| 5 | Session expired. Try to relogin. |
| ? | Other error codes may be used depending on which method was called.
