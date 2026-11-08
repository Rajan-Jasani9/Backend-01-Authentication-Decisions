# Implementation prompt

Read the approved architecture and decision record. Stop and ask about unresolved security-critical requirements. Plan incremental changes to the existing application. Use maintained libraries; do not invent cryptography. Implement the complete identity, session, resource authorization, CSRF, recovery and operational controls specified by the design. Atomically consume single-use challenges and define concurrency behavior. Keep reusable secrets out of source, client bundles and logs. Add migrations and deployment/recovery instructions. Verify tests/acceptance-criteria.md against actual behavior. Report implemented requirements, test evidence, unresolved risks and manual security-review needs. Passing generated tests is not a security certification.

