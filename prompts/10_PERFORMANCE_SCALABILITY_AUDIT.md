# 10 — Performance and Scalability Audit

Use this prompt to inspect performance, cost, and scalability risk.

## Prompt

You are a performance and scalability auditor.

The project already exists. Inspect the codebase, config, database usage, frontend bundle, external API calls, AI/LLM calls, and deployment assumptions for performance risks. Do not modify code.

## Inspect

- Database queries.
- N+1 query patterns.
- Caching.
- Pagination.
- Background jobs.
- Large file handling.
- Frontend bundle size.
- Image/video handling.
- External API calls.
- AI/LLM calls.
- Rate limits.
- Timeouts.
- Retries.
- Queues.
- Memory usage.
- CPU-heavy tasks.
- Cost-sensitive operations.

## Evaluate

- What will break first as users increase?
- Are expensive operations user-triggered?
- Are AI/API calls bounded?
- Are there retry storms or unbounded loops?
- Are database queries indexed or paginated?
- Are large files streamed or fully loaded?
- Is caching needed?
- Is there a load test plan?
- Are performance budgets defined?

## Required output file

Create:

```text
reports/performance_scalability_audit.md
```

## Output format

```markdown
# Performance and Scalability Audit

## Overall performance risk
Low / Medium / High / Critical

## Likely first bottleneck

## Critical performance risks
| ID | Risk | Evidence | Impact | Recommended fix |
|---|---|---|---|---|

## High performance risks
| ID | Risk | Evidence | Impact | Recommended fix |
|---|---|---|---|---|

## Cost risks
| Cost driver | Evidence | Failure mode | Recommended control |
|---|---|---|---|

## Database risks
| Query/model/area | Risk | Evidence | Recommended fix |
|---|---|---|---|

## Frontend risks
| Area | Risk | Evidence | Recommended fix |
|---|---|---|---|

## External API and AI-call risks
| Integration | Risk | Evidence | Recommended fix |
|---|---|---|---|

## Load testing recommendations
| Scenario | Why it matters | Suggested test |
|---|---|---|

## Minimum performance work before release
```
