---
layout: page
title: "Shipping Methods"
category: doc
parent: "API Basics"
date: 2014-07-29 12:12:51
order: 130
---

The following shipping methods are supported by the API where a "shipping_method" parameter is used. Some services may
not be available on your account or in your area but all services are listed for completeness.

#### FedEx Services

| Code | Description |
|:-----|:-------------|
| fedex_FIRST_OVERNIGHT | FedEx First Overnight&reg; |
| fedex_PRIORITY_OVERNIGHT | FedEx Priority Overnight&reg; |
| fedex_STANDARD_OVERNIGHT | FedEx Standard Overnight&reg; |
| fedex_FEDEX_2_DAY_AM | FedEx 2Day&reg; A.M. |
| fedex_FEDEX_2_DAY | FedEx 2Day&reg; |
| fedex_FEDEX_EXPRESS_SAVER | FedEx Express Saver&reg; |
| fedex_FEDEX_GROUND | FedEx Ground&reg; |
| fedex_GROUND_HOME_DELIVERY | FedEx Home Delivery&reg; |
| fedex_SMART_POST | FedEx SmartPost&reg; |
| fedex_INTERNATIONAL_FIRST | FedEx International First&reg; |
| fedex_INTERNATIONAL_PRIORITY | FedEx International Priority&reg; |
| fedex_INTERNATIONAL_ECONOMY | FedEx International Economy&reg; |
| fedex_INTERNATIONAL_GROUND | FedEx International Ground&reg; |

<!--
| fedex_SAME_DAY | FedEx SameDay&reg; |
| fedex_SAME_DAY_CITY | FedEx SameDay&reg; City |
-->

#### UPS Services

| Code | Description |
|:-----|:-------------|
| ups_01 | UPS Next Day Air |
| ups_02 | UPS Second Day Air |
| ups_03 | UPS Ground |
| ups_11 | UPS Standard |
| ups_12 | UPS Three-Day Select |
| ups_14 | UPS Next Day Air Early A.M. |
| ups_59 | UPS Second Day Air A.M. |
| ups_65 | UPS Worldwide Saver |
| ups_SP | UPS SurePost |

#### USPS Methods

| Code | Description |
|:-----|:-------------|
| usps_US-FC | USPS First-Class |
| usps_US-FCI | USPS First-Class International |
| usps_US-LM | USPS Library Mail |
| usps_US-MM | USPS Media Mail |
| usps_US-PS | USPS Parcel Select Ground |
| usps_US-PM | USPS Priority Mail |
| usps_US-PMI | USPS Priority Mail International |
| usps_US-XM | USPS Priority Mail Express |
| usps_US-EMI | USPS Priority Mail Express International |

#### Amazon Merchant Fulfillment

| Code | Description |
|:-----|:-------------|
| amazon_ANY | Amazon Merchant Fulfillment |
| amazon_Standard | Amazon Standard Delivery |
| amazon_FreeEconomy | Amazon Free Economy |
| amazon_SecondDay | Amazon Two-Day Delivery |
| amazon_NextDay | Amazon One-Day Delivery |
| amazon_Expedited | Amazon Expedited Delivery |

#### OnTrac Services

| Code | Description |
|:-----|:-------------|
| ontrac_S | OnTrac Sunrise |
| ontrac_C | OnTrac Ground |
| ontrac_DC | OnTrac Same Day |

#### LaserShip Services

| Code | Description |
|:-----|:-------------|
| lasership_NextDay | LaserShip NextDay |

#### GLS Services

| Code | Description |
|:-----|:-------------|
| gls_Ground | GLS Ground |
| gls_PriorityOvernight | GLS Priority Overnight |
| gls_EarlyPriorityOvernight | GLS Early Priority Overnight |
| gls_EarlySaturday | GLS Early Saturday |
| gls_SaturdayDelivery | GLS Saturday Delivery |

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
The External Shipping Methods are user defined whithin ShipStream.  This list is not exhaustive, but instead exemplifies how all External Shipping Method codes are prefixed with `external_` .  _For External Shipping Method codes used by your 3PL please contact your represintative._

| Code | Description |
|:-----|:-------------|
| external_ltl | LTL |
| external_ltl_thirdparty | LTL - Third Party |
