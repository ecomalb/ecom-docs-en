---
description: Processing Payments Using a Card Token
---

# TOKEN

A **card token** is a unique digital identifier that replaces actual card details for secure payments. By using a token, you can complete transactions without exposing the actual card number.

## How to Obtain a Card Token?

#### There are two ways to generate a token:

1.  **During a Payment Transaction** – When initiating a [Purchase](https://docs.merchant.alb.ua/en/payment-methods-h2h/purchase/purchase-request-step-1) or [C2A](https://docs.merchant.alb.ua/en/payment-methods-h2h/c2a/c2a-transaction-request-step-1) request, include the additional parameter:

    ```json
    "typeToken": "TOKEN_PER_CUSTOMER"
    ```
2. **Via a Separate Request** – Using the dedicated `"Create Token"` request.

## How to Pay Using a Token?

Once a token is created, a payment can be processed through a dedicated endpoint:

* `"Process Payment via Token"` for the **Purchase** transaction type.
* `"Process Payment via Token"` for the **C2A** transaction type.

Simply pass the token instead of card details, and the payment will be securely and efficiently processed.

Using tokens eliminates the need to store sensitive card data, enhancing the security of transactions.

## Additional Token-Related Requests

🔹 [**Retrieve Token by Customer ID**](https://docs.merchant.alb.ua/en/payment-methods-h2h/token/retrieve-token-by-customerid)\
To find a token linked to a specific customer, use the `"Retrieve Token by Customer ID"` request.

🔹 [**Retrieve Token Details**](https://docs.merchant.alb.ua/en/payment-methods-h2h/token/retrieve-token-data)\
To obtain detailed information about a token (such as expiration date, status, or associated card), use the `"Retrieve Token Details"` request.

🔹 [Token status change](https://docs.merchant.alb.ua/en/payment-methods-h2h/token/update-token-status)

To change the token status, the “Token Status Change” endpoint is used.

These requests enable seamless token management and ensure a secure and efficient payment process.
