---
description: '{{url}}/ecom/execute_request/payments/v1/google_pay_3ds/card_to_account'
---

# C2A request Step 2 (3DS)

## Input JSON parameters:

<table data-header-hidden><thead><tr><th></th><th></th><th width="136"></th><th width="131"></th><th></th></tr></thead><tbody><tr><td>Parameter</td><td>Description</td><td>Data Format</td><td>Required</td><td>Example</td></tr><tr><td>operationId</td><td>Operation ID received in Step 1</td><td>string</td><td>Yes</td><td>137d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>date</td><td>Payment date and time</td><td>string</td><td>Yes</td><td>{{currentdateT}}.00+00:00</td></tr><tr><td>browserInfo</td><td>Browser-related data object</td><td>object</td><td>Yes, if 3DS required</td><td></td></tr><tr><td>browserAcceptHeader</td><td>HTTP request header</td><td>string</td><td>Yes, if 3DS required</td><td>text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,...</td></tr><tr><td>browserUserAgent</td><td>User agent string</td><td>string</td><td>Yes, if 3DS required</td><td>Mozilla/5.0 (Windows NT 10.0; Win64; x64)...</td></tr><tr><td>browserLanguage</td><td>Browser language</td><td>string</td><td>Yes, if 3DS required</td><td>en-US,en</td></tr><tr><td>browserColorDepth</td><td>Screen color depth</td><td>string</td><td>Yes, if 3DS required</td><td>24</td></tr><tr><td>browserScreenHeight</td><td>Browser window height</td><td>string</td><td>Yes, if 3DS required</td><td>800</td></tr><tr><td>browserScreenWidth</td><td>Browser window width</td><td>string</td><td>Yes, if 3DS required</td><td>1280</td></tr><tr><td>browserTZ</td><td>Browser timezone</td><td>string</td><td>Yes, if 3DS required</td><td>-180</td></tr></tbody></table>

## Output JSON parameters:

| Parameter                  | Description                                                                 | Data Format         | Example                                                                                                         |
| -------------------------- | --------------------------------------------------------------------------- | ------------------- | --------------------------------------------------------------------------------------------------------------- |
| type                       | Transaction type.                                                           | string              | CARD\_2\_ACCOUNT                                                                                                |
| rrn                        | Transaction RRN number in MPS.                                              | string              | 2,55E+09                                                                                                        |
| purpose                    | Payment purpose.                                                            | string              | For goods                                                                                                       |
| comment                    | Comment.                                                                    | string              | Test                                                                                                            |
| coinAmount                 | Payment amount.                                                             | int                 | 2000                                                                                                            |
| merchantId                 | Merchant ID.                                                                | string              | 137d9304-0368-11ed-b939-0242ac120002                                                                            |
| operationId                | Transaction ID.                                                             | string              | 1712844596346b9F-WwrWZpq                                                                                        |
| ecomOperationId            | Ecom system transaction ID.                                                 | string              | 8c3303e9-7396-43b8-af4e-31d9facdde9b                                                                            |
| merchantName               | Merchant's name.                                                            | string              | KB test terminal                                                                                                |
| approvalCode               | Authorization code.                                                         | string              | 39203                                                                                                           |
| status                     | Transaction status.                                                         | string              | SUCCESS, FAIL, PENDING, REQUIRED\_3DS, DESIRED\_THREEDS\_MODE\_ERROR                                            |
| transactionType            | transaction type as a numeric value                                         | string              | 62                                                                                                              |
| merchantRequestId          | Merchant request id                                                         | string              | 72837906-f526-4aef-8d11-58d80b44cb75                                                                            |
| transactionCurrency        | Payment currency.                                                           | string              | 980                                                                                                             |
| merchantCommission         | Commission amount.                                                          | string              | 2                                                                                                               |
| createDateTime             | Transaction creation date.                                                  | string              | ########                                                                                                        |
| modificationDateTime       | Transaction modification date.                                              | string              | ########                                                                                                        |
| actionCode                 | Response code.                                                              | string              | 0                                                                                                               |
| responseCode               | Response details.                                                           | string              | 0                                                                                                               |
| description                | Response description.                                                       | string              | Approved                                                                                                        |
| bankCode                   | Issuing bank name.                                                          | string              | BANK\_ALLIANCE                                                                                                  |
| paymentSystem              | Issuing MPS name.                                                           | string              | MasterCard                                                                                                      |
| productType                | Terminal product type.                                                      | string              | C2A                                                                                                             |
| notificationUrl            | Callback URL.                                                               | string              | https://merchant.notification\_url/                                                                             |
| paymentServiceType         | Payment type.                                                               | string              | CARD/APPLE\_PAY/GOOGLE\_PAY                                                                                     |
| notificationEncryption     | Callback data encryption indicator.                                         | string              | true/false If the parameter is not passed or false is passed, then the data in the CallBack will be unencrypted |
| cardNumberMask             | Masked card number.                                                         | string              | 5573\*\*\*\*\*\*\*\*0304                                                                                        |
| desiredThreeDSMode         | 3DS usage preference.                                                       | string              | MUST/SHOULD/MUST\_NOT                                                                                           |
| threeDSMode                | Indicates whether 3DS was used.                                             | string              | MUST/MUST\_NOT                                                                                                  |
| statusThreeDs              | 3DS transaction status.                                                     | string              | Y - successful 3ds N - unsuccessful 3ds                                                                         |
| threeDSServerTransId       | 3DS system transaction ID.                                                  | string              | b6c35fdb-28c1-454d-a2f3-51098c26bda4                                                                            |
| acsTransId                 | ACS system transaction ID.                                                  | string              | 3e17fabb-71e6-498e-8794-ef8c95c5ba6f                                                                            |
| dsTransId                  | Directory Server transaction ID.                                            | string              | 12ebc556-82d3-4e35-9fb8-77ac18b050ea                                                                            |
| eci                        | Electronic Commerce Indicator (security level code).                        | string              | 2                                                                                                               |
| processingMerchantId       | Merchant ID in processing center.                                           | string              | AE100000                                                                                                        |
| processingTerminalId       | Terminal ID in processing center.                                           | string              | AE100000                                                                                                        |
| redirect3dsUrl             | URL for redirecting the client to the issuer's page for 3DS authentication. | string              | https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1702047427621BHu5X99yDbA               |
| txnType                    | Transaction subtype.                                                        | enum                | NONCVV/noncvv                                                                                                   |
| senderCustomerId           | Sender's customer ID.                                                       | string (255)        | 1258728c1                                                                                                       |
| senderFirstName            | Sender's first name.                                                        | string(30)          | Ivanenko                                                                                                        |
| senderLastName             | Sender's last name.                                                         | string(30)          | Ivan                                                                                                            |
| senderMiddleName           | Sender's middle name.                                                       | string(30)          | Ivanovich                                                                                                       |
| senderEmail                | Sender's email.                                                             | string (256)        | mail@gmail.com                                                                                                  |
| senderCountry              | Sender's country.                                                           | string (3) ISO 3166 | 804                                                                                                             |
| senderRegion               | Sender's region.                                                            | string (255)        | Kyivska                                                                                                         |
| senderCity                 | Sender's city.                                                              | string (25)         | Kyiv                                                                                                            |
| senderStreet               | Sender's street.                                                            | string (35)         | Sichovykh Striltsiv                                                                                             |
| senderAdditionalAddress    | Additional address data (floor, house number, apartment).                   | string (255)        | 23                                                                                                              |
| senderItn                  | Sender's tax ID.                                                            | string (20)         | 1,23E+08                                                                                                        |
| senderPassport             | Sender's passport.                                                          | string (255)        | AN123456                                                                                                        |
| senderIp                   | Sender's IP address.                                                        | string (50)         | 123.12.12.12                                                                                                    |
| senderPhone                | Sender's phone number.                                                      | string (20)         | 3,81E+11                                                                                                        |
| senderBirthday             | Sender's date of birth.                                                     | string (50)         | ########                                                                                                        |
| senderGender               | Sender's gender.                                                            | string (50)         | Male/Female                                                                                                     |
| senderZipCode              | Sender's postal code.                                                       | string (50)         | 49000                                                                                                           |
| senderBankCode             | Sender's issuing bank                                                       | string              | BANK\_ALLIANCE                                                                                                  |
| senderPaymentSystem        | Sender's issuer                                                             | string              | MasterCard                                                                                                      |
| senderCardNumberMask       | Masked card number of the sender                                            | string              | 5573\*\*\*\*\*\*\*\*0304                                                                                        |
| recipientCustomerId        | Recipient's client id                                                       | ​string(30)         | 1258728c1                                                                                                       |
| recipientFirstName         | Recipient's first name                                                      | string(30)          | Ivanenko                                                                                                        |
| recipientLastName          | Recipient's last name                                                       | string(30)          | Ivan                                                                                                            |
| recipientMiddleName        | Recipient's middle name                                                     | string(30)          | Ivanovich                                                                                                       |
| recipientEmail             | Recipient's email                                                           | string              | mail@gmail.com                                                                                                  |
| recipientСountry           | Recipient's county                                                          | string              | 804                                                                                                             |
| recipientRegion            | Recipient's region                                                          | string              | Kyivska                                                                                                         |
| recipientСity              | Recipient's city                                                            | string              | Kyiv                                                                                                            |
| recipientStreet            | Recipient's street                                                          | string              | Sichovykh Striltsiv                                                                                             |
| recipientAdditionalAddress | Recipient's additional address data (floor, house number, apartment).       | string              | 23                                                                                                              |
| recipientItn               | Recipient's tax ID.                                                         | string              | 1,23E+08                                                                                                        |
| recipientPassport          | Recipient's passport                                                        | string              | AN123456                                                                                                        |
| recipientIp                | Recipient's IP address.                                                     | string              | 123.12.12.12                                                                                                    |
| recipientPhone             | Recipient's phone number                                                    | string              | 3,81E+11                                                                                                        |
| recipientBirthday          | Recipient's date of birth.                                                  | string              | ########                                                                                                        |
| recipientGender            | Recipient's gender                                                          | string              | Male/Female                                                                                                     |
| recipientZipCode           | Recipient's zip code                                                        | string              | 49000                                                                                                           |
| recipientBankCode          | Recipient's issuing bank                                                    | string              | BANK\_ALLIANCE                                                                                                  |
| recipientPaymentSystem     | Recipient's issuer                                                          | string              | MasterCard                                                                                                      |
| recipientCardNumberMask    | Masked card number of the Recipienr                                         | string              | 5573\*\*\*\*\*\*\*\*0304                                                                                        |

## An example of a request body

```json
{
    "operationId": "1705414311419tEIgRRDZSLm",
    "browserInfo": {
        "browserAcceptHeader":",
        "browserUserAgent": "",
        "browserLanguage": "",
        "browserColorDepth": "",
        "browserScreenHeight": "",
        "browserScreenWidth": "",
        "browserTZ": ""
    },
    "notificationUrl": "https://api-ecom-prod.bankalliance.ua/mock",
    "date": "{{currentdateT}}.00+00:00"
}
```

## Example of a response body

```json
{
    "type": "CARD_2_ACCOUNT",
    "rrn": null,
    "purpose": "purpose",
    "comment": "comment",
    "coinAmount": null,
    "merchantId": "137d9304-0368-11ed-b939-0242ac120002",
    "operationId": "1712843252781OgXAcDp-0Gn",
    "ecomOperationId": "ec2ce45b-9a97-4507-980a-f8249e9ef84f",
    "merchantName": null,
    "approvalCode": null,
    "status": "REQUIRED_3DS",
    "transactionType": 62,
    "merchantRequestId": "a8fec362-b5ed-42c7-b2fd-c89e9d0ec508",
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
    "productType": "C2A",
    "notificationUrl": "https://webhook.site/cbf8c83a-ee1e-47c6-899c-eca5731ff084/mock",
    "paymentServiceType": "GOOGLE_PAY",
    "notificationEncryption": false,
    "senderCardNumberMask": null,
    "desiredThreeDSMode": "MUST",
    "threeDSMode": "MUST",
    "statusThreeDs": null,
    "threeDSServerTransId": "b6c35fdb-28c1-454d-a2f3-51098c26bda4",
    "redirect3dsUrl": "https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1712843252781OgXAcDp-0Gn",
    "recipientAccount": null,
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
    "recipientZipCode": null
}
```
