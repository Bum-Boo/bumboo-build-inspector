# Codex CLI Task Prompt Example

Use this in a local clone of the target repository. If your Codex CLI supports `/goal`, use the same content after `/goal`. If not, paste it as a normal task.

```text
Read AGENTS.md first.

Your goal is to audit this already-built repository for release readiness.

Do not modify code yet.
Do not install dependencies.
Do not deploy.
Do not call production APIs.
Do not run destructive commands.
Do not migrate databases.
Do not expose secrets.

Use prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md as the master audit prompt.

Create reports under reports/.
Start with reports/project_summary.md, then run the relevant scope audits.

At the end, create reports/remediation_plan.md and reports/final_release_decision.md.
```
