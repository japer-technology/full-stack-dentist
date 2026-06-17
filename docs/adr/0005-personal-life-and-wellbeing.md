# ADR 0005: Make Personal Life and Wellbeing a First-Class Dimension

## Status

Accepted

## Context

The charter describes itself as a sovereign operating system for a dentist's
"personal, professional, clinical, business, compliance, and knowledge life," and
the lifecycle spine commits to "serves and lives" across the whole human arc
(`docs/lifecycle-journey.md`). In practice, however, the documentation strongly
served the *practitioner* — credentials, clinical work, practice operations,
organised dentistry, compliance — while the *person* was only implied.

Dentistry makes the personal dimension unusually load-bearing: the work is
physically punishing and sense-dependent, the profession carries documented
elevated psychological and substance-use risk, and personal and practice finance
are deeply entangled through debt and ownership. A dentist's personal incapacity
or death is simultaneously a patient-safety and continuity event
(`docs/estate-succession-continuity.md`). Leaving the personal life undocumented
risked two failures: under-serving the human the platform claims to support, and —
worse — letting sensitive personal data leak into professional, employer,
insurer, or regulator contexts by default.

## Decision

Add `docs/personal-life-and-wellbeing.md` as a first-class charter document that:

- treats the dentist's personal vault as its own tenant, isolated by default from
  any practice, employer, or association tenant;
- defines a hard personal/professional boundary that is crossable only by
  explicit, audited, authority-bearing context switching;
- covers occupational and personal health, mental health/burnout (with extreme
  privacy and dignity safeguards), household finance and wealth, family and
  caregiving, personal legal and life admin, learning and identity beyond
  dentistry, and the personal digital estate;
- holds the same risk-class discipline as clinical features: these are support,
  organisation, and signposting tools, never medical, psychiatric, financial-
  advice, or legal-advice products;
- forbids mining, profiling, selling, or training on a dentist's personal data,
  and excludes personal-life data from analytics and benchmarking without
  specific, revocable, audited consent.

This is a documentation and design commitment. It introduces no code and does not
change the trust-substrate-first sequencing of ADR 0001.

## Consequences

Positive:

- the charter now serves the whole human, fulfilling the "personal … life" promise
  in the README rather than only the professional arc;
- the personal/professional data boundary is stated explicitly, reducing the risk
  of leakage being designed in by accident;
- wellbeing and crisis content is bounded against over-reach and over-collection
  from the start, protecting the dentist's dignity and interests.

Negative:

- another document to keep current as the platform is implemented;
- raises the bar for "done" on personal-facing features, which is intentional;
- some verification criteria (tenant isolation, no-leakage tests, consent-gated
  analytics) cannot be exercised until corresponding code exists.

## Verification

This ADR is satisfied when:

- `docs/personal-life-and-wellbeing.md` exists, ends with a clear rule, and defines
  verification criteria;
- it is cross-linked from `README.md` and `docs/repository-layout.md`, and its core
  terms appear in `docs/glossary.md`;
- it does not contradict the README principles, the engineering constitution, or
  ADRs 0001–0004 — in particular it reinforces sovereignty, continuity, privacy,
  clinical-safety discipline, and human-approved AI.
