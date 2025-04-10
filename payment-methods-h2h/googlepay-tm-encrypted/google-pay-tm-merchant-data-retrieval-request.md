---
description: '{{url}}/ecom/execute_request/payments/v1/googplepay/merchant/get'
---

# Google Pay™ Merchant Data Retrieval Request

This request allows a merchant to retrieve their Google Pay™ configuration and data. This request is optional, as Google Pay™ data can be hard-coded on the merchant's side.

## Response Parameters:

<table data-header-hidden><thead><tr><th>Parameter</th><th width="212">Description</th><th>Type</th><th>Example</th></tr></thead><tbody><tr><td>id</td><td>Merchant identifier in the Google Pay™ system</td><td>string</td><td> "1234567890"</td></tr><tr><td>gPayMerchantName</td><td>Merchant's name</td><td>string</td><td>Example Merchant</td></tr><tr><td>gatewayIds</td><td>List of gateway IDs associated with the merchant</td><td>list</td><td> </td></tr><tr><td>countryCode</td><td>Country code value</td><td>string</td><td>UA</td></tr><tr><td>allowedAuthMethods</td><td><p>Supported fields for card transaction authentication. </p><p></p><ul><li>PAN_ONLY: This authentication method is associated with payment cards stored in the user's Google Account. The returned payment data contains the Personal Account Number (PAN) along with the expiration month and expiration year.</li><li>CRYPTOGRAM_3DS: This authentication method is associated with cards stored as tokens on the Android device. The returned payment data contains a 3-D Secure (3DS) cryptogram generated on the device.</li></ul><p> </p></td><td>string</td><td>["PAN_ONLY", "CRYPTOGRAM_3DS"]</td></tr><tr><td>allowedCardNetworks</td><td><p>Supported card networks for Google Pay™ API</p><ul><li>MASTERCARD</li><li>VISA</li></ul></td><td>string</td><td>["MASTERCARD", "VISA"]</td></tr><tr><td>enabled</td><td>Indicates whether the merchant is active (<code>true</code>) or inactive (<code>false</code>)</td><td> string</td><td>true/false</td></tr></tbody></table>

## Request Example

```json
{  }
```

## Response Example

```json
{
    "id": "paujUKks5E7jFHdsGLgShAIZ",
    "gPayMerchantName": "gPayMerchantName00",
    "gatewayIds": [
        "9ACW_gv4dRs6yLIzdW_WZUNw"
    ],
    "allowedCardNetworks": [
        "MASTERCARD",
        "VISA"
    ],
    "allowedAuthMethods": [
        "PAN_ONLY",
        "CRYPTOGRAM_3DS"
    ],
    "enabled": true,
    "countryCode": "UA"
}
```
