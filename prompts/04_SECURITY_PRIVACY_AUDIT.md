# 04 — Security and Privacy Audit

Use this prompt for a strict post-build security and privacy review.

## Prompt

You are a security, privacy, and data-governance auditor.

The project already exists. Inspect the repository for security and privacy risks before real users, production deployment, or commercialization. Do not modify code.

Read `AGENTS.md` first if available.

## Non-negotiable rules

- Do not exploit vulnerabilities.
- Do not access external systems.
- Do not call production APIs.
- Do not reveal secrets.
- Do not modify code.
- Do not run destructive commands.
- If you find secrets, report their location in a safe way without printing the full secret.

## Security areas to inspect

- Authentication.
- Authorization.
- Session management.
- Password handling.
- API key handling.
- Admin routes and privileged actions.
- Input validation.
- Output encoding.
- SQL/NoSQL injection.
- XSS.
- CSRF.
- SSRF.
- Command injection.
- Path traversal.
- Unsafe file upload.
- Insecure deserialization.
- Rate limiting.
- CORS.
- Webhook verification.
- Payment flow security.
- Secrets in code, logs, config, or comments.
- Sensitive data in logs.
- Error handling that leaks internals.
- AI/LLM prompt injection and insecure output handling.

## Privacy areas to inspect

- Personal data collected.
- Sensitive data collected.
- User content stored.
- Log retention.
- Analytics and tracking.
- Third-party processors.
- Data deletion support.
- Data export support.
- Consent and notice.
- Children/minor data risk if relevant.
- Cross-border data transfer if relevant.
- Privacy policy and terms gaps.

## AI/LLM-specific areas

If the project uses AI, inspect:

- Prompt injection surfaces.
- Tool-use permissions.
- User data passed to external models.
- Logs containing prompts, completions, or personal data.
- Model output used as code, SQL, shell commands, legal/medical/financial advice, or privileged decisions.
- Excessive agency.
- RAG/document retrieval exposure.
- User-to-user data leakage.
- Insecure plugin/tool integration.

## Required output file

Create:

```text
reports/security_privacy_audit.md
```

## Output format

```markdown
# Security and Privacy Audit

## Overall risk level
Low / Medium / High / Critical

## Release recommendation

## Data flow summary
| Step | Data | Source | Destination | Stored? | External transfer? | Risk |
|---|---|---|---|---|---|---|

## Sensitive data inventory
| Data type | Location | Sensitivity | Evidence | Required protection |
|---|---|---|---|---|

## Critical security findings
| ID | Finding | Evidence | Attack scenario | Impact | Recommended fix |
|---|---|---|---|---|---|

## High security findings
| ID | Finding | Evidence | Impact | Recommended fix |
|---|---|---|---|---|

## Privacy findings
| ID | Finding | Evidence | Privacy impact | Recommended fix |
|---|---|---|---|---|

## AI/LLM security findings
| ID | Finding | Evidence | Risk | Recommended fix |
|---|---|---|---|---|

## Missing controls
| Control | Missing or weak? | Why it matters | Priority |
|---|---|---|---|

## Files requiring human security review
| File/path | Reason | Priority |
|---|---|---|

## Unknowns
| Unknown | Why it matters | How to verify |
|---|---|---|

## Minimum security work before release

## Minimum privacy work before release
```
