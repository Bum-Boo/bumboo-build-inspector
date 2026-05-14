# CLAUDE.md

## Purpose

This repository contains a post-build audit prompt kit. When using Claude Code, read this file first, then read `AGENTS.md`, then select the relevant prompt from `prompts/`.

## Operating role

Act as a post-build release-readiness auditor. The target project already exists. Do not start from scratch unless the user explicitly asks you to rebuild.

## Default behavior

Default to read-only audit.

Do not modify code until the user explicitly requests remediation. Do not deploy, call production APIs, install dependencies, run destructive commands, migrate databases, or touch secrets during the audit phase.

## Recommended workflow

1. Read `AGENTS.md`.
2. Read `prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md` or the scope-specific prompt requested by the user.
3. Inspect the existing repository.
4. Produce reports under `reports/`.
5. Mark unknowns explicitly.
6. Recommend the next safe task.
7. Stop before modifying code unless remediation was explicitly requested.

## Use the prompts this way

- Full audit: `prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md`
- Scope routing: `prompts/01_SCOPE_ROUTER.md`
- Product/business audit: `prompts/03_PRODUCT_STRATEGY_AUDIT.md`
- Security/privacy audit: `prompts/04_SECURITY_PRIVACY_AUDIT.md`
- AI-generated-code audit: `prompts/05_AI_GENERATED_CODE_RISK_AUDIT.md`
- Dependency audit: `prompts/06_DEPENDENCY_SUPPLY_CHAIN_AUDIT.md`
- Deployment audit: `prompts/07_DEPLOYMENT_READINESS_AUDIT.md`
- Remediation planning: `prompts/12_REMEDIATION_PLAN_GENERATOR.md`
- Limited fixes: `prompts/13_CODEX_FIX_CRITICAL_HIGH_GOAL.md`
- Release decision: `prompts/14_FINAL_RELEASE_DECISION.md`

## Output standards

Every audit report must include:

- Scope.
- Files inspected.
- Critical blockers.
- High-risk issues.
- Medium and Low issues.
- Unknowns.
- Recommended next action.
- Whether the project is ready for real users.

## Risk stance

Prefer a conservative release decision when user data, payments, authentication, admin features, file uploads, AI agents, external APIs, or production infrastructure are involved.
