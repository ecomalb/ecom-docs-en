# Using an authorization token

After decrypting the JWE response (see: [Decryption Example](https://docs.merchant.alb.ua/en/authentication#request-for-decrypting-the-technical-session)) for the authorization request `"/api-gateway/authorize_virtual_device"`, the session token and its expiration parameters are obtained:

* "tokenExpirationDateTime": "2025-02-27 12:12:34.0430 +0000" // UTC+00:00
* "tokenExpiration": "2025-02-27 14:12:34.430+02:00" // UTC+02:00 Kyiv

### **Potential Issues**

1. **Expired Authorization Token Due to Inactivity**

* If there is no activity for `serviceCode` for more than 200 days, API access is automatically revoked.
* When attempting to execute an authorization request to `"/api-gateway/authorize_virtual_device"`, the following error occurs: `"b_auth_token_expired"`

**Resolution:**

* To resolve this issue, contact the support team.
* After the issue is resolved, new parameters will be provided in the authorization response, which must be updated before making further API requests.

2. **Expired Current Token**

* If the following error occurs: `"b_expired_token"`
* A new authorization request to `"/api-gateway/authorize_virtual_device"` must be made.
