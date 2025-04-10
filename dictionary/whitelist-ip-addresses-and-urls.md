---
description: Using WhiteListing
---

# Whitelist IP addresses and URLs

To ensure security and enable interaction with API requests, you must provide a list of IP addresses and URLs to be added to the WhiteList.

### Callback Submission

* A URL address will be used for sending callbacks related to operations.
* When creating requests, the `notificationUrl` parameter must contain the URL to which the [Callback](https://docs.merchant.alb.ua/en/payment-methods-h2h/callback) will be sent.
* The URL address can be dynamic.

### IP Address Requirements

* The IP address must follow the IPv4 protocol.
* The provided IP address format must be `'192.168.1.1'`.

### URL Address Requirements

* Must support HTTPS (e.g., `https://docs.merchant.alb.ua/`).
* The server must be available 24/7 to receive notifications.
* Must correctly process requests in JSON format.
