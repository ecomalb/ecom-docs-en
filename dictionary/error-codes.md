---
description: >-
  The error codes listed below do not indicate the success or failure of
  transactions.
---

# Error codes

To check the transaction status, you must:

* Wait for the callback
* Check the transaction status by `OPERATION_ID`
* Check the transaction status by `merchantRequestId`

<table data-header-hidden><thead><tr><th width="137.5999755859375"></th><th width="157.4000244140625"></th><th></th><th></th></tr></thead><tbody><tr><td><strong>HTTP Code</strong></td><td><strong>msgType</strong></td><td><strong>msgCode</strong></td><td><strong>msgText</strong></td></tr><tr><td>200</td><td>ERROR</td><td><code>b_terminal_not_found</code></td><td>@Payment terminal not found</td></tr><tr><td></td><td>ERROR</td><td><code>b_merchant_not_found</code></td><td>@Merchant not found</td></tr><tr><td></td><td>ERROR</td><td><code>b_reverse_transaction_failed</code></td><td>@Failed to reverse transaction</td></tr><tr><td></td><td>ERROR</td><td><code>b_payment_invalid_refund_amount</code></td><td>@Payment invalid refund amount</td></tr><tr><td></td><td>ERROR</td><td><code>b_phys_transaction_not_found</code></td><td>@Phys transaction not found</td></tr><tr><td></td><td>ERROR</td><td><code>b_cannot_process_logic_transaction</code></td><td>@Cannot process logic transaction</td></tr><tr><td></td><td>ERROR</td><td><code>b_authorize_transaction_failed</code></td><td>@Failed to authorize transaction</td></tr><tr><td></td><td>ERROR</td><td><code>b_initiate_transaction_failed</code></td><td>@Failed to initiate transaction</td></tr><tr><td></td><td>ERROR</td><td><code>b_payment_logic_transaction_not_found</code></td><td>@Payment logic transaction not found</td></tr><tr><td></td><td>ERROR</td><td><code>b_explicit_payment_execution_not_supported</code></td><td>@Payment type doesn't support explicit execution</td></tr><tr><td></td><td>ERROR</td><td><code>b_payment_not_found</code></td><td>@Payment not found</td></tr><tr><td></td><td>ERROR</td><td><code>b_operation_not_found</code></td><td>@Operation not found</td></tr><tr><td></td><td>ERROR</td><td><code>b_payment_refund_not_supported</code></td><td>@Payment type doesn't support refund</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_invalid_request</code></td><td>Invalid request</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_unsupported_payment_system</code></td><td>Payment system is not supported</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_validation_card_expiration_date_and_security_code</code></td><td>Value must consist of 7 digits.</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_invalid_pan_format</code></td><td>Incorrect format of the full card number</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_payment_invalid_refund_status</code></td><td>@Payment invalid refund status</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_validation_card_expiration_date</code></td><td>Value must consist of 4 digits</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_encryptor_failed_decrypt_message</code></td><td>Failed to decrypt message</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_virtual_device_not_found</code></td><td>Virtual device not found</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_refresh_token_absent</code></td><td>Refresh token is missing</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_err_missing_recipient_id</code></td><td><code>recipientItn</code> or <code>recipientPassport</code> is not specified. One of the parameters is mandatory.</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_err_invalid_itn_format</code></td><td>Invalid format of <code>recipientItn</code>. Must contain only 10 digits.</td></tr><tr><td>200</td><td>ERROR</td><td><code>b_overload_error</code></td><td>@Overload error</td></tr><tr><td>400</td><td>ERROR</td><td><code>b_duplicate_field_value</code></td><td>Value <code>{data}</code> must be unique</td></tr><tr><td>400</td><td>ERROR</td><td><code>b_request_is_not_correct</code></td><td>Request is not in the correct format</td></tr><tr><td>400</td><td>ERROR</td><td><code>b_error_parse_json</code></td><td>JSON parse error: <code>{info}</code></td></tr><tr><td>400</td><td>ERROR</td><td><code>b_txn_not_allowed</code></td><td>@transaction type is not allowed for this Merchant</td></tr><tr><td>400</td><td>ERROR</td><td><code>b_failed_to_get_apple_pay_session</code></td><td>@Failed to get apple pay session</td></tr><tr><td>400</td><td>ERROR</td><td><code>b_user_merchant_request_mismatch</code></td><td>@User's merchant ID doesn't match the merchant ID from request</td></tr><tr><td>401</td><td>ERROR</td><td><code>b_expired_token</code></td><td>@Token Expired</td></tr><tr><td></td><td>ERROR</td><td><code>b_unknown_device</code></td><td>@Unknown Device</td></tr><tr><td>401</td><td>ERROR</td><td><code>b_used_token</code></td><td>Used token</td></tr><tr><td>401</td><td>ERROR</td><td><code>b_auth_token_expired</code></td><td>Authentication token expired</td></tr><tr><td>401</td><td>ERROR</td><td><code>b_previous_auth_token_expired</code></td><td>@Previous Auth Token Expired</td></tr><tr><td>404</td><td>ERROR</td><td><code>b_service_unavailable</code></td><td>@Service '{service}' unavailable</td></tr><tr><td>404</td><td>ERROR</td><td><code>payment_operation_not_found</code></td><td>@Payment operation is not found.</td></tr><tr><td>404</td><td>ERROR</td><td><code>b_hpp_order_not_found</code></td><td>@The HPP order not found</td></tr><tr><td>404</td><td>ERROR</td><td><code>b_merchant_balances_not_found</code></td><td>@Balance not found.</td></tr><tr><td>500</td><td>ERROR</td><td><code>b_hpp_order_expired</code></td><td>@The HPP order is expired</td></tr><tr><td>500</td><td>ERROR</td><td><code>b_unknown_error</code></td><td>Unknown error</td></tr><tr><td>503</td><td>ERROR</td><td><code>b_server_is_overloaded</code></td><td>@Server is overloaded (must retry the request later)</td></tr></tbody></table>

**Example Error Response**

```json
{
    "requestId": "29a36a0a-5926-11ed-9b6a-0242ac120002",
    "serviceId": "api-gateway",
    "msgCode": "b_used_token",
    "msgType": "ERROR",
    "msgText": "@Used Token Alert!",
    "isLocalized": false,
    "msgAttrs": {},
    "errorCauses": []
}
```

```json
```
