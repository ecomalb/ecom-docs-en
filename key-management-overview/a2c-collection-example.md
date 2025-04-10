# A2C Collection Example

## **1. Authorize by Virtual Device**

**Endpoint:**\
`{{url}}/api-gateway/authorize_virtual_device`

* The request requires a **serviceCode**, which is provided before integration into the production environment.
* In response, an **encrypted server key** (`serverPublicKey`) is returned in **JWE format**.
* This key is required for **Step 2**.
* In the testing environment, this key is already included in the collection data.

## **2. Decrypt Authorization Response**

**Endpoint:**\
`{{url}}/cipher/decrypt_by_jwk?message={{responseJwe}}`

* This request decrypts the bank’s response using the **private key** (`userPrivateKey`).
* The **Merchant** generates this key following the instructions in the "[Client Communication JWK Key Generation Process.](https://docs.merchant.alb.ua/en/authentication#process-of-generating-client-communication-jwk-keys)"
* The decrypted **serverPublicKey** obtained in this step is required for **Step 4**.
* **In the production environment, the Merchant must perform decryption independently.**

## **3. A2C Card Number Encryption**

**Endpoint:**\
`{{url}}/cipher/encrypt_by_jwk?message={{card_number}}`

* The **payment key** (`paymentPublicKey`), provided by the **Bank**, is used to encrypt the **customer’s card number**.
* For testing, an auxiliary method `/ecom/help/encrypt_by_jwk` is available.
* **In the production environment, the Merchant must handle encryption independently.**

## **4. A2C Encrypt Request Body**

**Endpoint:**\
`{{url}}/cipher/encrypt_by_jwk?message={{body_request}}`

* `{{body_request}}` must meet the **mandatory input parameters** for[ **A2C transactions**](https://docs.merchant.alb.ua/en/payment-methods-h2h/a2c).
* The **server key** (`serverPublicKey`), obtained in **Steps 1 and 2**, is used to encrypt the A2C request body.
* The response contains an **encrypted request body**: `{{encryptJweT}}`, required for **Step 5**.
* For testing, the auxiliary method `/ecom/help/encrypt_by_jwk` is available.

## **5. A2C v3 Transaction Execution**

**Endpoint:**\
`{{url}}/ecom/execute_request/payments/v3/account_to_card`

* The request sends the **encrypted request body** (`{{encryptJweT}}`), generated in **Step 4**.
* The response contains an **encrypted response** (`{{responseJwe}}`), required for **Step 6**.

## **6. A2C v3 Decrypt Response**

**Endpoint:**\
`{{url}}/cipher/decrypt_by_jwk?message={{responseJwe}}`

* This request decrypts the bank’s response using the **private key** (`userPrivateKey`).
* The **Merchant** generates this key following the instructions in the "[Client Communication JWK Key Generation Process.](https://docs.merchant.alb.ua/en/authentication#process-of-generating-client-communication-jwk-keys)"
* The response contains the **decrypted response body** from **Step 5**.

