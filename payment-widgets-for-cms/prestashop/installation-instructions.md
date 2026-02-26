# Installation instructions

**PrestaShop** Payment Widget:



{% file src="../../.gitbook/assets/prestashop-alliancepay-v.1.0.0.zip" %}

{% stepper %}
{% step %}
### Download the plugin archive and install it

Open "Modules" → "Module Manager"

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Click "Download module" and select the archive

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Module activation

Select the "Payment" category

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

A module named "AlliancePay v1.0.0 – Alliance Dgtl" should appear.

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

You need to select the module and click "Enable"

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

### Requirements for the server where to install the payment module

1. PHP version 7.4 or higher
2. For decryption and communication with Ecom, the payment module uses the following library - [GitHub - kelvinmo/simplejwt: A simple JSON web token library written in PHP](https://github.com/kelvinmo/simplejwt). , which is built into the module itself
3. The PHP extension - **gmp** must be enabled on the server \[for the simplejwt library to work]
4. The PHP extension - **hash** must be enabled on the server \[for the simplejwt library to work]
5. The PHP extension - **openssl** must be enabled on the server \[for the simplejwt library to work]
6. The PHP extension - **sodium** must be enabled on the server \[for the simplejwt library to work]
