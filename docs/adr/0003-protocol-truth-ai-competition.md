# ADR 0003: Protocol-Native Truth and AI Competition Architecture

## Status

Accepted

## Context

The platform must cross many boundaries: personal vault, practice, association, study club, university, CPD/CE provider, regulator, insurer, accountant, patient, government, AI model, and future estate executor.

The user also wants the whole software stack to behave as an AI competition: agents continuously propose better actions, challenge each other, and ask humans to approve consequential changes.

## Decision

full-stack-dentist will treat three subsystems as load-bearing platform primitives:

1. Interchange protocol gateway
   - Every import/export/event/action crossing a boundary uses explicit schemas, versions, authority, policy decisions, and audit events.
   - Adapters map to standards such as FHIR, DICOM, OpenAPI, AsyncAPI, CloudEvents, Verifiable Credentials, Open Badges, CLR, xAPI, and cmi5 where appropriate.

2. Claim/evidence/truth registry
   - Degrees, skills, licences, CPD/CE, memberships, roles, insurance, and authority are claims backed by evidence, issuers, verification state, expiry, revocation, and audit.
   - Documents support truth; they are not truth by themselves.

3. AI competition and human-approval substrate
   - Scouts, workers, critics, judges, executors, and auditors are separate roles.
   - AI may propose, extract, critique, rank, and draft.
   - Consequential actions require human approval and deterministic/narrow execution.

## Consequences

Positive:

- avoids SaaS lock-in
- supports institutional trust and credential verification
- makes AI safer by separating proposal from execution
- preserves dissent and evidence for audit
- creates reusable foundations for personal, practice, association, study-club, and clinical workflows

Negative:

- raises early architecture complexity
- requires disciplined schemas before flashy features
- needs approval UX and audit design early
- demands tests for protocol round-trips, claim states, and AI approval gates

## Verification

Before this architecture is considered implemented, tests must prove:

- an interchange envelope validates and round-trips
- a credential-style claim can be imported, parsed, human-reviewed, exported, and audited
- AI extraction is distinguishable from human verification
- competing candidates and critic findings are persisted
- a consequential write is blocked until approved
- executor records an execution result and audit receipt
