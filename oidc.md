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
