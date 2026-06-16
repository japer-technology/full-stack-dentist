# Compliance Model

## Intent

This project must support multiple countries without pretending compliance can be solved once in code. Compliance is modelled as configurable policy, documented operational process, and jurisdiction-specific review.

## Compliance is not a checkbox

For this product, compliance involves:

- software architecture
- hosting and data residency
- identity and access controls
- retention and deletion
- consent and legal basis
- audit logs
- breach response
- vendor management
- clinical safety and regulatory classification
- financial/tax recordkeeping
- staff/employment obligations
- user training and operating procedures

## Policy-pack model

Each jurisdiction gets a policy pack:

```text
policies/<jurisdiction>/
  README.md
  privacy.yaml
  health-records.yaml
  retention.yaml
  consent.yaml
  breach-response.yaml
  tax-accounting.yaml
  clinical-safety.yaml
  feature-flags.yaml
```

Policy packs should be data, not scattered conditionals.

## Example jurisdiction dimensions

- Country
- State/province/territory
- Practice type
- Individual vs company
- Public vs private healthcare context
- Adult vs child patient records
- Specialist vs general dental practice
- Data residency requirements
- Retention period
- Breach notification timelines
- Required audit evidence
- Clinical-device classification risk

## Regulated domains

### Privacy and health records

Examples to model:

- GDPR / UK GDPR
- HIPAA and state privacy laws
- PIPEDA and provincial health privacy laws
- Australian Privacy Act and state health-record laws
- New Zealand Privacy Act and health information rules
- Local dental-board recordkeeping rules

### Clinical safety

Features must be classified:

- administrative only
- recordkeeping only
- clinical workflow support
- clinical decision support
- diagnostic/therapeutic recommendation
- medical-device-like function

Anything above recordkeeping requires explicit safety review.

### Finance and tax

Finance features must avoid pretending to replace regulated accountants or payroll providers before proper jurisdiction-specific validation.

Model:

- chart of accounts mapping
- invoice/tax requirements
- payroll-export requirements
- audit trail
- document retention
- export to accountant

### Education and licensing

Track:

- university course evidence
- continuing professional development / continuing education
- licence/registration renewals
- board correspondence
- indemnity insurance
- professional memberships
- supervision/mentorship evidence

## Consent and authority registry

Every sensitive action should be explainable by one of:

- direct user authority
- patient consent
- treatment relationship
- legal obligation
- contract
- legitimate interest where lawful
- emergency/break-glass
- executor/estate authority
- court/regulator request

## Records lifecycle

Each record needs:

- owner/controller
- subject
- classification
- jurisdiction
- purpose
- created_at
- retention_rule
- deletion eligibility
- legal hold status
- export format
- audit requirements

## Launch gates

A module cannot be marketed for regulated use until it has:

1. documented scope
2. threat model
3. privacy impact assessment
4. access-control tests
5. audit-log tests
6. export tests
7. retention/deletion tests
8. backup/restore tests
9. jurisdiction review
10. user-facing limitation statement

## Compliance anti-patterns

Avoid:

- “HIPAA/GDPR compliant” claims without scope
- hard-coded country assumptions
- AI features with hidden data transfer
- delete buttons that ignore retention law
- admin panels without audit logs
- shared production/staging data
- vendor integrations without data-processing review
- “one global consent form”

## Rule

Compliance belongs in product design, data models, operational runbooks, and jurisdiction policy packs — not in marketing copy.
