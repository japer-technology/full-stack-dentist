# Degree, Skill, and Truth Management

## Purpose

A dentist’s professional truth is scattered: universities, dental boards, CPD/CE providers, employers, supervisors, study clubs, associations, insurers, specialist colleges, courts, regulators, patients, and the dentist’s own records all hold fragments.

full-stack-dentist should become a truth-management system for credentials, skills, authority, evidence, and claims — not just a document folder.

## Core idea

Represent professional truth as claims with evidence, issuer, subject, scope, expiry, confidence, revocation status, and audit history.

A certificate PDF is not the truth. It is evidence supporting a claim.

## Claim model

Examples:

- Eric holds Bachelor of Dental Surgery from X University.
- Eric is registered to practise in jurisdiction Y until date Z.
- Eric completed 3 hours CPD on infection control.
- Eric is competent in procedure family A under supervisor B.
- Eric is authorised as treasurer of association C.
- Eric attended study-club case session D.
- Eric holds indemnity cover with insurer E.
- Eric has disclosed conflict F for committee matter G.

Canonical fields:

```yaml
claim_id: unique id
claim_type: degree | licence | cpd | skill | role | authority | insurance | disclosure | membership
subject: person or organisation the claim is about
issuer: who asserts it
verifier: who verified it, if any
evidence_refs: documents, credentials, events, attestations
jurisdiction: where it applies
scope: what it covers
status: asserted | verified | expired | suspended | revoked | disputed | superseded
issued_at: timestamp
valid_from: timestamp
valid_until: optional timestamp
revocation_ref: optional revocation source
confidence: machine/human confidence rating
policy_refs: applicable rules
audit_refs: audit events
```

## Evidence types

- W3C Verifiable Credential
- Open Badge 3.0
- Comprehensive Learner Record
- xAPI learning statement
- signed PDF/certificate
- university transcript
- regulator register lookup
- insurance certificate
- supervisor attestation
- employer attestation
- association membership record
- study-club attendance record
- human-reviewed document extraction

## Truth states

Use explicit states, never a single boolean:

- claimed
- evidence uploaded
- machine parsed
- human reviewed
- externally verified
- issuer-signed
- expired
- superseded
- revoked
- disputed
- archived

## Skill graph

Represent skills as a graph, not a flat badge list.

Nodes:

- domain
- competency
- procedure
- instrument/system
- jurisdictional requirement
- CPD/CE topic
- supervisor
- assessment
- evidence

Edges:

- requires
- supports
- supersedes
- equivalent_to
- assessed_by
- authorised_by
- expires_after
- valid_in_jurisdiction

Use cases:

- prove licence renewal readiness
- detect CPD/CE gaps
- map degree curriculum to licence requirements
- show specialist training pathway
- generate regulator-ready evidence bundle
- match study-club events to skill gaps
- power AI recommendations without inventing qualifications

## Revocation and expiry

Every claim that can expire or be revoked must support:

- expiry monitoring
- renewal workflow
- revocation source
- stale-evidence warning
- downstream impact analysis

Example: if indemnity insurance expires, AI and workflow systems should know that some practice workflows are unsafe or blocked.

## Human verification

Human reviewers need structured tasks:

1. Review extracted claim.
2. Inspect evidence.
3. Confirm issuer.
4. Confirm dates/scope/jurisdiction.
5. Mark result.
6. Leave audit note.

The platform should separate “AI extracted this” from “human verified this.”

## Anti-fraud and provenance

Controls:

- cryptographic credential verification where possible
- issuer allowlists/registries
- document checksum history
- duplicate detection
- tamper-evident audit logs
- revocation checks
- suspicious-change alerts
- human review queues for high-risk credentials

## Association and study-club truth

Organised dentistry creates truth too:

- membership status
- officer/committee role
- CPD/CE attendance
- speaking engagement
- award/honour
- conflict disclosure
- vote eligibility
- disciplinary/ethics outcome where lawful
- supervision or peer-review participation

These claims require privacy controls because some are public, some member-only, and some highly confidential.

## AI use

AI may help extract, normalise, compare, and explain claims. It must not silently become the source of truth.

Allowed:

- parse a certificate
- suggest claim fields
- compare evidence against renewal rules
- detect missing evidence
- draft regulator-ready bundles
- explain why a claim is stale

Disallowed without human approval:

- mark a degree verified
- grant a skill
- revoke a credential
- submit regulator evidence
- change a member’s rights

## Rule

Truth management is claim + evidence + issuer + verification + revocation + audit. Anything less is a note-taking app pretending to know reality.
