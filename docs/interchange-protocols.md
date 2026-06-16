# Data Interchange Protocols

## Purpose

full-stack-dentist must not become another data prison. The platform should be a protocol-native system that can import, export, verify, sync, and delegate across personal, practice, association, education, regulatory, clinical, financial, and AI-agent boundaries.

The rule: internal models may be opinionated, but external interchange must be explicit, versioned, documented, testable, and reversible where lawful.

## Interchange layers

### 1. Identity and authority

Use standards where practical:

- OpenID Connect for user authentication
- OAuth 2.0 for delegated access
- SAML for enterprise/association integrations where needed
- W3C Decentralized Identifiers where decentralised credential workflows are useful
- W3C Verifiable Credentials 2.0 for cryptographically verifiable assertions

Use cases:

- dentist proves identity to a study club
- association issues membership credential
- university issues degree credential
- CPD provider issues verifiable attendance
- practice grants accountant access
- executor proves authority after death/incapacity

### 2. Health and dental data

Use adapter boundaries:

- HL7 FHIR for healthcare exchange where appropriate
- DICOM for dental imaging workflows where appropriate
- national e-health APIs where jurisdiction permits
- coding systems such as SNOMED CT, ICD, CDT, LOINC, RxNorm, and local equivalents where licensing permits

Internal objects should not blindly be raw FHIR. The platform owns its canonical dental model and maps to external standards through tested adapters.

### 3. Learning, degree, CPD/CE, and skills data

Use education credential standards:

- W3C Verifiable Credentials 2.0
- 1EdTech Open Badges 3.0
- 1EdTech Comprehensive Learner Record 2.0
- xAPI / IEEE 9274.1.1-2023 for learning-experience statements
- cmi5 where LMS/content launch and runtime interoperability is needed

Use cases:

- degree verification
- licence and registration evidence
- CPD/CE certificates
- micro-credentials
- competency maps
- specialist training records
- study-club attendance
- practical skill sign-offs
- mentorship/supervision evidence

### 4. Business, finance, and tax data

Prefer export and adapter patterns:

- CSV/JSON/Parquet for neutral tabular exports
- jurisdiction-specific tax invoice formats
- accounting-system adapters
- payment-provider webhooks
- payroll export formats where lawful
- immutable export manifests with checksums

### 5. Association and governance data

Association management needs interchange for:

- membership rosters
- dues and payments
- event registrations
- CPD/CE attendance
- election/vote exports
- minutes, motions, and resolutions
- regulator submissions
- sponsor/exhibitor data
- chapter/branch reporting

Election, complaints, ethics, and disciplinary-adjacent exports require special policy checks.

### 6. Event-driven system integration

Use:

- OpenAPI for synchronous HTTP APIs
- AsyncAPI for asynchronous/event-driven APIs
- CloudEvents for common event envelopes
- WebSub/RSS/Atom where simple publication/notification is enough
- signed webhooks for external callbacks

Every emitted event should include enough metadata for routing, audit, replay, and policy checks.

### 7. AI-agent interchange

AI agents need structured exchange, not free-form privilege.

Required envelopes:

- task request
- context bundle
- evidence bundle
- proposed action
- critique/review
- human approval decision
- execution result
- audit receipt

Agents should exchange signed, typed claims and evidence references, not arbitrary private database access.

## Canonical interchange envelope

Every sensitive import/export/event should carry:

```yaml
id: unique event/export/import id
type: semantic type
schema_version: version
producer: service or external party
subject_refs: people/organisations/records concerned
tenant_id: tenant context
jurisdiction: jurisdiction context
classification: data classification
purpose: declared purpose
authority: consent/legal basis/delegation
created_at: timestamp
expires_at: optional timestamp
payload_ref: inline payload or content-addressed reference
hash: payload checksum
signature: optional producer signature
policy_decision_ref: policy engine decision id
audit_event_ref: audit event id
```

## Protocol registry

The repo should eventually maintain:

```text
schemas/interchange/
  envelope.schema.json
  health/
  education/
  finance/
  association/
  ai-agent/
protocols/
  README.md
  registry.yaml
  mappings/
    fhir/
    open-badges/
    clr/
    xapi/
    cloudevents/
```

## Verification requirements

For each adapter:

- schema validation test
- round-trip import/export test
- lossy-field report
- access-policy test
- retention-policy test
- audit-event test
- malformed-input test
- version migration test

## Rule

If data cannot cross a boundary safely, with schema, authority, audit, and export evidence, the boundary is not ready.
