# Installation instructions

Magento 2 Payment Widget:

{% file src="../../.gitbook/assets/magento2_alliance_pay_v1.0.0.zip" %}

{% stepper %}
{% step %}
### Creating the required folder structure

```
mkdir -p app/code/Alliance/AlliancePay
```
{% endstep %}

{% step %}
### Download/copy the module files to the created folder

```
The path must be: app/code/Alliance/AlliancePay/registration.php
```
{% endstep %}

{% step %}
### Provide correct file permissions (optional)

```
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
```
{% endstep %}

{% step %}
### Install module dependencies

```
composer install
```
{% endstep %}

{% step %}
### Enable the module

```
php bin/magento module:enable Alliance_AlliancePay
```
{% endstep %}

{% step %}
### Update the system

```
php bin/magento setup:upgrade
```
{% endstep %}

{% step %}
### Start compilation

```
php bin/magento setup:di:compile
```
{% endstep %}

{% step %}
### Deploy static files

```
php bin/magento setup:static-content:deploy -f
```
{% endstep %}

{% step %}
### Clear the cache

```
php bin/magento cache:flush
```
{% endstep %}
{% endstepper %}

### Technical requirements

* PHP version - 8.2
* Magento 2 version - 2.4
* For decryption and communication with Ecom, the payment module uses the following library - [GitHub - kelvinmo/simplejwt: A simple JSON web token library written in PHP.](https://github.com/kelvinmo/simplejwt) , which is built into the module itself
* The server must have **PHP** extensions, `gmp`, `hash`, `openssl`, `sodium` enabled \[for the `simplejwt` library to work]
* To get the required country code in `ISO3166` format, you need to install the[ league/iso3166](https://packagist.org/packages/league/iso3166) library version 4.3.3
