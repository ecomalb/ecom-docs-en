# Encryption of card data

## Working with the JWE Encryption Standard

To ensure data confidentiality during transmission, the JWE (JSON Web Encryption) standard is used, which defines the format for encrypted JSON messages.

To encrypt the Card Number (PAN), the public payment key (`payment_public_key`) is used, which is provided during key generation (see "[Key Generation](https://docs.merchant.alb.ua/avtorizaciya-2.0/generaciya-klyuchiv#proces-otrimannya-klyuchiv)" documentation).

The key conforms to the JWK (JSON Web Key) format:

JSON

```json
"paymentPublicKey": 
{
    "kty": "EC",
    "x": "Hp833OY6a0VbFD1j8xFyXWcAA-HOlyr7B_-B05esZUy32RA41s0oGAMTal23AX9d",
    "y": "WGHeR9PhKRymoA-ggsR3VkQTgdfzt7PWa8P2qNpu0cV83lmLxE57b8rR7ajBurvj",
    "crv": "P-384"
}
```

> The Public Payment Key (`payment_public_key`) corresponds to the parameters:
>
> * "[kty](https://datatracker.ietf.org/doc/html/rfc7518#section-6.1)": "EC" - Key type (Elliptic Curve)
> * "[crv](https://datatracker.ietf.org/doc/html/rfc7518#section-6.2.1.1)": "P-384" - Elliptic Curve type
> * "[use](https://datatracker.ietf.org/doc/html/rfc7517#section-4.2)": "enc" – Parameter used for key encryption
> * "[alg](https://datatracker.ietf.org/doc/html/rfc7518#section-4.1)": ECDH-ES+A256KW - Algorithm for which the key is used

#### Example Endpoint for Encryption:

> Warning:
>
> The request is for testing purposes only. It is forbidden to execute the request with real keys. Encryption must be implemented on your side.

### Encrypting a Message using JWK
