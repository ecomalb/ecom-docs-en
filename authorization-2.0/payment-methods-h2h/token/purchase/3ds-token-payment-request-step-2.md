---
description: '{{url}}/ecom/execute_request/payments/v1/purchase/token_3ds'
---

# 3DS token payment request Step 2

## Input Parameters:

| Parameter           | Description                     | Data Format | Required                | Example                                      |
| ------------------- | ------------------------------- | ----------- | ----------------------- | -------------------------------------------- |
| operationId         | Operation ID obtained in Step 1 | string      | Yes                     | 1697008393082nW0c1jr6KVv                     |
| date                | Payment date and time           | string      | Yes                     | \{{currentdateT\}}.00+00:00                  |
| browserInfo         | Object containing browser data  | object      | Yes, if 3DS is required | -                                            |
| browserAcceptHeader | HTTP request header             | string      | Yes, if 3DS is required | text/html,application/xhtml+xml,...          |
| browserUserAgent    | Browser user-agent string       | string      | Yes, if 3DS is required | Mozilla/5.0 (Windows NT 10.0; Win64; x64)... |
| browserLanguage     | Browser language                | string      | Yes, if 3DS is required | en-US,en                                     |
| browserColorDepth   | Screen color depth value        | string      | Yes, if 3DS is required | 24                                           |
| browserScreenHeight | Browser viewport height         | string      | Yes, if 3DS is required | 800                                          |
| browserScreenWidth  | Browser viewport width          | string      | Yes, if 3DS is required | 1280                                         |
| browserTZ           | Browser timezone                | string      | Yes, if 3DS is required | -180                                         |

## Output Parameters:

| Parameter               | Description                        | Data Format | Example                                                                      |
| ----------------------- | ---------------------------------- | ----------- | ---------------------------------------------------------------------------- |
| type                    | Transaction type                   | string      | Purchase                                                                     |
| rrn                     | Transaction RRN in MPS             | string      | 2554256963                                                                   |
| purpose                 | Payment purpose                    | string      | For goods                                                                    |
| comment                 | Comment                            | string      | test                                                                         |
| coinAmount              | Payment amount                     | int         | 2000                                                                         |
| merchantId              | Merchant ID                        | string      | 137d9304-0368-11ed-b939-0242ac120002                                         |
| operationId             | Transaction ID                     | string      | 1712844596346b9F-WwrWZpq                                                     |
| ecomOperationId         | Transaction ID in Ecom system      | string      | 8c3303e9-7396-43b8-af4e-31d9facdde9b                                         |
| merchantName            | Merchant name                      | string      | KB test terminal                                                             |
| approvalCode            | Authorization code                 | string      | 39203                                                                        |
| status                  | Transaction status                 | string      | SUCCESS / FAIL / PENDING / REQUIRED\_3DS / DESIRED\_THREEDS\_MODE\_ERROR     |
| transactionType         | Numeric transaction type           | string      | 35                                                                           |
| merchantRequestId       | Merchant request ID                | string      | 72837906-f526-4aef-8d11-58d80b44cb75                                         |
| transactionCurrency     | Payment currency                   | string      | 980                                                                          |
| merchantCommission      | Commission amount                  | string      | 2                                                                            |
| creationDateTime        | Payment creation date              | string      | 2024.09.19 15:29:25.675                                                      |
| modificationDateTime    | Payment modification date          | string      | 2024.09.19 15:29:25.675                                                      |
| actionCode              | Response code                      | string      | 0                                                                            |
| responseCode            | Response details                   | string      | 0                                                                            |
| description             | Response description               | string      | approved                                                                     |
| bankCode                | Issuing bank name                  | string      | BANK\_ALLIANCE                                                               |
| paymentSystem           | Issuing MPS name                   | string      | MasterCard                                                                   |
| productType             | Terminal product type              | string      | PURCHASE                                                                     |
| notificationUrl         | Callback notification URL          | string      | https://merchant.notification\_url/                                          |
| paymentServiceType      | Payment type                       | string      | CARD / APPLE\_PAY / GOOGLE\_PAY                                              |
| notificationEncryption  | Callback data encryption flag      | string      | true / false                                                                 |
| cardNumberMask          | Masked card number                 | string      | 5573\*\*\*\*\*\*\*\*0304                                                     |
| desiredThreeDSMode      | Merchant's 3DS preference          | string      | MUST / SHOULD / MUST\_NOT                                                    |
| threeDSMode             | Whether 3DS was used               | string      | MUST / MUST\_NOT                                                             |
| statusThreeDs           | 3DS transaction status             | string      | Y (successful) / N (unsuccessful)                                            |
| threeDSServerTransId    | 3DS system transaction ID          | string      | b6c35fdb-28c1-454d-a2f3-51098c26bda4                                         |
| acsTransId              | ACS system transaction ID          | string      | 3e17fabb-71e6-498e-8794-ef8c95c5ba6f                                         |
| dsTransId               | Directory Server transaction ID    | string      | 12ebc556-82d3-4e35-9fb8-77ac18b050ea                                         |
| eci                     | Electronic Commerce Indicator code | string      | 02                                                                           |
| processingMerchantId    | Merchant ID in PC                  | string      | AE100000                                                                     |
| processingTerminalId    | Terminal ID in PC                  | string      | AE100000                                                                     |
| redirect3dsUrl          | 3DS redirect URL                   | string      | https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/... |
| txnType                 | Transaction subtype                | enum        | NONCVV/noncvv                                                                |
| senderCustomerId        | Sender customer ID                 | string      | 1258728c1                                                                    |
| senderFirstName         | Sender's first name                | string      | Ivanenko                                                                     |
| senderLastName          | Sender's last name                 | string      | Ivan                                                                         |
| senderMiddleName        | Sender's middle name               | string      | Ivanovich                                                                    |
| senderEmail             | Sender's email                     | string      | mail@gmail.com                                                               |
| senderCountry           | Sender's country                   | string      | Ukraine                                                                      |
| senderRegion            | Sender's region                    | string      | Kyiv region                                                                  |
| senderCity              | Sender's city                      | string      | Kyiv                                                                         |
| senderStreet            | Sender's street                    | string      | Sichovykh Striltsiv                                                          |
| senderAdditionalAddress | Additional address details         | string      | 23                                                                           |
| senderItn               | Sender's ITN                       | string      | 123456789                                                                    |
| senderPassport          | Sender's passport                  | string      | АН123456                                                                     |
| senderIp                | Sender's IP address                | string      | 123.12.12.12                                                                 |
| senderPhone             | Sender's phone number              | string      | 380630000000                                                                 |
| senderBirthday          | Sender's date of birth             | string      | 31.12.2000                                                                   |
| senderGender            | Sender's gender                    | string      | M                                                                            |
| senderZipCode           | Sender's zip code                  | string      | 12000                                                                        |
| senderBankCode          | Sender's issuing bank name         | string      | BANK\_ALLIANCE                                                               |
| senderPaymentSystem     | Sender's issuing MPS name          | string      | MasterCard                                                                   |
| senderCardNumberMask    | Sender's masked card number        | string      | 5573\*\*\*\*\*\*\*\*0304                                                     |
| externalCardToken       | token id                           | string      | tmkEYenZSa8FV03aawVXxbep                                                     |

## Request Body Example:

```json
{
    "operationId": "{{operationIdT}}",
    "browserInfo": {
        "browserAcceptHeader": "text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9",
        "browserUserAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like,Gecko)Chrome/87.0.4280.66 Safari/537.36",
        "browserLanguage": "en-US,en",
        "browserColorDepth": "24",
        "browserScreenHeight": "800",
        "browserScreenWidth": "1280",
        "browserTZ": "-180"
    },
    "date": "{{currentdateT}}.00+00:00"
}

```

## Example response body without 3DS

```json
{
    "type": "PURCHASE",
    "rrn": null,
    "purpose": "LLopo",
    "comment": "RRRR",
    "coinAmount": 100,
    "merchantId": "137d9304-0368-11ed-b939-0242ac120002",
    "operationId": "1712822536063CdDIRi8hhjq",
    "ecomOperationId": "82da90c3-50b8-4d5b-b357-2cbe55167200",
    "merchantName": null,
    "approvalCode": null,
    "status": "REQUIRED_3DS",
    "transactionType": 35,
    "merchantRequestId": "8aa31389-fe6f-4b40-bb5e-4ecedfefb847",
    "transactionCurrency": "980",
    "merchantCommission": null,
    "createDateTime": "2024.09.19 15:29:25.675",
    "modificationDateTime": "2024.09.19 15:29:25.675",
    "transactionResponseInfo": {
        "actionCode": null,
        "responseCode": null,
        "description": null
    },
    "bankCode": null,
    "paymentSystem": null,
    "productType": "PURCHASE",
    "notificationUrl": "https://webhook.site/6e35c4af-9af9-4212-9aa4-6a79ed6d7a0d",
    "paymentServiceType": "CARD",
    "notificationEncryption": true,
    "cardNumberMask": null,
    "desiredThreeDSMode": "MUST",
    "threeDSMode": "MUST",
    "statusThreeDs": null,
    "threeDSServerTransId": "0ce5cc44-2698-4a2c-969a-3155bad68b6e",
    "redirect3dsUrl": "https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1712822536063CdDIRi8hhjq",
    "txnType": "null",
    "senderCustomerId": null,
    "senderFirstName": null,
    "senderLastName": null,
    "senderMiddleName": null,
    "senderEmail": null,
    "senderCountry": null,
    "senderRegion": null,
    "senderCity": null,
    "senderStreet": null,
    "senderAdditionalAddress": null,
    "senderItn": null,
    "senderPassport": null,
    "senderIp": null,
    "senderPhone": null,
    "senderBirthday": null,
    "senderGender": null,
    "senderZipCode": null,
    "senderBankCode": null,
    "senderPaymentSystem": null,
    "senderCardNumberMask": null,
    "externalCardToken": "tmkEYenZSa8FV03aawVXxbep"
}
```
