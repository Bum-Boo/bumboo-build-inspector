# 08 — Testing and Quality Audit

Use this prompt to inspect whether tests actually protect users and critical behavior.

## Prompt

You are a testing and quality auditor.

The project already exists. Inspect the test suite, test commands, coverage signals, QA gaps, and quality controls. Do not modify code.

## Inspect

- Unit tests.
- Integration tests.
- End-to-end tests.
- Smoke tests.
- Security tests.
- Regression tests.
- Test fixtures.
- Mocks.
- CI test execution.
- Linting.
- Type checking.
- Build checks.
- Manual QA documentation.

## Evaluate

- Are critical user flows tested?
- Are auth and authorization tested?
- Are failure states tested?
- Are edge cases tested?
- Are payments, uploads, external APIs, and AI outputs tested if present?
- Are tests deterministic?
- Do mocks hide integration risk?
- Are tests shallow or implementation-mirroring?
- Are tests run in CI?
- Is there a release smoke test?

## Required output file

Create:

```text
reports/testing_quality_audit.md
```

## Output format

```markdown
# Testing and Quality Audit

## Overall quality risk
Low / Medium / High / Critical

## Test command inventory
| Command | Purpose | Evidence | Notes |
|---|---|---|---|

## Existing test coverage summary
| Area | Test coverage | Evidence | Risk |
|---|---|---|---|

## Critical missing tests
| ID | Missing test | Why it matters | Suggested test |
|---|---|---|---|

## High-priority missing tests
| ID | Missing test | Why it matters | Suggested test |
|---|---|---|---|

## Shallow or misleading tests
| Test file | Problem | Impact | Recommended fix |
|---|---|---|---|

## CI quality gates
| Gate | Present? | Evidence | Required action |
|---|---|---|---|

## Manual QA gaps
| Gap | Risk | Recommended checklist item |
|---|---|---|

## Minimum testing work before release
```
