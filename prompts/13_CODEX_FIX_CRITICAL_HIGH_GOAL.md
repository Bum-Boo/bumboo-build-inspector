# 13 — Codex Fix Critical and High Issues Goal

Use this prompt only after the audit reports and remediation plan have been reviewed by a human.

## Prompt

You are a coding agent performing limited remediation.

The project has already been audited. Your task is to fix only the approved Critical and High issues listed in the remediation plan. Do not expand scope.

Read these files first:

```text
AGENTS.md
reports/remediation_plan.md
reports/security_privacy_audit.md
reports/deployment_readiness_audit.md
reports/ai_generated_code_risk_audit.md
```

If any of these files are missing, stop and ask the user to provide them or confirm the scope.

## Approved scope

```text
{APPROVED_FINDING_IDS_OR_APPROVED_BATCH}
```

## Rules

- Fix only approved Critical and High issues.
- Do not rewrite unrelated areas.
- Do not add dependencies unless absolutely necessary and justified.
- Do not deploy.
- Do not migrate databases without explicit approval.
- Do not call production APIs.
- Do not modify secrets.
- Do not delete data.
- Before editing, write a short implementation plan.
- After editing, run available tests, lint, typecheck, and build commands if safe.
- If a command is risky or unavailable, explain why it was not run.
- Update `reports/remediation_summary.md`.

## Required workflow

1. Restate approved scope.
2. Produce implementation plan.
3. Identify files to change.
4. Apply minimal changes.
5. Add or update tests for the fixed behavior.
6. Run validation commands.
7. Produce remediation summary.
8. Stop.

## Required output file

Create or update:

```text
reports/remediation_summary.md
```

## Remediation summary format

```markdown
# Remediation Summary

## Approved scope

## Files changed
| File | Change | Related finding |
|---|---|---|

## Issues fixed
| Finding ID | Fix summary | Validation |
|---|---|---|

## Tests/checks run
| Command | Result | Notes |
|---|---|---|

## Issues not fixed
| Finding ID | Reason | Recommended next action |
|---|---|---|

## New risks introduced
| Risk | Mitigation |
|---|---|

## Remaining release blockers

## Recommended next step
```
