# SAML2

Similar Single-Sign-On to OAuth2 and OIDC.

## Terminology

-   **Subject** - User (person) or role account
-   **SAML Assertion** - security information (claims)
-   **SAML Profile** - How to use SAML messages in usecase
-   **Identity Provider** - IDP - Authorization server that provides SAML Assertions for a Subject (like UserInfo in OIDC)
-   **Service Provider** - Service or application that uses an IDP
-   **Trust Relationship** - between application and IDP
-   **SAML Protocol Binding** - SAML messages over a protocol like HTTPS
-   **Assertion Consumer Service** - endpoint to consume the SAML Assertion
-   **SP Initiated** - browse to the Service Provider, redirects to the IDP
-   **IDP Initiated** - start at portal, SAML Assertions for any number of applications, which the user may select

## Identity Federation

Use a single identifier in two account systems to associate identity.

### Authentication Brokers

Support for different authentication protocols via a broker (e.g. SAML support via an OIDC provider).
