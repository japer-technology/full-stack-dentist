# ADR 0004: Document the Full Human Lifecycle, Sovereignty, and Cross-Cutting Operating Layers

## Status

Accepted

## Context

The earlier charter documents (architecture, data model, security, compliance, interchange, truth, AI competition, association management) covered the platform's domains and trust substrate well, but left several critical understandings undocumented:

- the full human arc — a person becomes a dentist, serves, lives, retires, and hands their work to others — was implied across docs but never made the explicit narrative spine;
- estate, succession, and continuity ("beyond" the dentist) were referenced repeatedly but had no home;
- data sovereignty and the source-availability/licensing stance ("if you have the full source to a thing, you won that thing") were asserted as principles without a concrete, testable definition;
- cross-cutting engineering layers that the docs assumed — clinical-safety management, quality/testing strategy, observability/operations, accessibility/inclusion/UX, patient experience and rights, and project governance/contribution — had no dedicated documentation;
- the project lacked a shared glossary, so terms risked drifting in meaning.

The goal was to bring the documentation to world-class coverage across all layers and leave no critical understanding undocumented.

## Decision

Add a coherent set of charter documents that ground the platform across the whole human lifecycle, the sovereignty promise, and the cross-cutting operating layers:

- `docs/lifecycle-journey.md` — the aspiring→student→clinician→owner→retiree→legacy arc as the product's narrative spine, with the dangerous transitions made explicit.
- `docs/estate-succession-continuity.md` — authority, custody, and access transfer on death, incapacity, retirement, sale, and provider failure.
- `docs/data-sovereignty-and-licensing.md` — testable data- and source-sovereignty guarantees, the exit test, and the licensing constraints.
- `docs/clinical-safety.md` — risk classes, hazard log, and launch gates for clinically-meaningful features.
- `docs/quality-and-testing-strategy.md` — how "tests must prove" is operationalised into mandatory invariant tests.
- `docs/observability-and-operations.md` — how the platform is run, monitored, recovered, and audited in operation.
- `docs/accessibility-inclusion-and-ux.md` — accessibility, internationalisation, and safety-critical UX as requirements.
- `docs/patient-experience-and-rights.md` — the patient as a first-class subject with enforceable rights.
- `docs/governance-and-contribution.md` — how the initiative is steered and contributed to, fulfilling the Phase 0 contribution-rules deliverable.
- `docs/glossary.md` — the ubiquitous language for the whole charter.

These are documentation and design commitments. They introduce no code and do not change the trust-substrate-first sequencing of ADR 0001.

## Consequences

Positive:

- the documentation now spans the full lifecycle and all major layers, not just the billing years and core domains;
- sovereignty and continuity become testable commitments rather than slogans;
- previously-implied obligations (clinical safety, testing, operations, accessibility, patient rights, governance) have explicit homes and verification criteria;
- a shared glossary reduces vocabulary drift.

Negative:

- more documents to keep current as the system is implemented;
- raises the bar for what "done" means, which is intentional but increases up-front effort;
- some verification criteria cannot be exercised until corresponding code exists.

## Verification

This ADR is satisfied when:

- the new documents exist and are cross-linked from `README.md` and `docs/repository-layout.md`;
- each new document ends with a clear rule and defines verification or launch criteria where applicable;
- the glossary terms are consistent with usage across the charter;
- no new document contradicts the README principles, the engineering constitution, or ADRs 0001–0003.
