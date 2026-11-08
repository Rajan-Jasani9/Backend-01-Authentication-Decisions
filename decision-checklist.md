# Authentication decision checklist

For each item record the decision, alternatives, rationale, owner and verification criteria. An unchecked item is an open question, not an implicit approval.

- [ ] 01. Identities and user groups
- [ ] 02. Authentication ownership: provider, library or application
- [ ] 03. Supported login methods and secure account linking
- [ ] 04. Immutable user identifiers and account states
- [ ] 05. Password hashing algorithm, costs and hash migration
- [ ] 06. Email verification and challenge lifecycle
- [ ] 07. Session architecture and early revocation guarantees
- [ ] 08. Browser credential storage and CSRF defenses
- [ ] 09. Session expiry, rotation and reauthentication
- [ ] 10. Account recovery and post-reset session policy
- [ ] 11. Layered abuse protections for all sensitive endpoints
- [ ] 12. MFA enrollment, policy, recovery and removal
- [ ] 13. Resource authorization and tenant boundaries
- [ ] 14. Sensitive identity changes and trusted notifications
- [ ] 15. Generic public errors and protected diagnostics
- [ ] 16. Compromise response and structured security events
- [ ] 17. Secret storage, rotation and emergency revocation
- [ ] 18. Fail-closed behavior, dependency failure and safe deployment

Use reference-architecture.md as a browser SaaS example. Adapt it to the actual application.

