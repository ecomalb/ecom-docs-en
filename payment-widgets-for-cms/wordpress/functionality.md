# Functionality

### List of orders

A new column “AlliancePay payment status” is added to the list of orders. If the payment was made via AlliancePay, then in this column in the list for the order there will be a button “Payment status”. Please note that if there is no Callback for the order, then “No callback from AlliancePay” is indicated. Check “Payment status”

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2Fpb3ds2n2D5ih6VbthUEu%2Fimage.png?alt=media&#x26;token=eefaff4b-391d-4db0-a1a0-23840b505fa7" alt=""><figcaption></figcaption></figure>

### Order details

Callback is received, then the data is taken from the local DB, in which we saved the callback

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FLA8Sghj9cKnI38euQjzY%2Fimage.png?alt=media&#x26;token=41a4f171-8f1c-4a95-b581-090a8b0ccd23" alt=""><figcaption></figcaption></figure>

Callback is not received, then the data is taken by direct request to eCom

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2F2cFGOSMENrZaLuW1K2hK%2Fimage.png?alt=media&#x26;token=2827eac8-0556-43b4-a373-d12f1955542a" alt=""><figcaption></figcaption></figure>

### Payment page

The payment page must have the shortcode \[woocommerce\_checkout]. AlliancePay payment option will appear at checkout

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FyzbgkLC9J7wVcRs9lDhr%2Fimage.png?alt=media&#x26;token=bd8a2b5d-3a5e-4bb7-ae3a-d4c27d2bf726" alt=""><figcaption></figcaption></figure>

Payment widget:

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FK1jCUIqGjTXqxfo6N2l4%2Fimage.png?alt=media&#x26;token=f675779b-cae5-4d67-b4ac-943c38eda870" alt=""><figcaption></figcaption></figure>

After payment, Ecom must send us a Callback about the payment status and then we finalize the payment on our side.
