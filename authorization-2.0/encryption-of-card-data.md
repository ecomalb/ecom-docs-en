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

{% openapi-operation spec="ENEncryptCardDataAPI" path="/cipher/encrypt_by_jwk" method="post" %}
[OpenAPI ENEncryptCardDataAPI](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/a577d9a6e6c1382dc71582f3322cc944bed87b540a9da011eddab269f700aa0a.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20251215%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20251215T133757Z&X-Amz-Expires=172800&X-Amz-Signature=718f5dca75b6e9eabee970f3ef08b85f13f38109cf4ae1dd99e1526d2db79181&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
