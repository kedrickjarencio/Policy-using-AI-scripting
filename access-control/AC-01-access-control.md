# POL-AC-01: Identity, Authentication, and Access Control Policy

## 1. Purpose
To establish cryptographic identity verification, mandate the Principle of Least Privilege, and ensure strict credential management to protect organizational resources on GitHub.

## 2. Scope
Applies to all internal employees, contractors, third-party collaborators, and automated service accounts accessing the GitHub organization.

## 3. Mandatory Access Controls

### 3.1 Authentication & Multi-Factor Authentication (MFA)
* **Identity Provider (IdP) Integration:** All users must authenticate via Enterprise Single Sign-On (SSO) integrated with the company's centralized Directory (e.g., Okta, Entra ID).
* **Enforced MFA:** Multi-Factor Authentication (MFA) is strictly required for all GitHub accounts within the organization. Accounts failing to enroll in MFA within 24 hours of invitation will be automatically deprovisioned.
* **Session Lifetimes:** Idle sessions on GitHub Enterprise UI must be restricted to a maximum of 8 hours before requiring re-authentication.

### 3.2 Access Provisioning & Least Privilege
* **Default Permissions:** The default base permission for all organization members is set to **Read** only. 
* **Role-Based Access Control (RBAC):** Repository access must be granted using GitHub Teams. Direct individual user assignments to repositories are strictly prohibited.
* **Collaborator Policy:** External, third-party collaborators may only be added to private repositories with formal approval from the Information Security Team, subject to a bi-annual access review.

### 3.3 Token & Credential Lifetimes
* **Personal Access Tokens (PATs):** Only fine-grained Personal Access Tokens are permitted. Classic PATs are blocked at the organization policy level.
* **Token Expiration:** No PAT may exceed an expiration window of **30 days**.
* **IP Allow List:** Access to the Enterprise Organization resources via SSH, HTTPS, or API is restricted to authorized company VPN IP ranges.
