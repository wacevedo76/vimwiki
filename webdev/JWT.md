--------------------------------------------------------------------------------
JSON Web Token (JWT)
--------------------------------------------------------------------------------
What is a JSON Web Token?    | * JSON Web Token is a self-contained way to 
                             |   securely transmit data nd information between
                             |   two parties using a JSON Object.
                             |
                             | * JSON Web Tokens can be truested because each 
                             |   JWT can be digitally signed, which in turn 
                             |   allows the server to know if the JWT has been
                             |   changed at all
                             |
                             | * JWT should be used when dealing with 
                             |   authorization
                             |
                             | * JWT is a great way for information to be 
                             |   exchanged between the server and client
                             |
JSON Web Token Structure     | * A JSON Web Token is made of three separate
                             |   parts separated by dots (.) which include:
                             |
                             |   aaaaaaaa.bbbbbbbb.cccccccc
                             |
                             |   * Header: (a)
                             |   * Payload: (b)
                             |   * Signature: (c)
                             |
JWT Header                   | * A JWT header usually ocnsists of two parts:
                             |   * (alg) The algorithm for signing
                             |   * "typ" The specific type of Token
                             |
                             |     {
                             |       "alg": "HS256",
                             |       "typ": "JWT"
                             |     }
                             |
                             | * The JWT headers is then encoded using Base64 
                             |   to create the first part of the JWT (a)
                             |
JWT Payload                  | * A JWT Payload consists of the data. The 
                             |   payloads data contains claims, and there are 
                             |   three differet typs of claims.
                             |   * Registered - Predefined, recommended (but 
                             |                  not mandatory), claims: 
                             |       iss(uer), sub(ject), exp(iration)
                             |
                             |   * Public
                             |   * Private
                             |
                             |     {
                             |       "sub"
                             |
                             | * The JWT Payload is then encoded using Base64 
                             |   to create the second part of the JWT (b)
                             |
JWT Signature                | * A JWT Signature is created by using the 
                             |   algorithm in the header to hash out the encoded 
                             |   header, encoded playload with a secrete.
                             |
                             | * The secret can be anything, but is saved 
                             |   somewhere on the server that the client does 
                             |   not have access to
                             |
                             | * The Signature is the third and final part of a 
                             |   JWT (c)
                             |
                             |
                             | Example (from jwt.io):
                             | Header:  {
                             |            "alg": "HS256",
                             |            "typ": "JWT"
                             |          }
                             |
                             | Payload: {
                             |            "sub": "1234567890",
                             |            "name": "John Doe",
                             |            "iat": 1516239022
                             |          }
                             |
                             | Signature: HMACSHA256(
                             |              base64UrlEncode(header) + "." + 
                             |              base64UrlEncode(payload),
                             |              your-256-bit-secret
                             |            )
                             |
                             | Web Token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
                             |            eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ. 
                             |             SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
                             |
