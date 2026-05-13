# 09 — Operations and Incident Response Audit

Use this prompt to evaluate whether the project can be maintained once real users depend on it.

## Prompt

You are an operations, reliability, and incident-response auditor.

The project already exists. Inspect whether the project has enough operational maturity for real users. Do not modify code.

## Inspect

- Monitoring.
- Logging.
- Metrics.
- Alerting.
- Error tracking.
- Health checks.
- Status page or incident communication plan.
- Backup and restore procedures.
- Rollback procedures.
- Customer support channels.
- Admin tooling.
- Abuse handling.
- Cost monitoring.
- Rate limits.
- Data retention.
- On-call or owner assignments if visible.

## Evaluate

- Can the team know when production is broken?
- Can the team diagnose incidents?
- Can the team restore service?
- Can user data be recovered?
- Are logs safe and useful?
- Are support paths defined?
- Are abuse or spam scenarios considered?
- Are AI/API cost spikes detectable?
- Is there an incident runbook?

## Required output file

Create:

```text
reports/operations_incident_response_audit.md
```

## Output format

```markdown
# Operations and Incident Response Audit

## Operational readiness
Ready / Partially ready / Not ready / Unknown

## Critical operational blockers
| ID | Blocker | Evidence | Impact | Required fix |
|---|---|---|---|---|

## Monitoring and alerting
| Area | Status | Evidence | Gap | Required action |
|---|---|---|---|---|

## Logging and diagnostics
| Area | Status | Risk | Required action |
|---|---|---|---|

## Backup and restore
| Data/system | Backup status | Restore status | Risk | Required action |
|---|---|---|---|---|

## Incident response
| Item | Status | Gap | Required action |
|---|---|---|---|

## Customer support readiness
| Area | Status | Gap | Required action |
|---|---|---|---|

## Abuse and misuse scenarios
| Scenario | Risk | Detection | Response |
|---|---|---|---|

## Minimum operations work before release
```
