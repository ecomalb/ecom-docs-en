---
description: You need to run a script to check the support for paying with Apay on the page
---

# Request aPay support on the page

```javascript
if (!window.ApplePaySession || !window.ApplePaySession?.canMakePayments?.()) {
    return <div>Apple Pay is not supported on this device</div>;
}
```
