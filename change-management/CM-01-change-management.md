# POL-CM-01: Secure Software Development & Change Management Policy

## 1. Purpose
This policy defines the mandatory controls for proposing, developing, reviewing, testing, and deploying changes to production systems and codebases to minimize operational and security risks.

## 2. Scope
This policy applies to all source code repositories, configurations, infrastructure-as-code (IaC), and continuous integration/continuous deployment (CI/CD) pipelines managed under the Enterprise GitHub Organization.

## 3. GitHub Policy-as-Code Controls (Mandatory)

### 3.1 Repository Rulesets & Branch Protection
All production branch deployments (e.g., `main`, `master`, `production`) must enforce GitHub Repository Rulesets with the following minimum configurations:
* **Require a pull request before merging:** Direct pushes to default branches are strictly prohibited.
* **Required approvals:** A minimum of **two (2) independent peer reviews** (Write access or higher) must approve any PR before merge.
* **Code Owner Reviews:** If changes impact sensitive directories (e.g., `/infrastructure`, `/auth`), approval must be secured from designated individuals defined in the `CODEOWNERS` file.
* **Require status checks to pass:** Prior to merging, all automated CI pipelines (linters, unit tests, vulnerability scanners) must complete successfully.
* **Dismiss stale pull request approvals:** If a branch is updated after an approval, existing approvals are automatically revoked, requiring a re-review.
* **Restrict deletions:** Branch deletion of default or protected branches is restricted to Organization Administrators.

### 3.2 Commit Signing
* All commits must be cryptographically signed (GPG, SSH, or S/MIME keys) to guarantee authenticity and non-repudiation.
* Unsigned commits will be rejected automatically by GitHub push protection rules.

### 3.3 Security Gates
* **Static Application Security Testing (SAST):** GitHub Advanced Security (CodeQL) must run on every pull request. No PR can be merged with unresolved "High" or "Critical" vulnerability alerts.
* **Secret Scanning:** Active push protection must be enabled organization-wide to block commits containing plaintext API keys, passwords, or certificates.
