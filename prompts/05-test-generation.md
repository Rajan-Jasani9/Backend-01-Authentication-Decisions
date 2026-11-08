# Test-generation prompt

Read the approved design and tests/acceptance-criteria.md. Generate meaningful integration and concurrency tests for real boundaries rather than mirroring functions. Cover login failure, account state, session expiry and rotation, logout and compromise revocation, reused/concurrent reset tokens, MFA enrollment and recovery policy, CSRF, generic errors and secret-free logging. Attempt authenticated cross-user and cross-tenant access. Simulate store/database outages, email delivery delay, worker failure and compatible migrations. Make assertions specific to the approved policy and document prerequisites and untested conditions. Do not invent successful test output or interpret green tests as security certification.

