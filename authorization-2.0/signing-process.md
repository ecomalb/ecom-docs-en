# Work with subscriptions

## Working with Signing

### JWS Structure

A typical JWS (JSON Web Signature) consists of three parts, separated by dots (`.`):

```
{Base64Url(header)}.{Base64Url(payload)}.{Base64Url(signature)}
```

Where:

* header — describes general metadata.

JSON

```
{
    "alg": "ES256",  // Signing Algorithm
    "kid": "uuid",  // Public Key Identifier (provided by the bank employee)
    "ts" : "1763034308", // Date and time in timestamp format
    "targetUrl" : "/ecom/jws/payments/create/purchase_v3" // URL to which the request is sent
}
```

* payload — the data to be transmitted (required data for each request, see [H2H Payment Methods](https://docs.merchant.alb.ua/avtorizaciya-2.0/platizhni-metodi-h2h) documentation).
* signature — the digital signature created using the sender's private key.

JWS Example:

```
eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.
eyJ1c2VySWQiOiIxMjMiLCJyb2xlIjoiYWRtaW4ifQ.
MEYCIQDmG...
```

How Signing is Performed

1. The header (metadata) and payload (request data) are formed.
2. Both parts are encoded in Base64Url format.
3.  They are combined into a single message:

    ```
    signingInput = base64Url(header) + "." + base64Url(payload)
    ```
4. This message is signed with the private key (for details on how to get the key, see [Key Generation](https://docs.merchant.alb.ua/avtorizaciya-2.0/generaciya-klyuchiv)) using the specified algorithm.
5. The result (signature) is added as the third part of the JWS.

An example of JWS generation can be viewed on the website: [https://www.jwt.io/](https://www.jwt.io/)

Example Code for Signature Generation:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
import { CompactSign, importPKCS8 } from 'jose';

// === Data ===
const privateKeyPem = `
-----BEGIN EC PRIVATE KEY-----
MHcCAQEEIBOS+Xg3qgYSe5T4H2AoB0zWrhb0jNmcdW6o2bTXXWlQoAoGCCqGSM49
AwEHoUQDQgAEMO4qQsgPskZ4E1X6nHZU9yHnJrZ97K3QAjQ1oG1zgrht3mA4+lf5
aMqTIk1glXZpMT4pAzTURmmP2+prvQul3g==
-----END EC PRIVATE KEY-----
`;

const header = {
  alg: "ES256",
  kid: "9a3f6e6d-4f56-4b8b-99d3-24db19f54d8a",
  ts: Math.floor(Date.now() / 1000),
  targetUrl: "/ecom/jws/payments/create/purchase_v3"
};

// payload is the request body
const payload = {
  merchantId: "12345",
  amount: "1000.00",
  currency: "UAH",
  orderId: "ORD-2025-001"
};

// === JWS Generation ===
const privateKey = await importPKCS8(privateKeyPem, 'ES256');
const encoder = new TextEncoder();

const encodedHeader = Buffer.from(JSON.stringify(header)).toString('base64url');
const encodedPayload = Buffer.from(JSON.stringify(payload)).toString('base64url');
const signingInput = `${encodedHeader}.${encodedPayload}`;

const sign = new CompactSign(encoder.encode(JSON.stringify(payload)))
  .setProtectedHeader(header);

const jws = await sign.sign(privateKey);

console.log("JWS:", jws);


```
{% endtab %}

{% tab title="Python" %}
```python
from jwcrypto import jwk, jws
import json, time, base64

# === Private Key ===
private_key_pem = """-----BEGIN EC PRIVATE KEY-----
MHcCAQEEIBOS+Xg3qgYSe5T4H2AoB0zWrhb0jNmcdW6o2bTXXWlQoAoGCCqGSM49
AwEHoUQDQgAEMO4qQsgPskZ4E1X6nHZU9yHnJrZ97K3QAjQ1oG1zgrht3mA4+lf5
aMqTIk1glXZpMT4pAzTURmmP2+prvQul3g==
-----END EC PRIVATE KEY-----"""

key = jwk.JWK.from_pem(private_key_pem.encode())

header = {
    "alg": "ES256",
    "kid": "9a3f6e6d-4f56-4b8b-99d3-24db19f54d8a",
    "ts": int(time.time()),
    "targetUrl": "/ecom/jws/payments/create/purchase_v3"
}

payload = {
    "merchantId": "12345",
    "amount": "1000.00",
    "currency": "UAH",
    "orderId": "ORD-2025-001"
}

protected = base64.urlsafe_b64encode(json.dumps(header).encode()).decode().rstrip("=")
body = base64.urlsafe_b64encode(json.dumps(payload).encode()).decode().rstrip("=")

signing_input = f"{protected}.{body}"

signature = jws.JWS(json.dumps(payload))
signature.add_signature(key, protected=json.dumps(header), alg="ES256")

print("JWS:", signature.serialize(compact=True))
```
{% endtab %}

{% tab title="Java" %}
```java
import com.nimbusds.jose.*;
import com.nimbusds.jose.crypto.*;
import com.nimbusds.jose.util.Base64URL;

import java.security.*;
import java.security.spec.*;
import java.util.*;

public class GenerateJWS {
    public static void main(String[] args) throws Exception {
        // Load Private Key (EC P-256)
        String privateKeyPEM = """
        -----BEGIN EC PRIVATE KEY-----
        MHcCAQEEIBOS+Xg3qgYSe5T4H2AoB0zWrhb0jNmcdW6o2bTXXWlQoAoGCCqGSM49
        AwEHoUQDQgAEMO4qQsgPskZ4E1X6nHZU9yHnJrZ97K3QAjQ1oG1zgrht3mA4+lf5
        aMqTIk1glXZpMT4pAzTURmmP2+prvQul3g==
        -----END EC PRIVATE KEY-----
        """;

        // (Simple example: create an EC key pair)
        KeyPairGenerator keyGen = KeyPairGenerator.getInstance("EC");
        keyGen.initialize(Curve.P_256.toECParameterSpec());
        KeyPair pair = keyGen.generateKeyPair();

        Map<String, Object> payload = new HashMap<>();
        payload.put("merchantId", "12345");
        payload.put("amount", "1000.00");
        payload.put("currency", "UAH");
        payload.put("orderId", "ORD-2025-001");

        JWSHeader header = new JWSHeader.Builder(JWSAlgorithm.ES256)
                .customParam("kid", "9a3f6e6d-4f56-4b8b-99d3-24db19f54d8a")
                .customParam("ts", System.currentTimeMillis() / 1000)
                .customParam("targetUrl", "/ecom/jws/payments/create/purchase_v3")
                .build();

        Payload jwsPayload = new Payload(new com.nimbusds.jose.util.JSONObjectUtils().toJSONString(payload));

        JWSObject jwsObject = new JWSObject(header, jwsPayload);
        jwsObject.sign(new ECDSASigner((ECPrivateKey) pair.getPrivate()));

        System.out.println("JWS: " + jwsObject.serialize());
    }
}
```
{% endtab %}

{% tab title="PHP" %}
```php
<?php
require 'vendor/autoload.php';

use Jose\Component\Core\JWK;
use Jose\Component\Signature\JWSBuilder;
use Jose\Component\Signature\Algorithm\ES256;
use Jose\Component\Core\Util\JsonConverter;

// Private Key
$privateKey = <<<EOD
-----BEGIN EC PRIVATE KEY-----
MHcCAQEEIBOS+Xg3qgYSe5T4H2AoB0zWrhb0jNmcdW6o2bTXXWlQoAoGCCqGSM49
AwEHoUQDQgAEMO4qQsgPskZ4E1X6nHZU9yHnJrZ97K3QAjQ1oG1zgrht3mA4+lf5
aMqTIk1glXZpMT4pAzTURmmP2+prvQul3g==
-----END EC PRIVATE KEY-----
EOD;

$jwk = JWK::createFromPem($privateKey);

$header = [
    'alg' => 'ES256',
    'kid' => '9a3f6e6d-4f56-4b8b-99d3-24db19f54d8a',
    'ts' => time(),
    'targetUrl' => '/ecom/jws/payments/create/purchase_v3'
];

$payload = [
    'merchantId' => '12345',
    'amount' => '1000.00',
    'currency' => 'UAH',
    'orderId' => 'ORD-2025-001'
];

$jwsBuilder = new JWSBuilder(null, [new ES256()]);
$jws = $jwsBuilder
    ->create()
    ->withPayload(JsonConverter::encode($payload))
    ->addSignature($jwk, $header)
    ->build();

$serializer = new \Jose\Component\Signature\Serializer\CompactSerializer();
echo "JWS: " . $serializer->serialize($jws, 0);

```
{% endtab %}
{% endtabs %}

### JWS Requirements

#### 1. General JWS Requirements:

* All API requests must be signed using JWS (JSON Web Signature).
* The signature is formed according to the algorithm corresponding to the key type passed in the `kid` parameter.
* During JWS validation, the system checks the correctness of the header, payload, and signature.

In case of violation of any of the requirements, the request will be rejected with an error.

#### 2. JWS Header Requirements:

Supported header parameters:

| **Field**   | **Description**                                 | **Type**                         | **Mandatory** | **Example**                             |
| ----------- | ----------------------------------------------- | -------------------------------- | ------------- | --------------------------------------- |
| `alg`       | Signing algorithm corresponding to the key type | string                           | Yes           | `ES256`                                 |
| `kid`       | Public key identifier                           | string                           | Yes           | `28da60c2-d60f-404e-b4da-6b089fb29555`  |
| `ts`        | JWS generation time                             | number (Unix timestamp, seconds) | Yes           | `1763034308`                            |
| `targetUrl` | The URL for which the request is formed         | string (URL)                     | Yes           | `/ecom/jws/payments/create/purchase_v3` |

**2.1. Token Expiration Check (`ts`)**

* The `ts` field must contain a timestamp (in seconds).
* The JWS is considered valid for 60 seconds from the moment of generation.

> Error Conditions:
>
> * If `ts` > (current time + 60 seconds) or `ts` < (current time − 60 seconds).
> * If the value of `ts` does not match the format `1763938228`.

**2.2. `targetUrl` Check**

The system checks that the value:

* matches the URL format,
* is an allowed API route,
*   matches the actual endpoint to which the request is sent.

    Example:

    Request received at: {url}/ecom/jws/payments/create/purchase\_v3

    Actual targetUrl: /ecom/jws/payments/create/purchase\_v3

> Error Conditions:
>
> * If `targetUrl` is invalid, has the wrong format, or does not match the actual request path.
> * If the request was sent to `/ecom/jws/payments/account_to_card_v3`, but the `targetURL` value is specified as `/ecom/jws/payments/create/purchase_v3`.

**2.3. Signature Algorithm Check (`alg`)**

The `alg` value must match the algorithm of the key pair used for the signature, which is `ES256`.

> Error Condition:
>
> * If a value is passed in `alg` that does not match the algorithm of the generated key.

**2.4. Key Existence Check (`kid`)**

* `kid` must correspond to one of the merchant's active keys.

> Error Condition:
>
> If the key with the specified `kid` does not exist.

#### 3. JWS Payload Requirements

The JWS Payload must contain the request body in JSON format, which fully complies with the requirements of the specific endpoint.

Example: If the request is made to `/ecom/jws/payments/create/purchase_v3`, then the body of this request ([PURCHASE Request Step 1](https://docs.merchant.alb.ua/avtorizaciya-2.0/platizhni-metodi-h2h/purchase/zapit-provedennya-purchase-krok-1)) is included in the JWS payload.

**3.1. Request Body Structure Validation**

The payload must:

* contain all mandatory parameters defined for the corresponding endpoint,
* comply with the JSON schema,
* pass internal business validation.

> Error Condition:
>
> If the request body does not meet the requirements (missing fields, incorrect types).

**3.2. Merchant Check (`merchantId`)**

All operations must be performed on behalf of an existing merchant.

> Error Condition:
>
> If `merchantId` is passed in the payload that:
>
> * does not exist
> * is deactivated
> * is not linked to the `kid` key
