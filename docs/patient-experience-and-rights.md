# Patient Experience and Rights

## Purpose

Every clinical record in this platform is about a person who is not the dentist. The patient is the most vulnerable party in the system: they carry the health consequences, they often cannot see what is recorded about them, and they have legal rights over that data. A platform that models the dentist's whole life must not reduce the patient to a row in a chart.

This document defines the patient's place in the system: their rights, their experience, and the obligations the platform owes them.

## The patient is a first-class subject

- A patient is a person (`docs/data-model.md`), not a sub-feature of a dentist's account.
- Patient data has a clear controller and subject; the patient is the subject and the source of their own truth where the law recognises it.
- Patient records are classified as regulated health data and inherit the strongest access, audit, retention, and jurisdiction controls (`docs/security-privacy-threat-model.md`).

## Patient rights to honour

Subject to jurisdiction, the platform must be able to support:

- access — the patient can see the records held about them;
- portability/export — the patient can obtain their records in a documented, usable format (`docs/data-sovereignty-and-licensing.md`);
- correction — a workflow to challenge and correct inaccurate data, preserving history;
- consent and withdrawal — explicit, purpose-limited consent that can be granted and withdrawn (`docs/compliance-model.md`);
- restriction/objection — limiting certain processing where the law allows;
- erasure where lawful — deletion or anonymisation that still respects clinical retention obligations;
- explanation — understanding who accessed their data and why;
- continuity — continued access to their own history even if the dentist retires, sells, or dies (`docs/estate-succession-continuity.md`).

These rights vary by jurisdiction and are driven by policy packs, never hard-coded to one country's regime.

## Consent as a living record

- Consent is recorded with scope, purpose, basis, time, and evidence — not a one-time checkbox.
- A single global consent form is an anti-pattern; consent is specific to purpose and context.
- Consent withdrawal propagates: downstream processing, AI eligibility, and communications must respect it.
- Treatment consent (clinical) and data-processing consent (privacy) are distinct and tracked separately.

## Patient-facing access (when built)

The roadmap deliberately defers a patient portal until access, audit, and consent are mature (`docs/roadmap.md`). When a patient-facing surface exists, it must:

- show records in plain language, accessibly (`docs/accessibility-inclusion-and-ux.md`);
- make the patient's own rights and how to exercise them visible;
- audit patient access like any other sensitive access;
- never expose another patient's, the practice's, or staff's separately-owned data;
- clearly separate clinician-authored truth from AI-generated or draft content.

## Safety and dignity

- Communications to patients are human-approved before sending (`docs/ai-competition-human-loop.md`).
- Sensitive situations (safeguarding, family access, abusive-relationship risk) are explicitly considered: a curious or abusive family member is a named threat actor (`docs/security-privacy-threat-model.md`).
- Records use respectful, accurate language; corrections preserve dignity and history.
- The platform avoids dark patterns; the patient is not manipulated for the practice's commercial benefit.

## Verification

Patient-data features should demonstrate:

- a patient record can be exported in a documented format and audited;
- access to a patient record is policy-gated and logged, including patient self-access;
- consent and its withdrawal are recorded and enforced downstream;
- a correction preserves prior history;
- no cross-subject leakage between patients, staff, or the practice;
- retention and continuity keep patient access intact after the dentist exits.

## Rule

The patient is the most vulnerable subject in the system and is owed the strongest protections: access to their own truth, control over its use, a record of who touched it, and continuity of access beyond the dentist's career.
