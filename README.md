# Post-Build AI Auditor Prompt Kit

> A structured audit kit for reviewing software after the first AI-assisted build exists.

[English](#english) | [한국어](#한국어) | [中文](#中文) | [日本語](#日本語)

| Area | Detail |
|---|---|
| Use case | Post-build release-readiness and risk audit |
| Works with | Codex, Claude Code, ChatGPT, and similar coding agents |
| Default mode | Read-only audit before any modification |
| Outputs | Project summaries, audit reports, remediation plans, and release decisions |

## English

A reusable prompt and agent-instruction kit for inspecting software projects **after an initial build already exists**.

This kit is designed for projects that were built quickly with AI coding tools, vibe coding, no-code/low-code exports, or conventional development and now need a structured post-build audit before real users, production deployment, or commercialization.

## Core concept

Most AI coding workflows focus on creating code. This kit focuses on what happens **after the first build appears to work**:

1. Inspect the repository.
2. Identify the project type and stack.
3. Audit product readiness, security, privacy, performance, deployment, operations, dependencies, testing, legal risks, and AI-generated-code weaknesses.
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
- Checklists for product, security, privacy, performance, deployment, operations, dependencies, and AI-generated code.
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
│  ├─ PERFORMANCE_SCALABILITY_CHECKLIST.md
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
## Demo Walkthrough

This project is not a standalone app. It is a prompt and checklist kit for asking an AI coding agent to audit a project after the first build exists.

1. Prepare the target project's build logs, test results, and deployment target.
2. Open `CLAUDE.md` or a checklist from the `checklists` folder.
3. Give the checklist and project path to Codex, Claude, or another coding agent.
4. Turn the returned security, deployment, dependency, and release-readiness notes into an issue list.

The screenshot below is a non-developer demo guide. Prepare the materials in the order shown on the left, then open the prompt or checklist files shown on the right.

![Build inspector guide](docs/demo-screenshots/guide-build-inspector.png)

---

## 한국어

Post-Build AI Auditor Prompt Kit은 첫 빌드가 이미 존재하는 소프트웨어 프로젝트를 AI 코딩 에이전트에게 점검시키기 위한 프롬프트/체크리스트 모음입니다.

초기 생성 자체가 아니라, “일단 돌아가는 것처럼 보이는 코드”를 실제 사용자, 배포, 상용화 전에 다시 점검하는 데 초점을 둡니다.

### 핵심 흐름

1. 저장소를 읽고 프로젝트 유형과 스택을 파악합니다.
2. 제품 준비 상태, 보안, 개인정보, 성능, 배포, 운영, 의존성, 테스트, 법적 리스크를 점검합니다.
3. 위험도 기준으로 보고서를 작성합니다.
4. 사람이 수정 허용 범위를 고릅니다.
5. 승인된 Critical/High 항목만 제한적으로 수정합니다.
6. 테스트와 최종 릴리스 판단을 진행합니다.

### 빠른 사용법

```text
Read AGENTS.md first.
Then run a post-build audit using prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md.
Do not modify code yet.
Create the required reports under reports/.
```

### 데모 흐름

1. 점검할 프로젝트의 빌드 로그, 테스트 결과, 배포 대상 정보를 준비합니다.
2. `CLAUDE.md` 또는 `checklists` 폴더의 체크리스트를 엽니다.
3. Codex, Claude 같은 AI 도구에 체크리스트와 프로젝트 경로를 함께 전달합니다.
4. AI가 반환한 보안, 배포, 의존성, 제품 준비 상태 지적 사항을 이슈 목록으로 정리합니다.

---

## 中文

Post-Build AI Auditor Prompt Kit 是一套用于在初始构建完成后审查软件项目的提示词和检查清单。

它不负责生成项目骨架，而是关注“项目看起来已经能运行之后”需要进行的发布准备、风险、部署、安全和维护性审查。

### 核心流程

1. 读取仓库并识别项目类型和技术栈。
2. 审查产品准备度、安全、隐私、性能、部署、运维、依赖、测试和法律风险。
3. 生成按风险排序的报告。
4. 由人工选择允许修复的范围。
5. 只修复被批准的 Critical/High 项。
6. 运行验证并给出最终发布判断。

### 快速使用

```text
Read AGENTS.md first.
Then run a post-build audit using prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md.
Do not modify code yet.
Create the required reports under reports/.
```

### 演示流程

1. 准备目标项目的构建日志、测试结果和部署目标。
2. 打开 `CLAUDE.md` 或 `checklists` 文件夹中的检查清单。
3. 将检查清单和项目路径交给 Codex、Claude 或类似 coding agent。
4. 把返回的安全、部署、依赖和发布准备度问题整理成 issue 列表。

---

## 日本語

Post-Build AI Auditor Prompt Kit は、初回ビルドがすでに存在するソフトウェアプロジェクトを AI コーディングエージェントに監査させるためのプロンプト/チェックリスト集です。

プロジェクトを新規生成するためのものではなく、「一応動いているように見える状態」から、実ユーザー、デプロイ、商用利用の前にリスクを確認することに焦点を当てています。

### 基本フロー

1. リポジトリを読み、プロジェクト種別と技術スタックを把握します。
2. プロダクト準備、セキュリティ、プライバシー、性能、デプロイ、運用、依存関係、テスト、法務リスクを監査します。
3. リスク順にレポートを作成します。
4. 人間が修正してよい範囲を選びます。
5. 承認された Critical/High 項目だけを限定的に修正します。
6. 検証を実行し、最終的なリリース判断を行います。

### クイックスタート

```text
Read AGENTS.md first.
Then run a post-build audit using prompts/00_MASTER_POST_BUILD_AUDIT_GOAL.md.
Do not modify code yet.
Create the required reports under reports/.
```

### デモ手順

1. 監査対象プロジェクトのビルドログ、テスト結果、デプロイ先情報を準備します。
2. `CLAUDE.md` または `checklists` フォルダのチェックリストを開きます。
3. チェックリストとプロジェクトパスを Codex、Claude などの coding agent に渡します。
4. 返ってきたセキュリティ、デプロイ、依存関係、リリース準備に関する指摘を issue リストに整理します。
