# Authentication and Authorization

## Authorization

Can I log in?
Do you know who I am?

### Specifications/Tools

* Simple Login: "Forms authentication", "Basic Auth"
* SAML
* OAuth 2.0
* Open ID Client (OIDC)

## Authentication

Can I get a piece of data?



## Login Workflows

### Forms Authentication

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

### SAML

### OAuth

Several different 'flows' known as 'grants'.

### Open ID Client (OIDC)





Access control


RBAC - Role Based Access Control
IAM - Access Management
