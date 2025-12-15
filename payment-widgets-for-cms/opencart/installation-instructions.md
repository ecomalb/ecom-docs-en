# Installation instructions

OpenCart Payment Widget:

{% file src="../../.gitbook/assets/payment_widget_opencart.zip" %}

### Download Open Step-by-step instructions for installing the payment widget:

1. In the "OpenCart" admin in the "Extensions" -> "Installer" section, you need to download the archive specified above
2. In the "Extensions" -> "Extensions' section, you need to activate and configure the module

### Requirements for the server where to install the payment module&#x20;

1. The payment module is developed only for the OpenCart 4.X version. That is, the version must be 4.0.0 or higher (I personally developed and tested on version 4.1.0.0)
2. Php version 8.0 or higher
3. For decryption and communication with the EC, the payment module uses the following library - GitHub - kelvinmo/simplejwt: A simple JSON web token library written in PHP. , which is built into the module itself
4. The PHP extension must be enabled on the server - gmp \[for simplejwt library to work]
5. The server must have the php extension - hash \[for simplejwt library to work]
6. The server must have the php extension - openssl \[for simplejwt library to work]
7. The server must have the php extension - sodium \[for simplejwt library to work]
8. GuzzleHttp requires a module. In Opencart 4.1.0 it seems to come out of the box but you need to test it on different versions
