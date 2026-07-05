# IgniteBoot Security

## OAuth2 / CORS / CSP

- OAuth2/OIDC: validate `iss`, `aud`, `exp`, `nbf`, and signature using JCA/JCE with RSA/ECDSA.
- Accept only `Bearer` tokens and reject unsigned or weak-algorithm tokens.
- CORS: enforce allowlist origin policies, strict `Access-Control-Allow-Methods`, and disallow credentials unless explicitly needed.
- CSP: emit `Content-Security-Policy` like `default-src 'self'; script-src 'self'; object-src 'none'; frame-ancestors 'none';` by default.
- Add security headers automatically:
  - `Strict-Transport-Security`
  - `X-Content-Type-Options: nosniff`
  - `X-Frame-Options: DENY`
  - `Referrer-Policy: no-referrer`

## Validations and Body Transformation

- Validate headers, query parameters, path parameters, and body content separately.
- Use a lightweight validation layer with declarative rules and reusable validators.
- Collect validation errors and return a structured `400 Bad Request` JSON payload.
- Parse request bodies into DTOs using a small JSON mapper or hand-written parser.
- Normalize payloads: trim strings, reject unknown fields, enforce schema types.
- Serialize responses explicitly and wrap results in an envelope.

## Global Exception Handling

- Use a global error interceptor/filter in the server pipeline.
- Convert uncaught exceptions into safe HTTP responses.
- Map exceptions to responses:
  - `ValidationException` -> `400 Bad Request`
  - `AuthenticationException` -> `401 Unauthorized`
  - `AuthorizationException` -> `403 Forbidden`
  - `ResourceNotFoundException` -> `404 Not Found`
  - runtime -> `500 Internal Server Error`
- Log stack traces at the framework boundary, but return safe error messages to clients.
