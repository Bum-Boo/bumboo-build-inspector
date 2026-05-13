# Codex Web Task Prompt Example

Paste this into Codex Web after connecting the target GitHub repository.

```text
Read AGENTS.md first.

Mode: Post-build audit.

The initial build already exists. Do not start the project from scratch.
Do not modify code yet.
Do not deploy.
Do not install dependencies.
Do not call production APIs.
Do not migrate databases.
Do not rotate or expose secrets.

Use these prompt files:
- prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md
- prompts/01_SCOPE_ROUTER.md
- prompts/02_REPOSITORY_INTAKE_AND_SUMMARY.md
- prompts/04_SECURITY_PRIVACY_AUDIT.md
- prompts/05_AI_GENERATED_CODE_RISK_AUDIT.md
- prompts/07_DEPLOYMENT_READINESS_AUDIT.md
- prompts/12_REMEDIATION_PLAN_GENERATOR.md

Selected scope:
Full post-build audit with special attention to security, privacy, deployment readiness, dependency risk, testing gaps, and AI-generated-code weaknesses.

Required output:
Create reports under reports/:
- project_summary.md
- post_build_audit.md
- security_privacy_audit.md
- ai_generated_code_risk_audit.md
- dependency_supply_chain_audit.md
- deployment_readiness_audit.md
- testing_quality_audit.md
- remediation_plan.md
- final_release_decision.md

Mark missing information as Unknown.
Prioritize release blockers.
Recommend the next safe task.
```
