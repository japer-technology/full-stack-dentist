# Estate, Succession, and Continuity

## Purpose

"Think beyond" the dentist. A dentist's records, obligations, and patients outlive their active career and often the dentist themselves. Death, incapacity, retirement, practice sale, and provider failure are not edge cases — they are guaranteed events. A platform that holds a lifetime of regulated data must treat continuity as a designed feature, not an afterthought handled by lawyers after the fact.

This document defines how authority, custody, and access transfer when the dentist can no longer act.

## Triggering events

- death of the dentist
- temporary incapacity (illness, injury, detention)
- permanent incapacity
- retirement and deregistration
- practice sale, merger, or closure
- provider/vendor shutdown or platform exit
- regulatory suspension or intervention
- loss of the only key holder

Each event has a different authority basis, urgency, and reversibility. The platform must not collapse them into one "account closed" path.

## Continuity authorities

Access after the dentist cannot act must be explainable by a documented authority:

- nominated continuity officer or data custodian
- executor or administrator of the estate
- enduring power of attorney / guardian (for incapacity)
- practice successor or purchaser (for transferred records)
- regulator or court order
- next-of-kin within lawful limits

Authority is itself a claim with evidence, expiry, scope, and revocation (`docs/degree-skill-truth-management.md`). No authority grants blanket access; each is scoped to what continuity lawfully requires.

## What must continue

- patient access to their own clinical history
- lawful retention of clinical, financial, and employment records for their full statutory period
- handover of in-flight clinical care (referrals, labs, recalls, prescriptions)
- regulator and indemnity notifications
- staff and payroll obligations during wind-down
- association/committee role transfer or vacancy handling
- ability to produce a complete, verifiable export for successors

## What must stop

- new clinical actions in the deceased/incapacitated dentist's name
- AI actions on their behalf beyond read/summarise for handover
- communications appearing to come from the person
- silent, unaudited access by anyone

## Record custodianship

Clinical and other regulated records often must survive the person by years or decades.

- Records enter a custodianship state with a named custodian and retention clock.
- Retention and legal hold still bind the custodian; "tidying up" cannot override the law.
- Patients retain access and export rights to their own records.
- Custody can transfer (to a successor practice, an archive, or a regulator) with full provenance and audit.
- Cryptographic erasure or destruction happens only when retention lawfully ends and no hold applies.

## Break-glass and continuity access

Emergency continuity access reuses the break-glass discipline (`docs/security-privacy-threat-model.md`): declared purpose, MFA, time-limited scope, high-severity audit, notification, and post-event review. Continuity is a planned authority where possible and break-glass only when no plan exists.

## Succession and practice transfer

When a practice changes hands:

- the practice tenant, not the individual's personal vault, is the unit of transfer;
- personal, association, and clinical-custodian data are separated from transferable business data;
- patient consent and notification obligations are honoured before records move;
- a signed export manifest documents exactly what transferred, what did not, and why;
- audit history transfers with the records, not just the latest state.

## Platform exit and provider failure

Sovereignty means the dentist survives the platform failing, not only the dentist failing.

- A current, restorable export bundle must always be obtainable without vendor cooperation.
- Export formats are documented and openable by other tools (`docs/data-sovereignty-and-licensing.md`).
- Local-first and self-hosted modes mean core records do not vanish if a cloud provider disappears.
- Backups and restore drills are part of continuity, not just disaster recovery (`docs/observability-and-operations.md`).

## Pre-planning

Continuity is far safer when arranged in advance. The platform should let a dentist, while able:

- nominate a continuity officer and successor custodian;
- record where keys, exports, and credentials live;
- pre-authorise scoped continuity access with defined triggers;
- maintain an up-to-date "in case I cannot act" handover bundle;
- test the handover the same way backups are test-restored.

## Verification

Before continuity features are considered ready, tests must prove:

- a nominated continuity authority gains only its scoped access, fully audited;
- patients retain access to their own records after the dentist's account is frozen;
- retention and legal hold survive account closure and custody transfer;
- a practice-sale export separates personal/association data from transferable records;
- unplanned access requires break-glass and high-severity audit;
- a complete restorable export can be produced without provider cooperation.

## Rule

A dentist's death or incapacity must never become a patient's data emergency or a successor's archaeology project. Continuity is designed, scoped, audited, and rehearsed before it is needed.
