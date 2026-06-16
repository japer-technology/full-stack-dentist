# Data Model

## Canonical idea

All domains share a small set of platform primitives:

- tenant
- person
- organisation
- identity
- role
- authority
- consent
- record
- document
- event
- policy
- task
- communication
- financial transaction
- clinical encounter
- association membership
- study club
- committee
- event
- election/vote
- export package

Do not let each feature invent its own identity, document, audit, or permission system.

## Universal metadata

Every sensitive entity should carry:

```yaml
id: globally unique identifier
tenant_id: owning tenant/practice/user space
classification: data classification
jurisdiction: relevant jurisdiction
subject_refs: people or organisations the record concerns
owner_ref: data owner/controller
created_at: timestamp
created_by: actor
updated_at: timestamp
updated_by: actor
retention_rule_id: policy reference
legal_hold: boolean
source: manual/import/integration/ai/generated/system
provenance: where it came from
version: optimistic concurrency version
audit_required: boolean
```

## Person model

A person can be:

- dentist
- student
- patient
- staff member
- referrer
- supplier contact
- emergency contact
- executor
- guardian
- family member

Avoid duplicating humans across modules. A person has context-specific roles.

## Clinical model

Early canonical entities:

- patient profile
- medical/dental history
- allergy/intolerance
- medication
- encounter
- clinical note
- odontogram/charting record
- diagnosis/problem
- treatment plan
- consent record
- procedure record
- referral
- lab case
- imaging study reference
- prescription reference
- recall/maintenance plan

Use FHIR mappings where appropriate, but do not force every internal object to be raw FHIR. Maintain adapter boundaries.

## Dental-specific model considerations

Support multiple notation systems:

- FDI two-digit notation
- Universal numbering system
- Palmer notation
- deciduous/primary teeth
- surfaces and quadrants
- periodontal charting
- occlusion and orthodontic notes
- implant/prosthodontic state

Represent dental observations as structured data plus human narrative. Do not make images or PDFs the only source of truth.

## Document model

Documents need:

- file object
- metadata
- classification
- retention label
- subject links
- OCR text where appropriate
- checksum
- encryption envelope
- access log
- export path
- legal hold

Examples:

- licence certificate
- CPD evidence
- indemnity insurance
- tax invoice
- lab slip
- consent form
- radiograph report
- referral letter
- employment contract
- incident report
- estate instruction

## Association and study-club model

Organised dentistry requires institutional records separate from practice records.

Canonical entities:

- association tenant
- chapter/branch
- study club
- member profile
- membership class
- membership application
- membership term
- renewal
- dues invoice
- committee
- committee appointment
- officer role
- conflict disclosure
- meeting
- agenda
- minutes
- motion/resolution
- vote/election
- proxy
- CPD/CE event
- attendance record
- certificate
- speaker profile
- sponsor/exhibitor
- member communication
- survey/consultation response
- advocacy campaign
- complaint/ethics matter
- grant/donation

Context matters. The same dentist may appear as a private person, practice owner, member, chapter officer, study-club convener, speaker, voter, donor, complainant, or respondent. Access must be scoped to the context, not the person alone.

Study clubs need lightweight but serious workflows:

- meeting calendar
- case-presentation register
- attendance and CPD/CE credits
- topic library
- speaker and host rotation
- shared resources
- member dues
- sponsorship disclosure
- peer-consultation confidentiality
- action items
- local bylaws/rules

Complaints, ethics, peer review, elections, conflicts, and disciplinary-adjacent records require stronger separation and audit than ordinary member-directory records.

## Audit event model

Audit events are immutable business facts, not debug logs.

Examples:

- user signed in
- MFA changed
- patient record viewed
- document exported
- AI summary generated
- consent revoked
- break-glass access used
- policy changed
- backup restored
- record placed on legal hold

## Policy model

Policies should answer:

- who can access this?
- for what purpose?
- in which jurisdiction?
- with whose authority?
- for how long is it retained?
- can it be exported?
- can it be deleted?
- can AI process it?
- must access be audited?

## AI data model

AI records need their own evidence trail:

- model/provider
- input classification
- prompt template version
- retrieval sources
- redaction applied
- output
- reviewer
- acceptance/rejection
- downstream action taken

AI output should never overwrite source-of-truth records without human approval.

## Export model

Exports are first-class:

- scope
- requester
- authority
- timestamp
- format
- checksum manifest
- included records
- excluded records and reasons
- encryption status
- delivery method
- audit event IDs

## Deletion and retention

Deletion is not one thing.

Possible states:

- active
- archived
- retained by law
- legal hold
- soft deleted
- anonymised
- cryptographically erased
- physically purged

Policy decides which transitions are legal.

## Rule

Every data model must support export, audit, access control, retention, and jurisdiction before it is allowed to hold sensitive records.
