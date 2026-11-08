# Authentication threat model starter

Complete this for the actual application before accepting a design.

- Assets: passwords and hashes, recovery challenges, session credentials, user identities, tenant data, provider credentials and security events.
- Trust boundaries: browser → API; API → session/identity store; API → email delivery; identity-provider callback; administrative operations and deployment.
- Threats: credential stuffing, enumeration, XSS, CSRF, fixation, replay, unsafe account linking, recovery bypass, concurrent token consumption, tenant/resource isolation failures and compromised sessions.
- Operational threats: leaked secrets, stale revocation caches, store/database outages, email/worker failures, unsafe migrations and inconsistent restores.
- For each threat: record entry point, preconditions, likelihood, impact, controls, verification evidence, residual risk and responsible owner. Never record live credentials here.

