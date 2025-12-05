---
description: '{{url}}/ecom/execute_request/payments/v1/execute/preauth'
---

# Pre-authorization Request (Preauth) — Step 2

#### Input Parameters

| **Parameter Name**  | **Type / Format** | **Required**                          | **Description / Constraints**                                                                                                                                                                                                                                                                                                                                                                                                                 | **Example**                                |
| ------------------- | ----------------- | ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| operationId         | `string`          | Yes                                   | The operation ID received during Step 1 (initial request).                                                                                                                                                                                                                                                                                                                                                                                    | `1697008393082nW0c1jr6KVv`                 |
| encryptedCardData   | `string`          | Yes                                   | <p>Card expiration date (YYMM) and CVV2 encrypted in JWE.</p><p><br></p><p><em>Format:</em> The first 4 symbols are ExpDate (YYMM), the next 3 symbols are CVV.</p><p><br></p><p>Conditional Logic:</p><p><br></p><p>1. If <code>txnType</code> (from Step 1) was <code>NONCVV</code>/<code>noncvv</code>, send only YYMM.</p><p><br></p><p>2. Otherwise (if <code>txnType</code> was omitted), you must send the data in YYMMCVV format.</p> | `2503111` (Decrypted view, format YYMMCVV) |
| date                | `string`          | Yes                                   | Payment date and time.                                                                                                                                                                                                                                                                                                                                                                                                                        | `{{currentdateT}}.00+00:00`                |
| browserInfo         | `object`          | Conditional (Yes, if 3DS is required) | Object containing browser data. Required if the operation requires 3DS (i.e., if Step 1 returned `status: REQUIRED_3DS`).                                                                                                                                                                                                                                                                                                                     |                                            |
| browserAcceptHeader | `string`          | Conditional                           | HTTP Accept header of the request.                                                                                                                                                                                                                                                                                                                                                                                                            | `text/html,application/xhtml+xml...`       |
| browserUserAgent    | `string`          | Conditional                           | Browser software element identifying the user's system.                                                                                                                                                                                                                                                                                                                                                                                       | `Mozilla/5.0 (Windows NT 10.0...`          |
| browserLanguage     | `string`          | Conditional                           | Browser language.                                                                                                                                                                                                                                                                                                                                                                                                                             | `en-US,en`                                 |
| browserColorDepth   | `string`          | Conditional                           | Screen color depth value in the browser.                                                                                                                                                                                                                                                                                                                                                                                                      | `24`                                       |
| browserScreenHeight | `string`          | Conditional                           | Browser window viewport height.                                                                                                                                                                                                                                                                                                                                                                                                               | `800`                                      |
| browserScreenWidth  | `string`          | Conditional                           | Browser window viewport width.                                                                                                                                                                                                                                                                                                                                                                                                                | `1280`                                     |
| browserTZ           | `string`          | Conditional                           | Browser Timezone offset in minutes.                                                                                                                                                                                                                                                                                                                                                                                                           | `-180`                                     |

#### Output Parameters

The output parameters are largely the same as Step 1. Key fields for status tracking are:

| **Parameter Name**     | **Type** | **Description / Possible Values**                                                                                                                                                                       | **Example**                   |
| ---------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------- |
| status                 | `string` | <p>Transaction status.</p><p><br></p><p><em>Possible Values: <code>SUCCESS</code>, <code>FAIL</code>, <code>PENDING</code>, <code>REQUIRED_3DS</code>, <code>DESIRED_THREEDS_MODE_ERROR</code></em></p> | `SUCCESS`                     |
| approvalCode           | `string` | Authorization code (present on `SUCCESS`).                                                                                                                                                              | `39203`                       |
| redirect3dsUrl         | `string` | URL for customer redirection for 3DS authentication (present if `status` is `REQUIRED_3DS`).                                                                                                            | `https://api-ecom-release...` |
| statusThreeDs          | `string` | 3DS execution status. (Y - successful 3DS, N - unsuccessful 3DS)                                                                                                                                        | `Y`                           |
| description            | `string` | Response description.                                                                                                                                                                                   | `approved`                    |
| notificationEncryption | `string` | CallBack data encryption indicator.                                                                                                                                                                     | `true/false`                  |

***

#### Request and Response Examples

**Example Request Body**

JSON

```
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

```
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
    // ... remaining fields ...
    "externalCardToken": "tmkEYenZSa8FV03aawVXxbep"
}
```

**Example Response Body (3DS Required for Execution)**

This status means the client must proceed with the 3DS authentication flow (Step 3).

JSON

```
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
    // ... remaining fields ...
    "externalCardToken": "tmkEYenZSa8FV03aawVXxbep"
}
```
