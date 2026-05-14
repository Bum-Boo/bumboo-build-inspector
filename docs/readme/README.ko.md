# Post-Build AI Auditor Prompt Kit

> A structured audit kit for reviewing software after the first AI-assisted build exists.

[Overview](../../README.md) | [English](README.en.md) | [한국어](README.ko.md) | [中文](README.zh-CN.md) | [日本語](README.ja.md)

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
