# AWS IAM LEAST-PRIVILEGE ROLE MATRIX
**Document ID:** MX-IAM-2026-002  
**Classification:** Internal Corporate Use Only  
**Framework Alignment:** AWS IAM Best Practices / CompTIA Security+  

## 1. PURPOSE
This role matrix defines the standard functional roles authorized within the corporate AWS environment. To prevent privilege creep and enforce the Principle of Least Privilege, all user access must be assigned strictly via membership in these pre-configured groups. Direct inline policy attachment to individual IAM users is prohibited.

## 2. FUNCTIONAL ROLE DEFINITIONS

| Department / Role | AWS IAM Group Name | Attached AWS Managed Policies | Access Description / Justification |
| :--- | :--- | :--- | :--- |
| **Cloud Administrator** | `IAM-Group-CloudAdmin` | `AdministratorAccess` | Full access to all AWS resources. Reserved strictly for central IT infrastructure leads. |
| **Software Engineer** | `IAM-Group-Developer` | `AmazonEC2FullAccess`<br>`AmazonRDSFullAccess` | Permissions to build, configure, and maintain application servers and databases. |
| **Data Analyst** | `IAM-Group-DataAnalyst` | `AmazonS3ReadOnlyAccess` | Read-only access to specific S3 storage buckets containing data warehouse exports. Cannot delete files. |
| **Finance & Billing** | `IAM-Group-Finance` | `AWSBillingConduitFullAccess` | Access to the AWS Billing Dashboard to download invoices and review spend data. No infrastructure access. |
| **Security Auditor** | `IAM-Group-SecAuditor` | `SecurityAudit`<br>`AWSCloudTrail_ReadOnlyAccess` | Read-only access to view configurations, logs, and compliance dashboards without edit rights. |

## 3. CORE ENFORCEMENT RULES
1. **No Shared Accounts:** Every individual must use a unique IAM user account mapped to their corporate email. Shared administrative credentials are strictly forbidden.
2. **Explicit Deny on Root:** The AWS Account Root User must never be utilized for daily operational tasks. The root credentials are locked behind physical security controls with hardware-based MFA enabled.
3. **MFA Gate:** Any account missing Multi-Factor Authentication configuration will have an explicit `Deny` policy applied automatically across all AWS services.
