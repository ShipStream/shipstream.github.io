---
layout: default
title: "ShipStream Merchant API"
---

Integrate your clients with ShipStream
=======

Welcome to the **[ShipStream](https://shipstream.io)** Merchant API reference documentation.

What is an "API"?
------

An API, or Application Programming Interface, is a system that allows different software applications to communicate with each other.
In the case of ShipStream, our Merchant API allows you to integrate your own systems with our WMS.

### What can I do with the API?

First, you can use it to _push_ data into our system from yours, such as orders, products and deliveries
and you can _pull_ back data like order statuses, package contents and details and delivery processing results.
You can also request rate quotes which are based on your negotiated rates and update existing data (for example,
put an order on hold).  

You can also subscribe to "[Webhooks](/ref/webhook.html)" and have our system push information
(like inventory updates and tracking numbers) directly to yours in real-time!

Lastly, we have a [Middleware](https://github.com/ShipStream/middleware) system that let's you develop plugins that can
either be integrated directly into our system or run on a standalone environment that makes your plugin
operate like a first-class citizen in our environment complete with internal event notifications and the
ability to handle third-party webhooks!

### Looking for the Global API?

The Merchant API is designed for use by systems that access data for a specific merchant and is limited in scope
compared to our [Global API](https://shipstream.stoplight.io/docs/global-api/8e768e6831f6c-overview). The
Global API is designed for use by systems that need to access data across multiple merchants and perform
operational tasks like picking a shipment. The Merchant API is a subset of the Global API and is intended more
for order management and syncing data between shopping carts and ERPs of a single merchant.

Getting Started
-------

If you're new to the API but ready to get your hands dirty your first stop should be
the [Merchant API Basics](/doc/api-basics.html) page.

If you're trying to use our import feature, check out the
[Import Formats](/doc/import-formats.html) page for details about the various import formats
supported (like CSV and JSON) and how to use them.

In general, the in-depth details of the API methods are listed in their respective sections
under "API REFERENCE" to the left and the other reference material is provided in the "DOCUMENTATION"
section also to the left. If you have any trouble, [let us know](mailto:help@shipstream.io) how the documentation can be improved!
