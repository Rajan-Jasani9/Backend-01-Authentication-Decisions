# Reference authentication architecture

Conceptual starting point for individual users of a conventional React browser SaaS with a backend API and PostgreSQL. Authentication is a backend component, not necessarily a separate deployable service. Enterprise SSO, native mobile and specialized compliance requirements need separate design work. Evaluate maintained providers and libraries before implementing application-managed authentication.

## Request paths

1. Login: HTTPS request → validate input and abuse controls → load authentication identity and account state → verify Argon2id hash through a maintained library → satisfy any additional factor policy → create a cryptographically unpredictable opaque session → set cookie.
2. Protected request: cookie → validate server-side session, expiry, revocation and account policy → resolve trusted identity → enforce the resource authorization and tenant policy → execute operation. Apply CSRF defenses to state-changing cookie-authenticated requests.
3. Logout: revoke server-side session and clear cookie. Define effective revocation guarantees across any caches or replicas.
4. Recovery: generic public response → rate-limited unpredictable short-lived challenge → deliver by email → atomically consume a single-use token → update credential → apply explicit session revocation policy. Protect recovery from bypassing MFA.
5. Outage: if authentication cannot be verified, block protected operations with a controlled error. Never skip validation. Email delivery outages delay verification and recovery, with safe retry and pending-operation tracking.

## Identity and storage

Immutable internal user ID; separate authentication identities and business profile. Enforce account states. Configure Argon2id cost parameters and hash migration. Store sessions with user ID, creation time, expiry, revocation status and carefully selected metadata; hash opaque credentials at rest where the lookup design permits. PostgreSQL can avoid an extra session-store dependency for a smaller application; reassess traffic, latency and availability.

## Browser and operational controls

Host-only Secure, HttpOnly cookie; appropriate SameSite policy; HTTPS; CSRF validation appropriate to architecture. HttpOnly prevents ordinary JavaScript reads but does not eliminate XSS; SameSite alone is not the entire CSRF design. Define idle and absolute lifetimes, rotation after authentication, recent reauthentication for sensitive changes, and per-user/all-device revocation.

Layer account, endpoint and network abuse signals. Use generic public errors and consistent 401/403 semantics. Restrict security logs and retention; never record passwords, session credentials or reusable tokens. Define incident response, secret rotation, backup recovery, compatible migrations and dependency-failure tests. Email delivery does not decide session validity. JWT is a token format; a session is authenticated state. Alternatives may use both.

## Deliberate omissions

No extra auth microservice, event bus or JWT layer is required by this baseline. These may be justified by different requirements. Generated implementation and tests require dependency maintenance, threat modeling and appropriate human review.

