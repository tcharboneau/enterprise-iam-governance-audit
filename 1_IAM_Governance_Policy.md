# ENTERPRISE IDENTITY & ACCESS MANAGEMENT (IAM) POLICY
**Document ID:** POL-IAM-2026-001  
**Classification:** Internal Corporate Policy  
**Framework Alignment:** CompTIA Security+ / AWS IAM Best Practices  

## 1. OBJECTIVE & SCOPE
This policy establishes the mandatory governance framework for managing digital identities, user access rights, and cloud account lifecycles. It applies to all full-time employees, contractors, and third-party vendors accessing corporate AWS cloud environments.

## 2. THE PRINCIPLE OF LEAST PRIVILEGE
All access granted within corporate cloud infrastructure must strictly adhere to the **Principle of Least Privilege**. Users shall only be provisioned with the minimum necessary access rights required to perform their explicit job functions. Standard accounts must never possess administrative or root-level permissions.

## 3. IDENTITY LIFECYCLE MANAGEMENT

### 3.1 Employee Onboarding Procedure
* **Request Lifecycle:** All new user access requests must originate from HR via an authorized ticketing system.
* **Role Mapping:** Access must be provisioned using pre-defined AWS IAM Roles based on job description. Direct attachment of policies to individual users is strictly prohibited.
* **MFA Enforcement:** Multi-Factor Authentication (MFA) must be configured and verified during the initial login session before production access is granted.

### 3.2 Employee Offboarding & Access Revocation Procedure
* **SLA for Involuntary Termination:** Access to all corporate networks, single sign-on (SSO) portals, and AWS cloud environments must be revoked **immediately** (within 1 hour) upon notification from HR.
* **SLA for Voluntary Separation:** Access must be disabled no later than **18:00 hours** on the employee's final active working day.
* **Account Deletion:** User accounts must be disabled first to preserve audit logs, followed by permanent deletion after a 30-day retention window.

## 4. MANDATORY USER ACCESS REVIEWS (UAR)
The cybersecurity compliance team shall conduct a comprehensive **User Access Review (UAR)** on a quarterly basis. Any discovered account belonging to an inactive or terminated employee must be treated as a **Severity 1 Security Incident**, resulting in immediate account locking and an forensic lookback audit of the account's recent activity.
