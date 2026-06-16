# Standards and Assumptions

## External references

These are design references to evaluate against during implementation.

Security and privacy:

- NIST Cybersecurity Framework 2.0
- NIST Privacy Framework
- OWASP Application Security Verification Standard 5.0.0
- ISO/IEC 27001 information-security management principles
- ISO/IEC 27701 privacy-information management principles

Healthcare and dental interoperability:

- HL7 FHIR R5 where appropriate for health-data exchange
- DICOM where appropriate for imaging workflows
- SNOMED CT, ICD, CDT, LOINC, RxNorm, and local equivalents where licensing and jurisdiction permit

Identity and API design:

- OAuth 2.0
- OpenID Connect
- SAML where enterprise integrations require it
- OpenAPI
- AsyncAPI
- CloudEvents
- JSON Schema

Credentials and learning records:

- W3C Verifiable Credentials 2.0
- W3C Decentralized Identifiers where appropriate
- 1EdTech Open Badges 3.0
- 1EdTech Comprehensive Learner Record 2.0
- xAPI / IEEE 9274.1.1-2023
- cmi5 where LMS launch/runtime interoperability is needed

## Source checks performed

On 2026-06-16, web search confirmed current public references for:

- NIST CSF 2.0 official page
- NIST Privacy Framework official page
- OWASP ASVS official project page showing ASVS 5.0.0 as the latest stable release
- HL7 FHIR official specification page showing FHIR R5
- ISO pages for ISO/IEC 27701
- W3C Verifiable Credentials 2.0 and DID pages
- 1EdTech Open Badges 3.0 and CLR 2.0 pages
- xAPI / IEEE 9274.1.1-2023 references
- CloudEvents, AsyncAPI, and OpenAPI official pages

## Assumptions

- The project starts as a monorepo.
- It must support local-first operation.
- It must not require a third-party SaaS account for core personal/professional use.
- It will eventually need multiple deployment modes.
- It will eventually touch regulated health data, but should not begin with regulated clinical automation.
- Jurisdiction policy is data/configuration, not scattered conditionals.
- Exportability is a core feature, not an afterthought.
- AI is useful but high-risk; default stance is deny, minimise, audit, review.
- Data interchange is protocol-native: schema, version, authority, policy decision, and audit event travel with data.
- Degrees, skills, licences, memberships, authority, and CPD/CE are claims backed by evidence, issuers, verification state, expiry, revocation, and audit.
- The AI architecture is competitive and human-approved: multiple agents propose/criticise/rank, but narrow executors act only after approval for consequential changes.

## Open questions

- Primary first country: Australia, UK, US, NZ, Canada, EU, or another?
- Preferred initial stack: TypeScript, Python, Rust, or mixed?
- First target: local desktop, web app, or server-first?
- Licensing model: open source, source-available, open-core, or private?
- Intended first user: student, solo dentist, or practice owner?
- Whether clinical recordkeeping is in MVP 1 or deliberately deferred.

## Rule

When in doubt, choose the design that maximises data sovereignty, auditability, exportability, and jurisdictional adaptability.
