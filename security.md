# Defining Security Concepts and Terminology

## Open ID Connect - OIDC

## OAuth2

Used to grant access to an application to a resource owned by a user through an authorization service.

<div class="mermaid">
graph TD
    A-->B;
    A-->C;
</div>

### Grant Types

Grant process mostly uses an authorization code separate to a token. Auth Code grants access. Token is required for a session to access to the resource.

-   **PKCE** - Proof Key For Code Exchange
    -   Used to prove the application requesting the Token was also the same application granted the authorization code.
    -   Uses a crypto generator to prove application identity
    -   Useful for public applications that could be compromized and cannot store a secret.

*   **Implicit Grant**
    -   Simple redirect, skipping the authorization
    -   Typically uses a redirect to the callback with the token
    -   Token in the URL is risks leaking (browser cache). More common to POST to an endpoint.
    -   Newer support for HTTP messaging
*   **Resource Owner Password Credential Grant**
    -   Application captures and sends credentials (password) to the Authorization app.
    -   Only supported for legacy support - do not use
*   **Client Credentials Grant**
    -   Application asks for resource directly
    -   No user involvement required as resource is not owned by user

## SAML

## SASL
