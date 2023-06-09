# OAuth 2 / OpenID Connect for JavaScript Runtimes

This software provides a collection of routines that can be used to build client modules for OAuth 2.1, OAuth 2.0 with the latest Security Best Current Practices (BCP), and FAPI 2.0, as well as OpenID Connect where applicable. The primary goal of this software is to promote secure and up-to-date best practices while using only the capabilities common to both browser and non-browser JavaScript runtimes.

## Features

The following features are currently in scope and implemented in this software:

- Authorization Server Metadata discovery
- Authorization Code Flow (profiled under OpenID Connect 1.0, OAuth 2.0, OAuth 2.1, and FAPI 2.0), with PKCE
- Refresh Token, Device Authorization, and Client Credentials Grants
- Demonstrating Proof-of-Possession at the Application Layer (DPoP)
- Token Introspection and Revocation
- Pushed Authorization Requests (PAR)
- UserInfo and Protected Resource Requests
- Authorization Server Issuer Identification
- JWT Secured Introspection, Response Mode (JARM), Authorization Request (JAR), and UserInfo

## [Certification](https://openid.net/certification/faq/)

[<img width="96" height="50" align="right" src="https://user-images.githubusercontent.com/241506/166977513-7cd710a9-7f60-4944-aebe-a658e9f36375.png" alt="OpenID Certification">](#certification)

[Filip Skokan](https://github.com/panva) has certified that [this software](https://github.com/panva/oauth4webapi) conforms to the Basic RP Conformance Profile of the OpenID Connect™ protocol.

## [💗 Help the project](https://github.com/sponsors/panva)

## Dependencies: 0

`oauth4webapi` has no dependencies and it exports tree-shakeable ESM.

## [Documentation](docs/README.md)

## [Examples](examples/README.md)

**`example`** ESM import

```js
import * as oauth2 from 'oauth4webapi'
```

**`example`** Deno import

```js
import * as oauth2 from 'https://deno.land/x/oauth4webapi@v2.3.0/mod.ts'
```

- Authorization Code Flow - OpenID Connect [source](examples/code.ts), or plain OAuth 2 [source](examples/oauth.ts)
- Public Client Authorization Code Flow - [source](examples/public.ts) | [diff from code flow](examples/public.diff)
- Private Key JWT Client Authentication - [source](examples/private_key_jwt.ts) | [diff from code flow](examples/private_key_jwt.diff)
- DPoP - [source](examples/dpop.ts) | [diff from code flow](examples/dpop.diff)
- Pushed Authorization Request (PAR) - [source](examples/par.ts) | [diff from code flow](examples/par.diff)
- Client Credentials Grant - [source](examples/client_credentials.ts)
- Device Authorization Grant - [source](examples/device_authorization_grant.ts)
- FAPI 2.0 (Private Key JWT, PAR, DPoP) - [source](examples/fapi2.ts)
- FAPI 2.0 Message Signing (Private Key JWT, PAR, DPoP, JAR, JARM) - [source](examples/fapi2-message-signing.ts) | [diff](examples/fapi2-message-signing.diff)

1. **Authorization Code Flow - OpenID Connect**: This flow is generally recommended for server-side web applications where the application server can securely store the client secret. OpenID Connect extends OAuth 2.0 to provide identity information about the user.

2. **Public Client Authorization Code Flow**: This is similar to the Authorization Code Flow but is designed for public clients where the client secret cannot be securely stored. It's commonly used for mobile apps and Single Page Apps (SPAs).

3. **Private Key JWT Client Authentication**: This method provides a higher level of assurance about the client's identity and is often used in scenarios with higher security requirements. It involves the client creating a JWT and signing it using its private key.

4. **DPoP (Demonstration of Proof of Possession)**: This is a mechanism that binds tokens to a particular client's public key, providing additional security against token theft. It's suitable for high-security scenarios.

5. **Pushed Authorization Request (PAR)**: This method increases security by directly pushing authorization requests from the client to the authorization server, reducing exposure to potential interception. It's useful in high-security contexts.

6. **Client Credentials Grant**: This flow is best used for server-to-server communication where a client application needs to access a resource independently of any user interaction.

7. **Device Authorization Grant**: This flow is designed for devices with limited input capabilities (e.g., smart TVs, consoles). It allows users to authorize the device from a more input-friendly environment (like their smartphone or laptop).

8. **FAPI 2.0 (Private Key JWT, PAR, DPoP)**: FAPI 2.0 is designed for high-value scenarios, such as banking or financial services. It incorporates elements like Private Key JWT, PAR, and DPoP to provide high levels of security.

9. **FAPI 2.0 Message Signing (Private Key JWT, PAR, DPoP, JAR, JARM)**: This is similar to the above but includes JSON Web Token (JWT) Secured Authorization Request (JAR) and JWT Secured Authorization Response Mode (JARM), adding an extra layer of security via message signing. It's suitable for very high-security applications.


## Supported Runtimes

The supported JavaScript runtimes include those that support the utilized Web API globals and standard built-in objects. These are _(but are not limited to)_:

- Browsers
- Bun
- Cloudflare Workers
- Deno
- Electron
- Node.js ([runtime flags may be needed](https://github.com/panva/oauth4webapi/issues/8))
- Vercel's Edge Runtime

## Out of scope

The following features are currently out of scope:

- CommonJS
- Implicit, Hybrid, and Resource Owner Password Credentials Flows
- Mutual-TLS Client Authentication and Certificate-Bound Access Tokens
- JSON Web Encryption (JWE)
- Automatic polyfills of any kind
