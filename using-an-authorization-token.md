# Using an authorization token

Upon successful JWE response decryption (For details, see: Example of Decryption) to the `/api-gateway/authorize_virtual_device` authorization request, you receive a session token and its lifetime parameters:

<table data-header-hidden><thead><tr><th></th><th width="297.800048828125"></th><th></th></tr></thead><tbody><tr><td><strong>Parameter</strong></td><td><strong>Example Value</strong></td><td><strong>Description</strong></td></tr><tr><td><code>tokenExpirationDateTime</code></td><td><code>"2025-02-27 12:12:34.0430 +0000"</code></td><td>UTC+00:00</td></tr><tr><td><code>tokenExpiration</code></td><td><code>"2025-02-27 14:12:34.430+02:00"</code></td><td>UTC+02:00 (Kyiv Time)</td></tr></tbody></table>

The total authorization validity period is 24 hours from the moment the `/api-gateway/authorize_virtual_device` request was executed.

#### Recommended Usage

It is recommended to perform authorization every 8, 12, or 24 hours to reduce errors during authorization token usage.

> Important Note! You should not perform a new authorization request for every subsequent API request.

#### Possible Issues and Solutions

| **Problem**                                   | **Error Code / Message**                                                                | **Solution**                                                                                                                      |
| --------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Expired Authorization Token due to Inactivity | Error: `"b_auth_token_expired"`                                                         | Action Required: Contact the support team for resolution.                                                                         |
| Expired Current Token                         | Error: `"b_expired_token"`                                                              | Action Required: Execute a new authorization request to `/api-gateway/authorize_virtual_device`.                                  |
| Expired Current Session                       | Error: `"b_session_doesnt_exists"` (Text: "Сеансу не існує" - _Session does not exist_) | Action Required: Execute a new authorization request to `/api-gateway/authorize_virtual_device` and utilize the new session data. |

**Details on Inactivity Error**

If the serviceCode is inactive for more than 200 days, access to the API is automatically closed. After the issue is fixed by support, the authorization response will contain new parameters that must be updated before continuing to use API requests.
