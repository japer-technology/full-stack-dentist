# Accessibility, Inclusion, and UX

## Purpose

"Serves and lives" includes everyone the platform touches: dentists with disabilities, ageing practitioners, multilingual teams, stressed clinicians making safety-critical decisions, anxious patients, and older or low-literacy users reading their own records. Accessibility and clear design are not polish; in a clinical and high-stakes-data system they are safety and equity requirements.

This document defines the human-interface stance for full-stack-dentist.

## Principles

- Accessible by default. Every user-facing surface is usable by people with visual, motor, cognitive, and hearing differences from day one, not retrofitted.
- Clarity is safety. Confusing or misleading UI in clinical, financial, or consent contexts is a hazard, not a style issue (`docs/clinical-safety.md`).
- Inclusive of the whole career. Interfaces serve students, busy clinicians, administrators, retirees, and executors — different contexts, different literacy, different stress.
- Multilingual and multi-jurisdiction. Language, date/number/currency formats, names, and terminology vary by jurisdiction and must not be hard-coded (`docs/compliance-model.md`).
- Respect for the patient reader. Patients should be able to understand their own records and rights (`docs/patient-experience-and-rights.md`).

## Accessibility baseline

- Target WCAG 2.2 Level AA (confirm the current applicable version and any jurisdictional legal standard at implementation time).
- Full keyboard operability; visible focus; no keyboard traps.
- Semantic structure and ARIA where needed; works with screen readers.
- Sufficient colour contrast; never colour alone to convey meaning (critical for charting and warnings).
- Respect user settings: text scaling, reduced motion, high contrast, OS-level preferences.
- Accessible forms with clear labels, errors, and instructions.
- Time limits are avoidable or extendable; no essential information lost to timeout.

## Internationalisation and localisation

- All user-facing text is externalised for translation; no concatenated sentences that break grammar.
- Locale-aware dates, numbers, currencies, units, and address/name formats.
- Right-to-left layout support where languages require it.
- Jurisdiction-appropriate clinical and legal terminology, sourced from policy packs, not hard-coded.
- Translations of safety-critical content are reviewed, not machine-trusted.

## Clinical and high-stakes UX

- Critical data (allergies, warnings, tooth/site identity, amounts, recipients) is unambiguous and prominent.
- Destructive or consequential actions require clear confirmation and are reversible or audited.
- AI-generated content is visibly labelled and clearly separated from human-authored and source-of-truth records (`docs/ai-competition-human-loop.md`).
- Approval screens show exactly what will happen, what data is used, who receives it, and what is irreversible.
- Error states are honest and actionable, never silent failure.

## Cognitive load and inclusion

- Progressive disclosure: show what the task needs, not everything at once.
- Plain-language patient-facing content; avoid unexplained jargon.
- Consistent patterns across modules so skills transfer between contexts.
- Designed for interruption and stress — clinicians are often interrupted mid-task.
- Account for low-bandwidth, older devices, and offline/local-first use (`docs/architecture.md`).

## Verification

User-facing surfaces should demonstrate:

- automated accessibility checks in CI plus periodic manual screen-reader and keyboard testing;
- contrast and colour-independence checks, especially on charting and warnings;
- localisation tests including a non-Latin and a right-to-left locale;
- usability review of safety-critical and consent flows;
- accessibility regressions treated as defects, and clinical-information a11y failures treated as hazards (`docs/quality-and-testing-strategy.md`).

## Rule

If a person cannot perceive, understand, and safely act on what the interface shows them, the feature is not finished — and where that information is clinical, an inaccessible interface is a clinical hazard.
