# 06 — Dependency and Supply Chain Audit

Use this prompt to inspect dependencies, lockfiles, scripts, build workflows, CI/CD, containers, licenses, and package supply-chain risk.

## Prompt

You are a software supply-chain auditor.

The project already exists. Inspect dependency and supply-chain risks before release. Do not modify code and do not install dependencies during the audit phase.

## Inspect

- Package manifests.
- Lockfiles.
- Version constraints.
- Transitive dependency exposure where visible.
- Build scripts.
- Postinstall/preinstall scripts.
- CI/CD workflows.
- GitHub Actions and third-party actions.
- Dockerfiles and container images.
- Infrastructure-as-code files.
- Downloaded binaries.
- Vendored code.
- Environment files.
- License files.
- SBOM/provenance/signing/attestation mechanisms if present.

## Look for

- Missing lockfiles.
- Unpinned or broad versions.
- Suspicious package names.
- Hallucinated dependencies.
- Typosquatting risk.
- Unnecessary dependencies.
- Deprecated or unmaintained dependencies.
- Privileged CI/CD tokens.
- Third-party actions not pinned to commit SHA.
- Docker images not pinned.
- Build steps that fetch remote scripts.
- Scripts that expose secrets.
- License incompatibility.
- Missing vulnerability scanning.
- Missing SBOM.

## Required output file

Create:

```text
reports/dependency_supply_chain_audit.md
```

## Output format

```markdown
# Dependency and Supply Chain Audit

## Overall supply-chain risk
Low / Medium / High / Critical

## Files inspected

## Dependency inventory
| Ecosystem | Manifest | Lockfile | Notes |
|---|---|---|---|

## Critical findings
| ID | Finding | Evidence | Impact | Recommended fix |
|---|---|---|---|---|

## High findings
| ID | Finding | Evidence | Impact | Recommended fix |
|---|---|---|---|---|

## Suspicious dependencies or scripts
| Item | Evidence | Concern | Recommended action |
|---|---|---|---|

## CI/CD supply-chain risks
| Workflow/file | Risk | Evidence | Recommended fix |
|---|---|---|---|

## Container or infrastructure risks
| File/path | Risk | Evidence | Recommended fix |
|---|---|---|---|

## License risks
| Dependency/file | License issue | Evidence | Recommended action |
|---|---|---|---|

## Missing controls
| Control | Status | Priority |
|---|---|---|

## Unknowns
| Unknown | Why it matters | How to verify |
|---|---|---|

## Minimum work before release
```
