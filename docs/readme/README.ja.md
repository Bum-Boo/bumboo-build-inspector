# Post-Build AI Auditor Prompt Kit

> A structured audit kit for reviewing software after the first AI-assisted build exists.

[Overview](../../README.md) | [English](README.en.md) | [한국어](README.ko.md) | [中文](README.zh-CN.md) | [日本語](README.ja.md)

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
