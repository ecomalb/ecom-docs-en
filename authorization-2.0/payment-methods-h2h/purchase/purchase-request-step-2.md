---
description: '{{url}}/ecom/execute_request/payments/v1/execute/purchase'
---

# PURCHASE Request - Step 2

## Input Parameters:

<table data-header-hidden><thead><tr><th>Parameter</th><th width="221.800048828125">Description</th><th>Data Format</th><th width="73.4000244140625">Required</th><th>Example</th></tr></thead><tbody><tr><td>operationId</td><td>Operation ID obtained in Step 1</td><td>string</td><td>Yes</td><td>1697008393082nW0c1jr6KVv</td></tr><tr><td>encryptedCardData</td><td><p>card expiration date and cvv2 are encrypted in JWE. First 4 characters ExpDate, next 3 characters cvv</p><p></p><ul><li>If <code>"NONCVV\noncvv"</code> is passed in <code>TxnType</code> parameter then in <code>ecnryptedCardData</code> parameter only <strong>YYMM</strong> without <strong>CVV</strong> should be passed</li><li>Otherwise if nothing is passed in <code>TxnType</code> then in <strong>encryptedCardData</strong> parameter it is mandatory to pass in YYMMCVV format</li></ul></td><td>string</td><td>Yes</td><td>2503111 (decrypted format)</td></tr><tr><td>date</td><td>Payment date and time</td><td>string</td><td>Yes</td><td>{{currentdateT}}.00+00:00</td></tr><tr><td>browserInfo</td><td>Object containing browser data</td><td>object</td><td>Yes, if 3DS is required</td><td>-</td></tr><tr><td>browserAcceptHeader</td><td>HTTP request header</td><td>string</td><td>Yes, if 3DS is required</td><td>text/html,application/xhtml+xml,...</td></tr><tr><td>browserUserAgent</td><td>Browser user-agent string</td><td>string</td><td>Yes, if 3DS is required</td><td>Mozilla/5.0 (Windows NT 10.0; Win64; x64)...</td></tr><tr><td>browserLanguage</td><td>Browser language</td><td>string</td><td>Yes, if 3DS is required</td><td>en-US,en</td></tr><tr><td>browserColorDepth</td><td>Screen color depth value</td><td>string</td><td>Yes, if 3DS is required</td><td>24</td></tr><tr><td>browserScreenHeight</td><td>Browser viewport height</td><td>string</td><td>Yes, if 3DS is required</td><td>800</td></tr><tr><td>browserScreenWidth</td><td>Browser viewport width</td><td>string</td><td>Yes, if 3DS is required</td><td>1280</td></tr><tr><td>browserTZ</td><td>Browser timezone</td><td>string</td><td>Yes, if 3DS is required</td><td>-180</td></tr></tbody></table>

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
| externalCardToken       | Token id                           | string      | tmkEYenZSa8FV03aawVXxbep                                                     |

#### Приклади :

<details>

<summary>JWS Payload — тіло запиту перед підписанням</summary>

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

</details>

<details>

<summary>JWS Payload — тіло відповіді перед підписанням без 3дс</summary>

```json
{
    "type": "PURCHASE",
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
    "transactionType": 35,
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

</details>

<details>

<summary>JWS Payload — тіло відповіді перед підписанням з 3дс</summary>

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

</details>
