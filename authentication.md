---
description: Getting Started
---

# Authentication

## To start working with the Alliance pay platform, you need to:

1. Contact Alliance bank to obtain information about the terms of the internet acquiring service.
2. Open an account with Alliance bank.
3. Sign an agreement to connect to the internet acquiring service.
4. Connect to the test environment and conduct test transactions.
5. Connect to the production environment.
6. Start using the internet acquiring service.

## Creation of user security session

The process of creating a new user security session includes a sequence of steps, such as:

* Generating client keys - "Process of generating client communication JWK keys".
* Obtaining encrypted authorization data by encrypting the request body - "Process of creating JWE encrypted data" and sending the "Request to create a technical session".
* Decrypting the received data.

> ! For test purposes only! They are forbidden to be used with product keys.
>
> Clarification: Encryption and decryption URL
>
> <kbd>\{{url\}}cipher/decrypt\_by\_jwk?message=</kbd>
>
> <kbd>\{{url\}}cipher/encrypt\_by\_jwk?message=</kbd>
>
>

#### The following algorithms are used for encryption and decryption:

* Key encryption algorithm (alg) - `ECDH-ES+A256KW`
* Encryption of the request body using the algorithm (enc) - `A256GCM`

#### **Example of encrypt/decrypt**&#x20;

```python
def encrypt_data(self, msg: str, use_server_public_key: bool = False) -> str:
        """Get compact JWE token with encrypted data"""


        if not use_server_public_key:
            with open(self.public_key, 'rb') as public_key_file:
                public_key_raw = json.loads(public_key_file.read().decode())


        public_key = jwk.JWK()
        key_raw = self.server_public_key if use_server_public_key else public_key_raw
        public_key.import_key(**key_raw)
        protected_header = {'alg': 'ECDH-ES+A256KW', 'enc': 'A256GCM'}


        jwetoken = jwe.JWE(msg.encode('utf-8'), recipient=public_key, protected=protected_header)
        return jwetoken.serialize(compact=True)


    def decrypt_data(self, msg: str) -> str:
        """Get decrypted data (from JWE)"""


        with open(self.private_key, 'rb') as private_key_file:
            private_key_raw = json.loads(private_key_file.read().decode())


        private_key = jwk.JWK()
        private_key.import_key(**private_key_raw)


        jwetoken = jwe.JWE()
        jwetoken.deserialize(msg, key=private_key)
        return jwetoken.payload.decode()
```



## Process of Generating Client Communication JWK Keys

Generating a public and private key (JSON Web Key) is done with the following parameters:

* "[kty](https://datatracker.ietf.org/doc/html/rfc7518#section-6.1)": "EC" - key type
* "[crv](https://datatracker.ietf.org/doc/html/rfc7518#section-6.2.1.1)": "P-384" - elliptic curve of the key
* "[use](https://datatracker.ietf.org/doc/html/rfc7517#section-4.2)": "enc" – parameter used for key encryption
* "[alg](https://datatracker.ietf.org/doc/html/rfc7518#section-4.1)": "ECDH-ES+A256KW" - algorithm for which the key is used

An example of key generation for reference is available at [https://mkjwk.org/](https://mkjwk.org/)

Process of Creating [JWE](https://datatracker.ietf.org/doc/html/rfc7516) Encrypted Data

The object represents encrypted data.

To create it, the following parameters must be specified:

* Encoding of the encrypted data: UTF-8
* Encryption algorithm: ECDH-ES+A256KW
* Encryption method: A256GCM
* The corresponding algorithm's public key must be used.

**Example of pre-encryption data:**

```json
{
  "deviceType": "ECOM_MERCHANT_SERVICE_DEVICE",
  "clientPublicKey": {
    "kty": "EC",
    "crv": "P-384",
	"x": "Q0aVpIzurAJeLgcwr9SwrjBaxt6vWU9Xt9Om5WseRVHOK0KHt1fS-TmM4nNwocyl",
	"y": "nugxKjzsgyCBY8h095r3dex5LL0MduzU8ovLPYnl3jlExzpSG4sFTsBbUWJo8GLP"
  }
}
```

**Example of JWE after encryption:**

```json

eyJhbGciOiJFQ0RILUVTK0EyNTZLVyIsImVuYyI6IkEyNTZHQ00iLCJlcGsiOnsia3R5IjoiRUMiLCJ4IjoiSVprUG1oVm5fQUd2RkJXS2dIYmtfOFlLX2Q1aXZabHJJU19DaUxublhlVUkyX1NtSC0wWkJDOWkySDg1c3ladCIsInkiOiJ6SUFkSS1wNXZrdjVuVjNpSVNqMlFiSW85NnU0eXBhZVg0WHBJSUhiYlp4LWhkc3hwLUVCbDIwRDlNOTVHTWtQIiwiY3J2IjoiUC0zODQifX0.jfDIZ64JlVbdOgXkh0bqX6uA8H6Pkkg6s861OKn_vBtIQYk4BRxPjA.9ns8h0iFDcmG_hib.USraeD8abgHZwD_kas3L1rO1U0n_YhLx_LJpxKICAoVqVQ.myDB-We0sg1l5nzfi7b2sg

```

## **The process of decrypting JWE data:**

**Example JWE token**&#x20;

```json
eyJhbGciOiJFQ0RILUVTK0EyNTZLVyIsImVuYyI6IkEyNTZHQ00iLCJlcGsiOnsia3R5IjoiRUMiLCJ4IjoiSVprUG1oVm5fQUd2RkJXS2dIYmtfOFlLX2Q1aXZabHJJU19DaUxublhlVUkyX1NtSC0wWkJDOWkySDg1c3ladCIsInkiOiJ6SUFkSS1wNXZrdjVuVjNpSVNqMlFiSW85NnU0eXBhZVg0WHBJSUhiYlp4LWhkc3hwLUVCbDIwRDlNOTVHTWtQIiwiY3J2IjoiUC0zODQifX0.jfDIZ64JlVbdOgXkh0bqX6uA8H6Pkkg6s861OKn_vBtIQYk4BRxPjA.9ns8h0iFDcmG_hib.USraeD8abgHZwD_kas3L1rO1U0n_YhLx_LJpxKICAoVqVQ.myDB-We0sg1l5nzfi7b2sg
```

**Example of data after decrypting the JWE token**

```json
{
  "authToken": "c8e28b98-e3bd-42f3-8cba-7b3c3dd5c9da",
  "deviceId": "8485ff92-8ac3-4af1-aaa7-e72edfed2516",
  "serverPublicKey": {
	"kty": "EC",
	"crv": "P-384",
	"x": "glGAHNVNkXbygpcRnhoEGSUEQM-s8RrcaxY7HSJ4Cs0QIreWxYEJI2iz0W4ZtH8a",
	"y": "AQ_vq8Ks_dTB-HiQrPi_fpE-nlQXbHoEeInURhZFVFc1bpi7NqynflKnyBWLy590"
  }
}
```

**Request for creating a technical session**

```json
curl --location 'https://api-ecom-prod.bankalliance.ua/api-gateway/authorize_virtual_device' \
--header 'x-api_version: 1' \
--header 'Content-Type: application/json' \
--header 'Cookie: visid_incap_2770403=fJEGXzciTnG2/y/pST3lzBM/JGMAAAAAQUIPAAAAAAAV+dwIpk/4YrgvV5ijeEu6' \
--data '
{
    "serviceCode": "137d9304-0368-11ed-b939-0242ac120002"
}'
```

**Example response**

```json
{
"jwe": "eyJhbGciOiJFQ0RILUVTK0EyNTZLVyIsImVuYyI6IkEyNTZHQ00iLCJlcGsiOnsia3R5IjoiRUMiLCJ4IjoiZ3F2M0xDYnpDcEZoaWhEQlRZX1JxSFN6cUZsLWJYYVZjUHhJU2w4UmNPbHdjNU5UNnpvd3Y1WWhTQW5sekxPMCIsInkiOiJENWpYX2t4UGZVYlJySmVTZGNQbnhzN0dNMlZuZTdvSHA5N3g2SVNPdWNJdU81SVY2R2pFa3NRSlBicGQ2bWVfIiwiY3J2IjoiUC0zODQifX0.nbpNZhLmDpzMdhntvVOrpdLOLu6Ryhhb-S08LgdN8iJscD4j3mqX_w.8WWRrwzW93i0oGui.jjm3mvrLxDvJTy6-lKzXHTzMliD7x3cV3ZhgAcmgWL8uyHj3Cpb5LtcdUM6KxzBsAj0CWmdjj_VCzbloEHJVQCoDPpCqIe8ScIh5irXB3hG8onyK0tKXOibf7gRoEIWES_OuT3yAfXfNn0DuEK6PhKH1sihLMDWD_ns7CATBy6atZQkk00SkswDLgDVucCakC5RmyrDDFHsaEcKAIh6eehlhHotR6x82v9qplYObKMIqneEmYRUrildPyi43_RXmkSZUFt2Bx5Q7SEINQsFw6qRPzAkhpPH2d5JWefDr3elamiJeibMJQDcKcfUDnDCviX-e2Wf3sTnacufV8O5s1hDpfJYZAxZonGK8g3CvcWk34EsnPD0pm8DOoTtSeIP9cgS4w05s53LxbFPH9xXYtxkfrSBVtnbiHcZ37GVWOdEqVeqgmDKizu6WxQnW9oJdNEsG6a5FavarFURvS5Xgz46cluYj3ppZSqIQiRSRhNDH0AD9fFPeskvsGjZ5O8efA3eRyT5gNKCO05I9ZtnC.w3pu8oSnWaBkbBjQyQN9hQ"
}

```

## **Request for decrypting the technical session**&#x20;

**Example request body**

```json
curl --location 'https://api-ecom-release.develop.bankalliance.ua/cipher/decrypt_by_jwk?message={{responseJwe}}' \
--header 'Content-Type: application/json' \
--header 'Cookie: visid_incap_2770403=fJEGXzciTnG2/y/pST3lzBM/JGMAAAAAQUIPAAAAAAAV+dwIpk/4YrgvV5ijeEu6' \
--data '
{
    "kty": "EC",
    "d": "xVoCzl9Vvlk_bP_O1OLmlTSN9P07fq_7bEBnpQhoqo29PV2TR7smqu5nAz0wZhZ_",
    "use": "enc",
    "crv": "P-384",
    "x": "tfOqYVvawSq5HDGvWd_zm-ha8tDuZci5THnAokWJpdZSUk40VpAtofDY_Q8fUG9O",
    "y": "LMHt1lT4ZdK3puWwrdrAUZBLazDbwwoZveFnlcYlL7PO62dDdHdo_KhYeUoPOHgk",
    "alg": "ECDH-ES+A256KW"
}'
```

**Example response**

```json
{
    "refreshToken": "5aba78ac-8850-4619-8232-f62089cbcbb3",
    "authToken": "14a74387-9f20-4e73-a314-0d2ca80222b6",
    "deviceId": "1d9742cf-d392-4c2b-9982-4dc6ec2224b2",
    "serverPublic": {
        "kty": "EC",
        "crv": "P-384",
        "x": "BSWUuzrcIWk3GFUqD2ClMxVwycEWXoMnqJsDwOJNidTtfJJ0dn8h9m3Q8fRoxBaA",
        "y": "PnFAa3LNxJgiUYZXUx7-kr049B0IxOUXP2l8_Z7mEgUv9-xhVWuf0sJhiOn69VPe"
    },
    "tokenExpirationDateTime": "2023-03-18 12:34:52.0998 +0000"
}
```

Session **refresh** is not provided; to generate a new serverPublic, you need to repeat the request for creating a technical session.&#x20;
