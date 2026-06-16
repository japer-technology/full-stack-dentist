# Clinical Safety

## Purpose

Clinical data is the highest-risk domain in this platform. Software that touches clinical records, treatment planning, prescribing, or decision support can harm real patients if it misleads, loses information, or quietly oversteps its validated scope. This document defines how clinical risk is managed as an explicit, evidenced discipline rather than an assumption.

This is not a regulatory certification. It is the engineering stance the project commits to before any clinically-meaningful feature ships.

## Risk classes

Every feature touching clinical workflows must be classified. The class sets the controls and the review bar.

- administrative only — scheduling, contact, billing context; no clinical content.
- recordkeeping only — stores/retrieves clinician-authored clinical data without interpreting it.
- clinical workflow support — organises clinical work (recalls, task routing) without advising on care.
- clinical decision support — presents information intended to influence a clinical decision.
- diagnostic/therapeutic recommendation — suggests a diagnosis or treatment.
- medical-device-like function — meets a jurisdiction's definition of a medical device.

Anything above recordkeeping requires explicit clinical-safety review. Diagnostic/therapeutic and device-like functions require a formal regulatory pathway per jurisdiction before release (`docs/compliance-model.md`).

## Reference frameworks

Use as design inputs, not badges, and confirm currency per jurisdiction at implementation time:

- ISO 14971 — application of risk management to medical devices.
- IEC 62304 — medical-device software lifecycle processes.
- IEC 62366-1 — usability engineering for medical devices.
- UK DCB0129 / DCB0160 — clinical risk management for health IT manufacturers and deploying organisations.
- Relevant national device regulators (e.g. TGA, MHRA, FDA, EU MDR) where applicable.

## Hazard log

Clinical risk is tracked, not remembered. Each clinically-relevant feature maintains a hazard log entry:

```yaml
hazard_id: unique id
feature_ref: feature/module
description: what could go wrong
cause: how it could happen
effect: clinical consequence to a patient
risk_class: feature risk class
severity: harm severity
likelihood: estimated likelihood
initial_risk: severity x likelihood
controls: mitigations (design, process, UI, training)
residual_risk: after controls
owner: accountable clinical-safety owner
status: open | mitigated | accepted | closed
evidence_refs: tests, reviews, validation
```

Residual risk that cannot be reduced to acceptable must block release of that feature, not be silently accepted.

## Core safety controls

- Human clinician remains the accountable decision-maker; software supports, it does not decide.
- Source-of-truth clinical records are never overwritten by AI without human approval (`docs/ai-competition-human-loop.md`).
- Structured data plus human narrative; images/PDFs are never the only source of truth (`docs/data-model.md`).
- Notation, units, allergies, and medication data have explicit, tested representations to prevent transcription/conversion errors.
- Clinical-safety-relevant changes are audited with before/after evidence (`docs/security-privacy-threat-model.md`).
- Disclaimers and scope statements make the tool's limits visible at the point of use.
- Degradation is safe: if data is incomplete or stale (e.g. expired indemnity, missing allergy), the system warns rather than proceeds silently.

## AI under clinical safety

AI in clinical contexts is constrained by both this document and the AI operating model:

- Allowed under gates: summarise clinician-selected records, draft notes for clinician review, surface missing evidence, explain records to authorised users.
- Disallowed until formal safety/regulatory work exists: autonomous diagnosis, autonomous prescribing, irreversible clinical actions, unreviewed clinical decision support.
- Every clinical AI output is labelled as AI-generated, traceable to its sources, and requires clinician review before it affects care.

## Usability as safety

Misleading or confusing clinical UI is a hazard, not a polish issue (`docs/accessibility-inclusion-and-ux.md`).

- Critical information (allergies, warnings, tooth/site identity) must be unambiguous and hard to miss.
- Destructive or clinically-significant actions require confirmation and are reversible or audited.
- Accessibility failures that hide clinical information are treated as clinical hazards.

## Launch gates for clinical features

A clinical feature may not ship until it has:

1. a documented risk class and scope-of-use statement;
2. a hazard log with acceptable residual risk;
3. clinical-safety review by a suitably qualified person;
4. tests for data integrity, audit, export, retention, and safe degradation;
5. a regulatory pathway where the class requires one;
6. a user-facing limitation statement.

## Rule

Clinical safety is evidenced, owned, and gated — never assumed. If a feature could influence care and its residual risk is not documented and accepted by an accountable clinical-safety owner, it does not ship.
