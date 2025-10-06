---
description: Integrating Google Pay™ on a Web Page
---

# Google Pay™ Support Request on the Page

## To enable Google Pay™ on a webpage, follow these steps:

1. **Include the Google Pay™ script** on your page:

```javascript
 <script async src="https://pay.google.com/gp/p/js/pay.js" onload="onGooglePayLoaded()"></script>
```

2. **Insert the following script** to initialize Google Pay™ (the `onGooglePayLoaded` function should be triggered after `pay.js` is loaded):

```javascript
      const baseRequest = {
        apiVersion: 2,
        apiVersionMinor: 0,
      };

      const allowedCardNetworks = ["MASTERCARD", "VISA"];

      const allowedCardAuthMethods = ["PAN_ONLY", "CRYPTOGRAM_3DS"];

      const tokenizationSpecification = {
        type: "PAYMENT_GATEWAY",
        parameters: {
          gateway: "alliance_bank", // Specify the required gateway
          gatewayMerchantId: "123123123123324", // Specify the required merchantId
        },
      };

      const baseCardPaymentMethod = {
        type: "CARD",
        parameters: {
          allowedAuthMethods: allowedCardAuthMethods,
          allowedCardNetworks: allowedCardNetworks,
        },
      };
      
      const baseCardPaymentMethod = {
        type: "CARD",
        parameters: {
          allowedAuthMethods: allowedCardAuthMethods,
          allowedCardNetworks: allowedCardNetworks,
          assuranceDetailsRequired: true
        },
      };

      const cardPaymentMethod = Object.assign({}, baseCardPaymentMethod, {
        tokenizationSpecification: tokenizationSpecification,
      });

      let paymentsClient = null;

      function getGoogleIsReadyToPayRequest() {
        return Object.assign({}, baseRequest, {
          allowedPaymentMethods: [baseCardPaymentMethod],
        });
      }

      function getGooglePaymentDataRequest() {
        const paymentDataRequest = Object.assign({}, baseRequest);
        paymentDataRequest.allowedPaymentMethods = [cardPaymentMethod];
        paymentDataRequest.transactionInfo = getGoogleTransactionInfo();
        paymentDataRequest.merchantInfo = {
          merchantId: "12345678901234567890", // Specify the required merchantId
          merchantName: "Example Merchant", // Specify the required merchantName
        };
        return paymentDataRequest;
      }

      function getGooglePaymentsClient() {
        if (!paymentsClient) {
          paymentsClient = new google.payments.api.PaymentsClient({
            environment: "TEST", 
          });
        }
        return paymentsClient;
      }

      function onGooglePayLoaded() {
        const paymentsClient = getGooglePaymentsClient();
        paymentsClient
          .isReadyToPay(getGoogleIsReadyToPayRequest())
          .then(function (response) {
            if (response.result) {
              addGooglePayButton();
            }
          })
          .catch(function (err) {
            console.error(err);
          });
      }

      function addGooglePayButton() {
        const paymentsClient = getGooglePaymentsClient();
        const button = paymentsClient.createButton({
          onClick: onGooglePaymentButtonClicked,
          allowedPaymentMethods: [baseCardPaymentMethod],
        });
        document.getElementById("container").appendChild(button);
      }

      function getGoogleTransactionInfo() {
        return {
          countryCode: "UA",
          currencyCode: "UAH",
          totalPriceStatus: "FINAL",
          totalPrice: "1.00", // Specify the required price
        };
      }

      function prefetchGooglePaymentData() {
        const paymentDataRequest = getGooglePaymentDataRequest();
        paymentDataRequest.transactionInfo = {
          totalPriceStatus: "NOT_CURRENTLY_KNOWN",
          currencyCode: "UAH",
        };
        const paymentsClient = getGooglePaymentsClient();
        paymentsClient.prefetchPaymentData(paymentDataRequest);
      }

      function onGooglePaymentButtonClicked() {
        const paymentDataRequest = getGooglePaymentDataRequest();
        paymentDataRequest.transactionInfo = getGoogleTransactionInfo();

        const paymentsClient = getGooglePaymentsClient();
        paymentsClient
          .loadPaymentData(paymentDataRequest)
          .then(function (paymentData) {
            processPayment(paymentData);
          })
          .catch(function (err) {
            console.error(err);
          });
      }
      function processPayment(paymentData) {
        // Next, an example of a request to the server is recorded, you need to substitute your values ​​in the request
        // We send a request to the server, having previously encrypted it, this is not indicated in the example, and execute the request under authorization
        // Request processing is not described, due to the fact that each project has its own binding for calling requests
        // Focus the request on the structure only
        
        fetch('/ecom/execute_request/payments/v1/google_pay/token/purchase', {
          method: 'POST',
          headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({
            "googlePayPaymentData": {
              ...paymentData,
              merchantInfo: {
                merchantId: '123123123123324', // Specify the required gatewayMerchantId
                gateway: 'alliance_bank' // Specify the required gateway
              },
            },
            environment: 'TEST', // or PRODUCTION
            coinAmount: 100, // Price in cents
            desiredThreeDSMode: 'MUST_NOT',
            notificationUrl: 'https://www.google.com.ua/?hl=ru',
            resultRedirectUrl: 'https://www.google.com.ua/?hl=ru',
            purpose: 'purpose',
            comment: 'comment',
            merchantId: '137d6304-0668-11ed-b939-0242ac120002', // Specify the required merchantId
            merchantRequestId: uuid(), // Unique uuid
            date: getCurrentDate(), // пCurrent date in required format
            customerData: {
              senderCustomerId: '34234234',
              senderCountry: '804',
            },
            browserInfo: {
              browserAcceptHeader:
                'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7',
              browserUserAgent:
                'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/111.0.0.0 Safari/537.36',
              browserLanguage: 'ru-RU',
              browserColorDepth: '24',
              browserScreenHeight: '864',
              browserScreenWidth: '1536',
              browserTZ: '-180',
            },
          })
        })
      }
```

3. **Allowed Card Networks**: Specify supported card types in `allowedCardNetworks`.
4. **Tokenization Specification**: Set `gateway` and `gatewayMerchantId` accordingly.
5. **Google Payments Client**: Use `"PRODUCTION"` instead of `"TEST"` when processing live payments.
6. **Merchant Information**: Provide `merchantId` and `merchantName` in the `getGooglePaymentDataRequest` function.
7. **Payment Processing**: Ensure tokenized data is sent securely to the server in the `processPayment` function.
