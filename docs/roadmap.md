# Roadmap

## Strategy

Do not begin by cloning every dental SaaS. Build the trust substrate first, then modules.

Order of operations:

1. Identity
2. Policy
3. Audit
4. Vault
5. Export
6. Interchange protocol gateway
7. Degree, skill, and truth management
8. AI competition and human approval substrate
9. Personal/professional cockpit
10. Practice operations
11. Association and study-club management
12. Clinical records
13. Regulated clinical workflows
14. Advanced AI

## Phase 0: Product constitution

Deliverables:

- product charter
- architecture document
- security/privacy threat model
- compliance model
- data model
- initial ADRs
- contribution rules

Exit criteria:

- repo explains what it is and what it refuses to be
- risk boundaries are explicit
- first MVP scope is defensible

## Phase 1: Trust substrate MVP

Build:

- local app shell or web app shell
- encrypted local vault
- identity model
- role model
- jurisdiction profile
- audit event model
- document import
- export bundle

Validation:

- create user
- add credentials
- upload CPD evidence
- export all records
- restore from export
- verify audit events

## Phase 2: Protocol, truth, and AI approval substrate

Build:

- interchange envelope schema
- protocol registry skeleton
- claim/evidence/truth registry
- degree/licence/CPD/CE/skill claim types
- human verification queue
- AI task/candidate/critic/judge/approval records
- deterministic executor boundary
- approval audit receipts

Validation:

- import/export one verifiable-style credential envelope
- create a degree claim from evidence
- mark AI extraction separate from human verification
- run two competing AI candidates through critic/judge records
- require human approval before executor writes a consequential change
- export claim/evidence/audit bundle

## Phase 3: Dentist cockpit

Build:

- dashboard
- tasks
- contacts
- calendar integration
- credentials/licence register
- CPD/CE tracker
- renewal reminders
- policy-driven document retention labels

Validation:

- track licence renewal
- attach evidence
- produce regulator-ready export bundle

## Phase 4: Practice operating system

Build:

- organisation/practice model
- staff and delegated authority
- supplier register
- asset and inventory register
- incident/risk register
- policy/document templates
- accounting export adapters

Validation:

- invite staff role
- restrict access
- create incident
- export compliance pack

## Phase 5: Association and study-club management

Build:

- association tenant type
- study-club tenant type
- member directory with privacy/visibility controls
- membership classes and renewals
- dues/invoice export
- committees and officer roles
- meetings, agendas, minutes, motions, actions
- event and CPD/CE attendance tracking
- certificates
- sponsors and disclosures
- member communications
- basic surveys/consultations

Validation:

- create association tenant
- create study club
- enrol member
- restrict committee-only documents
- issue CPD/CE certificate from attendance
- export member register and event evidence
- prove association data does not leak into practice tenant context

## Phase 6: Patient relationship and records foundation

Build:

- patient identity
- consent and authority
- contact preferences
- referral records
- clinical document vault
- basic encounter note
- treatment-plan draft object
- audit-heavy sensitive views

Validation:

- prove tenant isolation
- prove sensitive-read audit
- export patient record
- apply retention policy

## Phase 7: Dental charting and imaging references

Build:

- tooth notation support
- odontogram data structure
- periodontal charting model
- imaging-study references
- procedure/progress notes
- lab-case workflow

Validation:

- convert notation systems
- record chart state over time
- attach image references
- export structured and human-readable records

## Phase 8: AI assistants

Build only after policy/audit/vault exist:

- study assistant
- document summariser
- policy drafter
- checklist generator
- patient-message draft assistant
- operations analytics assistant

Clinical AI remains limited until safety/regulatory work is complete.

Validation:

- AI input classification gate
- redaction tests
- retrieval-source traceability
- output review workflow
- AI audit log

## Phase 9: Multi-country policy packs

Initial candidates:

- Australia
- New Zealand
- United Kingdom
- European Union baseline
- United States baseline
- Canada baseline

Each pack needs local review before regulated claims.

## Phase 10: Ecosystem and integrations

Potential adapters:

- email/calendar/contact providers
- accounting systems
- payment processors
- dental imaging systems
- lab portals
- referral networks
- government/regulator portals where lawful
- FHIR endpoints

Adapters must be optional and scoped. The core cannot depend on vendor lock-in.

## Never list

Do not build these early:

- autonomous diagnosis
- autonomous prescribing
- uncontrolled model training on user data
- billing claims without jurisdiction-specific validation
- medical-device-like functions without regulatory plan
- patient portal before access/audit/consent is mature

## First concrete engineering milestone

Create the trust-substrate skeleton:

```text
packages/schemas
modules/identity
modules/policy
modules/audit
modules/vault
modules/export
apps/web
```

With tests for:

- tenant isolation
- audit event creation
- document classification
- export manifest creation
- policy denial by default
