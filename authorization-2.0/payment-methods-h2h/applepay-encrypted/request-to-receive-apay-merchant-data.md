---
description: '{{url}}/ecom/jws/payments/merchant/get_v1'
---

# Request to receive aPay merchant data

Request for the merchant to receive data and settings of aPay merchant \
Optional request. Hard-coded aPay data on the merchant side is possible<br>

#### Output parameters of the JWS payload part:

| Parameter            | Description                                                                                                                          | Data Format | Example                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ----------- | ------------------------------------------ |
| merchantCapabilities | determines which capabilities the merchant supports for processing payments through Apple Pay                                        | object      | supports3DS, supportsCredit, supportsDebit |
| supportedNetworks    | defines the list of payment networks (card types) supported by the merchant to process payments through Apple Pay.                   | object      | visa, masterCard                           |
| countryCode          | the two-letter country code (according to the ISO 3166-1 alpha-2 standard) where the Apple Pay transaction will be made.             | string      | UA                                         |
| currencyCode         | defines the currency in which the payment will be made via Apple Pay. Three-letter currency code according to the ISO 4217 standard. | string      | UAH                                        |

#### Examples

<details>

<summary>JWS Payload - the request body before signing up</summary>

```json
{  }
```

</details>

<details>

<summary>JWS Payload - the response body before signing up</summary>

```json
{
    "merchantCapabilities": [
        "SUPPORTS_3DS"
    ],
    "supportedNetworks": [
        "VISA"
    ],
    "countryCode": [
        "UA"
    ],
    "currencyCode": "UAH"
}
```

</details>
