# Installation instructions

WordPress Payment Widget:

{% file src="../../.gitbook/assets/alb-hpp-alliancepay.zip" %}

1.  Download the plugin archive and install via Plugins → Add New → Download Plugin.<br>

    <figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FmMnM1AJVrAWCFQ2aZgVe%2Fimage.png?alt=media&#x26;token=d7446d38-8d21-431f-a7a5-64c96b6fb07f" alt=""><figcaption></figcaption></figure>
2. Activate the plugin.
3. The AlliancePay item will appear in the Admin Panel menu.
4.  Then go to Woocommerce settings and activate the plugin. (screen 2) woocommerce->settings->payments<br>

    <figure><img src="https://1348498792-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FdjW26z83WQoOq0ZjunWw%2Fuploads%2FKBejjX2jLGnEQJbDVibQ%2Fimage.png?alt=media&#x26;token=3d4b7d4b-51b1-493a-aa9e-365e4ec02c8f" alt=""><figcaption></figcaption></figure>
5. The payment page should have the shortcode \[woocommerce\_checkout]

### Requirements

* WordPress 6.8.2+ (PHP 8.0+; PHP 8.2+ is recommended; PHP extensions: gmp, hash, openssl, sodium).&#x20;
* WooCommerce version: 10.1.0 + &#x20;
* Administrative rights to access the plugin. &#x20;
* Credentials: Merchant ID, Service Code, Private JWK (to obtain, please contact JSC “BANK ALLIANCE”). &#x20;
* Correct site time zone: Europe/Kyiv (to display tokenExpiration).

### Requirements for the server where the payment module is installed

* For decryption and communication with ECOM, the payment module uses the following library - GitHub - [GitHub - kelvinmo/simplejwt: A simple JSON web token library written in PHP.](https://github.com/kelvinmo/simplejwt) , which is built into the module itself
* The server must have the PHP extension - gmp enabled \[for the simplejwt library to work]
* The server must have the PHP extension - hash enabled \[for the simplejwt library to work]
* The server must have the PHP extension - openssl enabled \[for the simplejwt library to work]
* The server must have the PHP extension - sodium enabled \[for the simplejwt library to work]
