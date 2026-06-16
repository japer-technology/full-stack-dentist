# ADR 0002: Organised Dentistry Is a First-Class Domain

## Status

Accepted

## Context

Dentists organise through associations, specialist societies, study clubs, buying groups, alumni networks, charities, advocacy bodies, committees, and CPD/CE providers. These organisations need software that overlaps with but is not the same as individual dentist or practice software.

Association and study-club data can include member records, dues, CPD/CE evidence, committees, conflicts, confidential peer consultation, ethics/complaints matters, elections, advocacy campaigns, sponsors, donations, and governance records.

## Decision

full-stack-dentist will model organised dentistry as a first-class domain with association and study-club modules. These modules reuse the trust substrate but maintain separate tenant context, permissions, and audit trails from personal and practice data.

## Consequences

Positive:

- covers the real collective workflows dentists need
- avoids forcing associations into practice-management abstractions
- enables CPD/CE, meetings, committees, events, memberships, and advocacy from the same platform foundation
- improves data separation for confidential governance matters

Negative:

- increases domain scope
- adds governance/election/complaints/security complexity
- requires policy packs for association, charity, lobbying, CPD/CE, and non-profit obligations

## Verification

Before association/study-club modules are production-ready, tests must prove:

- association tenant data does not leak into practice tenant context
- committee-only records are inaccessible to ordinary members
- member directory visibility preferences are enforced
- CPD/CE certificates are generated only from verified attendance
- bulk member export and communications are audited
- complaint/ethics/election records use stronger compartment controls
