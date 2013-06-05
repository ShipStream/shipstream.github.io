---
layout: default
title: "ShipStream Merchant API"
---

Integrate your clients with ShipStream
=======

Welcome to the official **[ShipStream](https://shipstream.io)** client integration documentation site.
If you're a programmer looking for information about our API (Application Programming Interface)
and how to make use of it then you have come the the right place. We strive to maintain complete
coverage of the functionality of our web-based user interface via the API so that if you
can do it on the website you can do it with the API (and more).

What is this "API"?
------

Our API can do just about everything the user interface can do and a few other things as well.

First, you can use it to _push_ data into our system from yours, such as orders, products and deliveries
and you can _pull_ back data like order statuses, package contents and details and delivery processing results.
You can also request rate quotes which are based on your negotiated rates and update existing data (for example,
put an order on hold).  

You can also subscribe to "[Webhooks](/ref/webhook.html)" and have our system push information
(like inventory updates and tracking numbers) directly to yours in real-time!

Lastly, we have a [Middleware](/doc/middleware.html) system that let's you develop plugins that can
either be integrated directly into our system or run on a standalone environment that makes your plugin
operate like a first-class citizen in our environment complete with internal event notifications and the
ability to handle third-party webhooks!

Getting Started
-------

If you're new to the API but ready to get your hands dirty your first stop should be
the [API Basics](/doc/api-basics.html) page.

If you're trying to use our import feature, check out the
[Import Formats](/doc/import-fomrats.html) page for details about the various import formats
supported (like CSV and JSON) and how to use them.

In general, the in-depth details of the API methods are listed in their respective sections
under "API REFERENCE" to the left and the other reference material is provided in the "DOCUMENTATION"
section also to the left. If you have any trouble, let us know how the documentation can be improved!
