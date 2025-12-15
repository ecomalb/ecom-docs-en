---
description: '{{url}}/ecom/execute_request/payments/v1/execute/verification'
---

# Card verification request Step 2

### Input parameters:

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Data Format</th><th>Required</th><th>Example</th></tr></thead><tbody><tr><td>operationId</td><td>Operation ID received in step 1</td><td>string</td><td>Yes</td><td>1697008393082nW0c1jr6KVv</td></tr><tr><td>encryptedCardData</td><td>Card expiration date and CVV2 encrypted in JWE. First 4 characters are ExpDate, next 3 characters are CVV</td><td>string</td><td>Yes</td><td>2503111 (decrypted format, in YYMMCVV format)</td></tr><tr><td>date</td><td>Date and time of the payment</td><td>string</td><td>Yes</td><td>{{currentdateT}}.00+00:00</td></tr><tr><td>browserInfo</td><td>Object containing browser data</td><td>object</td><td>Yes, if the operation requires 3DS</td><td><br></td></tr><tr><td>browserAcceptHeader</td><td>HTTP request header</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9</td></tr><tr><td>browserUserAgent</td><td>Browser user agent string indicating the system being used</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like,Gecko)Chrome/87.0.4280.66 Safari/537.36</td></tr><tr><td>browserLanguage</td><td>Browser language</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>en-US,en</td></tr><tr><td>browserColorDepth</td><td>Color depth value of the browser screen</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>24</td></tr><tr><td>browserScreenHeight</td><td>Height of the browser window's viewport</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>800</td></tr><tr><td>browserScreenWidth</td><td>Width of the browser window's viewport</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>1280</td></tr><tr><td>browserTZ</td><td>Browser timezone</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>-180</td></tr></tbody></table>

### Output parameters:

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Data Format</th><th>Example</th></tr></thead><tbody><tr><td>type</td><td>Transaction type</td><td>string</td><td>Purchase</td></tr><tr><td>rrn</td><td>RRN number of the transaction in MPS</td><td>string</td><td>2554256963</td></tr><tr><td>purpose</td><td>Payment purpose</td><td>string</td><td>For goods</td></tr><tr><td>comment</td><td>Comment</td><td>string</td><td>Test</td></tr><tr><td>coinAmount</td><td>Payment amount</td><td>int</td><td>2000</td></tr><tr><td>merchantId</td><td>Merchant ID</td><td>string</td><td>137d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>operationId</td><td>Transaction ID</td><td>string</td><td>1712844596346b9F-WwrWZpq</td></tr><tr><td>ecomOperationId</td><td>Transaction ID in the Ecom system</td><td>string</td><td>8c3303e9-7396-43b8-af4e-31d9facdde9b</td></tr><tr><td>merchantName</td><td>Merchant name</td><td>string</td><td>KB test terminal</td></tr><tr><td>approvalCode</td><td>Authorization code</td><td>string</td><td>39203</td></tr><tr><td>status</td><td>Transaction status</td><td>string</td><td>SUCCESS<br>FAIL<br>PENDING<br>REQUIRED_3DS<br>DESIRED_THREEDS_MODE_ERROR</td></tr><tr><td>transactionType</td><td>Transaction type in numeric value</td><td>string</td><td>35</td></tr><tr><td>merchantRequestId</td><td>Merchant request ID</td><td>string</td><td>72837906-f526-4aef-8d11-58d80b44cb75</td></tr><tr><td>transactionCurrency</td><td>Payment currency</td><td>string</td><td>980</td></tr><tr><td>merchantCommission</td><td>Commission amount</td><td>string</td><td>2</td></tr><tr><td>creationDateTime</td><td>Payment creation date</td><td>string</td><td>2024.09.19 15:29:25.675</td></tr><tr><td>modificationDateTime</td><td>Payment modification date</td><td>string</td><td>2024.09.19 15:29:25.675</td></tr><tr><td>actionCode</td><td>Response code</td><td>string</td><td>0</td></tr><tr><td>responseCode</td><td>Response details</td><td>string</td><td>0</td></tr><tr><td>description</td><td>Response description</td><td>string</td><td>Approved</td></tr><tr><td>bankCode</td><td>Issuer bank name</td><td>string</td><td>BANK_ALLIANCE</td></tr><tr><td>paymentSystem</td><td>Issuer MPS name</td><td>string</td><td>MasterCard</td></tr><tr><td>productType</td><td>Terminal product type</td><td>string</td><td>PURCHASE</td></tr><tr><td>notificationUrl</td><td>URL to which the callback was sent</td><td>string</td><td><a href="https://merchant.notification_url/">https://merchant.notification_url/</a></td></tr><tr><td>paymentServiceType</td><td>Payment type</td><td>string</td><td>CARD/APPLE_PAY/GOOGLE_PAY</td></tr><tr><td>notificationEncryption</td><td>Indicates whether callback data is encrypted</td><td>string</td><td>true/false<br>If the parameter is not passed or false, the callback data will not be encrypted</td></tr><tr><td>cardNumberMask</td><td>Masked card number</td><td>string</td><td>5573********0304</td></tr><tr><td>desiredThreeDSMode</td><td>Indicates whether the merchant desires to use 3DS in the purchase</td><td>string</td><td>MUST/SHOULD/MUST_NOT</td></tr><tr><td>threeDSMode</td><td>Indicates whether 3DS was used in the purchase</td><td>string</td><td>MUST - payment with 3DS<br>MUST_NOT - payment without 3DS</td></tr><tr><td>statusThreeDs</td><td>3DS transaction status</td><td>string</td><td>Y - successful 3DS<br>N - unsuccessful 3DS</td></tr><tr><td>threeDSServerTransId</td><td>Transaction ID in the 3DS system</td><td>string</td><td>b6c35fdb-28c1-454d-a2f3-51098c26bda4</td></tr><tr><td>acsTransId</td><td>Transaction ID in the ACS system</td><td>string</td><td>3e17fabb-71e6-498e-8794-ef8c95c5ba6f</td></tr><tr><td>dsTransId</td><td>Transaction ID generated by the Directory Server</td><td>string</td><td>12ebc556-82d3-4e35-9fb8-77ac18b050ea</td></tr><tr><td>eci</td><td>Electronic Commerce Indicator code indicating the security level of the transaction</td><td>string</td><td>02</td></tr><tr><td>processingMerchantId</td><td>Merchant ID in the processing center</td><td>string</td><td>AE100000</td></tr><tr><td>processingTerminalId</td><td>Terminal ID in the processing center</td><td>string</td><td>AE100000</td></tr><tr><td>redirect3dsUrl</td><td>URL to redirect the client to the issuer's page for 3DS authentication</td><td>string</td><td><a href="https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1702047427621BHu5X99yDbA">https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1702047427621BHu5X99yDbA</a></td></tr><tr><td>txnType</td><td>Transaction subtype</td><td>enum</td><td>Possible values:<br>NONCVV/noncvv - CVV input and verification are not performed</td></tr><tr><td>senderCustomerId</td><td>Sender's customer ID</td><td>string</td><td>1258728c1</td></tr><tr><td>senderFirstName</td><td>Sender's first name</td><td>string</td><td>Ivanenko</td></tr><tr><td>senderLastName</td><td>Sender's last name</td><td>string</td><td>Ivan</td></tr><tr><td>senderMiddleName</td><td>Sender's middle name</td><td>string</td><td>Ivanovich</td></tr><tr><td>senderEmail</td><td>Sender's email</td><td>string</td><td>mail@gmail.com</td></tr><tr><td>senderCountry</td><td>Sender's country</td><td>string</td><td>Ukraine</td></tr><tr><td>senderRegion</td><td>Sender's region</td><td>string</td><td>Kyiv</td></tr><tr><td>senderCity</td><td>Sender's city</td><td>string</td><td>Kyiv</td></tr><tr><td>senderStreet</td><td>Sender's street</td><td>string</td><td>Sichovykh Striltsiv</td></tr><tr><td>senderAdditionalAddress</td><td>Additional sender address details (floor, house number, apartment)</td><td>string</td><td>23</td></tr><tr><td>senderItn</td><td>Sender's tax identification number</td><td>string</td><td>123456789</td></tr><tr><td>senderPassport</td><td>Sender's passport</td><td>string</td><td>AN123456</td></tr><tr><td>senderIp</td><td>Sender's IP address</td><td>string</td><td>123.12.12.12</td></tr><tr><td>senderPhone</td><td>Sender's phone number</td><td>string</td><td>380630000000</td></tr><tr><td>senderBirthday</td><td>Sender's date of birth</td><td>string</td><td>31.12.2000</td></tr><tr><td>senderGender</td><td>Sender's gender</td><td>string</td><td>M</td></tr><tr><td>senderZipCode</td><td>Sender's postal code</td><td>string</td><td>12000</td></tr><tr><td>senderBankCode</td><td>Sender's issuer bank name</td><td>string</td><td>BANK_ALLIANCE</td></tr><tr><td>senderPaymentSystem</td><td>Sender's issuer MPS name</td><td>string</td><td>MasterCard</td></tr><tr><td>senderCardNumberMask</td><td>Sender's masked card number</td><td>string</td><td>5573********0304</td></tr><tr><td>externalCardToken</td><td>Token ID</td><td>string</td><td>tmkEYenZSa8FV03aawVXxbep</td></tr></tbody></table>

### An example of a request body

```json
{
    "operationId": "{{operationId}}",
    "encryptedCardData": "{{encryptedCardData}}",
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

### Example of response body without 3DS

```json
{
    "type": "VERIFICATION",
    "rrn": "509310723011",
    "purpose": "",
    "comment": "",
    "coinAmount": 0,
    "merchantId": "137d9304-0368-11ed-b939-0242ac120",
    "operationId": "17436771609101HDujgZphks",
    "ecomOperationId": "1c97b778-d8d0-4680-89eb-8015842b45a3",
    "status": "SUCCESS",
    "transactionType": 215,
    "merchantRequestId": "03185335-3a9f-4aad-a3b9-c8b1e6d4051b",
    "transactionCurrency": "980",
    "creationDateTime": "2025.04.03 13:46:00.846",
    "modificationDateTime": "2025.04.03 13:46:01.465",
    "transactionResponseInfo": {
        "actionCode": "0",
        "responseCode": "00",
        "description": "Операція успішна"
    },
    "productType": "PURCHASE",
    "notificationUrl": "test",
    "paymentServiceType": "CARD",
    "notificationEncryption": false,
    "processingTerminalId": "AE001001",
    "processingMerchantId": "AE001001",
    "creatorSystem": "H2H",
    "desiredThreeDSMode": "MUST_NOT",
    "threeDSMode": "MUST_NOT",
    "senderCustomerId": "1234",
    "senderFirstName": "senderFirstName",
    "senderLastName": "senderLastName",
    "senderMiddleName": "senderMiddleName",
    "senderEmail": "aaaa@gmail.com",
    "senderCountry": "804",
    "senderRegion": "senderRegion",
    "senderCity": "senderCity",
    "senderStreet": "senderStreet",
    "senderAdditionalAddress": "senderAdditionalAddress",
    "senderItn": "5555555",
    "senderPassport": "passport",
    "senderIp": "55.555.44",
    "senderPhone": "5555",
    "senderBirthday": "20000110",
    "senderGender": "Female",
    "senderZipCode": "12345"
}
```

### Example response body from 3DS

```json
{
    "type": "VERIFICATION",
    "purpose": "",
    "comment": "",
    "coinAmount": 0,
    "merchantId": "137d9304-0368-11ed-b939-0242ac1200",
    "operationId": "1743677843021zx9DLwCfxz-",
    "ecomOperationId": "d8abe162-99a1-4cb9-8611-8b610cda510b",
    "status": "REQUIRED_3DS",
    "transactionType": 215,
    "merchantRequestId": "f821a5fa-cbfb-4ace-9c2f-83abc799d3a9",
    "transactionCurrency": "980",
    "creationDateTime": "2025.04.03 13:57:22.957",
    "modificationDateTime": "2025.04.03 13:57:23.752",
    "transactionResponseInfo": {},
    "productType": "PURCHASE",
    "notificationUrl": "test",
    "paymentServiceType": "CARD",
    "notificationEncryption": false,
    "processingTerminalId": "AE001001",
    "processingMerchantId": "AE001001",
    "creatorSystem": "H2H",
    "desiredThreeDSMode": "MUST",
    "threeDSMode": "MUST",
    "threeDSServerTransId": "1a85c9f3-c19c-448a-a4bb-04f265b62a28",
    "redirect3dsUrl": "https://api-ecom-preprod.develop.bankalliance.ua/threeDS/getRedirectHtml/1743677843021zx9DLwCfxz-",
    "senderCustomerId": "1234",
    "senderFirstName": "senderFirstName",
    "senderLastName": "senderLastName",
    "senderMiddleName": "senderMiddleName",
    "senderEmail": "aaaa@gmail.com",
    "senderCountry": "804",
    "senderRegion": "senderRegion",
    "senderCity": "senderCity",
    "senderStreet": "senderStreet",
    "senderAdditionalAddress": "senderAdditionalAddress",
    "senderItn": "5555555",
    "senderPassport": "passport",
    "senderIp": "55.555.44",
    "senderPhone": "5555",
    "senderBirthday": "20000110",
    "senderGender": "Female",
    "senderZipCode": "12345"
}
```
