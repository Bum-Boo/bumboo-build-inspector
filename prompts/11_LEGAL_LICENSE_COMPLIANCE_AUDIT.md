# 11 — Legal, License, and Compliance Audit

Use this prompt to identify legal, licensing, privacy-policy, terms-of-service, AI-disclosure, and compliance gaps. This is not legal advice.

## Prompt

You are a legal, license, and compliance risk auditor.

The project already exists. Inspect the repository and product surface for legal and compliance gaps before commercialization or public release. Do not modify code.

This is not legal advice. Mark anything that requires a qualified legal review.

## Inspect

- License file.
- Open-source dependencies and licenses.
- Terms of service.
- Privacy policy.
- Cookie notice.
- Data processing terms.
- AI usage disclosure.
- User-generated content handling.
- Copyright/IP risks.
- Marketplace or app-store requirements.
- Payment/subscription/refund terms.
- Industry-specific compliance risk.
- Geographic compliance risk.
- Export/sanctions risk if relevant.

## Evaluate

- Is there a license for the repository?
- Are dependency licenses compatible with intended use?
- Is user data collected or processed?
- Is there a privacy policy?
- Is there a terms of service document?
- Are AI-generated outputs disclosed or bounded?
- Are users told what the service does and does not guarantee?
- Are refunds, billing, and support terms defined?
- Does the project touch regulated domains such as healthcare, finance, legal, education, employment, children, biometric data, or government services?

## Required output file

Create:

```text
reports/legal_license_compliance_audit.md
```

## Output format

```markdown
# Legal, License, and Compliance Audit

## Overall legal/compliance risk
Low / Medium / High / Critical / Unknown

## Non-legal-advice disclaimer
This report is a technical risk screen and is not legal advice.

## Critical legal/compliance blockers
| ID | Blocker | Evidence | Risk | Required action |
|---|---|---|---|---|

## License review
| Item | License/status | Risk | Recommended action |
|---|---|---|---|

## Privacy and terms gaps
| Document/control | Status | Why it matters | Recommended action |
|---|---|---|---|

## AI disclosure and responsibility gaps
| Gap | Evidence | Risk | Recommended action |
|---|---|---|---|

## Regulated-domain risks
| Domain | Relevance | Risk | Expert review needed? |
|---|---|---|---|

## Marketplace/app-store risks
| Requirement area | Status | Risk | Recommended action |
|---|---|---|---|

## Expert review required
| Area | Why | Priority |
|---|---|---|

## Minimum legal/compliance work before release
```
