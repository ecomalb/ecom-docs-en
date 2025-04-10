# GooglePay™ decrypted

GooglePay™ API

## For the merchant:

1. Configure GooglePay™ to the website, according to the instructions posted on the links:

Documentation: [https://developers.google.com/pay/api/web\
](https://developers.google.com/pay/api/web)Branding requirements: [https://developers.google.com/pay/api/web/guides/brand-guidelines](https://developers.google.com/pay/api/web/guides/brand-guidelines)

#### 2.When the client pays for the service, decrypt the object [CARD](https://developers.google.com/pay/api/web/guides/resources/payment-data-cryptography?hl=ru#card) by means of [PublicKey](https://developers.google.com/pay/api/web/guides/resources/payment-data-cryptography?hl=ru#step-two) and [PrivateKey](https://developers.google.com/pay/api/web/guides/resources/payment-data-cryptography?hl=ru#step-three)

Example of a card:

```json
{
  "paymentMethod": "CARD",
  "paymentMethodDetails": {
    "authMethod": "PAN_ONLY",
    "pan": "1111222233334444",
    "expirationMonth": 10,
    "expirationYear": 2025
  },
  "gatewayMerchantId": "some-merchant-id",
  "messageId": "some-message-id",
  "messageExpiration": "1759309000000"
}
Example of an encrypted PAN:
{
  "paymentMethod": "CARD",
  "paymentMethodDetails": {
    "authMethod": "CRYPTOGRAM_3DS",
    "pan": "1111222233334444",
    "expirationMonth": 10,
    "expirationYear": 2025,
    "cryptogram": "AAAAAA...",
    "eciIndicator": "5"
   
  },
 
  "messageId": "some-message-id",
  "messageExpiration": "1759309000000"
}
```

#### 3.The `paymentData` object described in point 2 must be encrypted with the payment key
