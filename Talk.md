# Authentication and Authorization

How to Control Access to Resources and Data

---

## Authentication

* Can I log in?
* Do you know who I am?

> Authentication is the act of confirming the truth of an attribute of a single piece of data claimed true by an entity... authentication is the process of actually confirming that identity.

> It might involve confirming the identity of a person by validating their identity documents, verifying the authenticity of a website with a digital certificate,[1] determining the age of an artifact by carbon dating, or ensuring that a product is what its packaging and labeling claim to be. 

[Source - Wikipidia](https://en.wikipedia.org/wiki/Authentication)

---

## Authentication Factors

"Factor" - a way in which someone may be authenticated

Three categories:

* the knowledge factors - Something the user knows - e.g. a password, partial password, pass phrase, or personal identification number (PIN), Security question
* the ownership factors: Something the user has - e.g. wrist band, ID card, security token, implanted device, software token
* the inherence factors: Something the user is or does - e.g. fingerprint, retinal pattern, DNA sequence, signature, face, voice

[Source - Wikipidia](https://en.wikipedia.org/wiki/Authentication#Authentication_factors)

---

### Authentication Specifications/Tools

* Simple Login - "Forms authentication", "Basic Auth"
* Certificates
* SAML - Older XML based, requiring certs on both sides
* OAuth 2.0 - open standard for access delegation
* Open ID Client (OIDC) - authentication layer on top of OAuth 2.0, an authorization framework

---

## Authorization

* Can I get a piece of data?
* Can I view, query, write, modify, or delete a piece of data?

> Authorization is the function of specifying access rights/privileges to resources, which is related to information security and computer security in general and to access control in particular.
[Source - Wikipidia](https://en.wikipedia.org/wiki/Authorization)

---

## Authorization Types

---

## Login Workflows


---

### Forms Authentication


---

### Basic Authentication

Username and password are base64 encoded and included in auth header.

```
Authorization: <type> <credentials>
```

Example:

```
## base64("demo:p@55w0rd") == "ZGVtbzpwQDU1dzByZA=="
Authorization: Basic ZGVtbzpwQDU1dzByZA==
```

---

### Certificates

Types:

* Symmetric Encryption - simplest kind of encryption that involves only one secret key to cipher and decipher information
* Asymmetric Encryption

[Source - ssl2buy](https://www.ssl2buy.com/wiki/symmetric-vs-asymmetric-encryption-what-are-differences)

---

### Symmetric Encryption

* Uses a secret key that can either be a number, a word or a string of random letters
* Most widely used symmetric algorithms: AES-128, AES-192, and AES-256
* Disadvantage: all parties involved have to exchange the key

![Symmetric-Encryption](./docs/Symmetric-Encryption.png)

[Source - ssl2buy](https://www.ssl2buy.com/wiki/symmetric-vs-asymmetric-encryption-what-are-differences)

---

### Asymmetric Encryption

* Also known as public key cryptography
* Uses two keys to encrypt a plain text
* Anyone with a secret key can decrypt the message
* Example: HTTPS
* Encryption algorithms include: EIGamal, RSA, DSA, Elliptic curve techniques, PKCS

![Asymmetric-Encryption](./docs/Asymmetric-Encryption.png)

[Source - ssl2buy](https://www.ssl2buy.com/wiki/symmetric-vs-asymmetric-encryption-what-are-differences)

---

### Identity Provider

* Maintains 'identities' (user credentials)
* Provides authentication services (logins)

> An identity provider (abbreviated IdP) is a system entity that creates, maintains, and manages identity information for principals while providing authentication services to relying applications within a federation or distributed network. Identity providers offer user authentication as a service.

[Source - Wikipidia](https://en.wikipedia.org/wiki/Identity_provider)

---

### SAML



---

### OAuth

* Scopes - user defined rights, given to a service
* Grants or Flows - ways to acquire a token


### OAuth Scopes

* Rights the **user** gives to the service to access their data

---

### OAuth Grants

Grants (“methods”) for a client application to acquire an access token (which represents a user’s permission for the client to access their data) which can be used to authenticate a request to an API endpoint.

Types:

* Authorization Code Grant
* Client Credentials Grant
* Implicit Flow Grant
* Resource Owner Credentials Grant

[Source - Auth0](https://auth0.com/docs/flows)

---

### Authorization Code Grant (1/3)

> Because regular web apps are server-side apps where the source code is not publicly exposed, they can use the Authorization Code Flow (defined in defined in OAuth 2.0 RFC 6749, section 4.1), which exchanges an Authorization Code for a token. Your app must be server-side because during this exchange, you must also pass along your application's Client Secret, which must always be kept secure, and you will have to store it in your client.

[Source](https://auth0.com/docs/flows/concepts/auth-code)

---

### Authorization Code Grant (2/3)



---

### Authorization Code Grant (2/3)

Request/Response Flow

![OAuth Authorization Code Grant](./APIgw_Oauth_web_server_flow.png)
[Source](https://docs.axway.com/bundle/APIGateway_762_OAuthUserGuide_allOS_en_HTML5/page/Content/OAuthGuideTopics/oauth_flows_auth_code.htm)






### Client Credentials Grant

With machine-to-machine (M2M) applications, such as CLIs, daemons, or services running on your back-end, the system authenticates and authorizes the app rather than a user. For this scenario, typical authentication schemes like username + password or social logins don't make sense. Instead, M2M apps use the Client Credentials Flow (defined in OAuth 2.0 RFC 6749, section 4.4), in which they pass along their Client ID and Client Secret to authenticate themselves and get a token.

[Source](https://auth0.com/docs/flows/concepts/client-credentials)


### Open ID Client (OIDC)





Access control


RBAC - Role Based Access Control
IAM - Access Management
