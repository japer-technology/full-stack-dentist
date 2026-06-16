# AI Competition and Human-in-the-Loop Operating Model

## Purpose

The entire software stack should behave like a controlled competition of AI agents trying to improve outcomes, find risks, draft actions, and challenge each other — while humans retain authority over consequential decisions.

The system is not “one chatbot.” It is an AI tournament with rules, evidence, scoring, sandboxing, and approval gates.

## Core pattern

For any non-trivial task:

1. User or system creates an objective.
2. One or more scout agents analyse context and propose approaches.
3. Worker agents generate candidate outputs.
4. Critic agents attack candidates for safety, correctness, privacy, compliance, and quality.
5. Judge/ranker agents score candidates against explicit criteria.
6. Human reviews the best candidates, evidence, and dissent.
7. Approved action is executed by a narrow tool with audit logging.
8. Outcome is measured and fed back into future scoring.

## Agent roles

### Scout

Finds areas of interest, risks, missing context, standards, comparable workflows, and possible strategies.

### Worker

Produces a concrete artifact: draft, plan, code, policy, mapping, email, export bundle, claim extraction, or checklist.

### Critic

Tries to disprove, break, or improve the artifact. Separate critics should exist for security, privacy, clinical safety, compliance, data quality, and user intent.

### Judge

Compares candidates and critiques against an explicit rubric. It does not execute.

### Executor

Performs approved actions with minimum required privileges. Ideally deterministic, narrow, and boring.

### Auditor

Records what happened, why, with which model/tool/context, who approved it, and what changed.

## Competition modes

### Draft competition

Multiple agents draft alternatives. Human chooses or merges.

Examples:

- policy document
- patient message draft
- association newsletter
- study-club agenda
- regulator submission

### Risk competition

Agents compete to find flaws.

Examples:

- security threat model
- privacy impact assessment
- clinical-safety review
- data-mapping loss analysis
- compliance gap review

### Evidence competition

Agents extract claims from evidence, then critics challenge them.

Examples:

- degree certificate
- CPD certificate
- insurance document
- association membership record
- regulator register page

### Action competition

Agents propose actions; executor only runs approved action.

Examples:

- renew licence pack
- export patient record
- send member communication
- update policy pack
- create accounting export

## Human approval gates

Human approval is required for:

- sending external communications
- submitting regulator/government/board material
- clinical notes or treatment-related changes
- patient-facing messages
- credential verification or revocation
- membership rights changes
- payments, refunds, payroll, tax submissions
- deletion, retention override, legal hold
- association election/complaints/ethics outcomes
- AI provider use of regulated/sensitive data

Approval UX must show:

- proposed action
- data used
- data recipients
- policy decision
- confidence and dissent
- irreversible consequences
- rollback/export options

## Evidence bundle

Every candidate output should cite evidence:

```yaml
task_id: id
candidate_id: id
agent_id: model/tool identity
input_refs: documents/events/records used
claims_made: structured claims
uncertainties: known gaps
policy_checks: policy decisions
critic_findings: objections and severity
score: rubric scores
human_decision: approved/rejected/needs changes
execution_ref: if executed
audit_refs: audit events
```

## Sandboxing and authority

Agents should not have ambient authority.

Controls:

- task-scoped context bundles
- read-only by default
- no direct production writes
- no broad database access
- no hidden external network calls for sensitive data
- model/provider allowlist by classification
- deterministic executor for approved actions
- full audit trail

## Scoring dimensions

- correctness
- evidence support
- privacy minimisation
- security risk
- clinical-safety risk
- compliance risk
- reversibility
- user-intent match
- cost/time
- maintainability
- dissent strength

The winner is not always the highest-confidence answer. A high-confidence answer with weak evidence loses.

## Continuous improvement loop

After execution:

- measure outcome
- record human edits
- record rejection reasons
- identify recurring error patterns
- update prompts/rubrics/tests
- create regression tests for bad AI behaviour

## AI competition in product modules

### Dentist cockpit

Agents compete to prioritise renewals, CPD gaps, inbox tasks, and document filing.

### Degree/skill truth management

Agents extract credential claims; critics verify issuer/date/scope; human approves.

### Association/study-club management

Agents draft agendas, minutes, CPD certificates, newsletters, consultation summaries; critics check bylaws, conflicts, privacy, sponsor disclosure, and tone.

### Clinical modules

Agents may draft or summarise only under strict clinical-safety gates. Human clinician remains responsible.

### Compliance modules

Agents compete to find missing controls, stale policies, jurisdiction mismatch, and evidence gaps.

## Rule

AI should create pressure toward better decisions, not bypass human responsibility. The stack is a tournament; the human is the accountable approver; the audit log is the memory of power used.
