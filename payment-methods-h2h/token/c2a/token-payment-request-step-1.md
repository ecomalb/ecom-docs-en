---
description: '{{url}}/ecom/execute_request/payments/v1/token_card_2_terminal'
---

# Token payment request Step 1

## Input Parameters:

<table><thead><tr><th width="164">Parameter</th><th width="216">Description</th><th width="149">Data Format</th><th width="66">Required</th><th width="163">Example</th></tr></thead><tbody><tr><td>merchantRequestId</td><td>Unique identifier generated by the merchant's system, used to track the transaction status in case of an unknown error or disconnect.</td><td>string(36)</td><td>Yes</td><td>137d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>merchantId</td><td>Merchant ID generated in Ecom.</td><td>string(36)</td><td>Yes</td><td>137d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>token</td><td>card token</td><td>string</td><td>Yes</td><td>K24YmzXWbw6aCWQn3sdpk7E9</td></tr><tr><td>cvv</td><td>cvv card is encrypted in JWE</td><td>string</td><td>Yes</td><td>345 (decoded view)</td></tr><tr><td>txnType</td><td><p>The parameter is specified - cvv input and its verification does not occur</p><p>The parameter is NOT specified - cvv is entered and its verification is in progress</p></td><td>string</td><td>No</td><td><p>Possible values:</p><p>NONCVV/noncvv</p></td></tr><tr><td>typeToken</td><td>defines the type of token when it is created</td><td>string</td><td>No</td><td><p>possible values:</p><ul><li>TOKEN_PER_CUSTOMER - a token is created for a specific customer (customer)</li></ul></td></tr><tr><td>desiredThreeDSMode</td><td>Indicates whether the merchant wishes to use 3DS for the transaction.</td><td>string (50)</td><td>Yes</td><td><p>Default: SHOULD</p><ul><li>MUST - Payment must be processed with 3DS.</li></ul><ul><li>MUST_NOT - Payment must be processed without 3DS.</li></ul><ul><li>SHOULD - If the card supports 3DS, verification is performed.""Default: SHOULD.</li></ul></td></tr><tr><td>resultRedirectUrl</td><td>URL for client redirection after 3DS authentication.</td><td>string (1000)</td><td>No</td><td>https://support.google.com/</td></tr><tr><td>notificationUrl</td><td>URL to which the CallBack will be sent.</td><td>string (1000)</td><td>No</td><td>https://merchant.notification_url</td></tr><tr><td>notificationEncryption</td><td>Indicator for encrypting CallBack data.</td><td>string</td><td>No</td><td>true/false</td></tr><tr><td>merchantCommission</td><td>Commission amount.</td><td>int</td><td>No</td><td>0</td></tr><tr><td>date</td><td>Transaction date and time.</td><td>string</td><td>Yes</td><td>{{currentdateT}}.00+00:00</td></tr><tr><td>comment</td><td>Additional transaction description entered by the merchant's client.</td><td>string (1000)</td><td>No</td><td>///5555.25412</td></tr><tr><td>purpose</td><td>Payment purpose entered by the merchant.</td><td>string (255)</td><td>No</td><td>For goods</td></tr><tr><td>merchantComment</td><td>Additional order-related information/comment from the merchant.</td><td>string(255)</td><td>No</td><td>merchant Comment id 1258728c1</td></tr><tr><td>recipientAccount</td><td>Recipient's account.</td><td>string</td><td>No</td><td>2,9E+13</td></tr><tr><td>customerData</td><td>Object containing customer details.</td><td>object</td><td>Yes</td><td>-</td></tr><tr><td>senderCustomerId</td><td>Sender's customer ID.</td><td>string (255)</td><td>Yes</td><td>1258728c1</td></tr><tr><td>senderFirstName</td><td>Sender's first name.</td><td><p></p><p>string(30)</p><ul><li>the value cannot contain only numbers</li></ul><ul><li>cannot contain periods or other special characters</li></ul><ul><li>cannot contain “NULL”, “3D SECURE”, “SURNAME”, “CARDHOLDER”, ”UNKNOWN”</li></ul><ul><li>only alphanumeric values ​​are allowed</li></ul><ul><li>can accept a space and a hyphen, but can NOT consist exclusively of “ ” or “-“</li></ul><ul><li>a hyphen or space can be inside, but not at the beginning or end</li></ul><ul><li>For the apostrophe character, use the only available utf8 character - ' which in: utf 16 - u0027 utf32 - 00000027</li></ul></td><td>Yes</td><td>Ivanenko</td></tr><tr><td>senderLastName</td><td>Sender's last name.</td><td><p></p><p>string(30)</p><ul><li>the value cannot contain only numbers</li></ul><ul><li>cannot contain periods or other special characters</li></ul><ul><li>cannot contain “NULL”, “3D SECURE”, “SURNAME”, “CARDHOLDER”, ”UNKNOWN”</li></ul><ul><li>only alphanumeric values ​​are allowed</li></ul><ul><li>can accept a space and a hyphen, but can NOT consist exclusively of “ ” or “-“</li></ul><ul><li>a hyphen or space can be inside, but not at the beginning or end</li></ul><ul><li>For the apostrophe character, use the only available utf8 character - ' which in: utf 16 - u0027 utf32 - 00000027</li></ul></td><td>Yes</td><td>Ivan</td></tr><tr><td>senderMiddleName</td><td>Sender's middle name.</td><td><p></p><p>string(30)</p><ul><li>the value cannot contain only numbers</li></ul><ul><li>cannot contain periods or other special characters</li></ul><ul><li>cannot contain “NULL”, “3D SECURE”, “SURNAME”, “CARDHOLDER”, ”UNKNOWN”</li></ul><ul><li>only alphanumeric values ​​are allowed</li></ul><ul><li>can accept a space and a hyphen, but can NOT consist exclusively of “ ” or “-“</li></ul><ul><li>a hyphen or space can be inside, but not at the beginning or end</li></ul><ul><li>For the apostrophe character, use the only available utf8 character - ' which in: utf 16 - u0027 utf32 - 00000027</li></ul></td><td>No</td><td>Ivanovich</td></tr><tr><td>senderEmail</td><td>Sender's email.</td><td>string (256)</td><td>No</td><td>mail@gmail.com</td></tr><tr><td>senderCountry</td><td>Sender's country.</td><td>string (3)<br>ISO 3166</td><td>No</td><td>804</td></tr><tr><td>senderRegion</td><td>Sender's region.</td><td>string (255)</td><td>No</td><td>Kyivska</td></tr><tr><td>senderCity</td><td>Sender's city.</td><td>string (25)</td><td>No</td><td>Kyiv</td></tr><tr><td>senderStreet</td><td>Sender's street.</td><td>string (35)</td><td>No</td><td>Sichovykh Striltsiv</td></tr><tr><td>senderAdditionalAddress</td><td>Additional address data (floor, house number, apartment).</td><td>string (255)</td><td>No</td><td>23</td></tr><tr><td>senderItn</td><td>Sender's tax ID.</td><td>string (20)</td><td>No</td><td>123456789</td></tr><tr><td>senderPassport</td><td>Sender's passport.</td><td>string (255)</td><td>No</td><td>AN123456</td></tr><tr><td>senderIp</td><td>Sender's IP address.</td><td>string (50)</td><td>No</td><td>123.12.12.12</td></tr><tr><td>senderPhone</td><td>Sender's phone number.</td><td>string (20)</td><td>No</td><td>3,8063E+11</td></tr><tr><td>senderBirthday</td><td>Sender's date of birth.</td><td>string (50)</td><td>No</td><td>31.12.2000</td></tr><tr><td>senderGender</td><td>Sender's gender.</td><td>string (50)</td><td>No</td><td>Male/Female</td></tr><tr><td>senderZipCode</td><td>Sender's postal code.</td><td>string (50)</td><td>No</td><td>49000</td></tr><tr><td>recipientCustomerId</td><td>Recipient's client id</td><td><p></p><p>string(30)</p></td><td>No</td><td>1258728c1</td></tr><tr><td>recipientFirstName</td><td>Recipient's first name</td><td><p></p><p>string(30)</p><ul><li>the value cannot contain only numbers</li></ul><ul><li>cannot contain periods or other special characters</li></ul><ul><li>cannot contain “NULL”, “3D SECURE”, “SURNAME”, “CARDHOLDER”, ”UNKNOWN”</li></ul><ul><li>only alphanumeric values ​​are allowed</li></ul><ul><li>can accept a space and a hyphen, but can NOT consist exclusively of “ ” or “-“</li></ul><ul><li>a hyphen or space can be inside, but not at the beginning or end</li></ul><ul><li>For the apostrophe character, use the only available utf8 character - ' which in: utf 16 - u0027 utf32 - 00000027</li></ul></td><td>No</td><td>Ivanenko</td></tr><tr><td>recipientLastName</td><td>Recipient's last name </td><td><p></p><p>string(30)</p><ul><li>the value cannot contain only numbers</li></ul><ul><li>cannot contain periods or other special characters</li></ul><ul><li>cannot contain “NULL”, “3D SECURE”, “SURNAME”, “CARDHOLDER”, ”UNKNOWN”</li></ul><ul><li>only alphanumeric values ​​are allowed</li></ul><ul><li>can accept a space and a hyphen, but can NOT consist exclusively of “ ” or “-“</li></ul><ul><li>a hyphen or space can be inside, but not at the beginning or end</li></ul><ul><li>For the apostrophe character, use the only available utf8 character - ' which in: utf 16 - u0027 utf32 - 00000027</li></ul></td><td>No</td><td>Ivan</td></tr><tr><td>recipientMiddleName</td><td>Recipient's middle name</td><td>string</td><td>No</td><td>Ivanovich</td></tr><tr><td>recipientEmail</td><td>Recipient's email</td><td>string</td><td>No</td><td>mail@gmail.com</td></tr><tr><td>recipientСountry</td><td>Recipient's county</td><td>string</td><td>No</td><td>804</td></tr><tr><td>recipientRegion</td><td>Recipient's region</td><td>string</td><td>No</td><td>Kyivska</td></tr><tr><td>recipientСity</td><td>Recipient's city</td><td>string</td><td>No</td><td>Kyiv</td></tr><tr><td>recipientStreet</td><td>Recipient's street</td><td>string</td><td>No</td><td>Sichovykh Striltsiv</td></tr><tr><td>recipientAdditionalAddress</td><td>Recipient's additional address data (floor, house number, apartment).</td><td>string</td><td>No</td><td>23</td></tr><tr><td>recipientItn</td><td>Recipient's tax ID.</td><td>string</td><td>No</td><td>123456789</td></tr><tr><td>recipientPassport</td><td>Recipient's passport</td><td>string</td><td>No</td><td>AN123456</td></tr><tr><td>recipientIp</td><td>Recipient's IP address.</td><td>string</td><td>No</td><td>123.12.12.12</td></tr><tr><td>recipientPhone</td><td>Recipient's phone number</td><td>string</td><td>No</td><td>3,8063E+11</td></tr><tr><td>recipientBirthday</td><td>Recipient's date of birth.</td><td>string</td><td>No</td><td>31.12.2000</td></tr><tr><td>recipientGender</td><td>Recipient's gender</td><td>string</td><td>No</td><td>Male/Female</td></tr><tr><td>recipientZipCode</td><td>Recipient's zip code </td><td>string</td><td>No</td><td>49000</td></tr></tbody></table>

## Output Parameters:

| Parameter                  | Description                                                                 | Data Format               | Example                                                                                                         |
| -------------------------- | --------------------------------------------------------------------------- | ------------------------- | --------------------------------------------------------------------------------------------------------------- |
| type                       | Transaction type.                                                           | string                    | CARD\_2\_ACCOUNT                                                                                                |
| rrn                        | Transaction RRN number in MPS.                                              | string                    | 2554256963                                                                                                      |
| purpose                    | Payment purpose.                                                            | string                    | For goods                                                                                                       |
| comment                    | Comment.                                                                    | string                    | Test                                                                                                            |
| coinAmount                 | Payment amount.                                                             | int                       | 2000                                                                                                            |
| merchantId                 | Merchant ID.                                                                | string                    | 137d9304-0368-11ed-b939-0242ac120002                                                                            |
| operationId                | Transaction ID.                                                             | string                    | 1712844596346b9F-WwrWZpq                                                                                        |
| ecomOperationId            | Ecom system transaction ID.                                                 | string                    | 8c3303e9-7396-43b8-af4e-31d9facdde9b                                                                            |
| merchantName               | Merchant's name.                                                            | string                    | KB test terminal                                                                                                |
| approvalCode               | Authorization code.                                                         | string                    | 39203                                                                                                           |
| status                     | Transaction status.                                                         | string                    | SUCCESS, FAIL, PENDING, REQUIRED\_3DS, DESIRED\_THREEDS\_MODE\_ERROR                                            |
| transactionType            | transaction type as a numeric value                                         | string                    | 62                                                                                                              |
| merchantRequestId          | Merchant request id                                                         | string                    | 72837906-f526-4aef-8d11-58d80b44cb75                                                                            |
| transactionCurrency        | Payment currency.                                                           | string                    | 980                                                                                                             |
| merchantCommission         | Commission amount.                                                          | string                    | 2                                                                                                               |
| createDateTime             | Transaction creation date.                                                  | string                    | 19.09.2024 15:29                                                                                                |
| modificationDateTime       | Transaction modification date.                                              | string                    | 19.09.2024 15:29                                                                                                |
| actionCode                 | Response code.                                                              | string                    | 0                                                                                                               |
| responseCode               | Response details.                                                           | string                    | 0                                                                                                               |
| description                | Response description.                                                       | string                    | Approved                                                                                                        |
| bankCode                   | Issuing bank name.                                                          | string                    | BANK\_ALLIANCE                                                                                                  |
| paymentSystem              | Issuing MPS name.                                                           | string                    | MasterCard                                                                                                      |
| productType                | Terminal product type.                                                      | string                    | C2A                                                                                                             |
| notificationUrl            | Callback URL.                                                               | string                    | https://merchant.notification\_url/                                                                             |
| paymentServiceType         | Payment type.                                                               | string                    | CARD/APPLE\_PAY/GOOGLE\_PAY                                                                                     |
| notificationEncryption     | Callback data encryption indicator.                                         | string                    | true/false If the parameter is not passed or false is passed, then the data in the CallBack will be unencrypted |
| cardNumberMask             | Masked card number.                                                         | string                    | 5573\*\*\*\*\*\*\*\*0304                                                                                        |
| desiredThreeDSMode         | 3DS usage preference.                                                       | string                    | MUST/SHOULD/MUST\_NOT                                                                                           |
| threeDSMode                | Indicates whether 3DS was used.                                             | string                    | MUST/MUST\_NOT                                                                                                  |
| statusThreeDs              | 3DS transaction status.                                                     | string                    | Y - successful 3ds N - unsuccessful 3ds                                                                         |
| threeDSServerTransId       | 3DS system transaction ID.                                                  | string                    | b6c35fdb-28c1-454d-a2f3-51098c26bda4                                                                            |
| acsTransId                 | ACS system transaction ID.                                                  | string                    | 3e17fabb-71e6-498e-8794-ef8c95c5ba6f                                                                            |
| dsTransId                  | Directory Server transaction ID.                                            | string                    | 12ebc556-82d3-4e35-9fb8-77ac18b050ea                                                                            |
| eci                        | Electronic Commerce Indicator (security level code).                        | string                    | 2                                                                                                               |
| processingMerchantId       | Merchant ID in processing center.                                           | string                    | AE100000                                                                                                        |
| processingTerminalId       | Terminal ID in processing center.                                           | string                    | AE100000                                                                                                        |
| redirect3dsUrl             | URL for redirecting the client to the issuer's page for 3DS authentication. | string                    | https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1702047427621BHu5X99yDbA               |
| txnType                    | Transaction subtype.                                                        | enum                      | NONCVV/noncvv                                                                                                   |
| customerData               | Object containing customer details.                                         | object                    | -                                                                                                               |
| senderCustomerId           | Sender's customer ID.                                                       | string (255)              | 1258728c1                                                                                                       |
| senderFirstName            | Sender's first name.                                                        | <p>​</p><p>string(30)</p> | Ivanenko                                                                                                        |
| senderLastName             | Sender's last name.                                                         | <p>​</p><p>string(30)</p> | Ivan                                                                                                            |
| senderMiddleName           | Sender's middle name.                                                       | <p>​</p><p>string(30)</p> | Ivanovich                                                                                                       |
| senderEmail                | Sender's email.                                                             | string (256)              | mail@gmail.com                                                                                                  |
| senderCountry              | Sender's country.                                                           | string (3) ISO 3166       | 804                                                                                                             |
| senderRegion               | Sender's region.                                                            | string (255)              | Kyivska                                                                                                         |
| senderCity                 | Sender's city.                                                              | string (25)               | Kyiv                                                                                                            |
| senderStreet               | Sender's street.                                                            | string (35)               | Sichovykh Striltsiv                                                                                             |
| senderAdditionalAddress    | Additional address data (floor, house number, apartment).                   | string (255)              | 23                                                                                                              |
| senderItn                  | Sender's tax ID.                                                            | string (20)               | 123456789                                                                                                       |
| senderPassport             | Sender's passport.                                                          | string (255)              | AN123456                                                                                                        |
| senderIp                   | Sender's IP address.                                                        | string (50)               | 123.12.12.12                                                                                                    |
| senderPhone                | Sender's phone number.                                                      | string (20)               | 3,81E+11                                                                                                        |
| senderBirthday             | Sender's date of birth.                                                     | string (50)               | 31.12.2000                                                                                                      |
| senderGender               | Sender's gender.                                                            | string (50)               | Male/Female                                                                                                     |
| senderZipCode              | Sender's postal code.                                                       | string (50)               | 49000                                                                                                           |
| recipientCustomerId        | Recipient's client id                                                       | ​string(30)               | 1258728c1                                                                                                       |
| recipientFirstName         | Recipient's first name                                                      | <p>​</p><p>string(30)</p> | Ivanenko                                                                                                        |
| recipientLastName          | Recipient's last name                                                       | <p>​</p><p>string(30)</p> | Ivan                                                                                                            |
| recipientMiddleName        | Recipient's middle name                                                     | string(30)                | Ivanovich                                                                                                       |
| recipientEmail             | Recipient's email                                                           | string                    | mail@gmail.com                                                                                                  |
| recipientСountry           | Recipient's county                                                          | string                    | 804                                                                                                             |
| recipientRegion            | Recipient's region                                                          | string                    | Kyivska                                                                                                         |
| recipientСity              | Recipient's city                                                            | string                    | Kyiv                                                                                                            |
| recipientStreet            | Recipient's street                                                          | string                    | Sichovykh Striltsiv                                                                                             |
| recipientAdditionalAddress | Recipient's additional address data (floor, house number, apartment).       | string                    | 23                                                                                                              |
| recipientItn               | Recipient's tax ID.                                                         | string                    | 123456789                                                                                                       |
| recipientPassport          | Recipient's passport                                                        | string                    | AN123456                                                                                                        |
| recipientIp                | Recipient's IP address.                                                     | string                    | 123.12.12.12                                                                                                    |
| recipientPhone             | Recipient's phone number                                                    | string                    | 3,81E+11                                                                                                        |
| recipientBirthday          | Recipient's date of birth.                                                  | string                    | 31.12.2000                                                                                                      |
| recipientGender            | Recipient's gender                                                          | string                    | Male/Female                                                                                                     |
| recipientZipCode           | Recipient's zip code                                                        | string                    | 49000                                                                                                           |
| recipientBankCode          | the name of the recipient's issuing bank                                    | string                    | BANK\_ALLIANCE                                                                                                  |
| recipientPaymentSystem     | the name of the recipient's issuer                                          | string                    | MasterCard                                                                                                      |
| recipientCardNumberMask    | masked card number of the recipient                                         | string                    | 5573\*\*\*\*\*\*\*\*0304                                                                                        |
| externalCardToken          | token id                                                                    | string                    | K24YmzXWbw6aCWQn3sdpk7E9                                                                                        |

## An example of a request body

```json
{
    "merchantId":"467c8a10-c705-11ed-afa1-0242ac120002",
    "merchantRequestId": "{{requestUUIDT}}",
    "cvv": "eyJhbGciOiJFQ0RILUVTK0EyNTZLVyIsImVuYyI6IkEyNTZHQ00iLCJlcGsiOnsia3R5IjoiRUMiLCJ4IjoiZlJYSlpPOVYxSlFaTlJjNUZUdENnWWVQSGhRVGs0MEt1N0ZnQ3QxblpGYnRkSHlWVXp0Tkl0Rzh3TVdTZzNBbiIsInkiOiJZekxRZlYwM3dmRVlyTlN4M2dZUjQ3cXlnak9pNGxMNWxLV01qWktzS3ZCYXpWbmUySDBUVTBQUEd2azhvaWlBIiwiY3J2IjoiUC0zODQifX0",
    "token": "K24YmzXWbw6aCWQn3sdpk7E9",
    "coinAmount": "1000",
    "comment": "comment",
    "purpose": "purpose",
    "merchantCommission": "0",
    "desiredThreeDSMode": "MUST"
    "notificationUrl": "",
    "customerData": {
        "senderCustomerId": "1234567",
        "senderFirstName": "John",
        "senderLastName": "Doe",
        "senderMiddleName": "Fall",
        "senderEmail": "test@gmail.com",
        "senderCountry": "sender_country",
        "senderRegion": "sender_region",
        "senderCity": "sender_city",
        "senderStreet": "sender_street",
        "senderAdditionalAddress": "N 6",
        "senderItn": "12345",
        "senderPassport": "12345",
        "senderIp": "165.222.87.224",
        "senderPhone": "380967542344",
        "senderBirthday": "12/12/2000",
        "senderGender": "Male",
        "senderZipCode": "12345",
        "recipientCustomerId": "1234567",
        "recipientFirstName": "Yura",
        "recipientLastName": "Bura",
        "recipientMiddleName": "TestMiddle",
        "recipientEmail": "res@gmail",
        "recipientCountry": "804",
        "recipientRegion": "res_reg",
        "recipientCity": "res_dnipro",
        "recipientStreet": "res_street",
        "recipientAdditionalAddress": "res_addres",
        "recipientItn": "res_iin",
        "recipientPassport": "res_pasport",
        "recipientIp": "165.222.87.224",
        "recipientPhone": "380967542344",
        "recipientBirthday": "12/12/2000",
        "recipientGender": "Female",
        "recipientZipCode": "77777"
    }
    "date": "{{currentdateT}}.00+00:00"
}
```

#### Example response body without 3DS

```
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

#### Example of response body from 3DS

```
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
