# Lifecycle Journey

## Purpose

A human becomes a dentist, serves, lives, and eventually hands their work to others. Most dental software only sees a sliver of that arc — usually the years when the person is billing patients. full-stack-dentist must model the whole arc, because data, authority, obligations, and risk all change shape at every stage.

This document is the narrative spine of the product. Every module should be able to answer: which life stages does it serve, what changes at each transition, and what must never be lost when a person moves from one stage to the next.

## The arc

```text
aspiring -> student -> graduate -> clinician -> owner/leader -> educator/researcher -> retiree -> legacy
```

Stages are not strictly linear. A person can be a clinician and an educator and an association officer at once. The platform models stages as overlapping contexts and authorities, not as a single status field.

## Stage 1: Aspiring

The person is not yet a dentist. They are preparing, applying, or deciding.

- What exists: identity, study notes, application evidence, prerequisite records, aptitude/exam preparation.
- Platform value: personal knowledge vault, study tools, application/document tracking.
- Risks: this is ordinary personal data, but it seeds the credential graph that becomes regulated later.
- Transition out: enrolment creates the first formal education claim.

## Stage 2: Student

The person is in training. Truth begins to accumulate from institutions.

- What exists: degree-program claims, course evidence, placement/clinic logs, supervised-procedure sign-offs, early CPD/CE, indemnity for students.
- Platform value: study assistant, competency map against curriculum and future licence requirements, evidence vault.
- Risks: supervised clinical exposure begins; clinical-safety boundaries and patient-data rules already apply in teaching clinics.
- Transition out: graduation produces a degree claim; this must be exportable and verifiable for registration.

## Stage 3: Graduate / new registrant

The person becomes a registered dentist for the first time.

- What exists: registration/licence claims, indemnity insurance, first employment, mandatory early-career CPD/CE, supervision or provisional-registration conditions.
- Platform value: licence register, renewal reminders, CPD/CE tracker, regulator-ready evidence bundle, jurisdiction profile.
- Risks: first time the person personally holds regulated clinical responsibility; first time licence expiry can block lawful practice.
- Transition out: conditions lifted, full registration, possibly a move between jurisdictions (each move re-tests the jurisdiction model).

## Stage 4: Clinician

The person serves patients as their primary work.

- What exists: patient relationships, clinical records, treatment plans, consent, imaging, referrals, prescriptions hooks, ongoing CPD/CE, skill graph growth.
- Platform value: clinical cockpit, recall/maintenance workflows, evidence-backed competency tracking, AI drafting under clinical-safety gates.
- Risks: the highest-volume regulated-health-data stage; tenant isolation, audit of sensitive reads, and clinical-safety classification are load-bearing.
- Transition out: takes ownership, moves practice, specialises, or steps back.

## Stage 5: Owner / leader

The person runs a practice, leads a group, or holds office in organised dentistry.

- What exists: organisation/practice tenant, staff and delegated authority, suppliers, assets, finance/tax, compliance and incident registers, association/committee roles, employer obligations.
- Platform value: practice operating system, association management, policy packs, audit-heavy administration, role/context switching.
- Risks: the person now holds other people's data and livelihoods; insider-access, governance-abuse, and employment-law risks rise.
- Transition out: succession planning, sale, merger, or wind-down begins.

## Stage 6: Educator / researcher

The person creates knowledge and trains others. This overlaps every other stage.

- What exists: teaching records, supervision/mentorship attestations, research data and ethics approvals, publications, conference/CPD delivery.
- Platform value: credential issuance, learning-record interchange, study-club and event tooling, evidence provenance.
- Risks: research and human-subject data carry their own ethics and consent regimes distinct from routine clinical care.
- Transition out: emeritus, advisory, or honorary status.

## Stage 7: Retiree

The person stops active practice but retains a lifetime of records and obligations.

- What exists: retained clinical records under legal retention, lapsing/lapsed registration, residual CPD obligations for re-entry, pension/finance records, honorary memberships.
- Platform value: long-term retention with legal-hold awareness, controlled read-only access, re-entry evidence if they return, export to successors.
- Risks: records must outlive active use; deletion must respect retention law even when the person wants to "clean up."
- Transition out: incapacity or death triggers continuity authority.

## Stage 8: Legacy ("think beyond")

The person is gone or incapacitated, but their data, duties, and patients are not.

- What exists: estate/continuity authority, record custodianship, patient-record handover, regulator notifications, final exports, archival.
- Platform value: executor/continuity authority workflows, break-glass with audit, retention-respecting archival, documented handover bundles.
- Risks: orphaned records, unlawful destruction, loss of patient access to their own history, custody disputes.
- Detail: see `docs/estate-succession-continuity.md`.

## Transitions are the dangerous part

Most data loss, lock-in, and compliance failure happens at the seams between stages, not inside them. For every transition the platform must guarantee:

- export of everything the person owns or controls, in documented formats;
- preservation of audit history across the boundary;
- carry-over of retention and legal-hold obligations;
- re-evaluation of jurisdiction and authority;
- explicit handover of any authority being transferred;
- a record of who moved what, when, and under what authority.

## Cross-stage invariants

Regardless of stage, these never change:

- the person owns or controls their data and can leave with it (`docs/data-sovereignty-and-licensing.md`);
- truth is claim plus evidence, not a document folder (`docs/degree-skill-truth-management.md`);
- sensitive access is policy-gated, audited, and jurisdiction-scoped (`docs/security-privacy-threat-model.md`);
- clinical risk classes are never blurred with administrative convenience (`docs/clinical-safety.md`);
- AI proposes, humans approve consequential change (`docs/ai-competition-human-loop.md`);
- the person is served, not only the practitioner — private life stays isolated from the professional world by default (`docs/personal-life-and-wellbeing.md`).

## Rule

Design every feature for the whole arc, not the billing years. If a capability cannot survive the transition into and out of its stage — including the final handover to those who outlive the dentist — it is not finished.
