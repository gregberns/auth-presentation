# Authentication and Authorization

How to Control Access to Resources and Data

---

## Authorization

* Can I log in?
* Do you know who I am?

---

## Authentication

Can I get a piece of data?

---

### Authorization Specifications/Tools

* Simple Login: "Forms authentication", "Basic Auth"
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

### SAML


---

### OAuth

Several different 'flows' known as 'grants'.

### Open ID Client (OIDC)





Access control


RBAC - Role Based Access Control
IAM - Access Management
