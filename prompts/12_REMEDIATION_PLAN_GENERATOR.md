# 12 — Remediation Plan Generator

Use this prompt after one or more audit reports exist.

## Prompt

You are a remediation planner.

Read the audit reports under `reports/`. Do not modify code. Convert the findings into a prioritized, executable remediation plan that a coding agent can follow safely.

## Inputs

Audit reports:

```text
reports/*.md
```

Allowed action level:

```text
{READ_ONLY_PLANNING_OR_APPROVED_FIX_LEVEL}
```

## Tasks

1. Consolidate all Critical, High, Medium, Low, and Unknown findings.
2. Deduplicate overlapping findings.
3. Identify dependencies between fixes.
4. Separate fixes into safe batches.
5. Identify fixes that require human approval.
6. Identify fixes that require expert review.
7. Generate the next recommended coding-agent task.

## Required output file

Create:

```text
reports/remediation_plan.md
```

## Output format

```markdown
# Remediation Plan

## Executive summary

## Release blockers
| Priority | Finding ID | Source report | Fix objective | Files likely involved | Human approval required? |
|---|---|---|---|---|---|

## Fix batches
| Batch | Objective | Included findings | Excluded findings | Why this batch is safe |
|---|---|---|---|---|

## Critical fixes
| Finding | Required fix | Implementation notes | Validation method |
|---|---|---|---|

## High-priority fixes
| Finding | Required fix | Implementation notes | Validation method |
|---|---|---|---|

## Medium-priority backlog
| Finding | Recommended action | Owner | Target timing |
|---|---|---|---|

## Unknowns to investigate
| Unknown | Investigation task | Expected output |
|---|---|---|

## Expert review required
| Area | Why expert review is needed | Suggested reviewer |
|---|---|---|

## Next safe coding-agent task

Paste this into the coding agent only after human approval:

```text
{GENERATED_NEXT_TASK_PROMPT}
```
```
