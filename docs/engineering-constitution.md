# Engineering Constitution

## Rule 1: Sensitive by default

Assume every record may become sensitive. Classify data before storing it.

## Rule 2: Policy before feature

A feature that touches sensitive data must define access, purpose, jurisdiction, retention, export, AI eligibility, and audit behaviour before implementation.

## Rule 3: No invisible AI

AI use must be visible, scoped, logged, and reviewable. No private data is sent to an AI provider unless explicitly authorised by policy and user intent.

## Rule 4: Export is mandatory

Every module must ship with export tests. If a dentist cannot leave with their data, the feature is hostile.

## Rule 5: Audit is product behaviour

Audit logs are not debug logs. They are evidence. Sensitive reads matter as much as writes.

## Rule 6: Jurisdiction is first-class

No country-specific legal, tax, health-record, privacy, or retention rule may be hard-coded into generic application logic.

## Rule 7: Clinical safety boundary

Administrative tools, recordkeeping, and clinical decision support are different risk classes. The UI and docs must not blur them.

## Rule 8: Local-first core

Core personal/professional vault use should work without mandatory third-party SaaS dependencies.

## Rule 9: Least privilege

Users, services, jobs, integrations, and AI agents receive the minimum data and authority needed for the task.

## Rule 10: No compliance theatre

Do not claim compliance. Define scope, controls, evidence, and review status.
