# Observability and Operations

## Purpose

The architecture lists reliability expectations but does not say how the platform is run, watched, and recovered. This document defines the operational discipline for full-stack-dentist across its deployment modes, so that a system holding a lifetime of regulated data can be operated safely and recovered when things go wrong.

Operations must respect the same boundaries as the product: data classification, tenant isolation, least privilege, and audit apply to telemetry and tooling, not only to application features.

## Operational principles

- Observability is in scope, telemetry is sensitive. Logs, metrics, and traces can leak regulated data; they are classified, access-controlled, and retention-bound like any other record.
- Recoverable beats clever. Boring, deterministic, restorable operations win over sophisticated but unprovable ones.
- Test the recovery, not just the backup. An untested backup is a hope.
- Operate per deployment mode. Solo-local, private-practice, and regulated-cloud have different obligations (`docs/architecture.md`).
- Least-privilege operations. Operators, jobs, and integrations get the minimum access needed, fully audited.

## The three signals

- Logs — structured, correlation-ID-tagged, and scrubbed of regulated payloads. Distinct from the audit ledger: logs are for operating the system; audit events are evidence of power used (`docs/data-model.md`).
- Metrics — health, latency, error rates, saturation, queue depth, export/backup success, and security-relevant counters.
- Traces — request/correlation tracing across services for diagnosing failures without exposing sensitive content.

Audit logging is a product behaviour and is specified separately (`docs/security-privacy-threat-model.md`); it must never be conflated with operational logging or disabled for convenience.

## Health and SLOs

- Every service exposes health and readiness checks.
- Define service-level objectives for the load-bearing paths: authentication, policy decisions, audit write, document read, export, and backup.
- Alert on symptoms users feel and on trust-critical failures (audit pipeline down, backup failed, export errors, replication lag).
- Page humans only for actionable, trust-critical conditions; everything else is a ticket.

## Backup, recovery, and continuity

- Immutable, encrypted backups with a defined cadence per deployment mode.
- Point-in-time recovery where the datastore supports it.
- Independent backup of the audit ledger so it survives a compromise of the primary system.
- Documented Recovery Point Objective and Recovery Time Objective per deployment mode.
- Restore drills on a schedule, with results recorded; a backup that has not been test-restored is treated as untrusted.
- Recovery procedures coordinate with estate/continuity needs (`docs/estate-succession-continuity.md`).

## Incident response

- Documented runbooks for the predictable incidents: data exposure, ransomware, audit-pipeline failure, key loss, integration compromise, and prolonged outage.
- Severity classification that accounts for regulated-data impact, not just downtime.
- Breach handling follows jurisdiction policy packs and notification timelines (`docs/compliance-model.md`).
- Every significant incident produces a blameless post-incident review and at least one regression test or control change (`docs/quality-and-testing-strategy.md`).

## Change and release operations

- Infrastructure as code; environments are reproducible from source (`docs/data-sovereignty-and-licensing.md`).
- Deterministic, reviewed migrations with rollback or forward-fix plans.
- Secrets managed by a secrets manager, never committed, rotated on schedule and on compromise.
- Progressive rollout with the ability to halt and revert; trust-property test failures block release.

## Operational access and audit

- Privileged operator actions require MFA and are audited at high severity.
- Break-glass for production access mirrors the application break-glass workflow: declared purpose, time limit, audit, notification, review.
- Access to telemetry containing regulated data is least-privilege and reviewed periodically.

## Deployment-mode obligations

- Solo local — self-hosted backup guidance, local encryption, simple restore instructions; no mandatory cloud dependency.
- Private practice — central audit, monitored backups, incident runbooks, periodic access review.
- Regulated cloud — tenant isolation monitoring, data-residency controls, disaster-recovery drills, penetration testing, full IaC and secrets management.

## Verification

Before a deployment mode is considered operable, demonstrate:

- health checks, structured logs, metrics, and traces exist and exclude regulated payloads;
- a test-restore from backup succeeds within the stated RTO/RPO;
- the audit ledger has an independent, tamper-evident backup;
- incident runbooks exist for the predictable incident classes;
- privileged and break-glass operations are audited.

## Rule

A system that cannot be observed, recovered, and audited in operation is not production-ready for sensitive data — no matter how complete its features look.
