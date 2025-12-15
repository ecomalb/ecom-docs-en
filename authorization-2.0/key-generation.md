# Key generation

### Key Retrieval Process:

1. You need to go to the [key generation page](https://www.google.com/search?q=https://merchant.alb.ua/jwt).
2. Generate a key pair.
3. Save the `private_key` portion on your side.
4. Send the `public_key` portion to the bank employee.
5. After the bank employee completes the registration, all necessary data for working with signing will be sent to you.

> The following parameters will be provided:
>
> * `merchantId` - internal terminal identifier (used in requests).
> * `kid` - key identifier.
> * `payment_public_key` - public payment key (used for encrypting card data). You can learn more at this link: [https://docs.merchant.alb.ua/kriptuvannya-danikh#zapit-kriptuvannya-nomeru-kartki](https://docs.merchant.alb.ua/kriptuvannya-danikh#zapit-kriptuvannya-nomeru-kartki) (This link leads to the Ukrainian documentation on card number encryption).

#### Key Parameters for Signing

The keys are generated using the following parameters:

* `kty`: `"EC"` (Elliptic Curve)
* `crv`: `"P-256"` - (ES256) - the most common curve, supported by most frameworks and browsers, and provides a sufficient level of security.
* `use`: `"sig"` - indicates that the key is used for signature.
* `alg`: `"ES256"`.

They are displayed in X.509 PEM Format.

Example Key Appearance:

{% tabs %}
{% tab title="private_key" %}
```
-----BEGIN PRIVATE KEY-----
MEECAQAwEwYHKoZIzj0CAQYIKoZIzj0DAQcEJzAlAgEBBCDCOWlpGDoMfQ25x4Ku
K9J96WuwVn3Ri/UTYEMIV/KPXA==
-----END PRIVATE KEY-----
```
{% endtab %}

{% tab title="public_key" %}
```
-----BEGIN PUBLIC KEY-----
MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEHZ+3wM4Hmyq6f1H7RJjU4SSrqjt3
8f2VX9aS8ikCxXHID92roxYMsDBzAcVRPwNPiexCu5eS/UzyJsP8e9eydA==
-----END PUBLIC KEY-----
```
{% endtab %}
{% endtabs %}

