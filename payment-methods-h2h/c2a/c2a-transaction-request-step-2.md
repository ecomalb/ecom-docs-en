---
description: '{{url}}/ecom/execute_request/payments/v1/execute/card_to_account'
---

# C2A Transaction Request - Step 2

## **Input Parameters:**

<table data-header-hidden><thead><tr><th width="151"></th><th width="144"></th><th></th><th></th><th></th></tr></thead><tbody><tr><td>Parameter</td><td>Description</td><td>Data Format</td><td>Required</td><td>Example</td></tr><tr><td>operationId</td><td>Operation ID received in Step 1</td><td>string</td><td>Yes</td><td>137d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>encryptedCardData</td><td>Expiry date and CVV2 encrypted in JWE (first 4 chars ExpDate, next 3 chars CVV)</td><td>string</td><td>Yes</td><td>2503111 (decrypted view)</td></tr><tr><td>date</td><td>Payment date and time</td><td>string</td><td>Yes</td><td>{{currentdateT}}.00+00:00</td></tr><tr><td>browserInfo</td><td>Browser-related data object</td><td>object</td><td>Yes, if 3DS required</td><td></td></tr><tr><td>browserAcceptHeader</td><td>HTTP request header</td><td>string</td><td>Yes, if 3DS required</td><td>text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,...</td></tr><tr><td>browserUserAgent</td><td>User agent string</td><td>string</td><td>Yes, if 3DS required</td><td>Mozilla/5.0 (Windows NT 10.0; Win64; x64)...</td></tr><tr><td>browserLanguage</td><td>Browser language</td><td>string</td><td>Yes, if 3DS required</td><td>en-US,en</td></tr><tr><td>browserColorDepth</td><td>Screen color depth</td><td>string</td><td>Yes, if 3DS required</td><td>24</td></tr><tr><td>browserScreenHeight</td><td>Browser window height</td><td>string</td><td>Yes, if 3DS required</td><td>800</td></tr><tr><td>browserScreenWidth</td><td>Browser window width</td><td>string</td><td>Yes, if 3DS required</td><td>1280</td></tr><tr><td>browserTZ</td><td>Browser timezone</td><td>string</td><td>Yes, if 3DS required</td><td>-180</td></tr></tbody></table>

## **Output Parameters:**

| Parameter                  | Description                                                           | Data Format               | Example                                                                      |
| -------------------------- | --------------------------------------------------------------------- | ------------------------- | ---------------------------------------------------------------------------- |
| type                       | Transaction type                                                      | string                    | CARD\_2\_ACCOUNT                                                             |
| rrn                        | Transaction RRN number in MPS                                         | string                    | 2554256963                                                                   |
| purpose                    | Payment purpose                                                       | string                    | For goods                                                                    |
| comment                    | Transaction comment                                                   | string                    | test                                                                         |
| coinAmount                 | Payment amount                                                        | int                       | 2000                                                                         |
| merchantId                 | Merchant ID                                                           | string                    | 137d9304-0368-11ed-b939-0242ac120002                                         |
| operationId                | Transaction ID                                                        | string                    | 1712844596346b9F-WwrWZpq                                                     |
| ecomOperationId            | Transaction ID in Ecom system                                         | string                    | 8c3303e9-7396-43b8-af4e-31d9facdde9b                                         |
| merchantName               | Merchant name                                                         | string                    | KB test terminal                                                             |
| approvalCode               | Authorization code                                                    | string                    | 39203                                                                        |
| status                     | Transaction status                                                    | string                    | SUCCESS, FAIL, PENDING, REQUIRED\_3DS, DESIRED\_THREEDS\_MODE\_ERROR         |
| transactionType            | Transaction type (numeric)                                            | string                    | 62                                                                           |
| merchantRequestId          | Merchant request ID                                                   | string                    | 72837906-f526-4aef-8d11-58d80b44cb75                                         |
| transactionCurrency        | Payment currency                                                      | string                    | 980                                                                          |
| merchantCommission         | Merchant commission amount                                            | string                    | 2                                                                            |
| createDateTime             | Payment creation date and time                                        | string                    | 19.09.2024 15:29                                                             |
| modificationDateTime       | Payment modification date and time                                    | string                    | 19.09.2024 15:29                                                             |
| actionCode                 | Response code                                                         | string                    | 0                                                                            |
| responseCode               | Response details                                                      | string                    | 0                                                                            |
| description                | Response description                                                  | string                    | approved                                                                     |
| bankCode                   | Issuer bank name                                                      | string                    | BANK\_ALLIANCE                                                               |
| paymentSystem              | Issuer MPS name                                                       | string                    | MasterCard                                                                   |
| productType                | Terminal product type                                                 | string                    | C2A                                                                          |
| notificationUrl            | Callback notification URL                                             | string                    | https://merchant.notification\_url/                                          |
| paymentServiceType         | Payment type                                                          | string                    | CARD/APPLE\_PAY/GOOGLE\_PAY                                                  |
| notificationEncryption     | Callback data encryption flag                                         | string                    | true/false                                                                   |
| cardNumberMask             | Masked card number                                                    | string                    | 5573\*\*\*\*\*\*\*\*0304                                                     |
| desiredThreeDSMode         | Merchant preference for 3DS usage                                     | string                    | MUST/SHOULD/MUST\_NOT                                                        |
| threeDSMode                | Whether 3DS was used                                                  | string                    | MUST, MUST\_NOT                                                              |
| statusThreeDs              | 3DS transaction status                                                | string                    | Y, N                                                                         |
| threeDSServerTransId       | 3DS system transaction ID                                             | string                    | b6c35fdb-28c1-454d-a2f3-51098c26bda4                                         |
| redirect3dsUrl             | URL for client redirection for 3DS authentication                     | string                    | https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/... |
| txnType                    | Transaction subtype.                                                  | enum                      | NONCVV/noncvv                                                                |
| customerData               | Object containing customer details.                                   | object                    | -                                                                            |
| senderCustomerId           | Sender's customer ID.                                                 | string (255)              | 1258728c1                                                                    |
| senderFirstName            | Sender's first name.                                                  | <p>​</p><p>string(30)</p> | Ivanenko                                                                     |
| senderLastName             | Sender's last name.                                                   | <p>​</p><p>string(30)</p> | Ivan                                                                         |
| senderMiddleName           | Sender's middle name.                                                 | <p>​</p><p>string(30)</p> | Ivanovich                                                                    |
| senderEmail                | Sender's email.                                                       | string (256)              | mail@gmail.com                                                               |
| senderCountry              | Sender's country.                                                     | string (3) ISO 3166       | 804                                                                          |
| senderRegion               | Sender's region.                                                      | string (255)              | Kyivska                                                                      |
| senderCity                 | Sender's city.                                                        | string (25)               | Kyiv                                                                         |
| senderStreet               | Sender's street.                                                      | string (35)               | Sichovykh Striltsiv                                                          |
| senderAdditionalAddress    | Additional address data (floor, house number, apartment).             | string (255)              | 23                                                                           |
| senderItn                  | Sender's tax ID.                                                      | string (20)               | 123456789                                                                    |
| senderPassport             | Sender's passport.                                                    | string (255)              | AN123456                                                                     |
| senderIp                   | Sender's IP address.                                                  | string (50)               | 123.12.12.12                                                                 |
| senderPhone                | Sender's phone number.                                                | string (20)               | 3,81E+11                                                                     |
| senderBirthday             | Sender's date of birth.                                               | string (50)               | 31.12.2000                                                                   |
| senderGender               | Sender's gender.                                                      | string (50)               | Male/Female                                                                  |
| senderZipCode              | Sender's postal code.                                                 | string (50)               | 49000                                                                        |
| recipientCustomerId        | Recipient's client id                                                 | ​string(30)               | 1258728c1                                                                    |
| recipientFirstName         | Recipient's first name                                                | ​string(30)               | Ivanenko                                                                     |
| recipientLastName          | Recipient's last name                                                 | ​string(30)               | Ivan                                                                         |
| recipientMiddleName        | Recipient's middle name                                               | string(30)                | Ivanovich                                                                    |
| recipientEmail             | Recipient's email                                                     | string                    | mail@gmail.com                                                               |
| recipientСountry           | Recipient's county                                                    | string                    | 804                                                                          |
| recipientRegion            | Recipient's region                                                    | string                    | Kyivska                                                                      |
| recipientСity              | Recipient's city                                                      | string                    | Kyiv                                                                         |
| recipientStreet            | Recipient's street                                                    | string                    | Sichovykh Striltsiv                                                          |
| recipientAdditionalAddress | Recipient's additional address data (floor, house number, apartment). | string                    | 23                                                                           |
| recipientItn               | Recipient's tax ID.                                                   | string                    | 123456789                                                                    |
| recipientPassport          | Recipient's passport                                                  | string                    | AN123456                                                                     |
| recipientIp                | Recipient's IP address.                                               | string                    | 123.12.12.12                                                                 |
| recipientPhone             | Recipient's phone number                                              | string                    | 3,81E+11                                                                     |
| recipientBirthday          | Recipient's date of birth.                                            | string                    | 31.12.2000                                                                   |
| recipientGender            | Recipient's gender                                                    | string                    | Male/Female                                                                  |
| recipientZipCode           | Recipient's zip code                                                  | string                    | 49000                                                                        |
| recipientBankCode          | Recipient's issuing bank                                              | string                    | BANK\_ALLIANCE                                                               |
| recipientPaymentSystem     | Recipient's payment system                                            | string                    | MasterCard                                                                   |
| recipientCardNumberMask    | Recipient's masked card number                                        | string                    | 5573\*\*\*\*\*\*\*\*0304                                                     |
| externalCardToken          | Token id                                                              | string                    | tmkEYenZSa8FV03aawVXxbep                                                     |

## **Example Request Body**&#x20;

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

## Example response body without 3DS

```json
{
    "type": "CARD_2_ACCOUNT",
    "rrn": "410208187342",
    "purpose": "purpose",
    "comment": "comment",
    "coinAmount": 1010,
    "merchantId": "137d9304-0368-11ed-b939-0242ac120002",
    "operationId": "1712823122106xnUK8T9Z9d8",
    "ecomOperationId": "a4842af1-ab80-4685-9cef-0d97aedbb99f",
    "merchantName": null,
    "approvalCode": null,
    "status": "SUCCESS",
    "transactionType": 62,
    "merchantRequestId": "0d7a190d-9cfc-4b01-9615-e207ebe8b23b",
    "transactionCurrency": "980",
    "merchantCommission": 67,
    "createDateTime": "2024.09.19 15:29:25.675",
    "modificationDateTime": "2024.09.19 15:29:25.675",
    "transactionResponseInfo": {
        "actionCode": null,
        "responseCode": null,
        "description": "Операція успішна"
    },
    "bankCode": null,
    "paymentSystem": null,
    "productType": "C2A",
    "paymentServiceType": "CARD",
    "notificationEncryption": false,
    "senderCardNumberMask": null,
    "desiredThreeDSMode": "MUST_NOT",
    "threeDSMode": "MUST_NOT",
    "statusThreeDs": null,
    "threeDSServerTransId": null,
    "redirect3dsUrl": null,
    "recipientAccount": null,
    "senderCustomerId": null,
    "senderFirstName": "FirstName",
    "senderLastName": "Name",
    "senderMiddleName": null,
    "senderEmail": null,
    "senderCountry": "Ukraine",
    "senderRegion": null,
    "senderCity": "City",
    "senderStreet": "Str.",
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
    "recipientCustomerId": null,
    "recipientFirstName": null,
    "recipientLastName": null,
    "recipientMiddleName": null,
    "recipientEmail": null,
    "recipientCountry": null,
    "recipientRegion": null,
    "recipientCity": null,
    "recipientStreet": null,
    "recipientAdditionalAddress": null,
    "recipientItn": null,
    "recipientPassport": null,
    "recipientIp": null,
    "recipientPhone": null,
    "recipientBirthday": null,
    "recipientGender": null,
    "recipientZipCode": null,
    "externalCardToken": "tmkEYenZSa8FV03aawVXxbep"
}
```

## Example of response body from 3DS

```json
{
    "type": "CARD_2_ACCOUNT",
    "rrn": null,
    "purpose": "purpose",
    "comment": "comment",
    "coinAmount": 1010,
    "merchantId": "137d9304-0368-11ed-b939-0242ac120002",
    "operationId": "1712823334404zicRAYWIAm1",
    "ecomOperationId": "412ac336-aac5-43b5-8d35-b57ffa9d53ff",
    "merchantName": null,
    "approvalCode": null,
    "status": "REQUIRED_3DS",
    "transactionType": 62,
    "merchantRequestId": "60cb4f84-add5-48c6-984f-7b20a6b50c75",
    "transactionCurrency": "980",
    "merchantCommission": 67,
    "createDateTime": "2024.09.19 15:29:25.675",
    "modificationDateTime": "2024.09.19 15:29:25.675",
    "transactionResponseInfo": {
        "actionCode": null,
        "responseCode": null,
        "description": null
    },
    "bankCode": null,
    "paymentSystem": null,
    "productType": "C2A",
    "paymentServiceType": "CARD",
    "notificationEncryption": false,
    "senderCardNumberMask": null,
    "desiredThreeDSMode": "MUST",
    "threeDSMode": "MUST",
    "statusThreeDs": null,
    "threeDSServerTransId": "db259063-61ba-4681-a7e9-65fbbebead2d",
    "redirect3dsUrl": "https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1712823334404zicRAYWIAm1",
    "recipientAccount": null,
    "senderCustomerId": null,
    "senderFirstName": "FirstName",
    "senderLastName": "Name",
    "senderMiddleName": null,
    "senderEmail": null,
    "senderCountry": "Ukraine",
    "senderRegion": null,
    "senderCity": "City",
    "senderStreet": "Str.",
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
    "recipientCustomerId": null,
    "recipientFirstName": null,
    "recipientLastName": null,
    "recipientMiddleName": null,
    "recipientEmail": null,
    "recipientCountry": null,
    "recipientRegion": null,
    "recipientCity": null,
    "recipientStreet": null,
    "recipientAdditionalAddress": null,
    "recipientItn": null,
    "recipientPassport": null,
    "recipientIp": null,
    "recipientPhone": null,
    "recipientBirthday": null,
    "recipientGender": null,
    "recipientZipCode": null,
    "externalCardToken": "tmkEYenZSa8FV03aawVXxbep"
}
```
