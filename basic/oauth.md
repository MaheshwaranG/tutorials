### OAUTH

OAuth is an open standard authorization protocol or framework that defines how unrelated servers and services can safely allow authenticated access to their assets. (OAuth works only on secure HTTPS sites)

**Resource Owner :** user having resource on other sites like google. Now he want to use service provided by Notes App. Instead of directly creating a account on Notes app. He can use his google account authorization and resource available on google. That why user called as Resource owner.

**Client:** Notes application providing some sort of services. Notes app want to access data or perform action on behalf of the resource. Notes Application is called Client in OAuth flow.

**Authorization Server :** Resource owner application authorization Server.

**Resource Server:** Client get information from Resource server on behalf of the resource owner after authorization.

**Redirect URI:** The URL the AUthorization server wants to redirect after a successfull authorization(granting permission). Usually called as Callback URL.

**Response Type:** The Type of information user expect to receive. Mostly it could be authorization code.

**Scope:** These are the granular permission the client application wants.

**Consent:** The Authorization server takes the scopes the client is requesting and verify with resource owner.

**Client ID:** This is the ID used to identify client (Here it is Notes Application)

**Client Secret:** This is the secret password that only know by client and authorization server knows. This allows securely share information privately behind the scenes.

**Authorization Code:** Short lived temporary code the client gives to Authorization server in exchange of an Access Token.

**Access Token:** The key the client will use to communicate with the resource server. (comaparably short lived)

**Refresh Token:** Refresh token are long lived to regenerate access token instead of verify every time to get acess token.
