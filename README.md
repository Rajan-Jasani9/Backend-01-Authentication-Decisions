# Backend 01 — Authentication Decisions

The engineering decision kit for **Backend - 01: Before You Vibe Code Authentication** on Engineering Systems.

AI can write authentication code in minutes. What it can't do is decide what your application needs. This kit gets those decisions made deliberately, by you, before any code is written, and then has your AI coding assistant implement, review and test them.

It works with any framework: FastAPI, Django, Express, NestJS, Rails, Spring or anything else. The implementation will differ, but the engineering questions stay the same.

## What's inside

```
.
├── decision-checklist.md        18 decisions to make before implementation
├── reference-architecture.md    The baseline architecture from the video
├── threat-model.md              Threat-model starter to complete for your app
├── prompts/
│   ├── 01-discovery.md          Gather requirements and open questions
│   ├── 02-architecture.md       Produce a design and get approval before code
│   ├── 03-implementation.md     Turn approved decisions into working code
│   ├── 04-security-review.md    Challenge the implementation and find gaps
│   └── 05-test-generation.md    Generate failure, revocation and access tests
└── tests/
    └── acceptance-criteria.md   Behavior the finished system must show
```

## How to use it

Work through the stages in order, one at a time. Review each stage's output before you move to the next.

1. **Decide.** Open `decision-checklist.md`. For each item, write down the decision, the alternatives, the reasoning, an owner and how it will be verified. An unchecked item is an open question, not a quiet approval.
2. **Discover.** Give your assistant `prompts/01-discovery.md` with access to your codebase. It produces a requirements document that separates what is known from what is still open.
3. **Design.** Run `prompts/02-architecture.md`. Compare its design with `reference-architecture.md` and approve the design before anything is implemented.
4. **Implement.** Run `prompts/03-implementation.md` against the approved design.
5. **Review.** Run `prompts/04-security-review.md` alongside `threat-model.md`.
6. **Test.** Run `prompts/05-test-generation.md` and check the results against `tests/acceptance-criteria.md`.

Paste a prompt into your assistant (Claude Code, Cursor, Codex, Copilot or any other) and point it at the relevant files in this kit.

## The 18 decisions and the choices made in the video

The video works through each decision for one example: a conventional browser SaaS for individual users. These are that example's answers, **not universal defaults**. Make your own for your application.

| #  | Decision | Choice in the video's example |
|----|----------|-------------------------------|
| 01 | Who are your users? | Individual users; organizations later |
| 02 | Build or buy? | Evaluate established solutions first |
| 03 | Login methods | Email + password first; providers later |
| 04 | User model | Immutable user ID; identities stored separately |
| 05 | Password storage | Argon2id, tunable cost, migration plan |
| 06 | Email verification | Register freely; verify for email-dependent features |
| 07 | Sessions | Server-managed sessions + secure cookies |
| 08 | Browser credentials | `__Host-` cookie · Secure · HttpOnly · SameSite + CSRF defense |
| 09 | Session lifecycle | Expiry, revocation, ID rotation, reauthentication |
| 10 | Account recovery | Reset consumes the token; defined session revocation |
| 11 | Abuse protection | Multi-signal policy on every abusable endpoint |
| 12 | MFA | Support it; require it for privileged / high-risk users |
| 13 | Authorization | Check on every operation, using server identity and the real resource |
| 14 | Identity changes | Verify sensitive changes; audit security events |
| 15 | Errors | Generic public errors, rich protected logs, 401 ≠ 403 |
| 16 | Compromise response | Revocable sessions, security events, kill switch |
| 17 | Secrets | Opaque cookies, protected state, documented rotation |
| 18 | Failure behavior | Fail closed, known dependencies, failure tests |

## Important limits

- The reference architecture is a **starting point** for typical web applications. Enterprise SSO, native mobile and specialized compliance requirements need separate design work.
- These prompts produce requirements, designs and test specifications. **Passing generated tests is not a security certification.** Generated code still needs dependency maintenance, threat modeling and appropriate human review.
- Never paste live secrets, credentials or production data into an AI assistant or into these files.

## Watch the video

Backend - 01: Before You Vibe Code Authentication, on the Engineering Systems YouTube channel.
