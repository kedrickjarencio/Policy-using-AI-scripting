# POL-IR-01: Information Security Incident Management Policy

## 1. Purpose
This policy establishes a coordinated approach to identifying, classifying, managing, and resolving information security incidents. The objective is to minimize operational downtime, protect organizational assets, and fulfill legal, regulatory, and contractual notification obligations.

## 2. Scope
This policy applies to all production environments, corporate infrastructure, source code repositories, and physical facilities. It encompasses all employees, contractors, and third-party vendors operating on behalf of the organization.

## 3. Incident Governance & Ownership
* **Policy Owner:** Head of Information Security / CISO.
* **Primary Responders:** Dedicated Security Team (SecOps).
* **System of Record:** All incident tracking, communication, and post-mortem notes must be documented within the centralized **Jira Service Management (JSM)** system under the designated Security project (`SEC-IR`).

## 4. Incident Lifecycle Procedures

### Phase 1: Identification & Logging
* **Internal Reporting:** Any employee who suspects a security anomaly or data breach must raise an emergency ticket via the **Jira Service Desk Portal** immediately.
* **Automated Alerting:** Continuous monitoring systems (SIEM, log aggregators, and runtime cloud security tools) are configured to automatically generate high-priority tickets within Jira via webhook integration upon detecting anomalous behavior.
* **Centralized Registry:** To guarantee an immutable audit trail for SOC 2 and ISO 27001 auditors, Jira ticket deletions are strictly disabled across the organization.

### Phase 2: Classification & Severity Matrix
Upon ticket creation, the **Dedicated Security Team** must instantly triage the event based on the following framework:

| Severity Level | Definition | Response SLA | Escalation Path |
| :--- | :--- | :--- | :--- |
| **P1 - Critical** | Active data breach involving PII/sensitive data, or total production outage. | **Within 30 Mins** | Dedicated Security Team, Legal, CISO, Executive Board |
| **P2 - High** | Localized system compromise or partial degradation of critical production services. | **Within 2 Hours** | Dedicated Security Team, IT Infrastructure Lead |
| **P3 - Medium** | Isolated malware detection on an endpoint or minor policy violation with no data loss. | **Within 12 Hours** | On-Duty Security Analyst |
| **P4 - Low** | Phishing attempt reported by user; standard vulnerability scan findings. | **Within 24 Hours** | Helpdesk / IT Support Tier 1 |

### Phase 3: Containment, Eradication, & Recovery
* **Containment:** The Dedicated Security Team will execute immediate tactical actions to limit the blast radius (e.g., isolating networks, rotating compromised keys, revoking credential access).
* **Eradication:** The Security Team, in coordination with Engineering, will neutralize the root cause (e.g., purging malicious binaries, rebuilding affected microservices from known secure images).
* **Recovery:** Systems must be safely restored to normal operations using verified, clean backups, followed by a minimum of 48 hours of enhanced logging and monitoring.

### Phase 4: Regulatory & Contractual Notifications
* **Strict Data Privacy Mandate:** In compliance with strict regional and global data privacy regulations, if a P1 incident involves unauthorized access, alteration, or exposure of Personal Identifiable Information (PII), the Compliance Officer and Legal Team must notify the relevant Privacy Authorities and affected data subjects **within 72 hours** of breach confirmation.
* **Auditor Tracking:** All regulatory notifications, correspondence, and evidence logs must be attached directly to the corresponding Jira incident ticket to satisfy SOC 2 CC7.3/CC7.4 criteria.

### Phase 5: Post-Incident Review & Lessons Learned
* For all **P1** and **P2** incidents, the Dedicated Security Team must lead a formal Post-Incident Review (PIR) within five (5) business days of resolution.
* The review must document the root cause, timeline of events, containment efficacy, and permanent preventative fixes.
* The finalized PIR report must be attached to the Jira issue, and the ticket status marked as `Resolved-Closed` only after engineering management sign-off.
