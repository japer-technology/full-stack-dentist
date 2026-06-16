# Governance and Contribution

## Purpose

The roadmap names "contribution rules" as a Phase 0 deliverable. This document provides them, and defines how the initiative is steered: how decisions are made, how changes are proposed and reviewed, and what every contribution must respect. A platform that asks for trust must itself be governed in a trustworthy, transparent way.

## Governance principles

- The charter is binding. The README principles and the engineering constitution are the supreme rules; nothing merges that contradicts them without an ADR changing them deliberately.
- Decisions are recorded. Significant or hard-to-reverse choices become Architecture Decision Records (`docs/adr/`).
- Trust substrate before features. Identity, policy, audit, vault, and export take priority over flashy modules (`docs/roadmap.md`).
- Safety and law are not overridden by convenience, deadlines, or demos.

## Roles

- Maintainers — accountable for the charter, architecture direction, and merge decisions; own ADR acceptance.
- Domain reviewers — security/privacy, clinical-safety, and compliance reviewers whose sign-off is required for changes in their area.
- Contributors — anyone proposing changes under these rules.

Until the project formally designates these roles, the repository owner acts as maintainer and must still record decisions as ADRs.

## Decision process and ADRs

- Use an ADR for: architecture changes, new load-bearing primitives, security/privacy/clinical-safety stances, licensing, jurisdiction strategy, and anything expensive to reverse.
- ADRs are numbered, dated, and carry a status (proposed, accepted, superseded).
- An ADR states context, decision, consequences (positive and negative), and verification.
- Superseding an ADR references the one it replaces; history is preserved, not rewritten.

## Contribution workflow

1. Understand the charter and the relevant domain docs before proposing change.
2. Open a focused change; keep unrelated concerns separate.
3. For sensitive areas, define access, purpose, jurisdiction, retention, export, AI eligibility, and audit behaviour before implementation (engineering constitution Rule 2).
4. Include or update the mandatory tests for trust properties (`docs/quality-and-testing-strategy.md`).
5. Update documentation alongside code; docs are part of the change, not an afterthought.
6. Obtain the required domain-reviewer sign-off for security, clinical-safety, or compliance-affecting changes.

## What every contribution must respect

- No secrets committed; scan before committing.
- No new high-severity security vulnerabilities; address those related to the change.
- No hard-coded jurisdiction assumptions in generic logic (engineering constitution Rule 6).
- No invisible AI; AI use is scoped, logged, and reviewable (engineering constitution Rule 3).
- No feature holding sensitive data without export, audit, access control, retention, and jurisdiction support.
- No clinical feature above recordkeeping without a hazard log and clinical-safety review (`docs/clinical-safety.md`).
- No claim of compliance; define scope, controls, evidence, and review status (engineering constitution Rule 10).

## Documentation as a first-class artifact

- This `docs/` set is the canonical understanding of the system; it is kept current with reality.
- New load-bearing concepts get a doc; significant decisions get an ADR.
- The glossary defines shared terms so contributors mean the same things (`docs/glossary.md`).

## Security and responsible disclosure

- Security issues are handled privately first, not in public issues, until a fix is available.
- A `SECURITY.md` with a disclosure contact and process should exist before any public deployment.
- Incidents feed back into controls and regression tests (`docs/observability-and-operations.md`).

## Licensing of contributions

- The project's licence (to be decided and recorded as an ADR) governs all contributions (`docs/data-sovereignty-and-licensing.md`).
- Contributors must have the right to contribute what they submit and accept the project's licensing and any contributor agreement once established.

## Rule

The initiative is steered by its charter, its decisions are recorded, and its contributions are gated by the same trust properties the product promises. Governance that cannot be inspected is as untrustworthy as software that cannot be audited.
