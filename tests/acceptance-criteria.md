# Acceptance criteria

Adapt exact timeouts, HTTP contracts and revocation guarantees to the approved architecture. These are requirements, not evidence of passing tests.

- Valid login creates a fresh unpredictable session only after account state and additional-factor policy checks. Wrong credentials return generic public failures.
- Cookies use approved host-only, Secure, HttpOnly and SameSite settings; state-changing requests enforce the designed CSRF control. HttpOnly is not treated as a complete XSS defense.
- Idle and absolute expiry, logout, all-device logout and incident revocation prevent protected operations within the documented guarantee. Rotation prevents fixation.
- Authenticated users cannot read or modify other users’ or tenants’ private resources without an explicit policy grant; authorization runs for each protected operation.
- Verification/reset challenges expire, cannot be reused, and allow at most one successful atomic consumption under concurrency. Failed/expired challenges do not change credentials. Post-reset session policy is applied.
- Recovery and MFA removal cannot bypass approved authentication guarantees. Sensitive identity changes require approved recent authentication and verification.
- Abuse controls cover login, verification, reset and MFA/recovery; shared IPs and attacker-induced lockout are considered.
- Public errors avoid account enumeration; internal diagnostics remain useful and access-controlled. No reusable secret is logged.
- Session-store/database unavailability blocks protected operations with controlled failure. Email/worker failures preserve pending work and safe retry without granting unverified access.
- Credential rotation, compatible deployment and restore procedures are documented and exercised with appropriate review.

