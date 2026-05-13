# Claude Code Task Prompt Example

Paste this into Claude Code from the target repository root.

```text
Read CLAUDE.md first if present.
Then read AGENTS.md if present.

You are auditing an already-built project. Do not start over.

Run a post-build read-only audit using:
- prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md
- prompts/01_SCOPE_ROUTER.md
- prompts/02_REPOSITORY_INTAKE_AND_SUMMARY.md
- prompts/04_SECURITY_PRIVACY_AUDIT.md
- prompts/05_AI_GENERATED_CODE_RISK_AUDIT.md
- prompts/07_DEPLOYMENT_READINESS_AUDIT.md

Do not modify code during this task.
Create reports under reports/.
Mark unknowns clearly.
Prioritize Critical and High release blockers.
```
