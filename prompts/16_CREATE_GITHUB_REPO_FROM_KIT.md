# 16 — Create or Update GitHub Repository From This Kit

Use this prompt when the user wants a coding agent to create a GitHub repository or commit this prompt kit into an existing repository.

## Prompt

You are a repository setup agent.

Your task is to create or update a GitHub repository containing the Post-Build AI Auditor Prompt Kit. This is a prompt and documentation repository, not an application runtime.

## Inputs

```text
Target repository: {GITHUB_REPOSITORY_URL_OR_NEW_REPO_NAME}
Source files: {PATH_TO_DOWNLOADED_KIT_OR_UPLOADED_FILES}
Branch name: {BRANCH_NAME_OR_post-build-audit-kit}
Commit message: Add post-build AI auditor prompt kit
```

## Rules

- Do not alter unrelated files in the target repository.
- Do not run application build scripts unless this is an application repository and the user explicitly requests it.
- Preserve Markdown file names and folder structure.
- Ensure `README.md`, `AGENTS.md`, `CLAUDE.md`, and `REFERENCES.md` are at the root.
- Ensure prompt files are under `prompts/`.
- Ensure checklist files are under `checklists/`.
- Ensure report templates are under `templates/`.
- Create a pull request if the environment supports PR creation.
- If direct GitHub access is unavailable, produce exact git commands for the user.

## Tasks

1. Inspect the target repository.
2. Create the directory structure if needed.
3. Copy all kit files.
4. Verify file paths.
5. Create a short repository setup summary.
6. Commit changes on a new branch if allowed.
7. Create a PR if allowed.

## Required output

```markdown
# Repository Setup Summary

## Files added

## Files changed

## Branch

## Commit

## Pull request

## Manual steps required

## Suggested next prompt
```
