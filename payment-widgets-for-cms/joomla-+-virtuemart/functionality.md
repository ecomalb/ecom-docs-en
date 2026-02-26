# Functionality

### Order creation process

After the customer has selected the products and gone to the payment page, they need to choose the payment method via "AlliancePay"

<figure><img src="../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

After that, the buyer is redirected to the payment page to enter personal data.

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

### View orders in the admin panel

To view all orders, go to `Components → VirtueMart → Orders`

<figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

Viewing payment details is done by clicking on the value in the `"Order number/Invoice"` column.

<figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

### Перевірка статусу замовлення

{% hint style="info" %}
У разі виникнення проблем з статусом замовлення, присутній функціонал ручної перевірки
{% endhint %}

In the payment details there is a section "AlliancePay update transactions and statuses"

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

When you click the "Update" button, the payment status will be checked.

### Making returns

In the payment details, you can find two sections "Partial Refund (Alliance)" and "Full Refund (AlliancePay)"

{% hint style="info" %}
Обов'язково "Статус оплати" плтежу повинен мати "SUCCESS", що вказує на його успішність

![](<../../.gitbook/assets/image (57).png>)
{% endhint %}

{% tabs %}
{% tab title="Partial refund" %}
To perform a partial refund, in the "Partial refund (Alliance)" section, you need to use the checkboxes to select the products for which the refund will be performed.

<figure><img src="../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

Thus, the system automatically calculates the amount for the selected products

After that, you need to click the "Return for selected products" button, a window will immediately appear with a message about a successful partial return

<figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

In the payment details in the "Alliance Transaction History" section, a new payment with the transaction type "REFUND" will appear.

<figure><img src="../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Full refund" %}
To perform a full refund, click the "Execute Order Refund" button in the "Full Refund (AlliancePay)" section.

<figure><img src="../../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

After that, a new payment with the transaction type "REFUND" will appear in the "Alliance Transaction History" section.

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

And also in the "Items" section, each product will receive the status "Refunded"

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}
