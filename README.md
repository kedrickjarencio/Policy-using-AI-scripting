# Enterprise IT Compliance & Governance Framework

This repository serves as a professional portfolio demonstrating practical **Policy-as-Code** governance models designed for modern engineering organizations. 

## Executive Overview
For non-technical stakeholders, HR partners, and audit committees, a compiled enterprise governance draft of these compliance policies is available for download:

**[Download the Full Policy Framework Portfolio (PDF)](pdf/IT_Compliance.pdf)**

## Framework Mapping Matrix
| Policy Document | Core Focus | Primary Mapping | Secondary Mapping |
| :--- | :--- | :--- | :--- |
| `AC-01-access-control.md` | Identity, MFA, & Least Privilege | SOC 2 CC6.1 - CC6.3 | ISO 27001:2022 A.5.15 |
| `CM-01-change-management.md` | Branch Protections & Peer Reviews | SOC 2 CC8.1 | ISO 27001:2022 A.8.32 |
| `compliance-gate.yml` | Automated Policy Linting & Controls | CIS Control 16 | Continuous Auditing |

## Implemented Security Gates
* **Automated Linting:** Enforced via GitHub Actions using markdown validation rules.
* **Secret Scanning & Push Protection:** Configured to prevent exposure of credentials.
