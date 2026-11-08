# Security-review prompt

Review the actual code, configuration and deployment against the approved decisions and threat-model.md. Trace every protected request and sensitive account change. Investigate stolen or revoked sessions, token replay, concurrent recovery, account enumeration including timing, cross-user/cross-tenant access, unsafe linking, CSRF, fixation, MFA reset bypass, secret leakage and dependency failures. Check revocation caches and replica delays. Verify hashing parameters, atomic challenge consumption, generic public responses, controlled diagnostics and safe migrations. Report concrete evidence and prioritized remediation. Distinguish tested behavior, code inspection and unverified assumptions. Do not certify the system secure.

