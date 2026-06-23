# Build Philosophy and Evolutionary Model

## Purpose

The charter describes *what* the platform must be. This document describes *how* it is built and how it improves over time. Two claims appear often around this project — that it is "created using the best AI available" and that the stack evolves by "survival of the fittest." Both are easy to say and dangerous as slogans. This document turns them into disciplined, testable commitments that respect the rest of the charter rather than overriding it.

## How the stack is built

### Best available AI, under the human-in-the-loop model

The stack is designed and assembled with the strongest AI tools available at the time, but always inside the operating model defined in `docs/ai-competition-human-loop.md`:

- AI scouts, drafts, critiques, and ranks candidate designs, schemas, code, policies, and documentation.
- Humans retain authority over every consequential decision, with evidence, dissent, and audit receipts.
- "Best AI" means best for the task and risk class, not a single fixed vendor. Model choice is itself a candidate that can be challenged and replaced.

AI accelerates the work; it does not own it. No AI output enters the trust substrate (identity, policy, audit, vault, export, clinical, compliance) without human review and the mandatory tests for trust properties (`docs/quality-and-testing-strategy.md`).

### In consultation with dental groups and associations

The platform serves dentists and organised dentistry, so the people it serves shape it:

- Practitioners, practice owners, educators, researchers, retirees, patients, and association, society, study-club, and college administrators are treated as design inputs, not afterthoughts.
- Consultation is recorded as evidence, not asserted as endorsement. Input that changes a load-bearing decision becomes an Architecture Decision Record (`docs/adr/`).
- Consultation does not override safety, privacy, or law. A popular request that breaks clinical-safety, sovereignty, or jurisdiction rules is declined and the reason is recorded.
- No group, association, or vendor is given silent control over a dentist's data or the right to lock peers out. Sovereignty guarantees (`docs/data-sovereignty-and-licensing.md`) bind every contributor equally.

This avoids two failure modes: building in an ivory tower with no real users, and letting the loudest stakeholder capture the platform.

## The evolutionary model

"Survival of the fittest" is adopted literally as an engineering method, with explicit rules so that "fittest" cannot quietly mean "cheapest," "flashiest," or "whatever shipped first."

### Variation

- Multiple candidate solutions are generated for non-trivial problems — competing designs, modules, models, mappings, or policies — rather than committing to the first idea (`docs/ai-competition-human-loop.md`).
- Variation is encouraged at the edges (apps, modules, integrations) and constrained at the core (identity, policy, audit, schemas), so experimentation never destabilises the trust substrate.

### Selection

A candidate only survives if it is *measurably fitter* against an explicit, charter-aligned fitness function. Fitness is judged on, at minimum:

- Safety: clinical-safety risk class respected; no new hazards (`docs/clinical-safety.md`).
- Security and privacy: no new high-severity vulnerabilities; least privilege; data minimisation (`docs/security-privacy-threat-model.md`).
- Sovereignty: passes the exit test; data remains exportable and owned by the dentist (`docs/data-sovereignty-and-licensing.md`).
- Correctness and quality: passes the mandatory invariant tests (`docs/quality-and-testing-strategy.md`).
- Jurisdiction fit: no hard-coded country assumptions in generic logic (engineering constitution Rule 6).
- Human and patient value: accessibility, real-user benefit, and patient rights honoured (`docs/accessibility-inclusion-and-ux.md`, `docs/patient-experience-and-rights.md`).

Survival is decided by humans against this rubric, informed by AI judges that score but never execute. Selection pressure is evidence, not opinion or popularity.

### Inheritance and extinction

- Survivors are documented: the winning decision and the discarded alternatives are captured so future work inherits the reasoning, not just the result.
- Losing candidates are retired cleanly, with data export honoured, so no user is stranded on a path the project abandons.
- Superseding a decision references the one it replaces; history is preserved, not rewritten (`docs/governance-and-contribution.md`).

### Guardrails on "fitness"

Evolution is bounded by the charter; it cannot mutate away from it:

- The README principles and the engineering constitution are invariants. Nothing "wins" by violating them; changing them requires a deliberate ADR, not a quiet drift.
- Speed, demos, and deadlines never count as fitness on their own.
- Regressions in safety, privacy, sovereignty, or auditability are extinction-level failures, not acceptable trade-offs.

## Anti-slogan commitments

To keep these ideas honest rather than decorative:

- "Best AI" is meaningless without the human-in-the-loop model and trust tests that constrain it.
- "Consultation" is meaningless without recorded evidence and the freedom to decline unsafe requests.
- "Survival of the fittest" is meaningless without a written fitness function, real measurement, and clean extinction with data export.

If any of these three commitments cannot be evidenced for a change, the change is not "fit," however impressive it looks.

## Related documents

- `docs/ai-competition-human-loop.md` — the agent competition and approval model this philosophy runs on.
- `docs/governance-and-contribution.md` — how decisions are steered, recorded, and superseded.
- `docs/quality-and-testing-strategy.md` — the trust-property tests that selection depends on.
- `docs/data-sovereignty-and-licensing.md` — the exit test that bounds extinction and consultation.
- `docs/engineering-constitution.md` — the invariants that evolution may not violate.
