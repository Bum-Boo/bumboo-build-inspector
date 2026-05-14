# Post-Build AI Auditor Prompt Kit

> A structured audit kit for reviewing software after the first AI-assisted build exists.

[Overview](../../README.md) | [English](README.en.md) | [한국어](README.ko.md) | [中文](README.zh-CN.md) | [日本語](README.ja.md)

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
