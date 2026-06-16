# Data Sovereignty and Licensing

## Purpose

"If you have the full source to a thing, you won that thing." Ownership is not a marketing promise; it is a verifiable property of the system. This document defines what sovereignty means for full-stack-dentist, how it is guaranteed in design, and how source-availability and licensing reinforce it.

Sovereignty here has two faces:

- data sovereignty — the dentist (or practice, or association) owns and can always leave with their data;
- source sovereignty — the operator can obtain, read, build, run, and continue the software itself.

A platform that owns your data and hides its own source has not given you sovereignty. It has rented you a nicer cage.

## Data sovereignty guarantees

1. Ownership is explicit. Every record has an owner/controller; the platform is a custodian acting under authority, never the owner of the dentist's data.
2. Export is always available. Every module ships with export; a complete, restorable export bundle can be produced at any time (`docs/data-model.md`, engineering constitution Rule 4).
3. Formats are documented and open. Exports use documented schemas and neutral formats (JSON, CSV, Parquet, FHIR/DICOM/VC where applicable) that other tools can open without this platform.
4. No silent lock-in. No dark patterns, ransom of data behind upgrades, or export crippling. Leaving is a supported, tested workflow.
5. Local-first capable. Core personal/professional use works without a mandatory third-party SaaS account (engineering constitution Rule 8).
6. Audit travels with data. Export includes the provenance and audit trail needed to trust the records elsewhere.
7. Retention and law respected. Sovereignty operates within retention and legal-hold obligations; "delete everything" still obeys the law (`docs/estate-succession-continuity.md`).

## The exit test

Sovereignty is proven by the exit, not the onboarding. A credible exit means:

- a dentist can export everything they own or control, in documented formats, unaided;
- the export is complete enough to reconstruct their working state elsewhere;
- the export carries checksums and a manifest of what is included and excluded, with reasons;
- no feature degrades or destroys data to discourage leaving;
- the operator can stand up the software from source on their own infrastructure.

If the exit test cannot be run and verified, the sovereignty claim is theatre.

## Source sovereignty

The operator's independence depends on access to the software itself.

- The repository is the single source of truth for apps, services, schemas, policies, and infrastructure definitions.
- Builds are reproducible from source; deployment is defined as code (`docs/observability-and-operations.md`).
- Self-hosting is a first-class deployment mode, not a grudging concession.
- No critical core capability is hidden behind an opaque, non-portable service that cannot be self-operated.

## Licensing stance

Licensing is an open question to be resolved by the maintainers (see `docs/standards-and-assumptions.md` open questions), but the constraints it must satisfy are not open:

- The chosen licence must preserve the operator's right to obtain, run, modify, and continue the software.
- "Open-core" or "source-available" arrangements, if used, must keep the trust substrate and data-portability paths in the openly available core — never paywalled.
- Any proprietary or hosted add-ons must not be able to capture the dentist's data or prevent export.
- Third-party dependencies must have licences compatible with the project's distribution and self-hosting goals.
- A `LICENSE` file must exist before any public distribution; until then the repository is unlicensed and all rights are reserved by default.

Candidate directions to evaluate (decision deferred to maintainers): a strong copyleft licence (e.g. AGPL-family) to keep hosted derivatives open, a permissive licence (e.g. Apache-2.0) for maximum adoption, or an open-core split with a permissive/copyleft core. The decision must be recorded as an ADR.

## Boundaries and non-negotiables

- User data is never sold or used to train external models by default (`docs/security-privacy-threat-model.md`).
- Sovereignty does not override clinical-safety, privacy, or retention law.
- Sovereignty applies per owner: a dentist's personal sovereignty does not grant access to patients', staff's, or an association's separately-owned data.

## Verification

Before the sovereignty claim may be made publicly, the project must show:

- a passing end-to-end export-and-restore test for each module that holds data;
- documented, versioned export schemas;
- a self-host path that builds and runs from source;
- a `LICENSE` file and an ADR recording the licensing decision;
- a dependency-licence review with no incompatible obligations.

## Rule

Ownership is a property you can test, not a sentence in a brochure. If a dentist cannot leave with everything they own — and an operator cannot run the software from source — the platform has not been won by its users, and the sovereignty claim must be withdrawn until it can be proven.
