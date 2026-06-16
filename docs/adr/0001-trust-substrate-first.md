# ADR 0001: Start with Trust Substrate, Not Patient Charting

## Status

Accepted

## Context

The product ambition spans personal, business, medical, dental, financial, educational, compliance, multi-country, and estate data. Starting with patient charting would create high regulatory and safety risk before the platform has identity, consent, audit, policy, export, retention, and backup foundations.

## Decision

The first engineering milestone will build the trust substrate:

- identity
- access control
- policy engine
- audit ledger
- encrypted vault
- export mechanism
- jurisdiction profile

Clinical charting and treatment workflows are deferred until those foundations are implemented and tested.

## Consequences

Positive:

- lower early regulatory risk
- reusable foundation for every module
- stronger credibility with security/privacy/compliance reviewers
- avoids rebuilding access/audit/export later

Negative:

- slower path to visible dental-charting UI
- less immediately impressive demo
- requires discipline to avoid feature sprawl

## Verification

Before clinical modules begin, the repo must have tests proving:

- policy denies sensitive access by default
- tenant boundaries hold
- audit events are emitted for sensitive reads/writes
- export bundles include checksums and manifests
- document classification affects access and AI eligibility
