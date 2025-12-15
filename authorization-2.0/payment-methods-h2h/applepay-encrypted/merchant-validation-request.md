---
description: >-
  Request through a proxy server to the apple pay server to receive merchant
  validation
---

# Merchant validation request

`fetchAppleSessionAPI` and `purchaseApplePayAPI` - functions that call the API, use your functions to work with the API, or `fetch` \
\
An example of an ApplePay payment button click event handler is described below:

```javascript

const onApplePayButtonClicked = async () => {
    // Additional check whether the browser supports Apple Pay
    if (!window.ApplePaySession) {
      return;
    }
    
    // An object to create a session
    const request = {
      countryCode: 'UA', 
      currencyCode: 'UAH',
      merchantCapabilities: ['supports3DS'],
      supportedNetworks: ['visa', 'masterCard'],
      total: {
        label: 'PoC Merchant Apple Pay', // merchant name
        type: 'final',
        amount: amount.toString(), // transaction amount
      },
    };

    // Creating a session
    const session = new window.ApplePaySession(3, request);

    session.onvalidatemerchant = async (event: any) => {
      try {
        // Call request to create a session сесії https://docs.merchant.alb.ua/platizhni-metodi-h2h/applepay-encrypted/zapit-vstanovlennya-sesiyi-v-apau
        const response = await fetchAppleSessionAPI(event.validationURL, applePayMercantId, { deviceId, refreshToken });

        session.completeMerchantValidation(response.applePaySessionData);
      } catch (error) {
        // error handling of a request to create a session
      }
    };

    session.onshippingmethodselected = () => {
      const newTotal = {
        label: 'PoC Merchant Apple Pay', // merchant name
        type: 'final',
        amount: amount.toString(), // transaction amount
      };
      session.completeShippingMethodSelection(window.ApplePaySession.STATUS_SUCCESS, {}, newTotal);
    };

    // event when the user has successfully selected a card for payment
    session.onpaymentauthorized = async (event: any) => {

      const result = {
        status: window.ApplePaySession.STATUS_SUCCESS,
      };
      
      session.completePayment(result);
      
      try {
        // payment request call https://docs.merchant.alb.ua/platizhni-metodi-h2h/applepay-encrypted/zapit-provedennya-platezhu
        const response = await purchaseApplePayAPI(
          {
            paymentToken: event.payment.token,
            // other data required for the call
            
          }
          { deviceId, refreshToken, serverPublicKey }
        );
        
      } catch (error) {
         // payment request error error
      }
    };

    session.begin();
  };

```
