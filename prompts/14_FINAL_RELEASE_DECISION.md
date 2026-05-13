# 14 — Final Release Decision

Use this prompt after audits and remediation summaries exist.

## Prompt

You are a release decision reviewer.

Read all audit reports and remediation summaries. Decide whether the project is ready for internal testing, controlled beta, or production release. Do not modify code.

## Inputs

Read:

```text
reports/project_summary.md
reports/*audit*.md
reports/remediation_plan.md
reports/remediation_summary.md
```

If some reports are missing, include that as an Unknown or release risk.

## Decision options

Choose exactly one:

- Ready for internal testing only.
- Ready for controlled beta.
- Ready for production release.
- Not ready; release blocked by Critical issues.
- Not ready; High issues must be fixed first.
- Not ready; major redesign recommended.

## Required output file

Create:

```text
reports/final_release_decision.md
```

## Output format

```markdown
# Final Release Decision

## Decision

## Confidence level
High / Medium / Low

## One-sentence judgment

## Evidence reviewed
| Report/file | Reviewed? | Notes |
|---|---|---|

## Remaining Critical issues
| Finding | Source | Release impact | Required action |
|---|---|---|---|

## Remaining High issues
| Finding | Source | Release impact | Required action |
|---|---|---|---|

## Accepted risks
| Risk | Reason accepted | Owner | Review date |
|---|---|---|---|

## Required before release
| Task | Owner | Completion evidence |
|---|---|---|

## Required after release
| Task | Owner | Timing |
|---|---|---|

## Unknowns
| Unknown | Release risk | How to resolve |
|---|---|---|

## Final recommendation
```
