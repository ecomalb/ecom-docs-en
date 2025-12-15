---
description: '{{url}}/ecom/execute_request/payments/v1/google_pay_3ds/purchase'
---

# Payment Processing Request - Step 2 (3DS)

## **Incoming JSON Parameters:**

<table data-header-hidden><thead><tr><th></th><th></th><th></th><th width="131"></th><th></th></tr></thead><tbody><tr><td>Parameter</td><td>Description</td><td>Data Format</td><td>Mandatory</td><td>Example</td></tr><tr><td>operationId</td><td>The operation ID obtained in step 1</td><td>string</td><td>Yes</td><td>137d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>date</td><td>Date and time of payment</td><td>string</td><td>Yes</td><td>{{currentdateT}}.00+00:00</td></tr><tr><td>browserInfo</td><td>Object containing browser data</td><td>object</td><td>Yes, if the operation requires 3DS</td><td>-</td></tr><tr><td>browserAcceptHeader</td><td>HTTP request header</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,/;q=0.8,application/signed-exchange;v=b3;q=0.9</td></tr><tr><td>browserUserAgent</td><td>Browser software element identifying the system</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.66 Safari/537.36</td></tr><tr><td>browserLanguage</td><td>Browser language</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>en-US,en</td></tr><tr><td>browserColorDepth</td><td>Screen color depth value in the browser</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>24</td></tr><tr><td>browserScreenHeight</td><td>Height of the browser viewport</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>800</td></tr><tr><td>browserScreenWidth</td><td>Width of the browser viewport</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>1280</td></tr><tr><td>browserTZ</td><td>Browser timezone offset</td><td>string</td><td>Yes, if the operation requires 3DS</td><td>-180</td></tr></tbody></table>

## **Output JSON Parameters:**

<table data-header-hidden><thead><tr><th></th><th></th><th width="143"></th><th></th></tr></thead><tbody><tr><td>Parameter</td><td>Description</td><td>Data Format</td><td>Example</td></tr><tr><td>type</td><td>Transaction type</td><td>string</td><td>Purchase</td></tr><tr><td>rrn</td><td>Transaction reference number in MPS</td><td>string</td><td>2554256963</td></tr><tr><td>purpose</td><td>Payment purpose</td><td>string</td><td>For the goods</td></tr><tr><td>comment</td><td>Comment</td><td>string</td><td>test</td></tr><tr><td>coinAmount</td><td>Payment amount</td><td>int</td><td>2000</td></tr><tr><td>merchantId</td><td>Merchant ID</td><td>string</td><td>137d9304-0368-11ed-b939-0242ac120002</td></tr><tr><td>operationId</td><td>Transaction ID</td><td>string</td><td>1712844596346b9F-WwrWZpq</td></tr><tr><td>ecomOperationId</td><td>Transaction ID in Ecom system</td><td>string</td><td>8c3303e9-7396-43b8-af4e-31d9facdde9b</td></tr><tr><td>merchantName</td><td>Merchant name</td><td>string</td><td>KB test terminal</td></tr><tr><td>approvalCode</td><td>Authorization code</td><td>string</td><td>39203</td></tr><tr><td>status</td><td>Transaction status</td><td>string</td><td>SUCCESS, FAIL, PENDING, REQUIRED_3DS, DESIRED_THREEDS_MODE_ERROR</td></tr><tr><td>transactionType</td><td>Transaction type in digital format</td><td>string</td><td>35</td></tr><tr><td>merchantRequestId</td><td>Merchant request ID</td><td>string</td><td>72837906-f526-4aef-8d11-58d80b44cb75</td></tr><tr><td>transactionCurrency</td><td>Payment currency</td><td>string</td><td>980</td></tr><tr><td>merchantCommission</td><td>Commission amount</td><td>string</td><td>2</td></tr><tr><td>createDateTime</td><td>Payment creation date</td><td>string</td><td>19.09.2024 15:29</td></tr><tr><td>modificationDateTime</td><td>Payment modification date</td><td>string</td><td>19.09.2024 15:29</td></tr><tr><td>actionCode</td><td>Response code</td><td>string</td><td>0</td></tr><tr><td>responseCode</td><td>Response details</td><td>string</td><td>0</td></tr><tr><td>description</td><td>Response description</td><td>string</td><td>approved</td></tr><tr><td>bankCode</td><td>Issuing bank name</td><td>string</td><td>BANK_ALLIANCE</td></tr><tr><td>paymentSystem</td><td>Issuer's MPS name</td><td>string</td><td>MasterCard</td></tr><tr><td>productType</td><td>Terminal product type</td><td>string</td><td>PURCHASE</td></tr><tr><td>notificationUrl</td><td>URL for CallBack notifications</td><td>string</td><td>https://merchant.notification_url/</td></tr><tr><td>paymentServiceType</td><td>Payment type</td><td>string</td><td>CARD/APPLE_PAY/GOOGLE_PAY</td></tr><tr><td>notificationEncryption</td><td>CallBack data encryption flag</td><td>string</td><td>true/false</td></tr><tr><td>cardNumberMask</td><td>Masked card number</td><td>string</td><td>5573********0304</td></tr><tr><td>desiredThreeDSMode</td><td>3DS requirement indicator</td><td>string</td><td>MUST/SHOULD/MUST_NOT</td></tr><tr><td>threeDSMode</td><td>3DS usage status</td><td>string</td><td>MUST/MUST_NOT</td></tr><tr><td>statusThreeDs</td><td>3DS verification status</td><td>string</td><td>Y/N</td></tr><tr><td>threeDSServerTransId</td><td>Transaction ID in the 3DS system</td><td>string</td><td>b6c35fdb-28c1-454d-a2f3-51098c26bda4</td></tr><tr><td>acsTransId</td><td>Transaction ID in the ACS system</td><td>string</td><td>3e17fabb-71e6-498e-8794-ef8c95c5ba6f</td></tr><tr><td>dsTransId</td><td>Transaction ID generated by Directory Server</td><td>string</td><td>12ebc556-82d3-4e35-9fb8-77ac18b050ea</td></tr><tr><td>eci</td><td>Electronic Commerce Indicator</td><td>string</td><td>2</td></tr><tr><td>processingMerchantId</td><td>Merchant ID in HR</td><td>string</td><td>AE100000</td></tr><tr><td>processingTerminalId</td><td>Terminal ID in PC</td><td>string</td><td>AE100000</td></tr><tr><td>redirect3dsUrl</td><td>URL for redirecting clients to issuer's 3DS page</td><td>string</td><td>https://api-ecom-release.develop.bankalliance.ua/threeDS/getRedirectHtml/1702047427621BHu5X99yDbA</td></tr><tr><td>txnType</td><td>Transaction type enum</td><td>enum</td><td>NONCVV/noncvv</td></tr><tr><td>senderCustomerId</td><td>Sender client ID</td><td>string</td><td>1258728c1</td></tr><tr><td>senderFirstName</td><td>Sender's first name</td><td>string</td><td>Ivan</td></tr><tr><td>senderLastName</td><td>Sender's last name</td><td>string</td><td>Ivanenko</td></tr><tr><td>senderMiddleName</td><td>Sender's patronymic</td><td>string</td><td>Ivanovych</td></tr><tr><td>senderEmail</td><td>Sender's email</td><td>string</td><td>mail@gmail.com</td></tr><tr><td>senderCountry</td><td>Sender's country</td><td>string</td><td>Ukraine</td></tr><tr><td>recipientRegion</td><td>Recipient's region</td><td>string</td><td>Kyivska</td></tr><tr><td>recipientСity</td><td>Recipient's city</td><td>string</td><td>Kyiv</td></tr><tr><td>recipientStreet</td><td>Recipient's street</td><td>string</td><td>Sichovykh Striltsiv</td></tr><tr><td>recipientAdditionalAddress</td><td>Recipient's additional address data (floor, house number, apartment).</td><td>string</td><td>23</td></tr><tr><td>recipientItn</td><td>Recipient's tax ID.</td><td>string</td><td>123456789</td></tr><tr><td>recipientPassport</td><td>Recipient's passport</td><td>string</td><td>AN123456</td></tr><tr><td>recipientIp</td><td>Recipient's IP address.</td><td>string</td><td>123.12.12.12</td></tr><tr><td>recipientPhone</td><td>Recipient's phone number</td><td>string</td><td>3,81E+11</td></tr><tr><td>recipientBirthday</td><td>Recipient's date of birth.</td><td>string</td><td>31.12.2000</td></tr><tr><td>recipientGender</td><td>Recipient's gender</td><td>string</td><td>Male/Female</td></tr><tr><td>recipientZipCode</td><td>Recipient's zip code </td><td>string</td><td>49000</td></tr><tr><td>senderBankCode</td><td>Sender's issuing bank</td><td>string</td><td>BANK_ALLIANCE</td></tr><tr><td>senderPaymentSystem</td><td>Sender's issuer</td><td>string</td><td>MasterCard</td></tr><tr><td>senderCardNumberMask</td><td>Masked card number of the sender</td><td>string</td><td>5573********0304</td></tr></tbody></table>

#### Приклади :

<details>

<summary>JWS Payload — тіло запиту перед підписанням</summary>

<pre class="language-json"><code class="lang-json">{
    "operationId": "1702047427621BHu5X99yDbA",
    "browserInfo": {
<strong>        "browserAcceptHeader"text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9",
</strong>        "browserUserAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like,Gecko)Chrome/87.0.4280.66 Safari/537.36",
        "browserLanguage": "en-US,en",
        "browserColorDepth": "24",
        "browserScreenHeight": "800",
        "browserScreenWidth": "1280",
        "browserTZ": "-180"
    },
    "notificationUrl": "https://api-ecom-prod.bankalliance.ua/mock",
    "date": "{{currentdateT}}.00+00:00"
}
</code></pre>

</details>

<details>

<summary>JWS Payload — тіло відповіді перед підписанням</summary>

```json
{
    "type": "PURCHASE",
    "rrn": null,
    "purpose": "purpose",
    "comment": "comment",
    "coinAmount": null,
    "merchantId": "137d9304-0368-11ed-b939-0242ac120002",
    "operationId": "17128429092802o9koN8eABn",
    "ecomOperationId": "99261a33-cfae-4dfa-9396-812817b5dffb",
    "merchantName": null,
    "approvalCode": null,
    "status": "PENDING",
    "transactionType": 35,
    "merchantRequestId": "8bf3bc51-53e8-4d12-9e86-c13dd6af3b9e",
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
    "notificationUrl": "https://webhook.site/cbf8c83a-ee1e-47c6-899c-eca5731ff084",
    "paymentServiceType": "GOOGLE_PAY",
    "notificationEncryption": false,
    "cardNumberMask": null,
    "desiredThreeDSMode": "MUST",
    "threeDSMode": "MUST",
    "statusThreeDs": null,
    "threeDSServerTransId": "5d175446-df26-4ad0-a60c-cd8f95570c0c",
    "redirect3dsUrl": null,
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
    "senderCardNumberMask": null
}
```

</details>
