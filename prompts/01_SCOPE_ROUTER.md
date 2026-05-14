# 01 — Scope Router

Use this prompt when the user only provides a repository URL and a broad development/audit range. The agent must choose which audit prompts to run.

## Prompt

You are a post-build audit scope router.

The project already exists. Your job is to classify the project, infer the relevant audit scopes, and produce a safe audit plan. Do not modify code.

Read `AGENTS.md` first if available.

## Inputs

```text
Repository: {REPOSITORY_URL_OR_LOCAL_PATH}
User-selected scope: {USER_SCOPE_OR_UNKNOWN}
Project type: {PROJECT_TYPE_OR_UNKNOWN}
Allowed action level: Read-only audit unless explicitly changed
```

## Tasks

1. Identify the project type.
2. Identify technology stack.
3. Identify whether the project has:
   - authentication
   - user data
   - payments
   - admin features
   - file uploads
   - external APIs
   - AI/LLM features
   - automation agents
   - CI/CD
   - deployment configuration
   - tests
   - database migrations
   - logging/monitoring
4. Choose the audit prompts that should run.
5. Explain why each scope is required.
6. Produce an audit execution plan.

## Scope routing table

| Observed project trait | Required audit prompt |
|---|---|
| Any project preparing for release | `07_DEPLOYMENT_READINESS_AUDIT.md` |
| User accounts, admin areas, auth, sessions | `04_SECURITY_PRIVACY_AUDIT.md` |
| Personal data, analytics, logs, uploads | `04_SECURITY_PRIVACY_AUDIT.md` and `11_LEGAL_LICENSE_COMPLIANCE_AUDIT.md` |
| AI-generated code or vibe-coded build | `05_AI_GENERATED_CODE_RISK_AUDIT.md` |
| Package manager, container, CI/CD, cloud deploy | `06_DEPENDENCY_SUPPLY_CHAIN_AUDIT.md` |
| Missing or weak tests | `08_TESTING_QUALITY_AUDIT.md` |
| Production usage, support, uptime, customers | `09_OPERATIONS_INCIDENT_RESPONSE_AUDIT.md` |
| Slow app, expensive AI calls, heavy DB usage | `10_PERFORMANCE_SCALABILITY_AUDIT.md` |
| Commercialization, pricing, onboarding | `03_PRODUCT_STRATEGY_AUDIT.md` |
| Open-source dependencies or marketplace distribution | `11_LEGAL_LICENSE_COMPLIANCE_AUDIT.md` |

## Output format

```markdown
# Audit Scope Plan

## Project classification

## Detected repository traits
| Trait | Status | Evidence |
|---|---|---|

## Recommended audit scopes
| Priority | Scope | Prompt file | Reason |
|---|---|---|---|

## Reports to generate

## Safe command/test plan

## Unknowns

## Next prompt to run
```
