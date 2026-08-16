# QUARTERLY USER ACCESS REVIEW (UAR) AUDIT REPORT
**Audit Period:** Q1 2026  
**Auditor:** GRC Compliance Analyst  
**Audit Date:** March 15, 2026  
**Status:** REMEDIATED / CLOSED  

## 1. AUDIT METHODOLOGY
The cybersecurity compliance team conducted an automated and manual reconciliation of all active accounts within the corporate AWS IAM environment. The active AWS user roster was cross-referenced directly against the official active employee master list provided by the Human Resources (HR) Department. A total of 50 accounts were audited.

## 2. COMPLIANCE METRICS SUMMARY
* **Total Accounts Reviewed:** 50
* **Accounts Mapped to Active Employees:** 48
* **Critical Access Anomalies Discovered:** 2
* **MFA Non-Compliance Issues:** 0

## 3. AUDIT FINDINGS LOG & EXCEPTION REPORT

| User ID / Corporate Email | Assigned AWS IAM Group | HR Status | Audit Status | Risk / Security Violation | Remediation Action Taken |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `j.doe@company.com` | `IAM-Group-Developer` | Active | **PASS** | Compliant access matching role profile. | None required. |
| `m.smith@company.com` | `IAM-Group-Finance` | Active | **PASS** | Compliant access matching role profile. | None required. |
| **`t.stark@company.com`** | `IAM-Group-CloudAdmin` | **TERMINATED**<br>(Feb 14, 2026) | 🔴 **CRITICAL FAIL** | **Stale Administrative Access:** Ex-employee retained full `AdministratorAccess` permissions 30 days post-separation. | **Immediate Access Revocation:** Account locked, login profile deleted, and active API access keys rotated within 15 minutes of discovery. |
| **`n.romanoff@company.com`** | `IAM-Group-DataAnalyst` | **TERMINATED**<br>(Mar 01, 2026) | 🔴 **CRITICAL FAIL** | **Stale Data Access:** Ex-employee retained read access to production S3 data buckets 14 days post-separation. | **Immediate Access Revocation:** Account disabled and credentials purged. |

## 4. ROOT CAUSE ANALYSIS & PROCESS IMPROVEMENT
An investigation into the two critical compliance failures revealed an administrative breakdown in communication. The HR department failed to submit the official offboarding tickets to the IT Security helpdesk upon the employees' separation dates, violating the 1-hour access revocation SLA defined in **POL-IAM-2026-001**.

### Mandatory Corrective Actions:
1. **API Integration:** Transition the manual quarterly review process to an automated sync between the HR Identity Management system and AWS IAM via AWS IAM Identity Center.
2. **HR Retraining:** Conduct a mandatory training session with the HR offboarding team regarding SLA enforcement for involuntary separations.
3. **Forensic Lookback:** Initiated an AWS CloudTrail log review for both stale accounts. Confirmed that no unauthorized logins or data exfiltration events occurred between their termination dates and the audit remediation date.
