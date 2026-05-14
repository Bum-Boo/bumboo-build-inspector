# Post-Build AI Auditor Prompt Kit

A reusable prompt and agent-instruction kit for inspecting software projects **after an initial build already exists**.

This kit is designed for projects that were built quickly with AI coding tools, vibe coding, no-code/low-code exports, or conventional development and now need a structured post-build audit before real users, production deployment, or commercialization.

## Core concept

Most AI coding workflows focus on creating code. This kit focuses on what happens **after the first build appears to work**:

1. Inspect the repository.
2. Identify the project type and stack.
3. Audit product readiness, security, privacy, deployment, operations, dependencies, testing, legal risks, and AI-generated-code weaknesses.
4. Produce structured reports.
5. Prioritize release blockers.
6. Generate safe follow-up instructions for a coding agent.
7. Fix only approved Critical and High issues.
8. Run tests and produce a release decision.

This is not a pre-build scaffold. It is a **post-build release-readiness and risk-audit system**.

## What this kit is

- A set of Markdown prompts for Codex, Claude Code, ChatGPT, and similar coding agents.
- A root `AGENTS.md` file for agents that support repository-level instructions.
- A `CLAUDE.md` file for Claude Code-oriented usage.
- Scope-specific audit prompts.
- Checklists for product, security, privacy, deployment, operations, dependencies, and AI-generated code.
- Report templates that agents can write into `reports/` in the target repository.
- Example task prompts for Codex Web, Codex CLI, and Claude Code.

## What this kit is not

- It is not a guarantee that a project is secure or legally compliant.
- It is not a substitute for professional security review, legal review, privacy review, or production SRE review.
- It should not automatically deploy, migrate databases, rotate secrets, or call production APIs.
- It should not be used to give an agent unlimited autonomy.

## Recommended operating model

```text
Initial build exists
→ Post-build audit
→ Risk-ranked report
→ Human selects allowed fixes
→ Agent fixes selected Critical/High issues
→ Tests/lint/typecheck/build
→ PR or patch summary
→ Human review
→ Release decision
```

Do not start with automatic modification. Start with **read-only audit**.

## Directory structure

```text
post_build_ai_auditor_prompt_kit/
├─ README.md
├─ AGENTS.md
├─ CLAUDE.md
├─ REFERENCES.md
├─ prompts/
│  ├─ 00_MASTER_POST_BUILD_AUDIT_GOAL.md
│  ├─ 01_SCOPE_ROUTER.md
│  ├─ 02_REPOSITORY_INTAKE_AND_SUMMARY.md
│  ├─ 03_PRODUCT_STRATEGY_AUDIT.md
│  ├─ 04_SECURITY_PRIVACY_AUDIT.md
│  ├─ 05_AI_GENERATED_CODE_RISK_AUDIT.md
│  ├─ 06_DEPENDENCY_SUPPLY_CHAIN_AUDIT.md
│  ├─ 07_DEPLOYMENT_READINESS_AUDIT.md
│  ├─ 08_TESTING_QUALITY_AUDIT.md
│  ├─ 09_OPERATIONS_INCIDENT_RESPONSE_AUDIT.md
│  ├─ 10_PERFORMANCE_SCALABILITY_AUDIT.md
│  ├─ 11_LEGAL_LICENSE_COMPLIANCE_AUDIT.md
│  ├─ 12_REMEDIATION_PLAN_GENERATOR.md
│  ├─ 13_CODEX_FIX_CRITICAL_HIGH_GOAL.md
│  ├─ 14_FINAL_RELEASE_DECISION.md
│  ├─ 15_MULTI_AGENT_REPORT_COMPARISON.md
│  └─ 16_CREATE_GITHUB_REPO_FROM_KIT.md
├─ checklists/
│  ├─ PRODUCT_READINESS_CHECKLIST.md
│  ├─ SECURITY_PRIVACY_CHECKLIST.md
│  ├─ DEPENDENCY_SUPPLY_CHAIN_CHECKLIST.md
│  ├─ DEPLOYMENT_OPERATIONS_CHECKLIST.md
│  └─ AI_GENERATED_CODE_CHECKLIST.md
├─ templates/
│  ├─ project_summary_template.md
│  ├─ audit_report_template.md
│  ├─ remediation_plan_template.md
│  ├─ remediation_summary_template.md
│  └─ final_release_decision_template.md
└─ examples/
   ├─ codex_web_task_prompt.md
   ├─ codex_cli_task_prompt.md
   ├─ claude_code_task_prompt.md
   └─ user_scope_intake_form.md
```

## Quick start: Codex Web

1. Connect Codex to GitHub.
2. Open the target repository in Codex.
3. Add or reference this kit in the task context.
4. Paste the task from `examples/codex_web_task_prompt.md` or `prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md`.
5. Keep the first run read-only.
6. Ask Codex to write reports under `reports/`.
7. Review the reports before asking Codex to modify code.

Use the first task like this:

```text
Read AGENTS.md first.
Then run a post-build audit using prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md.
Do not modify code yet.
Create the required reports under reports/.
```

## Quick start: Codex CLI

In a local clone of the target repository, copy this kit or reference it from a known path. Then paste:

```text
Read AGENTS.md first.
Use prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md as the operating prompt.
Mode: Post-build audit.
Do not modify code yet.
Create reports under reports/.
```

If your Codex version supports a `/goal` command, you can use the same content as a goal-style task. If it does not, paste it as a normal task prompt.

## Quick start: Claude Code

Claude Code can use `CLAUDE.md` project-level memory/instructions. Place `CLAUDE.md` at the repository root or keep it in this kit and explicitly tell Claude Code to read it.

Example:

```text
Read CLAUDE.md first.
Then read prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md.
Audit the existing repository as a post-build release-readiness auditor.
Do not modify code yet.
```

## Scope catalog

| Scope | Use when | Primary prompt |
|---|---|---|
| Full post-build audit | You want a broad release-readiness inspection | `00_MASTER_POST_BUILD_AUDIT_GOAL.md` |
| Scope routing | You want the agent to decide which audits to run | `01_SCOPE_ROUTER.md` |
| Repository summary | You need a neutral project summary before auditing | `02_REPOSITORY_INTAKE_AND_SUMMARY.md` |
| Product and strategy | You need commercialization/product gaps | `03_PRODUCT_STRATEGY_AUDIT.md` |
| Security and privacy | You handle auth, user data, APIs, files, payments, or admin features | `04_SECURITY_PRIVACY_AUDIT.md` |
| AI-generated code risk | The project was built with Codex, Copilot, Cursor, Claude Code, or similar tools | `05_AI_GENERATED_CODE_RISK_AUDIT.md` |
| Dependency and supply chain | You need package, lockfile, license, and CI/CD supply-chain review | `06_DEPENDENCY_SUPPLY_CHAIN_AUDIT.md` |
| Deployment readiness | You are preparing for staging or production | `07_DEPLOYMENT_READINESS_AUDIT.md` |
| Testing and quality | You need test coverage, regression, and QA gaps | `08_TESTING_QUALITY_AUDIT.md` |
| Operations and incidents | You need monitoring, backup, rollback, and support readiness | `09_OPERATIONS_INCIDENT_RESPONSE_AUDIT.md` |
| Performance and scalability | You need load, cost, database, bundle, or API bottleneck review | `10_PERFORMANCE_SCALABILITY_AUDIT.md` |
| Legal/license/compliance | You need terms, privacy policy, license, or regulated-domain checks | `11_LEGAL_LICENSE_COMPLIANCE_AUDIT.md` |
| Remediation planning | You have reports and need an execution plan | `12_REMEDIATION_PLAN_GENERATOR.md` |
| Fix Critical/High issues | You want Codex to make limited fixes after audit approval | `13_CODEX_FIX_CRITICAL_HIGH_GOAL.md` |
| Final release decision | You need a go/no-go decision | `14_FINAL_RELEASE_DECISION.md` |
| Multi-agent comparison | You have reports from several AIs and need a combined judgment | `15_MULTI_AGENT_REPORT_COMPARISON.md` |

## Safety levels

| Level | Name | Agent may modify code? | Intended use |
|---:|---|---:|---|
| 0 | Read-only audit | No | First inspection |
| 1 | Planning only | No | Turn findings into a plan |
| 2 | Safe fixes | Limited | Docs, tests, obvious low-risk issues |
| 3 | Critical/High remediation | Yes, with constraints | Fix approved blockers |
| 4 | PR preparation | Yes, with review | Prepare a pull request |
| 5 | Production operations | No automatic action | Deployment, migrations, secrets, production APIs |

The kit defaults to Level 0 unless the user explicitly requests otherwise.

## Minimum user input

A user should only need to provide:

```text
Repository URL:
Project type:
Selected audit scopes:
Allowed action level:
Known production constraints:
```

If any field is missing, the agent must write `Unknown` rather than inventing details.

## Required report outputs

For a full audit, the agent should create:

```text
reports/project_summary.md
reports/post_build_audit.md
reports/product_strategy_audit.md
reports/security_privacy_audit.md
reports/ai_generated_code_risk_audit.md
reports/dependency_supply_chain_audit.md
reports/deployment_readiness_audit.md
reports/testing_quality_audit.md
reports/operations_incident_response_audit.md
reports/remediation_plan.md
reports/final_release_decision.md
```

For scoped audits, only create the relevant reports.

## Severity rubric

| Severity | Meaning | Release implication |
|---|---|---|
| Critical | Likely security, data, legal, or production failure if released | Must fix before release |
| High | Material risk to users, reliability, maintainability, or trust | Fix before MVP or controlled beta |
| Medium | Important weakness but can be scheduled if risk is accepted | Track with owner and date |
| Low | Improvement or cleanup | Backlog |
| Unknown | Insufficient evidence | Requires investigation |

## Agent behavior rules

Agents must:

- Audit before modifying.
- Report before fixing.
- Use evidence from files where possible.
- Avoid guessing.
- Mark unknowns explicitly.
- Avoid destructive commands.
- Avoid production calls.
- Avoid installing new dependencies during audit.
- Avoid exposing secrets.
- Treat AI-generated code as untrusted until reviewed.
- Separate facts, inferences, and assumptions.

## Recommended human workflow

1. Run `00_MASTER_POST_BUILD_AUDIT_GOAL.md`.
2. Review reports.
3. Run `12_REMEDIATION_PLAN_GENERATOR.md`.
4. Select only Critical and High items.
5. Run `13_CODEX_FIX_CRITICAL_HIGH_GOAL.md`.
6. Ask Codex or Claude Code to run tests/lint/typecheck/build where available.
7. Run `14_FINAL_RELEASE_DECISION.md`.
8. Optionally request an additional PR review from another agent.

## Notes for maintainers

Keep prompts short enough to be useful but specific enough to constrain the agent. The strongest pattern is:

```text
Read-only audit first.
Plan second.
Modify only selected issues third.
Always produce a report.
```

## References

See `REFERENCES.md` for source links and standards that informed this kit.
