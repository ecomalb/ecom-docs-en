---
description: Setting up the payment module before starting work.
---

# Functionality and description of the payment module

#### The path to the module settings&#x20;

In the admin panel is "Extensions"->"Extensions"->"Payments" -> "Alliance Payment"

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FMkqTB69mSNf6x2KSwyYZ%2Fimage.png?alt=media&#x26;token=d0c33831-71c6-4d70-b6b5-0fdd850f0c0b" alt=""><figcaption></figcaption></figure>

#### Module configuration interface

In the parameters, specify the data that was received by the bank employee.

In the `Alliance API URL` field, you need to specify the value - https://api-ecom-prod.bankalliance.ua

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FiGvVncs340HKoW7uXPK6%2Fimage.png?alt=media&#x26;token=a2d0973d-d6d6-4875-bbb0-a0f75db73d86" alt=""><figcaption></figcaption></figure>

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FQDbVLOmUkRVYNGFJOiiQ%2Fimage.png?alt=media&#x26;token=a92b1682-39b9-4ce4-920e-5d6c22a82029" alt=""><figcaption></figcaption></figure>

#### Check order status

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2Fn30GwG2JZ2Wkld53rRFW%2Fimage.png?alt=media&#x26;token=7db61778-448d-4e3b-8c1b-99fe738cfe6c" alt=""><figcaption></figcaption></figure>

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FEDPGJyCwU0THI9HAXD5W%2Fimage.png?alt=media&#x26;token=7d208475-db76-42bf-a3d0-4794184d7e99" alt=""><figcaption></figcaption></figure>

### Transaction review

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FOCw4vXFA21UfgQLF0Wrz%2Fimage.png?alt=media&#x26;token=79637ddc-91ef-4cae-ad21-ea4fd6b3abbe" alt=""><figcaption></figcaption></figure>

### Order history

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FhvvOdcx0K6qG2efaGYKe%2Fimage.png?alt=media&#x26;token=f0443499-867b-4ef1-84eb-1ee1bcfa080a" alt=""><figcaption></figcaption></figure>

#### Checkout

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FeW354tcyVdz0guNW7KIY%2Fimage.png?alt=media&#x26;token=07564406-a46e-418f-bdcc-bd490c3b4ab4" alt=""><figcaption></figcaption></figure>

#### Checkout result

<figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FbMrt4hvmhIsZwx8vDO6t%2Fimage.png?alt=media&#x26;token=be11c5a9-9b03-462e-9d1b-8655feb2b759" alt=""><figcaption></figcaption></figure>

### Making a refund

{% tabs %}
{% tab title="OpenCart 3.0" %}
To make a refund, you need to go to the order details

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

and here you will find the "Повне повернення коштів" and "Часткове повернення" buttons

### Full refund

When clicked, a pop-up window appears with a message about the successful completion of a full refund

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

In the order details, each product will be marked with an icon as returned and a new entry about a full refund will appear in the order history.

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>



### Partial refund

In the order details, you need to select which products will be partially refunded.

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

After clicking the "Часткове повернення" button, a confirmation window appears.

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

After that, a confirmation window will appear.

<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

In the payment details, the goods will be marked as returned.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### View return details

Additionally, there is a "Returns" tab where you can view details of completed returns

The return is tied to each product, so each line displays which product the return was completed for

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Натиснувши на редагувати ![](<../../.gitbook/assets/image (9).png>) , opens the verification details where you can view information about the user, view\specify the reason for the verification, change the status and change the product

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="OpenCart 4.0" %}



{% endtab %}
{% endtabs %}
