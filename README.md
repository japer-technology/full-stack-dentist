# full-stack-dentist

A single-source, open-core super app for the full dental lifecycle: student, clinician, practice owner, researcher, educator, retiree, and estate executor.

The goal is not “practice-management software with extra features.” The goal is a sovereign operating system for a dentist’s personal, professional, clinical, business, compliance, and knowledge life — without forcing them to rent fragmented third-party tools forever.

## Product thesis

Dentists currently stitch together dozens of systems:

- notes, tasks, email, calendar, contacts
- study tools, CPD/CE records, licensing evidence
- patient records, treatment planning, consent, recalls
- imaging, labs, prescriptions, referrals
- accounting, payroll, insurance, inventory, suppliers
- website, CRM, reputation, analytics, marketing
- compliance, incident response, audits, policies
- association, study-club, society, committee, event, CPD/CE, advocacy, and member-management tools
- estate, succession, retirement, data export, continuity

That fragmentation creates cost, lock-in, duplicated data, weak security boundaries, and poor continuity across a dentist’s career.

full-stack-dentist exists to make one trustworthy repo that can generate deployable apps, services, policies, schemas, automations, and documentation for every stage of that lifecycle.

## Non-negotiable principles

1. Dentist data sovereignty
   - The dentist or practice owns the data.
   - Every record must be exportable in documented formats.
   - No silent lock-in, dark patterns, or forced SaaS dependency.

2. Privacy and security by design
   - Zero-trust architecture.
   - Least privilege everywhere.
   - Encryption in transit and at rest.
   - Strong audit logs.
   - Explicit consent and purpose limitation.

3. Multi-country from day zero
   - Jurisdiction is a first-class concept, not an afterthought.
   - Legal, tax, health-record, privacy, and retention rules are policy modules.
   - The core platform must not hard-code one country’s assumptions.

4. Clinical safety before convenience
   - The app must distinguish administrative support, clinical recordkeeping, clinical decision support, and regulated medical-device behavior.
   - No feature may pretend to diagnose, prescribe, or automate clinical judgment without an explicit regulatory pathway.

5. Interoperability first
   - Prefer open standards over proprietary formats.
   - Healthcare exchange should align with HL7 FHIR where applicable.
   - Dental concepts should map to recognised coding and imaging standards where licensing permits.

6. Local-first capable, cloud-optional
   - A solo dentist should be able to run a useful version locally.
   - A group practice should be able to run a hardened private deployment.
   - Cloud services are accelerators, not mandatory dependencies.

7. Auditability over magic
   - Every important state change should answer: who, what, when, where, why, and under what authority.
   - AI features must be explainable, reviewable, reversible, and clearly labelled.

## Reference standards and frameworks

Use these as baseline design inputs, not decorative badges:

- NIST Cybersecurity Framework 2.0
- NIST Privacy Framework
- OWASP ASVS 5.0.0
- ISO/IEC 27001 family for information-security management
- ISO/IEC 27701 for privacy-information management
- HL7 FHIR R5 for healthcare interoperability where appropriate
- DICOM for imaging workflows where appropriate
- GDPR, UK GDPR, HIPAA, PIPEDA, Australian Privacy Act, NZ Privacy Act, and other jurisdiction modules as applicable

See `docs/standards-and-assumptions.md`.

## Primary users

- Dental student
- New graduate dentist
- Associate dentist
- Specialist dentist
- Practice owner
- Multi-site group operator
- Dental educator
- Researcher
- Retired dentist
- Executor or continuity officer handling records after death/incapacity
- Dental association, society, chapter, study-club, buying-group, alumni, charity, or committee administrator

## Core domains

- Identity, access, roles, delegated authority
- Personal knowledge management
- Study and exam preparation
- CPD/CE and licensing evidence
- Patient relationship management
- Clinical records and charting
- Treatment planning and consent
- Imaging and documents
- Lab and referral workflows
- Prescriptions and medication safety hooks
- Practice operations
- Finance, tax, payroll, and accounting integrations
- Inventory, suppliers, assets, maintenance
- Marketing, website, reviews, CRM
- Compliance, risk, policies, incident response
- Association management, study-club management, membership, committees, events, CPD/CE, elections, advocacy
- Analytics, reporting, benchmarking
- AI assistants and automations
- Data export, succession, retirement, and estate continuity

## Architecture stance

This repo should become a modular monorepo:

```text
apps/              End-user applications
services/          Backend services and workers
packages/          Shared libraries, schemas, SDKs
modules/           Domain modules: clinical, finance, compliance, etc.
policies/          Jurisdiction and compliance policy packs
schemas/           Canonical data contracts
infra/             Deployment, observability, secrets, backup, recovery
docs/              Product, architecture, security, compliance, roadmap
```

The canonical architecture is documented in `docs/architecture.md`.

## MVP definition

The first credible MVP is not a full dental empire. It is a secure personal/professional cockpit for one dentist:

1. Identity and local encrypted vault
2. Personal profile and credentials register
3. CPD/CE evidence tracker
4. Document vault with retention labels
5. Task/calendar/contact foundation
6. Jurisdiction profile
7. Audit log
8. Export bundle
9. AI assistant limited to retrieval, summarisation, drafting, and checklists — no autonomous clinical advice

See `docs/roadmap.md`.

## Organised dentistry

This project also covers software dentists need when they organise together:

- dental associations and societies
- study clubs and peer groups
- specialist colleges and interest groups
- alumni networks
- CPD/CE providers
- buying groups and supplier collectives
- advocacy groups
- charities and outreach programs
- committees, boards, elections, ethics panels, and complaints processes

Association and study-club management is documented in `docs/association-management.md`.

## Repository status

Early product-charter phase. No clinical, privacy, or security guarantees exist until implemented and verified.

## Legal and safety notice

This project is not yet a medical device, electronic health record, prescribing system, accounting system, legal-compliance product, or regulated clinical decision-support system. Any feature entering those categories must be designed, reviewed, validated, and deployed under the relevant regulatory obligations for each jurisdiction.
