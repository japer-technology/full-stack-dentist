# Security, Privacy, and Threat Model

## Security posture

Assume this platform will eventually contain health, financial, identity, employment, legal, credential, and estate data. Treat compromise as a catastrophic event, not a routine SaaS nuisance.

Design baseline:

- NIST Cybersecurity Framework 2.0 for governance, identify, protect, detect, respond, recover
- NIST Privacy Framework for privacy-risk management
- OWASP ASVS 5.0.0 for application-security verification
- ISO/IEC 27001-style control discipline
- ISO/IEC 27701-style privacy-management discipline

## Core assets

- Dentist identity and credentials
- Patient records
- Treatment plans and consent evidence
- Imaging and documents
- Prescriptions and medication-related data
- Financial and tax records
- Staff and payroll records
- Practice analytics
- AI prompts, outputs, embeddings, and retrieval logs
- Audit logs
- Backups and exports
- Estate/continuity authority records

## Threat actors

- External attacker
- Malicious insider
- Curious staff member
- Compromised vendor/integration
- Compromised dentist device
- Ransomware operator
- Nation-state or organised crime actor targeting healthcare
- Abusive partner/family member seeking personal/financial/health information
- Model/provider receiving excessive AI context
- Future maintainer accidentally weakening boundaries

## Critical threats

### Cross-tenant data exposure

Risk: one practice sees another practice’s data.

Controls:

- tenant ID in every sensitive table
- row-level security where possible
- tenant-scoped encryption keys where possible
- tenant boundary tests
- no admin bypass without break-glass audit

### Overbroad staff access

Risk: receptionist, assistant, associate, bookkeeper, or contractor sees data outside their purpose.

Controls:

- role-based and attribute-based access
- purpose-of-use prompts for sensitive records
- minimum necessary views
- audit every sensitive read
- periodic access review

### AI data leakage

Risk: private patient/business data sent to an external model or retained in prompts/vector stores without proper authority.

Controls:

- AI is denied by default for regulated data
- per-provider data-processing policy
- prompt/context minimisation
- redaction and classification gates
- user-visible AI audit log
- no training on private data by default
- local model option for sensitive tasks

### Ransomware and destructive deletion

Risk: attacker encrypts, deletes, corrupts, or exports records.

Controls:

- immutable backups
- point-in-time recovery
- export anomaly detection
- deletion delay for regulated records
- legal hold
- privileged-action MFA
- disaster-recovery drills

### Jurisdictional failure

Risk: one-country assumptions violate another country’s privacy, tax, medical-record, employment, or retention obligations.

Controls:

- jurisdiction policy packs
- data-residency labels
- configurable retention schedules
- consent/legal-basis registry
- country-specific feature flags
- local legal review before regulated launch

### Audit-log tampering

Risk: attacker or insider hides access or changes.

Controls:

- append-only audit store
- hash chaining or signed log batches
- independent backup of audit events
- restricted admin access
- alert on audit pipeline failure

### Unsafe clinical automation

Risk: software gives or appears to give clinical advice beyond validated scope.

Controls:

- feature risk classification
- human-in-the-loop requirements
- explicit clinical disclaimers where relevant
- formal validation before regulated decision support
- jurisdiction-specific regulatory review

## Privacy principles

- data minimisation
- purpose limitation
- consent and legal basis tracking
- retention by class and jurisdiction
- user access and export rights
- correction workflow
- deletion/anonymisation workflow where lawful
- privacy impact assessment for new high-risk modules

## Secure development requirements

Before production use:

- threat model each module
- secrets never committed
- dependency scanning
- static analysis
- security unit tests
- integration tests for tenant isolation
- migration tests
- backup/restore tests
- incident-response runbooks
- penetration test for regulated deployments

## Audit event minimum fields

- event_id
- timestamp
- actor_user_id
- tenant_id
- subject_type
- subject_id
- action
- purpose
- legal_basis_or_authority
- source_ip/device/session
- result
- before/after hash where applicable
- request_id/correlation_id

## Break-glass access

Emergency access must be possible but painful:

1. User declares emergency purpose.
2. MFA required.
3. Time-limited elevated access granted.
4. Every action audited at high severity.
5. Practice owner/privacy officer notified.
6. Post-event review required.

## Rule

If a feature cannot be audited, exported, access-controlled, and jurisdiction-scoped, it is not ready for sensitive data.
