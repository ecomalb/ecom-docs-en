---
description: '{{url}}/ecom/execute_request/payments/v1/execute/preauth'
---

# Pre-authorization Request (Preauth) — Step 2

#### Input Parameters

| operationId         | The operation ID received during Step 1 (initial request).                                                                                                                                                                                                                                                                                                                                                                                    | `string` | Yes                                   | `1697008393082nW0c1jr6KVv`                 |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------------------------------------- | ------------------------------------------ |
| encryptedCardData   | <p>Card expiration date (YYMM) and CVV2 encrypted in JWE.</p><p><br></p><p><em>Format:</em> The first 4 symbols are ExpDate (YYMM), the next 3 symbols are CVV.</p><p><br></p><p>Conditional Logic:</p><p><br></p><p>1. If <code>txnType</code> (from Step 1) was <code>NONCVV</code>/<code>noncvv</code>, send only YYMM.</p><p><br></p><p>2. Otherwise (if <code>txnType</code> was omitted), you must send the data in YYMMCVV format.</p> | `string` | Yes                                   | `2503111` (Decrypted view, format YYMMCVV) |
| date                | Payment date and time.                                                                                                                                                                                                                                                                                                                                                                                                                        | `string` | Yes                                   | `{{currentdateT}}.00+00:00`                |
| browserInfo         | Object containing browser data. Required if the operation requires 3DS (i.e., if Step 1 returned `status: REQUIRED_3DS`).                                                                                                                                                                                                                                                                                                                     | `object` | Conditional (Yes, if 3DS is required) |                                            |
| browserAcceptHeader | HTTP Accept header of the request.                                                                                                                                                                                                                                                                                                                                                                                                            | `string` | Conditional                           | `text/html,application/xhtml+xml...`       |
| browserUserAgent    | Browser software element identifying the user's system.                                                                                                                                                                                                                                                                                                                                                                                       | `string` | Conditional                           | `Mozilla/5.0 (Windows NT 10.0...`          |
| browserLanguage     | Browser language.                                                                                                                                                                                                                                                                                                                                                                                                                             | `string` | Conditional                           | `en-US,en`                                 |
| browserColorDepth   | Screen color depth value in the browser.                                                                                                                                                                                                                                                                                                                                                                                                      | `string` | Conditional                           | `24`                                       |
| browserScreenHeight | Browser window viewport height.                                                                                                                                                                                                                                                                                                                                                                                                               | `string` | Conditional                           | `800`                                      |
| browserScreenWidth  | Browser window viewport width.                                                                                                                                                                                                                                                                                                                                                                                                                | `string` | Conditional                           | `1280`                                     |
| browserTZ           | Browser Timezone offset in minutes.                                                                                                                                                                                                                                                                                                                                                                                                           | `string` | Conditional                           | `-180`                                     |

#### Output Parameters

| type                    | transaction type                                                                                                                                                                                        | string | PREAUTH                                                                                                         |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | --------------------------------------------------------------------------------------------------------------- |
| rrn                     | rrn transaction number in MPS                                                                                                                                                                           | string | 2554256963                                                                                                      |
| purpose                 | payment destination                                                                                                                                                                                     | string | For goods                                                                                                       |
| comment                 | comment                                                                                                                                                                                                 | string | test                                                                                                            |
| coinAmount              | Payment amount                                                                                                                                                                                          | int    | 2000                                                                                                            |
| merchantId              | Merchant ID generated in Ecom                                                                                                                                                                           | string | 137d9304-0368-11ed-b939-0242ac120002                                                                            |
| operationId             | Transaction ID                                                                                                                                                                                          | string | 1712844596346b9F-WwrWZpq                                                                                        |
| ecomOperationId         | Transaction ID in the Ecom system                                                                                                                                                                       | string | 8c3303e9-7396-43b8-af4e-31d9facdde9b                                                                            |
| merchantName            | Merchant name                                                                                                                                                                                           | string | KB test terminal                                                                                                |
| approvalCode            | Authorization code (present on `SUCCESS`).                                                                                                                                                              | string | 39203                                                                                                           |
| status                  | <p>Transaction status.</p><p><br></p><p><em>Possible Values: <code>SUCCESS</code>, <code>FAIL</code>, <code>PENDING</code>, <code>REQUIRED_3DS</code>, <code>DESIRED_THREEDS_MODE_ERROR</code></em></p> | string | SUCCESS                                                                                                         |
| transactionType         | Transaction type in numerical form                                                                                                                                                                      | string | 195                                                                                                             |
| merchantRequestId       | Merchant ID                                                                                                                                                                                             | string | 72837906-f526-4aef-8d11-58d80b44cb75                                                                            |
| transactionCurrency     | Payment currency                                                                                                                                                                                        | string | 980                                                                                                             |
| merchantCommission      | Commission amount                                                                                                                                                                                       | string | 2                                                                                                               |
| creationDateTime        | Transaction creation date                                                                                                                                                                               | string | 2024.09.19 15:29:25.675                                                                                         |
| modificationDateTime    | Transaction modification date                                                                                                                                                                           | string | 2024.09.19 15:29:25.675                                                                                         |
| actionCode              | response code                                                                                                                                                                                           | string | 0                                                                                                               |
| responseCode            | Response details                                                                                                                                                                                        | string | 0                                                                                                               |
| description             | Response description                                                                                                                                                                                    | string | approved                                                                                                        |
| bankCode                | Issuer bank name                                                                                                                                                                                        | string | BANK\_ALLIANCE                                                                                                  |
| paymentSystem           | Issuer MPS name                                                                                                                                                                                         | string | MasterCard                                                                                                      |
| productType             | Terminal product type                                                                                                                                                                                   | string | PURCHASE                                                                                                        |
| notificationUrl         | URL to which the CallBack is sent                                                                                                                                                                       | string | [https://merchant.notification\_url/](https://merchant.notification_url/)                                       |
| paymentServiceType      | Payment type                                                                                                                                                                                            | string | CARD/APPLE\_PAY/GOOGLE\_PAY                                                                                     |
| notificationEncryption  | Callback data encryption feature                                                                                                                                                                        | string | true/false If the parameter is not passed or false is passed, then the data in the CallBack will be unencrypted |
| cardNumberMask          | Masked card number                                                                                                                                                                                      | string | 5573\*\*\*\*\*\*\*\*0304                                                                                        |
| desiredThreeDSMode      | A feature that indicates whether the merchant wants to use the 3DS in the purchase or not                                                                                                               | string | MUST/SHOULD/MUST\_NOT                                                                                           |
| threeDSMode             | A parameter that indicates whether a 3DS is used in the purchase or not                                                                                                                                 | string | MUST- pay with 3DS MUST\_NOT- pay without 3DS                                                                   |
| statusThreeDs           | 3DS holding status                                                                                                                                                                                      | string | Y - successful 3ds N - unsuccessful 3ds                                                                         |
| threeDSServerTransId    | Id of the transaction in the 3ds system                                                                                                                                                                 | string | 8a811df4-91e0-436b-a9ac-9b0772c96f28                                                                            |
| acsTransId              | Id of the transaction in the ACS system                                                                                                                                                                 | string | 3e17fabb-71e6-498e-8794-ef8c95c5ba6f                                                                            |
| dsTransId               | Transaction ID generated by Directory Server                                                                                                                                                            | string | 12ebc556-82d3-4e35-9fb8-77ac18b050ea                                                                            |
| eci                     | Electronic Commerce Indicator A code that indicates the security level of a transaction                                                                                                                 | string | 02                                                                                                              |
| processingMerchantId    | Id of the merchant in PC                                                                                                                                                                                | string | AE100000                                                                                                        |
| processingTerminalId    | Id of the terminal in the PS                                                                                                                                                                            | string | AE100000                                                                                                        |
| redirect3dsUrl          | URL for customer redirection for 3DS authentication (present if `status` is `REQUIRED_3DS`).                                                                                                            | string | `https://api-ecom-release...`                                                                                   |
| txnType                 | Under the type of transaction                                                                                                                                                                           | string | Possible values: NONCVV/noncvv- upon receipt of a given value of cvv input and its verification does not occur  |
| senderCustomerId        | Id of the sender's client                                                                                                                                                                               | string | 1258728c1                                                                                                       |
| senderFirstName         | Sender's first name                                                                                                                                                                                     | string | Ivanenko                                                                                                        |
| senderLastName          | Sender's last name                                                                                                                                                                                      | string | Ivan                                                                                                            |
| senderMiddleName        | Sender's middle name                                                                                                                                                                                    | string | Ivanovich                                                                                                       |
| senderEmail             | Sender's mail                                                                                                                                                                                           | string | mail@gmail.com                                                                                                  |
| senderCountry           | Sender's country                                                                                                                                                                                        | string | Ukraine                                                                                                         |
| senderRegion            | Sender's area                                                                                                                                                                                           | string | Kyivska                                                                                                         |
| senderCity              | Sender's city                                                                                                                                                                                           | string | Kyiv                                                                                                            |
| senderStreet            | Sender's street                                                                                                                                                                                         | string | Sichovykh strilʹtsiv                                                                                            |
| senderAdditionalAddress | Additional data of the sender's address (floor, house number, apartment)                                                                                                                                | string | 23                                                                                                              |
| senderItn               | Sender's tax identification number.                                                                                                                                                                     | string | 123456789                                                                                                       |
| senderPassport          | Sender's passport number.                                                                                                                                                                               | string | АН123456                                                                                                        |
| senderIp                | Sender's IP address.                                                                                                                                                                                    | string | 123.12.12.12                                                                                                    |
| senderPhone             | Sender's phone number.                                                                                                                                                                                  | string | 380630000000                                                                                                    |
| senderBirthday          | Sender's date of birth                                                                                                                                                                                  | string | 31.12.2000                                                                                                      |
| senderGender            | Sender's gender                                                                                                                                                                                         | string | M                                                                                                               |
| senderZipCode           | Sender's postal code                                                                                                                                                                                    | string | 12000                                                                                                           |
| senderBankCode          | The name of the sender's issuing bank                                                                                                                                                                   | string | BANK\_ALLIANCE                                                                                                  |
| senderPaymentSystem     | The name of the sender's issuer                                                                                                                                                                         | string | MasterCard                                                                                                      |
| senderCardNumberMask    | masked card number of the sender                                                                                                                                                                        | string | 5573\*\*\*\*\*\*\*\*0304                                                                                        |
| preAuthExpDate          | Pre-authorization expiration date and time.                                                                                                                                                             | string | 2025.10.07 14:27:00.000                                                                                         |

#### Request and Response Examples

**Example Request Body**

```json
{
    "operationId": "{{operationIdT}}",
    "encryptedCardData": "{{encryptedDateAndSecurityT}}",
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

**Example Response Body (Successful, No 3DS Required)**

This response indicates that the transaction was completed successfully without 3DS involvement.

JSON

```json
{
    "type": "PREAUTH",
    "rrn": "410114186775",
    "purpose": "purpose",
    "comment": "comment",
    "coinAmount": 1000,
    "merchantId": "137d9304-0368-11ed-b939-0242ac120002",
    "operationId": "17127594157429eggOuxH5yl",
    "ecomOperationId": "63feb70f-8eb0-43cc-96c3-2e2eea9cec1e",
    "merchantName": null,
    "approvalCode": null,
    "status": "SUCCESS",
    "transactionType": 195,
    "merchantRequestId": "1d4787d6-75cb-4c75-8466-59cc698e7bbf",
    "transactionCurrency": "980",
    "merchantCommission": null,
    "createDateTime": "2024.09.19 15:29:25.675",
    "modificationDateTime": "2024.09.19 15:29:25.675",
    "transactionResponseInfo": {
        "actionCode": null,
        "responseCode": null,
        "description": "Операція успішна"
    },
    "bankCode": null,
    "paymentSystem": null,
    "productType": "PURCHASE",
    "preAuthExpDate": "2025-10-07 14:27:00.00+03:00",
    "paymentServiceType": "CARD",
    "notificationEncryption": false,
    "cardNumberMask": null,
    "desiredThreeDSMode": "MUST_NOT",
    "threeDSMode": "MUST_NOT",
    "statusThreeDs": null,
    "threeDSServerTransId": null,
    "redirect3dsUrl": null,
    "txnType": "NONCVV",
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

**Example Response Body (3DS Required for Execution)**

This status means the client must proceed with the 3DS authentication flow (Step 3).

```json
{
    "type": "PREAUTH",
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
    "transactionType": 195,
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
    "preAuthExpDate": "2025-10-07 14:27:00.00+03:00",
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
