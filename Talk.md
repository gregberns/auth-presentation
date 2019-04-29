# Authentication and Authorization

How to Control Access to Resources and Data

> You must be authenticated (logged in) before your request can be authorized (granted permission to access)

---

## Objective

Provide overview of "Auth" concepts for further reasearch.

---

## Overview

* Terms
* Authentication
  * Types and details
* Authorization

---

## Terms

Lets set a base line for terminology:

* Certificates
  * Symmetric
  * Asymmetric
* Identity Provider
* Authentication
  * Factors
* Authorization

---

## Certificates

Types:

* Symmetric Encryption
* Asymmetric Encryption

[Source - ssl2buy](https://www.ssl2buy.com/wiki/symmetric-vs-asymmetric-encryption-what-are-differences)

---

## Symmetric Encryption

* Simplest kind of encryption that involves only one secret key to cipher and decipher information
* Secret key can be: a number, a word or a string of random letters
* Most widely used symmetric algorithms: AES-128, AES-192, and AES-256
* Disadvantage
  * All parties involved have to exchange the key
  * Assumes both parties are trusted

![Symmetric-Encryption](https://raw.githubusercontent.com/gregberns/auth-presentation/master/docs/Symmetric-Encryption.png)

[Source - ssl2buy](https://www.ssl2buy.com/wiki/symmetric-vs-asymmetric-encryption-what-are-differences)

---

## Asymmetric Encryption

* Also known as public key cryptography
* Uses two keys to encrypt a plain text
* Anyone with a secret key can decrypt the message
* Example: HTTPS
* Encryption algorithms include: EIGamal, RSA, DSA, Elliptic curve techniques, PKCS

![Asymmetric-Encryption](https://raw.githubusercontent.com/gregberns/auth-presentation/master/docs/Asymmetric-Encryption.png)

[Source - ssl2buy](https://www.ssl2buy.com/wiki/symmetric-vs-asymmetric-encryption-what-are-differences)

---

## Identity Provider

* Maintains 'identities' (user credentials)
* Provides authentication services (logins)

Definition:

> An identity provider (abbreviated IdP) is a system entity that creates, maintains, and manages identity information for principals while providing authentication services to relying applications within a federation or distributed network. Identity providers offer user authentication as a service.

[Source - Wikipidia](https://en.wikipedia.org/wiki/Identity_provider)

---

## Access Delegation

> Delegation is when a person authorizes another to serve as his or her representative for a particular task.

Access delegation allows you to request access to another user's profile or grant someone else access to your profile.

Terms:

* Delegation: The act of delegating one's access to another user.
* Delegator: A person that delegates access to another user (app)
* Proxy: An user (app) granted access to act on behalf of a user
* Revoke: When delegated access is withdrawn

Example:

I delegate access to Evernote to access my Google Email address

[Source - Oracle](https://docs.oracle.com/cd/E92915_01/cs92pbr8/eng/cs/lscc/concept_UnderstandingDelegatedAccess-888000.html)

---

## Authentication

* Can I log in?
* Do you know who I am?

Definition:

> Authentication is the act of confirming the truth of an attribute of a single piece of data claimed true by an entity... authentication is the process of actually confirming that identity.

> It might involve confirming the identity of a person by validating their identity documents, verifying the authenticity of a website with a digital certificate, determining the age of an artifact by carbon dating, or ensuring that a product is what its packaging and labeling claim to be.

[Source - Wikipidia](https://en.wikipedia.org/wiki/Authentication)

---

## Authentication Factors

"Factor" - a way in which someone may be authenticated

Three categories:

* the knowledge factors - Something the user knows - e.g. a password, partial password, pass phrase, or personal identification number (PIN), Security question
* the ownership factors: Something the user has - e.g. cell phone holding a software token, wrist band, ID card, security token, implanted device, software token
* the inherence factors: Something the user is or does - e.g. fingerprint, retinal pattern, DNA sequence, signature, face, voice

[Source - Wikipidia](https://en.wikipedia.org/wiki/Authentication#Authentication_factors)

---

## Authorization

* Can I get a specific piece of data?
* Can I view, query, write, modify, or delete a piece of data?

> Authorization is the function of specifying access rights/privileges to resources, which is related to information security and computer security in general and to access control in particular.

[Source - Wikipidia](https://en.wikipedia.org/wiki/Authorization)

---

### Authentication Specifications

* Simple Login - Basic Auth
* SAML - Older XML based, requiring certs on both sides
* OAuth 2.0 - open standard for access delegation
* Open ID Client (OIDC) - authentication layer on top of OAuth 2.0, an authorization framework


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

### SAML - Overview

* 'Vintage' - has been used for quite a while (SAML V1.1 2003)
* Often used in conjunction with LDAP/AD
* XML Based, verbose
* Need Certs on both 'sides': Identity Provider and Service

---

### SAML - Parts

Terms:

* User Agent - The User's Browser
* Identity Provider - Hosts the user login page
* Service Provider - Website server that needs the user logged in

SAML Requestor = "Service Provider"
SAML Responder = "Identity Provider"

![OAuth Authorization Code Grant](https://raw.githubusercontent.com/gregberns/auth-presentation/master/docs/sstc-saml-binding-simplesign-cd-02_html_20f95218.png)

---

### OAuth

OAuth is an open standard for access delegation

> A way for Internet users to grant websites or applications access to their information on other websites but without giving them the passwords.

Aspects:

* Scopes - defines what the 'proxy' has rights to, the user delegates these rights
  * Example: I give Evernote access to my email address, but not access to my email content
* Grants or Flows - ways to acquire a token

[Source - Wikipedia](https://en.wikipedia.org/wiki/OAuth)

---

### OAuth Scopes

Defines what the 'proxy' has rights to, the user delegates these rights

* Rights the **user** gives to the service to access their data

* 
  * Example: I give Evernote access to my email address, but not access to my email content

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

[Source - auth0](https://auth0.com/docs/flows/concepts/auth-code)

---

### Authorization Code Grant (2/3)

* Will involve
  * Resource Owner (User) - entity capable of granting access to a protected resource
  * User Agent - browser or app
  * Web Server - facilitates communication and holds the Client Id + Secret
  * Authorization Server - server issuing access tokens
  * Resource Server (API) - server hosting the protected resources

---

### Authorization Code Grant (3/3)

Request/Response Flow

![OAuth Authorization Code Grant](https://raw.githubusercontent.com/gregberns/auth-presentation/master/docs/APIgw_Oauth_web_server_flow.png)

[Source - axway](https://docs.axway.com/bundle/APIGateway_762_OAuthUserGuide_allOS_en_HTML5/page/Content/OAuthGuideTopics/oauth_flows_auth_code.htm)

---

### Client Credentials Grant (1/3)

> With machine-to-machine (M2M) applications, such as CLIs, daemons, or services running on your back-end, the system authenticates and authorizes the app rather than a user. For this scenario, typical authentication schemes like username + password or social logins don't make sense. Instead, M2M apps use the Client Credentials Flow (defined in OAuth 2.0 RFC 6749, section 4.4), in which they pass along their Client ID and Client Secret to authenticate themselves and get a token.

[Source](https://auth0.com/docs/flows/concepts/client-credentials)

---

### Client Credentials Grant (2/3)

* Will involve
  * Client App - Secure app with its own credentials (the Client ID and Client Secret)
  * Authorization Server - server issuing access tokens
  * Resource Server (API) - server hosting the protected resources

---

### Client Credentials Grant (3/3)

* "M2M App" - Client App
* "Auth0 Tenant" - Authorization Server
* "Your API" - Resource Server

![OAuth Client Credentials Grant](https://raw.githubusercontent.com/gregberns/auth-presentation/master/docs/auth-sequence-client-credentials.png)

---

### Open ID Client (OIDC)



---

## Authorization




RBAC - Role Based Access Control
IAM - Access Management

---

## Role-Based Access Control (RBAC)

Assigning permissions to users based on their role within an organization.

* provides fine-grained control
* offers a simple, manageable approach to access management
* less prone to error than assigning permissions to users individually

Steps:

* analyze the needs of your users
* group them into roles based on common responsibilities and needs
* assign one or more roles to each user and one or more permissions to each role

> The user-role and role-permissions relationships make it simple to perform user assignments since users no longer need to be managed individually, but instead have privileges that conform to the permissions assigned to their role(s).

---

## Benefits of RBAC

* create systematic, repeatable assignment of permissions
* easily audit user privileges and correct identified issues
* quickly add and change roles, as well as implement them across APIs
* cut down on the potential for error when assigning user permissions
* integrate third-party users by giving them pre-defined roles
* more effectively comply with regulatory and statutory requirements for confidentiality and privacy


[Source - auth0](https://auth0.com/docs/authorization/concepts/rbac)

---

## Identity and Access Management (IAM)

> A framework of policies and technologies for ensuring that the proper people in an enterprise have the appropriate access to technology resources.

Identity management (IdM) is the task of controlling:

* information that authenticates the identity of a user
* information that describes information and actions they are authorized to access and/or perform.

So... IAM encompases **both** Authentication and Authorization.

[Source - Wikipidia](https://en.wikipedia.org/wiki/Identity_management)

## Identity Management - Functions

Identity management can involve four basic functions:

* Pure identity function: Creation, management and deletion of identities without regard to access or entitlements
* User access (log-on) function: For example: a smart card and its associated data used by a customer to log on to a service or services (a traditional view)
* Service function: A system that delivers personalized, role-based, online, on-demand, multimedia (content), presence-based services to users and their devices
* Identity Federation: A system that relies on federated identity to authenticate a user without knowing his or her password

[Source - Wikipidia](https://en.wikipedia.org/wiki/Identity_management#Function)

## Identity Management - Capabilities

* Authentication: Verification that an entity is who/what it claims to be using a password
* Authorization: defines what operations an entity can perform in the context of a specific application
* Roles : Roles are groups of operations and/or other roles. Users are granted roles often related to a particular job or job function.
* Delegation : allows local administrators to perform system modifications without a global administrator or for one user to allow another to perform actions on their behalf
* Interchange : The SAML protocol is a prominent means used to exchange identity information between two identity domains.[12] OpenID Connect is another such protocol.

[Source - Wikipidia](https://en.wikipedia.org/wiki/Identity_management#System_capabilities)