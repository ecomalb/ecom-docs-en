---
description: Using data from the registers to verify successful transactions.
---

# Instructions for reconciliation by registers

Stages of reconciliation

* Based on the data obtained from the registers, you can collect data on the specified parameters from your system.
* Search by key parameters (e.g., operationId or rrn) to find the relevant records. You can also use parameters from `merchantComment` for more flexible reconciliation.
* Verify the statuses and dates of processing to confirm the correctness of the transaction data.
* Document any discrepancies and contact support for resolution.



### Work with  **`merchantComment`**

A new merchantComment parameter has been added to the payment API, which will also be included in the registers.

* [PURCHASE Requrest Step 1 ](https://docs.merchant.alb.ua/en/payment-methods-h2h/purchase/purchase-request-step-1)
* [A2C](https://docs.merchant.alb.ua/en/payment-methods-h2h/a2c)
* [C2A transaction Request - Step 1 ](https://docs.merchant.alb.ua/en/payment-methods-h2h/c2a/c2a-transaction-request-step-1)
* [REFUND](https://docs.merchant.alb.ua/en/payment-methods-h2h/refund)

This option can make it easier for you to identify the transaction later in reconciliations in the registers.

#### Requirements for the parameter **`merchantComment`.**

* Type: string&#x20;
* Maximum length: 255 characters
* Validation rules: \[a-zA-Z0-9 ,.;:@#$%'-=+1,256$]&#x20;

Exampl&#x65;**:** \
&#xNAN;**`"merchantComment": "1712822901491QtPAxAWOrrg,1258728c1,alb"`**\
where, \
`1712822901491QtPAxAWOrrg` - operationId of the original operation, \
`1258728c1` - senderCustomerId, \
`alb` - any other value you need to simplify the identification of the operation in the register, \
`,` - separator.

You can pass the `senderCustomerId` and/or `recipientCustomerId`, operationId of the original transaction when making a refund, and other parameters necessary for your work to this parameter.

The data passed in the `merchantComment` parameter will be automatically exported to the daily registers.

This update is intended to provide more flexibility and convenience in working with the registers. If you have any questions or need additional information, please feel free to contact the relevant technical chats.







