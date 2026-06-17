# Glossary

## Purpose

A world-class system needs a shared, precise vocabulary so that contributors, reviewers, and users mean the same thing by the same word. This glossary defines the ubiquitous language used across the charter. Where a term has a dedicated document, it is linked.

## Platform and architecture

- Trust substrate — the load-bearing core that every module depends on: identity, policy, audit, vault, and export. Built before features (`docs/roadmap.md`).
- Module — a domain capability (clinical, finance, association, etc.) built on the trust substrate (`docs/architecture.md`).
- Bounded context — a domain boundary owning its own data and rules; contexts integrate through explicit contracts.
- Deployment mode — solo-local, private-practice, or regulated-cloud configuration of the same platform.
- Local-first — core use works without a mandatory third-party SaaS account.
- Tenant — an isolated data space (a personal vault, a practice, or an association). Cross-tenant leakage is a critical threat.

## Identity, access, and authority

- Identity — the verified account of a person or service.
- Role — a named set of permissions within a context.
- Authority — the documented basis for an action (consent, treatment relationship, legal obligation, delegation, executor, court order). Authority is itself a claim.
- Delegated authority — access granted by one party to another, scoped and audited.
- Break-glass — emergency access that is possible but painful: declared purpose, MFA, time-limited, high-severity audit, notification, review.
- Least privilege — every actor (user, service, job, AI agent) receives only the access a task needs.
- Context switching — a person acting explicitly as one of their roles (private, practice owner, member, officer) with separate permissions and audit.

## Data and records

- Classification — the sensitivity label on every object that drives access, retention, export, AI use, and logging (`docs/architecture.md`).
- Record — a unit of stored information carrying universal metadata (`docs/data-model.md`).
- Document — a stored file plus metadata, classification, retention, and access log; evidence, not truth by itself.
- Provenance — where a record came from and how it changed.
- Retention rule — the policy governing how long a record is kept.
- Legal hold — a state preventing deletion regardless of retention or user wishes.
- Data residency — the jurisdiction(s) where data may be stored.

## Audit and policy

- Audit ledger — append-only, tamper-evident evidence of material events; distinct from operational logs (`docs/security-privacy-threat-model.md`).
- Audit event — an immutable business fact (who, what, when, where, why, under what authority).
- Policy engine — the component deciding access, purpose, jurisdiction, retention, export, deletion, and AI eligibility.
- Policy pack — jurisdiction-specific rules expressed as data, not scattered conditionals (`docs/compliance-model.md`).
- Purpose of use — the declared reason for accessing sensitive data, checked and recorded.

## Truth and credentials

- Claim — a structured assertion (degree, licence, skill, role, authority, insurance) with subject, issuer, scope, status, and audit (`docs/degree-skill-truth-management.md`).
- Evidence — documents, credentials, or attestations supporting a claim. A certificate is evidence, not truth.
- Issuer — who asserts a claim (university, board, CPD provider, association).
- Verifier — who confirmed a claim, if anyone.
- Claim state — the explicit lifecycle status (claimed, verified, expired, revoked, disputed, superseded, etc.), never a single boolean.
- Skill graph — skills/competencies modelled as connected nodes and edges, not a flat badge list.
- Verifiable credential — a cryptographically verifiable assertion (W3C VC and related standards).

## Interchange

- Interchange envelope — the standard metadata wrapper on every sensitive import/export/event (schema, version, authority, policy decision, audit ref) (`docs/interchange-protocols.md`).
- Adapter — a tested boundary mapping internal models to external standards (FHIR, DICOM, Open Badges, etc.).
- Lossy-field report — documentation of what information is lost or unmapped when crossing a boundary.
- Round-trip test — proving data can be exported and re-imported without corruption.

## AI operating model

- AI competition — the scout/worker/critic/judge/executor/auditor pattern where agents propose and humans approve (`docs/ai-competition-human-loop.md`).
- Scout / Worker / Critic / Judge / Executor / Auditor — the separated agent roles.
- Human-in-the-loop — required human approval for consequential actions.
- Approval gate — the control point where a human authorises a consequential AI-proposed action.
- Context bundle — the scoped, task-specific data an agent is given; agents have no ambient authority.
- Dissent — recorded critic objections preserved even when not the winning answer.
- Execution receipt — the audited record of an approved action being performed.

## Clinical

- Risk class — the clinical-safety category of a feature, from administrative-only to medical-device-like (`docs/clinical-safety.md`).
- Hazard log — the tracked register of clinical hazards, controls, and residual risk.
- Clinical decision support — information presented to influence a clinical decision; gated and reviewed.
- Recordkeeping — storing clinician-authored clinical data without interpreting it.
- Odontogram — the structured dental chart; one of several notation systems the platform supports.

## People and lifecycle

- Person — a human modelled once with context-specific roles (dentist, student, patient, staff, executor, etc.) (`docs/data-model.md`).
- Personal tenant / personal vault — the dentist's private life space (health, finance, family, personal legal, digital estate), isolated by default from any practice, employer, or association tenant (`docs/personal-life-and-wellbeing.md`).
- Personal/professional boundary — the hard divide between a dentist's private life and their regulated professional life; crossed only by explicit, audited, authority-bearing context switching.
- Subject — the person or organisation a record is about; the patient is the subject of clinical records (`docs/patient-experience-and-rights.md`).
- Lifecycle stage — where a person sits on the aspiring→student→clinician→owner→retiree→legacy arc (`docs/lifecycle-journey.md`).
- Continuity authority / data custodian — who may act for the dentist's data after incapacity or death (`docs/estate-succession-continuity.md`).
- Executor — the authority administering an estate after death.

## Organised dentistry

- Association — a professional body modelled as its own tenant, separate from practice data (`docs/association-management.md`).
- Study club — a smaller peer/education group with its own sensitive workflows.
- Committee / officer role — governance structures with scoped permissions and stronger audit.
- Confidential matter — complaints, ethics, elections, and disciplinary-adjacent records requiring compartment controls.

## Sovereignty

- Data sovereignty — the owner can always leave with their data in documented formats (`docs/data-sovereignty-and-licensing.md`).
- Source sovereignty — the operator can obtain, build, run, and continue the software from source.
- Exit test — the verification that a full, restorable export and self-host path actually work.

## Rule

When a term in this glossary appears in code, docs, or UI, it carries this meaning. If a new concept needs a new word, define it here before relying on it.
