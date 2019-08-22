---
layout: page
title: "Import Formats"
category: doc
date: 2015-06-18 19:52:21
order: 180
---

* [Order - Standard CSV](#order_standard_csv)
* [Order - Standard JSON](#order_standard_json)
* [Product - Standard CSV](#product_standard_csv)
* [Product - Standard JSON](#product_standard_json)
* [Delivery - Standard CSV](#delivery_standard_csv)
* [Delivery - Standard JSON](#delivery_standard_json)

---

ShipStream supports importing <a href="/ref/order.html#ordercreate">orders</a>,
<a href="/ref/product.html#product_create">products</a> and <a href="/ref/delivery.html#delivery_create">deliveries</a>
either via the Merchant Panel or the <a href="/ref/import.html">Import</a> API.
Standard CSV and JSON filters are provided which format the data to use the same values as
the respective API '*.create' methods so please see the documentation for those methods for
details about supported field names and values.

If you would like to create a custom import format please contact us for help and see the
<a href="#custom_filter">Create custom import format</a> section for more information.

---
<h2 id="order_standard_csv">
Order - Standard CSV
</h2>

The header row defines which columns are used and each following line should consist of the
order data, SKU and quantity for one order item. If the order contains multiple items they
can be specified using additional rows and the order data can be either repeated (it will
be ignored) or omitted as long as the 'order_ref' column is not omitted since it is used
to group the order items together.

<strong>Note:</strong>  
To group multi-product orders together for CSV imports either the `unique_id` or the `order_ref` must be supplied unless there is only one order per file.  
When the `unique_id` is supplied with no `order_ref` then the `unique_id` will be used to group rows.  
When the `order_ref` is supplied with no `unique_id` then the `order_ref` will be used to group rows.  
If both `unique_id` and `order_ref` are supplied then the `unique_id` will be used to group rows.

#### Example Input File [\[Download Sample\]](/samples/order_import_sample.csv)

```
order_ref,shipping_method,firstname,lastname,company,street1,city,region,postcode,country,phone,sku,qty
123456,ups_01,Bill,Gates,Microsoft,11 Times Square,New York,NY,10036,US,212.245.2100,product1,5
123456,,,,,,,,,,,,product2,1
123456,,,,,,,,,,,,product3,2
```

<h2 id="order_standard_json">
Order - Standard JSON
</h2>

Importing orders in JSON format should follow the '<a href="/ref/order.html#ordercreate">order.create</a>' inputs exactly.

#### Example Input File [\[Download Sample\]](/samples/order_import_sample.json){:download="order_import_sample.json"}

```json
{ 
  "order_ref" : "123456", 
  "shipping_method" : "ups_01", 
  "firstname" : "Bill",
  "lastname" : "Gates",
  "company" : "Microsoft", 
  "street1" : "11 Times Square", 
  "city" : "New York", 
  "region" : "NY", 
  "postcode" : "10036", 
  "country" : "US", 
  "phone" : "212.245.2100", 
  "items" : { 
    "product1" : 2, 
    "product2" : 3, 
    "product3" : 1
  }
}
```

<strong><span style="color:red">Important!</span></strong> JSON for each order must be a single line. Multi-line JSON is not allowed.

<h2 id="product_standard_csv">
Product - Standard CSV
</h2>

The header row should contain all field names and each following row contains product data. Each row must specify a SKU at minimum.

If a field supports multiple values such as 'hts_country_code' or 'special_other' then multiple values can be assigned by specifying values separated by the 'pipe' character: |

#### Example Input File [\[Download Sample\]](/samples/product_import_sample.csv)

```
sku,name,barcode,goods_type,weight,length,width,height,country_of_manufacture,hts_base_code,hts_country_code,requires_packaging,confirmation_per_item,special_box,special_infill,special_tape,special_other,unit_qty
"productsku","Product Name","productbarcode","NORMAL","1.75","123","100","28","DK","1234.56","BH:1000|ZW:1001",1,0,"specialboxsku","specialinfillsku","specialtapesku","specialothersku1|specialothersku2",5
```

<h2 id="product_standard_json">
Product - Standard JSON
</h2>

Importing products in JSON format should follow the '<a href="/ref/product.html#product_create">product.create</a>' inputs exactly.

#### Example Input File [\[Download Sample\]](/samples/product_import_sample.json){:download="product_import_sample.json"}

```json
{
  "name" : "Product 3",
  "barcode" : "product3",
  "goods_type" : "NORMAL",
  "weight" : 1.75,
  "length" : 123,
  "width" : 100,
  "height" : 28,
  "country_of_manufacture" : "DK",
  "hts_base_code" : 1234.56,
  "hts_country_code" : "BH:1000|ZW:1001",
  "requires_packaging" : 1,
  "confirmation_per_item" : 0,
  "special_box" : "specialboxsku",
  "special_infill" : "specialinfillsku",
  "special_tape" : "specialtapesku",
  "special_other" : "specialothersku1|specialothersku2"
  "unit_qty" : 5,
  "additional_regulatory_info" : "EX1995120111C",
  "meets_hazmat_specs" : 1
}  
```

<strong><span style="color:red">Important!</span></strong> JSON for each product must be a single line. Multi-line JSON is not allowed.

<h2 id="delivery_standard_csv">
Delivery - Standard CSV
</h2>

The "id" field is only used to group multiple lines into a single delivery. If importing
a single delivery it can be blank, but if importing multiple deliveries it should be unique
for each separate delivery in the CSV file.

#### Example Input File [\[Download Sample\]](/samples/delivery_import_sample.csv)

```
id,delivery_type,sender_name,carrier_name,expected_delivery,merchant_ref,sender_ref,sku,qty_expected
1,asn,Bill Gates,FedEx,"2014-07-31",12345,333,product1,50
1,,,,,,,product2,100
2,asn,Bill Gates,FedEx,"2014-08-12",12346,339,product3,40
2,,,,,,,product4,200
```

<h2 id="delivery_standard_json">
Delivery - Standard JSON
</h2>

Importing deliveries in JSON format should follow the '<a href="/ref/delivery.html#delivery_create">delivery.create</a>' inputs exactly.

#### Example Input File [\[Download Sample\]](/samples/delivery_import_sample.json){:download="delivery_import_sample.json"}

```json
{ 
  "delivery_type" : "asn", 
  "sender_name" : "Bill Gates", 
  "carrier_name" : "FedEx", 
  "expected_delivery" : "2014-07-31", 
  "merchant_ref" : "12345", 
  "sender_ref" : "333", 
  "items" : [ 
    { 
      "sku" : "product1", 
      "qty_expected" : 5
    }, 
    { 
      "sku" : "product2", 
      "qty_expected" : 1 
    } 
  ] 
}
```

<strong><span style="color:red">Important!</span></strong> JSON for each delivery must be a single line. Multi-line JSON is not allowed.

---

<h2 id="custom_filter">
Create custom import format
</h2>

Logstash uses input {...}, filter {...} and output {...} configuration. "input" and "output" configuration
is already defined and only the "filter" part of the configuration can be specified by the user.

The "input" uses stdin and adds "line_number" to each line of the import files. The "output" is different
for each import type. A custom import format should get data after "input", make required modifications and
prepare the data for the "output" format corresponding to the import type.

#### input

```json
input {
  stdin { type => "stdin-type" }
}

filter {
  ruby {
    code => '
      if !$LINE
        $LINE = 0;
      end;
      $LINE += 1; event["line_number"] = $LINE;'
  }
}
```

#### filter for JSON format

```json
filter {
  json {
    source => "message"
  }
  ruby {
    code => 'event["raw_data"] = event["message"]'
  }
}
```

#### output for Order

```json
filter {
  ruby {
    code => 'event["parsed_data"] = {
      "api_method" => "order.create",
      "args" => {
        "items" => event["items"],
        "address" => {
          "firstname"=> event["firstname"],
          "lastname" => event["lastname"],
          "company"  => event["company"],
          "street1"  => event["street1"],
          "city"     => event["city"],
          "region"   => event["region"],
          "postcode" => event["postcode"],
          "country"  => event["country"],
          "phone"    => event["phone"]
        },
        "info" => {
          "unique_id"           => event["unique_id"],
          "order_ref"           => event["order_ref"],
          "shipping_method"     => event["shipping_method"],
          "custom_greeting"     => event["custom_greeting"],
          "note"                => event["note"],
          "signature_required"  => event["signature_required"],
          "overbox"             => event["overbox"],
          "requested_ship_date" => event["requested_ship_date"],
          "delayed_ship_date"   => event["delayed_ship_date"]
        }
      }
    }'
  }
}
```

#### output for Product

```json
filter {
  ruby {
    code => 'event["parsed_data"] = {
      "api_method" => "product.create",
      "args" => {
        "sku" => event["sku"],
        "product_data" => {
          "name"         => event["name"],
          "barcode"      => event["barcode"],
          "goods_type"   => event["goods_type"],
          "weight"       => event["weight"],
          "length"       => event["length"],
          "width"        => event["width"],
          "height"       => event["height"]
        }
      }
    }'
  }
}
```

#### output for Delivery

```json
filter {
  ruby {
    code => 'event["parsed_data"] = {
      "api_method" => "delivery.create",
      "args" => {
        "delivery_type" => event["delivery_type"],
        "data" => {
          "sender_name"       => event["sender_name"],
          "carrier_name"      => event["carrier_name"],
          "expected_delivery" => event["expected_delivery"],
          "delivery_type"     => event["delivery_type"],
          "merchant_ref"      => event["merchant_ref"],
          "sender_ref"        => event["sender_ref"]
        },
        "items" => event["items"]
      }
    }'
  }
}
```
