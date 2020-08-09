# OAuth2

Used to grant access to an application to a resource owned by a user through an authorization service.

<div class="mermaid">
graph TD
    User-->Application;
    User--Login-->Authorization;
    Application-- Token -->Resource;
    Application-->Authorization;
    Authorization--Auth Code / Token -->Application;
</div>

## Grant Types

Grant process mostly uses an authorization code separate to a token. Auth Code grants access. Token is required for a session to access to the resource.

### Authorization Code Grant

Supports grant using Authorization Code, separate to a Token. The application is given an Authorization Code when the user interaction is complete. The Application can then go on to request a token using the Authorization Code.

**PKCE** - Proof Key For Code Exchange

-   Used to prove the application requesting the Token was also the same application granted the authorization code.
-   Uses a crypto generator to prove application identity
-   Useful for public applications that could be compromised and cannot store a secret.

### Implicit Grant

-   Simple redirect, skipping the authorization
-   Typically uses a redirect to the callback with the token
-   Token in the URL is risks leaking (browser cache). More common to POST to an endpoint
-   Newer support for HTTP messaging.

### Resource Owner Password Credential Grant

-   Application captures and sends credentials (password) to the Authorization Provider.
-   Only for legacy support - **do not use**

### Client Credentials Grant

-   Application asks for resource directly
-   No user involvement required as resource is not owned by user

```typescript
const token = authorizationServer.token({
    header: {
        Authorization: `Basic ${credential}`,
        contentType: "application/x-www-formurlencoded",
    },
    content: {
        grant_type: "client_credentials",
        scope: scope as string | string[],
        resource: apiIdentifier,
    },
});
```

## Best Practices

-   Common to use Refresh Tokens, limiting session time of token
-   Common to force a new Refresh Token on each refresh (refresh token cycle) to avoid Refresh Tokens being leaked
