# Association Management

## Why this belongs in scope

Dentists do not only operate as individuals or practices. They organise through professional bodies, study clubs, buying groups, alumni networks, specialist societies, unions, committees, charities, local branches, research collaboratives, and advocacy organisations.

Those organisations need software too, and they often handle sensitive mixtures of professional, financial, educational, political, disciplinary, and member data. full-stack-dentist must treat organised dentistry as a first-class domain.

## Target organisations

- national dental associations
- state/provincial/territorial branches
- specialist societies
- study clubs
- continuing-education providers
- dental schools and alumni groups
- group purchasing organisations
- peer-review and quality committees
- ethics and complaints committees
- charitable dental programs
- advocacy and lobbying groups
- research networks
- mutual-aid and benevolent funds
- retired-dentist associations

## Core capabilities

### Membership

- member profiles
- membership classes
- student, associate, full, retired, honorary, affiliate, corporate, and international memberships
- applications and approvals
- renewals
- dues billing
- hardship/waiver handling
- member status history
- chapter/branch assignment
- specialist-interest groups
- directory visibility controls

### Governance

- board and committee registers
- terms, offices, eligibility, conflicts of interest
- nominations and elections
- voting, proxies, quorum, resolutions
- agendas, minutes, action items
- policy register
- constitution/bylaw document control
- disclosures and recusals
- delegated authority

### Events and education

- conferences
- webinars
- hands-on courses
- study-club meetings
- attendance tracking
- CPD/CE credit issuance
- certificates
- speaker management
- sponsor/exhibitor management
- ticketing and refunds
- abstract/poster submissions

### Advocacy and communications

- campaigns
- member surveys
- consultations
- submissions to regulators/government
- newsletters
- segmented email/SMS/push
- public website content
- press releases
- media contacts
- issue tracking

### Finance and commercial operations

- dues
- invoices
- sponsorships
- donations
- grants
- event revenue
- chapter revenue sharing
- budget and approvals
- expense claims
- accounting exports
- tax/reporting evidence

### Professional services

- member helpdesk
- legal/indemnity referral workflows
- mentoring and supervision matching
- peer consultation groups
- classified ads/jobs
- supplier discounts
- group purchasing
- practice transition marketplace

### Compliance and risk

- privacy and consent
- conflicts of interest
- complaints/ethics workflows
- disciplinary boundaries
- whistleblower/confidential reports
- charitable/fundraising compliance
- lobbying-register evidence
- records retention
- breach response

## Data boundaries

Association data is not the same as practice data.

A dentist may have:

- personal vault
- practice tenant
- association member profile
- committee role
- association admin role
- event speaker profile
- public directory listing

These must be separate contexts connected by explicit authority, not silently merged.

## Required access controls

- member self-service access
- staff/admin access
- board access
- committee-scoped access
- chapter/branch-scoped access
- finance-scoped access
- confidential complaints/ethics access
- election administrator access
- auditor/regulator export access

Sensitive association workflows such as complaints, elections, conflicts, lobbying, and disciplinary matters require stronger audit and separation than ordinary membership records.

## Association-specific records

- membership application
- membership invoice
- renewal decision
- committee appointment
- conflict disclosure
- meeting agenda
- meeting minutes
- motion/resolution
- vote/election ballot
- CPD event
- attendance evidence
- certificate
- complaint/ethics matter
- advocacy campaign
- regulator submission
- sponsor contract
- grant agreement
- donation record
- member directory listing

## Integration stance

Association management should reuse the trust substrate:

- identity
- policy
- audit
- document vault
- export
- notifications
- payments/accounting adapters
- AI drafting/retrieval with strict context controls

It should not build a second CRM, second document store, second audit log, or second permission system.

## AI use cases

Allowed early:

- draft meeting agendas and minutes
- summarise consultation responses
- prepare member-newsletter drafts
- classify incoming member requests
- generate CPD certificates from verified attendance
- search bylaws/policies for authorised users

High-risk or restricted:

- ethics/complaints recommendations
- election outcome handling
- lobbying or political targeting
- legal advice to members
- decisions affecting membership rights

## MVP for association management

First useful association module:

1. association tenant type
2. member directory with visibility controls
3. membership classes and renewals
4. committees and officer roles
5. event/CPD tracker
6. document vault for bylaws/minutes/policies
7. invoices/accounting export
8. member communications
9. audit log and export bundle

## Rule

Organised dentistry is a separate institutional layer between the individual dentist, the practice, the regulator, and the public. The platform must model that layer explicitly.
