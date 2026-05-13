# 03 — Product and Strategy Audit

Use this prompt to evaluate whether the built project is commercially and strategically coherent enough to show to real users.

## Prompt

You are a product strategist and release-readiness auditor.

The project already exists. Inspect the repository, README, UI copy, documentation, routes, onboarding flows, pricing references, and feature structure to determine whether this project is product-ready. Do not modify code.

## Audit questions

Evaluate:

- Who is the target user?
- What user problem is the product solving?
- Is the value proposition clear?
- Is the MVP scope coherent?
- Are there features that look impressive but are not tied to user value?
- Is onboarding sufficient?
- Can a new user understand what to do without guidance?
- Is there a repeat-use reason?
- Is pricing or monetization implied or defined?
- Is support, documentation, or help available?
- Are error states, empty states, and edge cases handled?
- Is the product safe to offer to external users?
- Are trust, quality, and responsibility boundaries clear?

## Inspect for common post-build gaps

- Demo-only functionality presented as real functionality.
- No clear target customer.
- Missing onboarding.
- Missing pricing model.
- Missing customer support process.
- Missing terms, privacy, or usage boundaries.
- Too many features without a core workflow.
- No clear success metric.
- No user feedback collection mechanism.
- No quality control for AI-generated outputs.
- No clear data retention policy.

## Required output file

Create:

```text
reports/product_strategy_audit.md
```

## Output format

```markdown
# Product and Strategy Audit

## Product maturity score
Score: 0-100
Stage: Idea / Prototype / MVP / Controlled beta / Production-ready / Redesign needed

## One-sentence judgment

## Target user assessment
| Item | Finding | Evidence | Risk |
|---|---|---|---|

## Value proposition assessment

## MVP scope assessment
| Feature | Keep in MVP? | Reason | Risk if kept/removed |
|---|---|---|---|

## Commercialization gaps
| Gap | Severity | Why it matters | Recommended fix |
|---|---|---|---|

## User experience gaps
| Gap | Evidence | Impact | Recommended fix |
|---|---|---|---|

## Trust and quality gaps
| Gap | Evidence | Risk | Recommended fix |
|---|---|---|---|

## Product release blockers
| Severity | Blocker | Evidence | Required action |
|---|---|---|---|

## Recommended MVP definition
- Core user:
- Core problem:
- Core workflow:
- Must-have features:
- Excluded features:
- Success metric:
- Failure metric:

## Next product tasks
| Priority | Task | Output | Owner |
|---|---|---|---|
```
