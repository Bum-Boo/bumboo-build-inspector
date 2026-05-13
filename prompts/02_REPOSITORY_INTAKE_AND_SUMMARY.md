# 02 — Repository Intake and Summary

Use this prompt before deeper audits to create a neutral project summary from the repository itself.

## Prompt

You are a repository intake analyst.

Inspect the existing repository and produce a neutral, evidence-based project summary. Do not modify code.

Read `AGENTS.md` first if available.

## Tasks

1. Identify project type.
2. Identify stack, frameworks, runtime, package managers, database, infrastructure, and deployment target.
3. Summarize repository structure.
4. Identify main entry points.
5. Identify core user-facing features.
6. Identify data model and storage if visible.
7. Identify external APIs and integrations.
8. Identify authentication and authorization mechanisms.
9. Identify test, build, lint, typecheck, and deployment commands.
10. Identify missing or unclear information.

## Required output file

Create:

```text
reports/project_summary.md
```

## Output format

```markdown
# Project Summary

## One-line summary

## Project type

## Apparent target users

## Technology stack
| Layer | Detected technology | Evidence |
|---|---|---|

## Repository structure
| Path | Purpose | Notes |
|---|---|---|

## Main entry points
| File/path | Role | Evidence |
|---|---|---|

## Core user flows
| Flow | Evidence | Unknowns |
|---|---|---|

## Data and storage
| Data type | Storage location | Sensitivity | Evidence |
|---|---|---|---|

## External integrations
| Integration | Purpose | Risk | Evidence |
|---|---|---|---|

## Build/test/deploy commands
| Command | Purpose | Evidence | Notes |
|---|---|---|---|

## Immediate audit concerns
| Concern | Why it matters | Suggested next audit |
|---|---|---|

## Unknowns
| Unknown | Why it matters | How to verify |
|---|---|---|
```
