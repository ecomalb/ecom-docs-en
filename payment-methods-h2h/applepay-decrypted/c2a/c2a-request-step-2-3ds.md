---
description: '{{url}}/ecom/execute_request/payments/v1/apple_pay_3ds/card_to_account'
---

# C2A request Step 2 (3DS)

## **Input JSON Parameters:**

<table data-header-hidden><thead><tr><th width="151"></th><th width="144"></th><th width="139"></th><th width="117"></th><th></th></tr></thead><tbody><tr><td>Parameter</td><td>Description</td><td>Data Format</td><td>Required</td><td>Example</td></tr><tr><td>operationId</td><td>Operation ID received in Step 1</td><td>string</td><td>Yes</td><td>137d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>date</td><td>Payment date and time</td><td>string</td><td>Yes</td><td>{{currentdateT}}.00+00:00</td></tr><tr><td>browserInfo</td><td>Browser-related data object</td><td>object</td><td>Yes, if 3DS required</td><td></td></tr><tr><td>browserAcceptHeader</td><td>HTTP request header</td><td>string</td><td>Yes, if 3DS required</td><td>text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,...</td></tr><tr><td>browserUserAgent</td><td>User agent string</td><td>string</td><td>Yes, if 3DS required</td><td>Mozilla/5.0 (Windows NT 10.0; Win64; x64)...</td></tr><tr><td>browserLanguage</td><td>Browser language</td><td>string</td><td>Yes, if 3DS required</td><td>en-US,en</td></tr><tr><td>browserColorDepth</td><td>Screen color depth</td><td>string</td><td>Yes, if 3DS required</td><td>24</td></tr><tr><td>browserScreenHeight</td><td>Browser window height</td><td>string</td><td>Yes, if 3DS required</td><td>800</td></tr><tr><td>browserScreenWidth</td><td>Browser window width</td><td>string</td><td>Yes, if 3DS required</td><td>1280</td></tr><tr><td>browserTZ</td><td>Browser timezone</td><td>string</td><td>Yes, if 3DS required</td><td>-180</td></tr></tbody></table>

## **Output Parameters:**

<table data-header-hidden><thead><tr><th></th><th></th><th width="135"></th><th></th></tr></thead><tbody><tr><td>Parameter</td><td>Description</td><td>Data Format</td><td>Example</td></tr><tr><td>type</td><td>Transaction type.</td><td>string</td><td>CARD_2_ACCOUNT</td></tr><tr><td>rrn</td><td>Transaction RRN number in MPS.</td><td>string</td><td>2554256963</td></tr><tr><td>purpose</td><td>Payment purpose.</td><td>string</td><td>For goods</td></tr><tr><td>comment</td><td>Comment.</td><td>string</td><td>Test</td></tr><tr><td>coinAmount</td><td>Payment amount.</td><td>int</td><td>2000</td></tr><tr><td>merchantId</td><td>Merchant ID.</td><td>string</td><td>137d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>operationId</td><td>Transaction ID.</td><td>string</td><td>1712844596346b9F-WwrWZpq</td></tr><tr><td>ecomOperationId</td><td>Ecom system transaction ID.</td><td>string</td><td>8c3303e9-7396-43b8-af4e-31d9facdde9b</td></tr><tr><td>merchantName</td><td>Merchant's name.</td><td>string</td><td>KB test terminal</td></tr><tr><td>approvalCode</td><td>Authorization code.</td><td>string</td><td>39203</td></tr><tr><td>status</td><td>Transaction status.</td><td>string</td><td>SUCCESS, FAIL, PENDING, REQUIRED_3DS, DESIRED_THREEDS_MODE_ERROR</td></tr><tr><td>transactionType</td><td>transaction type as a numeric value</td><td>string</td><td>62</td></tr><tr><td>merchantRequestId</td><td>Merchant request id</td><td>string</td><td>72837906-f526-4aef-8d11-58d80b44cb75</td></tr><tr><td>transactionCurrency</td><td>Payment currency.</td><td>string</td><td>980</td></tr><tr><td>merchantCommission</td><td>Commission amount.</td><td>string</td><td>2</td></tr><tr><td>createDateTime</td><td>Transaction creation date.</td><td>string</td><td>19.09.2024 15:29</td></tr><tr><td>modificationDateTime</td><td>Transaction modification date.</td><td>string</td><td>19.09.2024 15:29</td></tr><tr><td>actionCode</td><td>Response code.</td><td>string</td><td>0</td></tr><tr><td>responseCode</td><td>Response details.</td><td>string</td><td>0</td></tr><tr><td>description</td><td>Response description.</td><td>string</td><td>Approved</td></tr><tr><td>bankCode</td><td>Issuing bank name.</td><td>string</td><td>BANK_ALLIANCE</td></tr><tr><td>paymentSystem</td><td>Issuing MPS name.</td><td>string</td><td>MasterCard</td></tr><tr><td>productType</td><td>Terminal product type.</td><td>string</td><td>C2A</td></tr><tr><td>notificationUrl</td><td>Callback URL.</td><td>string</td><td>https://merchant.notification_url/</td></tr><tr><td>paymentServiceType</td><td>Payment type.</td><td>string</td><td>CARD/APPLE_PAY/GOOGLE_PAY</td></tr><tr><td>notificationEncryption</td><td>Callback data encryption indicator.</td><td>string</td><td>true/false If the parameter is not passed or false is passed, then the data in the CallBack will be unencrypted</td></tr><tr><td>cardNumberMask</td><td>Masked card number.</td><td>string</td><td>5573********0304</td></tr><tr><td>desiredThreeDSMode</td><td>3DS usage preference.</td><td>string</td><td>MUST/SHOULD/MUST_NOT</td></tr><tr><td>threeDSMode</td><td>Indicates whether 3DS was used.</td><td>string</td><td>MUST/MUST_NOT</td></tr><tr><td>statusThreeDs</td><td>3DS transaction status.</td><td>string</td><td>Y - successful 3ds N - unsuccessful 3ds</td></tr><tr><td>threeDSServerTransId</td><td>3DS system transaction ID.</td><td>string</td><td>b6c35fdb-28c1-454d-a2f3-51098c26bda4</td></tr><tr><td>acsTransId</td><td>ACS system transaction ID.</td><td>string</td><td>3e17fabb-71e6-498e-8794-ef8c95c5ba6f</td></tr><tr><td>dsTransId</td><td>Directory Server transaction ID.</td><td>string</td><td>12ebc556-82d3-4e35-9fb8-77ac18b050ea</td></tr><tr><td>eci</td><td>Electronic Commerce Indicator (security level code).</td><td>string</td><td>2</td></tr><tr><td>processingMerchantId</td><td>Merchant ID in processing center.</td><td>string</td><td>AE100000</td></tr><tr><td>processingTerminalId</td><td>Terminal ID in processing center.</td><td>string</td><td>AE100000</td></tr><tr><td>redirect3dsUrl</td><td>URL for redirecting the client to the issuer's page for 3DS authentication.</td><td>string</td><td>https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1702047427621BHu5X99yDbA</td></tr><tr><td>txnType</td><td>Transaction subtype.</td><td>enum</td><td>NONCVV/noncvv</td></tr><tr><td>customerData</td><td>Object containing customer details.</td><td>object</td><td>-</td></tr><tr><td>senderCustomerId</td><td>Sender's customer ID.</td><td>string (255)</td><td>1258728c1</td></tr><tr><td>senderFirstName</td><td>Sender's first name.</td><td><p>​</p><p>string(30)</p></td><td>Ivanenko</td></tr><tr><td>senderLastName</td><td>Sender's last name.</td><td><p>​</p><p>string(30)</p></td><td>Ivan</td></tr><tr><td>senderMiddleName</td><td>Sender's middle name.</td><td><p>​</p><p>string(30)</p></td><td>Ivanovich</td></tr><tr><td>senderEmail</td><td>Sender's email.</td><td>string (256)</td><td>mail@gmail.com</td></tr><tr><td>senderCountry</td><td>Sender's country.</td><td>string (3) ISO 3166</td><td>804</td></tr><tr><td>senderRegion</td><td>Sender's region.</td><td>string (255)</td><td>Kyivska</td></tr><tr><td>senderCity</td><td>Sender's city.</td><td>string (25)</td><td>Kyiv</td></tr><tr><td>senderStreet</td><td>Sender's street.</td><td>string (35)</td><td>Sichovykh Striltsiv</td></tr><tr><td>senderAdditionalAddress</td><td>Additional address data (floor, house number, apartment).</td><td>string (255)</td><td>23</td></tr><tr><td>senderItn</td><td>Sender's tax ID.</td><td>string (20)</td><td>123456789</td></tr><tr><td>senderPassport</td><td>Sender's passport.</td><td>string (255)</td><td>AN123456</td></tr><tr><td>senderIp</td><td>Sender's IP address.</td><td>string (50)</td><td>123.12.12.12</td></tr><tr><td>senderPhone</td><td>Sender's phone number.</td><td>string (20)</td><td>3,81E+11</td></tr><tr><td>senderBirthday</td><td>Sender's date of birth.</td><td>string (50)</td><td>31.12.2000</td></tr><tr><td>senderGender</td><td>Sender's gender.</td><td>string (50)</td><td>Male/Female</td></tr><tr><td>senderZipCode</td><td>Sender's postal code.</td><td>string (50)</td><td>49000</td></tr><tr><td>senderBankCode</td><td>Sender's issuing bank</td><td>string</td><td>BANK_ALLIANCE</td></tr><tr><td>senderPaymentSystem</td><td>Sender's issuer</td><td>string</td><td>MasterCard</td></tr><tr><td>senderCardNumberMask</td><td>Masked card number of the sender</td><td>string</td><td>5573********0304</td></tr><tr><td>recipientCustomerId</td><td>Recipient's client id</td><td>​string(30)</td><td>1258728c1</td></tr><tr><td>recipientFirstName</td><td>Recipient's first name</td><td><p>​</p><p>string(30)</p></td><td>Ivanenko</td></tr><tr><td>recipientLastName</td><td>Recipient's last name </td><td><p>​</p><p>string(30)</p></td><td>Ivan</td></tr><tr><td>recipientMiddleName</td><td>Recipient's middle name</td><td>string(30)</td><td>Ivanovich</td></tr><tr><td>recipientEmail</td><td>Recipient's email</td><td>string</td><td>mail@gmail.com</td></tr><tr><td>recipientСountry</td><td>Recipient's county</td><td>string</td><td>804</td></tr><tr><td>recipientRegion</td><td>Recipient's region</td><td>string</td><td>Kyivska</td></tr><tr><td>recipientСity</td><td>Recipient's city</td><td>string</td><td>Kyiv</td></tr><tr><td>recipientStreet</td><td>Recipient's street</td><td>string</td><td>Sichovykh Striltsiv</td></tr><tr><td>recipientAdditionalAddress</td><td>Recipient's additional address data (floor, house number, apartment).</td><td>string</td><td>23</td></tr><tr><td>recipientItn</td><td>Recipient's tax ID.</td><td>string</td><td>123456789</td></tr><tr><td>recipientPassport</td><td>Recipient's passport</td><td>string</td><td>AN123456</td></tr><tr><td>recipientIp</td><td>Recipient's IP address.</td><td>string</td><td>123.12.12.12</td></tr><tr><td>recipientPhone</td><td>Recipient's phone number</td><td>string</td><td>3,81E+11</td></tr><tr><td>recipientBirthday</td><td>Recipient's date of birth.</td><td>string</td><td>31.12.2000</td></tr><tr><td>recipientGender</td><td>Recipient's gender</td><td>string</td><td>Male/Female</td></tr><tr><td>recipientZipCode</td><td>Recipient's zip code </td><td>string</td><td>49000</td></tr><tr><td>recipientBankCode</td><td>Recipient's issuing bank</td><td>string</td><td>BANK_ALLIANCE</td></tr><tr><td>recipientPaymentSystem</td><td>Recipient's issuer</td><td>string</td><td>MasterCard</td></tr><tr><td>recipientCardNumberMask</td><td>Masked card number of the Recipienr</td><td>string</td><td>5573********0304</td></tr></tbody></table>

## An example of a request body:

```json
{
    "operationId": "",
    "browserInfo": {
        "browserAcceptHeader":",
        "browserUserAgent": "",
        "browserLanguage": "",
        "browserColorDepth": "",
        "browserScreenHeight": "",
        "browserScreenWidth": "",
        "browserTZ": ""
    },
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
    "operationId": "1712826797010P-juYeIJRx3",
    "ecomOperationId": "cbf7e357-d216-46ca-a885-71d917b0e405",
    "merchantName": null,
    "approvalCode": null,
    "status": "REQUIRED_3DS",
    "transactionType": 62,
    "merchantRequestId": "004dbc84-f3c1-4cc7-b7fb-50a3b0b6fa7e",
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
    "notificationUrl": "https://api-ecom-prod.bankalliance.ua/mock",
    "paymentServiceType": "APPLE_PAY",
    "notificationEncryption": false,
    "senderCardNumberMask": null,
    "desiredThreeDSMode": "MUST",
    "threeDSMode": "MUST",
    "statusThreeDs": null,
    "threeDSServerTransId": "e13f7b12-fcc9-4028-9307-0749d7076bdd",
    "redirect3dsUrl": "https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1712826797010P-juYeIJRx3",
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
    "recipientZipCode": null
}
```
