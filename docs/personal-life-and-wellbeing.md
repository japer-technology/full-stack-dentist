# Personal Life and Wellbeing

## Purpose

A dentist is a whole human before, during, and after they are a clinician. The
charter so far is strong on the professional arc — student, clinician, owner,
educator, retiree, legacy (`docs/lifecycle-journey.md`) — but a dentist also has
a body that wears out, a mind under chronic load, a family, money that is not the
practice's money, personal legal obligations, hobbies, beliefs, and a private
digital life. "Software a dentist requires over their lifetime" is not satisfied
by practice-management software with extra features; it must serve the *person*,
not only the *practitioner*.

This document makes the personal dimension a first-class part of the platform and
defines the hard boundary between a dentist's private life and their regulated
professional life. It is deliberately ambitious — thinking outside the billing
years — while staying inside the platform's non-negotiable principles.

## Why this matters more in dentistry than most fields

Dentistry is not an average desk job, and the personal-life burden is shaped by
the profession itself:

- It is physically punishing. Sustained static posture, fine motor precision,
  vibration, and repetitive loading drive musculoskeletal injury, and the senses
  the work depends on — vision, hearing, fine touch — degrade with age and
  exposure. A career-ending personal injury is an occupational risk, not bad luck.
- It carries documented psychological load. Isolation in the operatory,
  perfectionism, complaint and litigation stress, financial pressure of practice
  ownership, and emotional labour with anxious patients contribute to burnout and
  to mental-health and substance-use risk that the profession has long recognised
  as elevated. This must be handled with extraordinary care for privacy and
  dignity (see "Crisis, safety, and dignity" below).
- It blurs personal and professional finance. Student debt, the leap into
  practice ownership, equipment loans, partnership buy-ins, and self-employment
  mean a dentist's household balance sheet is entangled with business and
  regulatory risk in ways most employees never face.
- It demands continuity beyond the self. Because the dentist holds other people's
  regulated records, their personal incapacity, illness, or death is also a
  professional and patient-safety event (`docs/estate-succession-continuity.md`).

A platform that ignores the person fails the very practitioner it claims to serve.

## Principles

1. The person owns the platform; the practice is a tenant of it.
   - The dentist's private vault is their own tenant, isolated from any practice,
     association, or employer tenant (`docs/glossary.md`, "Tenant").
   - Personal data must never be silently visible to an employer, partner, or
     successor by virtue of the dentist using the same product at work.

2. Hard personal/professional boundary, always crossable on purpose, never by
   accident.
   - Moving information between the private and professional contexts is an
     explicit, audited, authority-bearing act of context switching
     (`docs/security-privacy-threat-model.md`), not a side effect.
   - The default is separation; integration is opt-in and reversible.

3. Personal data is the dentist's, with the platform's highest privacy posture.
   - Health, financial, family, and belief data about the dentist are sensitive
     personal data and may attract special-category protections
     (`docs/compliance-model.md`).
   - The platform itself must not mine, profile, sell, or train on a dentist's
     personal life. AI may assist the dentist; it must not surveil them
     (`docs/ai-competition-human-loop.md`).

4. Support, never diagnose or treat — including for the dentist.
   - Wellbeing, financial, and legal features are organisation, information, and
     prompting tools. They are not medical, psychiatric, financial-advice, or
     legal-advice products and must respect the same risk-class discipline applied
     to patient-facing features (`docs/clinical-safety.md`).
   - The platform must signpost qualified human help and must never position
     itself as a substitute for it.

5. The whole-life arc, not the working day.
   - Personal capabilities must survive every lifecycle transition — career
     breaks, illness, jurisdiction moves, retirement, incapacity, and death —
     under the same export and continuity guarantees as professional data
     (`docs/data-sovereignty-and-licensing.md`, `docs/estate-succession-continuity.md`).

## The personal domains

These are personal-vault capabilities. Each is local-first capable, exportable,
and isolated from professional tenants by default.

### Occupational and personal health

- Ergonomics and musculoskeletal load: posture, loupes/magnification settings,
  exercise and stretch prompts, and a private log of strain or injury — held as
  the dentist's personal health data, never as employment surveillance.
- Sensory health over a career: vision and hearing baselines and check reminders,
  given the work's dependence on both.
- Immunisation, exposure, and sharps-injury personal records that the dentist
  needs across employers and jurisdictions, portable with them when they move.
- General personal health admin: appointments, medications, and conditions the
  dentist chooses to track for themselves — clearly the dentist's own clinical
  record, never confused with a patient record (`docs/data-model.md`).

### Mental health, resilience, and burnout

- Private, opt-in self-check and reflection tools framed as wellbeing support,
  not assessment or diagnosis.
- Workload and on-call/after-hours signals the dentist can review for themselves
  to recognise overload — visible to the dentist only.
- A curated, jurisdiction-aware directory of professional support: practitioner
  health programmes, peer-support and colleague-assistance schemes, regulators'
  health pathways, and emergency services.

### Crisis, safety, and dignity

- Wellbeing data is among the most sensitive the platform can hold. It is private
  to the dentist by default, excluded from analytics and benchmarking, and never
  exposed to employers, regulators, insurers, or successors without the dentist's
  specific, revocable, audited consent or an overriding legal authority.
- Any high-distress signposting prioritises immediate qualified human help and
  emergency services over any in-product flow.
- The platform must not create records that could be weaponised in fitness-to-
  practise, employment, or insurance disputes against the dentist's interest; it
  minimises what it stores and lets the dentist purge personal wellbeing notes
  (subject only to genuine legal hold, never to platform convenience).

### Personal finance and wealth

- A household financial picture distinct from, but reconcilable with, practice
  finance (`docs/architecture.md`): personal accounts, student debt, mortgages,
  pensions and retirement provision, insurances (income protection, life,
  disability, indemnity-adjacent personal cover), and net-worth tracking.
- Career-transition modelling: associate→owner, practice purchase, partnership
  buy-in, sale, and retirement decumulation — the financial seams that map onto
  the professional lifecycle stages.
- Read-only by design: information and organisation, with clear signposting to
  qualified advisers. The platform does not give regulated financial advice.

### Family, relationships, and caregiving

- Private household and family records the dentist chooses to keep: dependants,
  caregiving responsibilities, emergency contacts, and the documents a family
  needs in a crisis.
- Coordination with the dentist's own continuity plan: who in their personal life
  is a nominated continuity officer or holds authority on incapacity, and how that
  links to professional continuity (`docs/estate-succession-continuity.md`).
- Work-life sustainability: leave, sabbaticals, parental and carer's leave, and
  career-break planning treated as first-class life events, not gaps to hide.

### Personal legal, identity, and life admin

- Personal legal and identity documents: wills, powers of attorney, advance
  directives, property, citizenship/visa and right-to-work evidence, and personal
  contracts — stored as evidence with retention awareness (`docs/data-model.md`).
- Personal credential and membership claims that are not professional licences —
  modelled with the same claim-plus-evidence rigour where useful
  (`docs/degree-skill-truth-management.md`) but kept in the personal tenant.
- Everyday life admin: personal tasks, calendar, contacts, and document vault that
  share the platform's foundations but live in the private context.

### Learning, identity, and life beyond dentistry

- Personal knowledge management and lifelong learning that is not CPD/CE: a place
  for the person's own curiosity, projects, and interests.
- Space for the dentist's identity outside the chair — hobbies, community, faith,
  volunteering, and the retiree's "second act" — so the platform still serves them
  when they are no longer billing (`docs/lifecycle-journey.md`, Stage 7–8).

### Personal digital estate

- The dentist's *personal* digital assets and accounts, distinct from professional
  and patient records, with their own continuity and handover plan so a family —
  not a regulator — can recover what is personal when the dentist cannot act
  (`docs/estate-succession-continuity.md`).

## Boundaries and anti-goals

To stay world-class and trustworthy, this dimension explicitly does **not**:

- become a medical, psychiatric, financial-advice, or legal-advice product;
- let an employer, partner, insurer, regulator, or platform operator see a
  dentist's personal life by default;
- mine, profile, sell, or train models on a dentist's personal data;
- treat wellbeing or crisis signposting as a substitute for qualified human help;
- create personal records whose main effect is to expose the dentist to
  professional, employment, or insurance jeopardy.

## How this connects to the rest of the charter

- Tenancy and isolation: the personal vault is a tenant, equal in rigour to a
  practice or association tenant (`docs/architecture.md`).
- Sovereignty: personal data is exportable and the dentist can leave with it
  (`docs/data-sovereignty-and-licensing.md`).
- Continuity: personal incapacity and death route through the same continuity
  authorities as professional records, with personal vs. professional custody
  kept distinct (`docs/estate-succession-continuity.md`).
- Privacy and audit: personal special-category data gets the strongest policy,
  consent, and audit treatment (`docs/security-privacy-threat-model.md`,
  `docs/compliance-model.md`).
- AI: assistants help the person retrieve, organise, draft, and remember — under
  human approval and without surveillance (`docs/ai-competition-human-loop.md`).

## Verification

This dimension is honoured when the platform can demonstrate:

- a personal tenant whose data is provably invisible to professional, employer,
  and association tenants unless the dentist explicitly and revocably shares it;
- every personal↔professional data movement is an audited, authority-bearing
  context switch, with tests proving no accidental leakage across the boundary;
- wellbeing and crisis features signpost qualified human help and carry no
  diagnostic or advisory claim;
- personal data is included in the dentist's export bundle and in their continuity
  plan, with personal and professional custody clearly separated;
- no analytics, benchmarking, profiling, or model training touches personal-life
  data without specific, audited, revocable consent.

## Rule

Serve the person, not only the practitioner. If a capability would expose a
dentist's private life to their professional world by default, pretend to treat or
advise where it can only support, or fail to travel with the person through career
breaks, retirement, incapacity, and death, it is not finished — and where it
touches the dentist's health, finances, or family, getting the boundary wrong is a
trust hazard, not a feature gap.
