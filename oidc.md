# Open ID Connect

OIDC builds on top of OAuth2 to add Authorization checks. OIDC adds an additional `ID Token` to the authorization flow. This provides access to the `userinfo` data from the provider.

The **Scope** parameter is used to request claims from the provider. `profile` and `email` are standard scope claims, which are then provided via `userinfo`.

## Flows

Similar to [OAuth2](./oauth2.md) grant types

### Authorization Code Flow

Similar to the "Authorization Code" grant for OAuth2. OIDC flow provides an additional ID Token to the application.

### Implicit Flow

Similar to the **Implicit Grant** type from OAuth2. This flow allows for a redirect callback to return the `ID Token` and optionally `Access Token` from the provider.

Note that returning the `Access Token` via a URL is not recommended because of leak risks through browser history.

### Hybrid Flow

Combination of Authorization Code Flow and Implicit Flow. The frontend is responsible for obtaining the `Authorization Code` and the `ID Token`, the backend is responsible for obtaining the `access token` and optional `refresh token`.

## `UserInfo` Endpoint

-   Active Directory Group Membership Available [see here](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-fed-group-claims)

## List of Providers

See [list](https://connect2id.com/products/nimbus-oauth-openid-connect-sdk/openid-connect-providers)

Example discovery document (Google):

```json
{
    "issuer": "https://accounts.google.com",
    "authorization_endpoint": "https://accounts.google.com/o/oauth2/v2/auth",
    "device_authorization_endpoint": "https://oauth2.googleapis.com/device/code",
    "token_endpoint": "https://oauth2.googleapis.com/token",
    "userinfo_endpoint": "https://openidconnect.googleapis.com/v1/userinfo",
    "revocation_endpoint": "https://oauth2.googleapis.com/revoke",
    "jwks_uri": "https://www.googleapis.com/oauth2/v3/certs",
    "response_types_supported": [
        "code",
        "token",
        "id_token",
        "code token",
        "code id_token",
        "token id_token",
        "code token id_token",
        "none"
    ],
    "subject_types_supported": ["public"],
    "id_token_signing_alg_values_supported": ["RS256"],
    "scopes_supported": ["openid", "email", "profile"],
    "token_endpoint_auth_methods_supported": ["client_secret_post", "client_secret_basic"],
    "claims_supported": [
        "aud",
        "email",
        "email_verified",
        "exp",
        "family_name",
        "given_name",
        "iat",
        "iss",
        "locale",
        "name",
        "picture",
        "sub"
    ],
    "code_challenge_methods_supported": ["plain", "S256"],
    "grant_types_supported": [
        "authorization_code",
        "refresh_token",
        "urn:ietf:params:oauth:grant-type:device_code",
        "urn:ietf:params:oauth:grant-type:jwt-bearer"
    ]
}
```
