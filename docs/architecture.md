# Architecture

## North star

full-stack-dentist is a modular, policy-driven, local-first-capable platform for dental life and dental business operations.

It must handle unusually sensitive cross-domain data:

- personal data
- professional credential data
- clinical patient data
- dental imaging and documents
- financial and tax data
- employment and payroll data
- marketing and website data
- association, study-club, committee, election, event, advocacy, and membership data
- estate and continuity data

The architecture must assume compromise, jurisdictional variation, and long retention periods.

## System shape

```text
clients
  web app
  mobile app
  desktop/local app
  admin console
  clinician cockpit
  patient/third-party portal

edge
  API gateway
  auth boundary
  rate limiting
  tenant routing
  request signing

core platform
  identity and access
  consent and authority
  audit ledger
  policy engine
  event bus
  document vault
  notification service
  export service
  AI orchestration service

domain modules
  student
  credentials and CPD
  personal productivity
  patient CRM
  clinical records
  treatment planning
  imaging
  lab/referrals
  prescribing hooks
  practice operations
  finance and accounting
  inventory and assets
  marketing and reputation
  association and study-club management
  compliance and risk
  analytics
  succession and estate

data layer
  operational database
  append-only audit/event store
  object/document storage
  search index
  vector index for user-approved AI retrieval
  backup and archive storage

policy packs
  country/state/territory rules
  retention schedules
  privacy bases
  consent templates
  breach response playbooks
  tax/accounting mappings
```

## Deployment modes

### Solo local

For students, associates, retired dentists, and privacy-focused users.

- Runs on a single machine or private NAS.
- Encrypted local database.
- Manual or self-hosted backup.
- No cloud dependency for core vault, CPD, tasks, documents, or exports.

### Private practice server

For a single clinic or small group.

- Self-hosted or managed private deployment.
- Central identity and audit logs.
- Encrypted object storage.
- Role-based access and delegated authority.
- Backups, monitoring, incident response, and export tooling.

### Regulated cloud deployment

For multi-site groups and managed service providers.

- Tenant isolation.
- Strong logging and monitoring.
- Infrastructure as code.
- Secrets management.
- Disaster recovery.
- Data residency controls.

## Bounded contexts

### Identity and authority

Owns users, roles, groups, sessions, MFA, delegated access, emergency access, and estate/continuity authority.

### Policy engine

Owns jurisdiction, retention, consent, purpose, access rules, breach workflow, and feature availability.

### Audit ledger

Owns append-only evidence of material events. Every sensitive read/write/delete/export/admin action should be recorded.

### Document vault

Owns encrypted file storage, metadata, labels, retention, legal hold, OCR index, provenance, and export.

### Clinical module

Owns patient, encounter, charting, treatment-plan, consent, referral, imaging-link, and clinical-note data. This module is the highest-risk domain and must be isolated from general productivity features.

### Business module

Owns practice operations, suppliers, inventory, assets, payroll integrations, accounting exports, and non-clinical reporting.

### Association and study-club module

Owns organised-dentistry workflows: association tenants, member records, membership classes, renewals, chapters, study clubs, committees, officer roles, elections, motions, minutes, CPD/CE events, certificates, sponsors, advocacy campaigns, complaints/ethics workflows, and member communications.

This module must not collapse association data into practice data. A dentist can be an individual user, practice owner, association member, committee chair, event speaker, and association administrator at the same time. Those roles require explicit context switching, separate permissions, and separate audit trails.

### AI module

Owns model routing, prompts, retrieval permissions, AI audit logs, human-review gates, and safety boundaries. AI never receives data unless the policy engine authorises purpose, scope, and minimum necessary context.

## Data classification

Every object must have a classification:

- public
- internal
- confidential personal
- confidential business
- regulated health
- regulated financial
- legal/privileged
- credential/licensing
- association/member governance
- estate/continuity

Access, retention, export, deletion, AI use, and logging depend on classification.

## Access model

Use layered controls:

1. Tenant isolation
2. User identity
3. Role-based access control
4. Attribute-based policy checks
5. Purpose-of-use checks
6. Consent/authority checks
7. Break-glass workflow for emergencies
8. Immutable audit logging

## AI architecture

AI must be useful without becoming a liability.

Allowed early:

- summarise user-selected documents
- draft emails, policies, checklists, study notes
- explain records to authorised users
- retrieve from explicitly indexed private knowledge
- produce non-clinical operational insights

Disallowed until formal safety/regulatory work exists:

- autonomous diagnosis
- autonomous prescribing
- irreversible clinical actions
- hidden model-to-model data sharing
- training external models on private data by default
- unreviewed clinical decision support

## Interoperability

Use adapters, not hard-coded vendor dependence.

Potential standards and mappings:

- HL7 FHIR for health data exchange where appropriate
- DICOM for imaging metadata/workflows
- SNOMED CT, ICD, CDT, LOINC, RxNorm or national equivalents where licensing and jurisdiction permit
- OAuth2/OIDC/SAML for identity integration
- OpenAPI and AsyncAPI for service contracts
- JSON Schema for internal data contracts

## Reliability expectations

Minimum platform capabilities:

- deterministic migrations
- backup and restore drills
- point-in-time recovery where supported
- tamper-evident audit trail
- health checks
- structured logs
- metrics and traces
- data export tests
- deletion/retention tests
- security regression tests

## Monorepo target layout

```text
apps/
  web/
  mobile/
  desktop/
services/
  api/
  worker/
  policy/
  audit/
  export/
packages/
  schemas/
  sdk/
  crypto/
  ui/
modules/
  identity/
  vault/
  student/
  credentials/
  association/
  study-club/
  clinical/
  business/
  finance/
  compliance/
  ai/
policies/
  au/
  ca/
  eu/
  nz/
  uk/
  us/
infra/
  docker/
  terraform/
  kubernetes/
  monitoring/
docs/
  architecture.md
  security-privacy-threat-model.md
  compliance-model.md
  data-model.md
  roadmap.md
```

## First architectural decision

Do not start with patient charting. Start with identity, vault, audit, policy, and export. Those are the load-bearing beams every later module needs.
