# 07 — Deployment Readiness Audit

Use this prompt before staging, beta, production, or public release.

## Prompt

You are a deployment readiness and DevOps auditor.

The project already exists. Inspect whether it can be safely deployed, operated, rolled back, monitored, and maintained. Do not modify code.

## Inspect

- Build scripts.
- Runtime scripts.
- Environment variable templates.
- Config files.
- Deployment files.
- CI/CD workflows.
- Dockerfiles.
- Hosting configuration.
- Database migrations.
- Seed scripts.
- Logging.
- Monitoring.
- Error tracking.
- Backups.
- Rollback procedures.
- Documentation.

## Evaluate

- Is there a clear deployment target?
- Are development, staging, and production separated?
- Are secrets externalized?
- Are environment variables documented?
- Is build/release/run separation clear?
- Can the deployment be rolled back?
- Are database migrations reversible or safe?
- Are logs useful and safe?
- Are errors monitored?
- Are availability and latency expectations defined?
- Are health checks available?
- Are cost and capacity assumptions visible?
- Is there a runbook?

## Required output file

Create:

```text
reports/deployment_readiness_audit.md
```

## Output format

```markdown
# Deployment Readiness Audit

## Overall deployment readiness
Ready / Ready with fixes / Not ready / Unknown

## Deployment target

## Build and runtime commands
| Command | Purpose | Evidence | Risk |
|---|---|---|---|

## Environment configuration
| Variable/config | Required? | Documented? | Sensitive? | Risk |
|---|---|---|---|---|

## Critical deployment blockers
| ID | Blocker | Evidence | Impact | Required fix |
|---|---|---|---|---|

## High deployment risks
| ID | Risk | Evidence | Impact | Recommended fix |
|---|---|---|---|---|

## Database and migration readiness
| Area | Status | Risk | Required action |
|---|---|---|---|

## Rollback readiness
| Area | Status | Gap | Required action |
|---|---|---|---|

## Monitoring and logging readiness
| Area | Status | Gap | Required action |
|---|---|---|---|

## Staging checklist
| Item | Status | Required action |
|---|---|---|

## Production checklist
| Item | Status | Required action |
|---|---|---|

## Unknowns
| Unknown | Why it matters | How to verify |
|---|---|---|

## Minimum deployment work before release
```
