---
layout: page
title: "Shipping Methods"
category: doc
parent: "API Basics"
date: 2014-07-29 12:12:51
order: 130
---

The following shipping methods are supported by the API where a "shipping_method" parameter is used.

#### FedEx Methods

| Code | Description |
|:-----|:-------------|
| fedex_FEDEX_2_DAY | FedEx 2Day&reg; |
| fedex_FEDEX_2_DAY_AM | FedEx 2Day&reg; A.M. |
| fedex_FEDEX_EXPRESS_SAVER | FedEx Express Saver&reg; |
| fedex_FEDEX_GROUND | FedEx Ground&reg; |
| fedex_INTERNATIONAL_ECONOMY | FedEx International Economy&reg; |
| fedex_INTERNATIONAL_PRIORITY | FedEx International Priority&reg; |
| fedex_FIRST_OVERNIGHT | FedEx First Overnight&reg; |
| fedex_GROUND_HOME_DELIVERY | FedEx Home Delivery&reg; |
| fedex_PRIORITY_OVERNIGHT | FedEx Priority Overnight&reg; |
| fedex_STANDARD_OVERNIGHT | FedEx Standard Overnight&reg; |
| fedex_SMART_POST | FedEx SmartPost&reg; |

#### UPS Methods

| Code | Description |
|:-----|:-------------|
| ups_01 | UPS Next Day Air |
| ups_02 | UPS Second Day Air |
| ups_03 | UPS Ground |
| ups_12 | UPS Three-Day Select |
| ups_14 | UPS Next Day Air Early A.M. |
| ups_59 | UPS Second Day Air A.M. |

#### USPS Methods

| Code | Description |
|:-----|:-------------|
| usps_US-EMI | USPS Priority Mail Express International |
| usps_US-FC | USPS First-Class |
| usps_US-FCI | USPS First-Class International |
| usps_US-FCPI | USPS First-Class Package International |
| usps_US-LM | USPS Library Mail |
| usps_US-MM | USPS Media Mail |
| usps_US-PM | USPS Priority Mail |
| usps_US-PMI | USPS Priority Mail International |
| usps_US-PS | USPS Parcel Select Ground |
| usps_US-XM | USPS Priority Mail Express |

#### Amazon Merchant Fulfillment

| Code | Description |
|:-----|:-------------|
| amazon_ANY | Amazon Merchant Fulfillment |
| amazon_Standard | Amazon Standard Delivery |
| amazon_FreeEconomy | Amazon Free Economy |
| amazon_SecondDay | Amazon Two-Day Delivery |
| amazon_NextDay | Amazon One-Day Delivery |
| amazon_Expedited | Amazon Expedited Delivery |

#### "Cheapest" Methods

| Code | Description |
|:-----|:-------------|
| cheapest_ALL | Cheapest method overall |
| cheapest_GROUND | Cheapest ground shipping method |
| cheapest_POSTAL | Cheapest USPS or USPS last-mile shipping method |
| cheapest_THREE_DAY | Cheapest 3-day shipping method |
| cheapest_TWO_DAY | Cheapest 2-day shippng method |
| cheapest_OVERNIGHT | Cheapest overnight shipping method |
| cheapest_ON_TIME | Cheapest shipping method to arrive on-time. This requires valid "desired_delivery_date" as well.

#### Other

| Code | Description |
|:-----|:-------------|
| external_ltl | LTL |
| external_ltl_thirdparty | LTL - Third Party |
