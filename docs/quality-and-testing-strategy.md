# Quality and Testing Strategy

## Purpose

Across these documents the phrase "tests must prove" appears repeatedly. This document defines what that means in practice: the kinds of tests this platform considers non-negotiable, how they map to the trust substrate, and the bar a module must clear before it may hold sensitive data.

Testing here is not about coverage percentages. It is about producing evidence that the load-bearing properties — isolation, audit, export, retention, policy, safety — actually hold.

## Quality principles

- Trust properties are tested, not asserted. Every claim in the constitution and threat model must have a corresponding executable test where possible.
- Default-deny is the default test. The first test for any sensitive path is that unauthorised access fails.
- Evidence over coverage. A small number of high-value invariant tests outranks a large suite that never exercises the dangerous paths.
- Tests are part of the launch gate. A module without its mandatory tests is not "done"; it is unverified.
- Bad behaviour becomes a regression test. Any incident, AI failure, or escaped bug yields a permanent test.

## Test layers

- Unit — pure logic: classification rules, notation conversion, claim-state transitions, policy evaluation.
- Contract/schema — interchange envelopes, export schemas, and adapter mappings validate and version correctly (`docs/interchange-protocols.md`).
- Integration — tenant isolation, audit emission, policy enforcement across service boundaries.
- End-to-end — real user journeys: create user, add credential, upload evidence, export, restore, verify audit.
- Migration — deterministic, reversible-where-possible schema migrations with data-integrity checks.
- Security — authn/authz, injection, access-control regression, secrets hygiene, dependency scanning, SAST.
- Privacy — data-minimisation, redaction, consent/legal-basis enforcement, deletion/anonymisation correctness.
- Resilience — backup/restore drills, point-in-time recovery, failure injection (`docs/observability-and-operations.md`).
- Accessibility — automated and manual a11y checks on user-facing surfaces (`docs/accessibility-inclusion-and-ux.md`).

## Mandatory invariant tests

These map directly to the engineering constitution and threat model. Every module touching sensitive data must include them:

- policy denies sensitive access by default;
- tenant boundaries hold (no cross-tenant read/write/export);
- audit events are emitted for sensitive reads, writes, deletes, exports, and admin actions;
- document classification affects access and AI eligibility;
- export bundles include checksums and a manifest of included/excluded records;
- export round-trips: export then restore reproduces the working state;
- retention and legal hold block deletion where the law requires;
- AI extraction is distinguishable from human verification, and consequential writes are blocked until approved.

## Domain-specific test obligations

- Clinical — data integrity, notation/units/allergy correctness, safe degradation, hazard-log-linked tests (`docs/clinical-safety.md`).
- Truth/credentials — claim-state transitions, expiry/revocation handling, evidence provenance (`docs/degree-skill-truth-management.md`).
- Association — committee/confidential compartment isolation, election/complaints separation, no leak into practice tenant (`docs/association-management.md`).
- Interchange — schema validation, round-trip, lossy-field report, malformed-input, version migration per adapter.
- AI — input-classification gate, redaction, retrieval-source traceability, approval-gate enforcement, output-review workflow.

## Test data discipline

- Never use real patient, member, or financial data in tests or non-production environments.
- Production and staging data are never shared (`docs/compliance-model.md`).
- Synthetic data generators produce realistic but fictional records, including multi-jurisdiction and edge cases.
- Secrets are never committed; tests use ephemeral, scoped credentials.

## Environments and gating

- Changes run the mandatory invariant suite in CI before merge.
- Regulated-deployment releases additionally require security, migration, backup/restore, and (for clinical features) clinical-safety evidence.
- A failing trust-property test blocks release regardless of feature pressure.

## Definition of done

A unit of work is done when:

- its behaviour is covered by tests at the appropriate layers;
- all mandatory invariant tests relevant to it pass;
- its documentation (including any hazard-log or schema changes) is updated;
- no new secrets, high-severity vulnerabilities, or unaudited sensitive paths are introduced.

## Rule

If a trust property is not covered by a test that can fail, it is a wish, not a guarantee. Sensitive data may only live behind properties the test suite actively defends.
