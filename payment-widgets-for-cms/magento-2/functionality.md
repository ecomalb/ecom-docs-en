# Functionality

### Order creation process

After the customer has selected the products and gone to the payment page, they need to choose the payment method via "Alliance Pay"

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

After that, the buyer is redirected to the payment page to enter personal data.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

### View orders in the admin panel

To view all orders, go to `Sales → Orders`

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

Viewing order details is done via the "View" button.

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

### Checking order status

{% hint style="info" %}
У разі виникнення проблем з статусом замовлення, присутній функціонал ручної перевірки
{% endhint %}

In the payment details there is a section called "Payment & Shipping Method"

<figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

When you click on the "Check Payment Status" button, the order status will be checked.

### Making refunds

To make a refund, you need to go to the payment details and go to "Invoices"

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

And we go to the invoice details via "View"

{% hint style="info" %}
The invoice status must be "Paid", which indicates its success.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

In the invoice details, you need to create a return document by clicking on "Credit Memo"

Then in the "Items to Refund" section, you need to select all the products in the "Qty to Refund" column

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

Then press the "Refund" button

{% hint style="warning" %}
Refund Offline will not create a request to the Alliance Bank API for a refund, this is a standard process for Online\Offline payment methods
{% endhint %}

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

After completing the return, a new operation with the type "Refund" will appear in the order details, and the "Item Status" column will change to "Refunded"

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>
