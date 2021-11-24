---
layout: page
title: "Media"
category: ref
parent: "Product"
date: 2014-12-05 12:40:01
order: 110
---

#### Methods

 * [product_media.list](#product_media_list)
 * [product_media.types](#product_media_types)
 * [product_media.create](#product_media_create)
 * [product_media.update](#product_media_update)
 * [product_media.remove](#product_media_remove)

----

#### Entity Properties

 * [Image Type](#image_type_properties)
 * [Image Mime Type](#image_mime_type)
 * [Image Data](#image_data)
 
----

<h1 id="product_media_list">
product_media.list
<code>(string $sku)</code>
</h1>

Retrieve list of product images

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>string - Product SKU.</td>
    </tr>
</tbody>
</table>

#### Return Value

An array of objects. Each object will contain "<a href="#image_data">Image Data</a>".

#### Example Request

Get product images by product SKU:

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "product_media.list",
        [
            "product2"
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
    "result" : [
        {
            "file" : "/b/l/blackberry8100_2.jpg",
            "position" : 1,
            "exclude" : 0,
            "url" : "http://magentohost/media/catalog/product/b/l/blackberry8100_2.jpg",
            "types" : [
                "image", 
                "thumbnail"
            ]
        }
    ]
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Requested store view not found. |
| 101 | Product not exists. |

----

<h1 id="product_media_types">
product_media.types
<code>(number $setId)</code>
</h1>

Retrieve product image types

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>int - Attribute set id.</td>
    </tr>
</tbody>
</table>

#### Return Value

An array of objects. Each object will contain "<a href="#image_type_properties">Image Type Properties</a>".

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "product_media.types",
        [
            4        
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
    "result" : [
        {
            "code" : "image",
            "scope" : "store"
        },
        {
            "code" : "thumbnail",
            "scope" : "store"
        }
    ]
}}
```

----

<h1 id="product_media_create">
product_media.create
<code>(string $sku, object $data)</code>
</h1>

Upload new product image

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>string - Product SKU.</td>
    </tr>
    <tr>
        <td>1</td>
        <td>object - Image data.</td>
    </tr>
</tbody>
</table>

#### Return Value

Image file name (e.g., "/i/m/image.png")

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "product_media.create",
        [
            "product2",
            {
                "file" : {
                    "content" : "base64 encoded content",
                    "mime": "image/jpeg"
                },
                "position" : 100,
                "types" : [
                    "thumbnail"
                ],
                "exclude" : 0
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
    "result" : [
        "/i/m/image.png"
    ]
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Requested store view not found. |
| 101 | Product not exists. |
| 102 | Invalid data given. Details in error message. |
| 104 | Image creation failed. Details in error message. |
| 107 | Requested product doesn't support images |

----

<h1 id="product_media_update">
product_media.update
<code>(string $sku, string $file, object $data)</code>
</h1>

Update product image

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>string - Product SKU.</td>
    </tr>
    <tr>
        <td>1</td>
        <td>string - Image file name.</td>
    </tr>
    <tr>
        <td>2</td>
        <td>object - Image data.</td>
    </tr>
</tbody>
</table>

#### Return Value

True, if the image has been uploaded

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "product_media.update",
        [
            "product2",
            "/i/m/image.png",
            {
                "file" : {
                    "content" : "base64 encoded content",
                    "mime": "image/jpeg"
                },
                "position" : 100,
                "types" : [
                    "thumbnail"
                ],
                "exclude" : 1
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
    "result" : 1
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Requested store view not found. |
| 101 | Product not exists. |
| 102 | Invalid data given. Details in error message. |
| 103 | Requested image not exists in product images' gallery. |
| 104 | Image creation failed. Details in error message. |
| 107 | Requested product doesn't support images |

----

<h1 id="product_media_remove">
product_media.remove
<code>(string $sku, string $file)</code>
</h1>

Remove product image

#### Parameters

<table class="table">
<thead><tr><th>order</th><th>description</th></tr></thead>
<tbody>
    <tr>
        <td>0</td>
        <td>string - Product SKU.</td>
    </tr>
    <tr>
        <td>1</td>
        <td>string - Image file.</td>
    </tr>
</tbody>
</table>

#### Return Value

True, if the image has been removed

#### Example Request

```json
{
    "jsonrpc" : 2.0,
    "id" : 1234,
    "method" : "call",
    "params" : [
        "be1c13ed4e03f0ed7f1e4053dfff9658",
        "product_media.remove",
        [
            "product2",
            "/b/l/blackberry8100_2.jpg"
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
    "result" : 1
}
```

----

#### Error Codes

| code | message |
| ---- | ------- |
| 100 | Requested store view not found. |
| 101 | Product not exists. |
| 106 | Image not removed. Details in error message. |
| 107 | Requested product doesn't support images |

----

## Entity Properties

<h3 id="image_type_properties">
    Image Type Properties
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>code</th>
        <td>
            <pre><code>{ "code" : "image" }</code></pre>
            A unique identifier for an image type. Allowed: "image", "thumbnail".
        </td>
    </tr>
    <tr>
        <th>scope</th>
        <td>
            <pre><code>{ "scope" : "global" }</code></pre>
            The "Scope" property. Allowed: "global", "website", "store".
        </td>
    </tr>
</tbody>
</table>

----

<h3 id="image_mime_type">
    Image Mime Type
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>image/jpeg</th>
        <td>
            <pre><code>{ "mime" : "image/jpeg" }</code></pre>
            JPEG
        </td>
    </tr>
    <tr>
        <th>image/gif</th>
        <td>
            <pre><code>{ "mime" : "image/gif" }</code></pre>
            GIF
        </td>
    </tr>
    <tr>
        <th>image/png</th>
        <td>
            <pre><code>{ "mime" : "image/png" }</code></pre>
            PNG
        </td>
    </tr>
</tbody>
</table>

----

<h3 id="image_data">
    Image Data
</h3>

<table class="table-striped">
<tbody>
    <tr>
        <th>file</th>
        <td>
            Creating a new file:
            <pre><code>{ "file" : { "content" : "base64 encoded content", "mime" : "image/jpeg" }}</code></pre>
            Retriving existing file:
            <pre><code>{ "file" : "/b/l/blackberry8100_2.jpg" }</code></pre>
        </td>
    </tr>
    <tr>
        <th>position</th>
        <td>
            <pre><code>{ "position" : 3 }</code></pre>
        </td>
    </tr>
    <tr>
        <th>exclude</th>
        <td>
            <pre><code>{ "exclude" : 1 }</code></pre>
            Allowed: "0" or "1".
        </td>
    </tr>
    <tr>
        <th>url</th>
        <td>
            <pre><code>{ "url" : "https://shipstream.io/media/catalog/product/b/l/blackberry8100_2.jpg" }</code></pre>
        </td>
    </tr>
    <tr>
        <th>types</th>
        <td>
            <pre><code>{ "types" : ["image", "thumbnail"] }</code></pre>
            Allowed: "image", "thumbnail".
        </td>
    </tr>
</tbody>
</table>
