# Control Implementation Statements

**System:** Bundle — Electronic Healthcare Management System
**Document:** Control Implementation Statements
**Step:** Step 3 — Implement
**Version:** 1.0
**Prepared By:** Priya Nair, ISSE
**Reviewed By:** James Okafor, ISSO
**Approved By:** Dr. Sarah Mitchell, System Owner
**Date:** 2025

---

## What This Document Covers

For every security control selected in Step 2, this document provides
a detailed statement explaining exactly how that control is implemented
in Bundle. Each entry includes the implementation status and the
evidence that supports it.

---

## Implementation Status Definitions

| Status | Meaning |
|--------|---------|
| Implemented | Fully in place and operating. Evidence available. |
| Partially Implemented | In place but not fully meeting requirements. POA&M raised. |
| Planned | Not yet implemented. POA&M entry with target date exists. |
| Inherited | Implemented by AWS. Compliance docs retained as evidence. |

---

## AC — Access Control

### AC-2 — Account Management
**Status:** Implemented
**Owner:** James Okafor, ISSO

All Bundle user accounts are provisioned through AWS IAM following
receipt of a completed and signed Access Request Form approved by the
relevant department head. Accounts are created within one business day.
Role-Based Access Control (RBAC) is applied at account creation. Accounts
are reviewed quarterly against the HR active staff list. Any account not
on the active list is disabled immediately. When a staff member leaves,
HR notifies the ISSO within the same business day and the account is
disabled within 24 hours. Shared and generic accounts are prohibited.

**Evidence:** evidence/AC/AC-2-account-request-form.pdf |
evidence/AC/AC-2-quarterly-review-log.xlsx

---

### AC-3 — Access Enforcement
**Status:** Implemented
**Owner:** Priya Nair, ISSE

Role-Based Access Control is enforced at two layers. At the application
layer the Bundle web application checks the user role on every request.
At the database layer RDS PostgreSQL users are granted permissions
matching their application role. Six roles defined: Clinical Doctor,
Clinical Nurse, Administrator, Billing Staff, IT Admin, Read-Only.

**Evidence:** evidence/AC/AC-3-rbac-role-definitions.md |
evidence/AC/AC-3-access-control-matrix.xlsx

---

### AC-7 — Unsuccessful Login Attempts
**Status:** Implemented
**Owner:** Priya Nair, ISSE

AWS Cognito locks accounts after 5 consecutive failed login attempts
for 30 minutes. All lockout events generate an SNS alert to the ISSO.
Failed logins are recorded in CloudWatch with timestamp, username,
and source IP.

**Evidence:** evidence/AC/AC-7-cognito-lockout-config.png

---

## AU — Audit and Accountability

### AU-2 — Event Logging
**Status:** Implemented
**Owner:** Priya Nair, ISSE

Bundle logs all user authentication events, patient record access and
modification, administrative actions, system errors, failed access
attempts, AWS API calls via CloudTrail, and infrastructure changes to
AWS CloudWatch Logs in real time.

**Evidence:** evidence/AU/AU-2-cloudwatch-log-groups.png |
evidence/AU/AU-2-sample-log-entries.png

---

### AU-11 — Audit Record Retention
**Status:** Implemented
**Owner:** James Okafor, ISSO

CloudWatch logs retained 90 days active. Then exported automatically
to S3 (bundle-audit-archive) with S3 Object Lock for 12 further months.
After 15 months total, transitioned to S3 Glacier Deep Archive.
Meets and exceeds HIPAA audit log retention requirements.

**Evidence:** evidence/AU/AU-11-cloudwatch-retention.png |
evidence/AU/AU-11-s3-lifecycle-policy.json

---

## IA — Identification and Authentication

### IA-2 — Multi-Factor Authentication
**Status:** Implemented
**Owner:** Priya Nair, ISSE

All 500 Bundle users authenticate via AWS Cognito with two factors:
username plus password, and a TOTP code from an authenticator app.
MFA is enforced at the Cognito User Pool level and cannot be bypassed
by any user. Session tokens expire after 8 hours.

**Evidence:** evidence/IA/IA-2-cognito-mfa-config.png

---

### IA-5 — Authenticator Management
**Status:** Implemented
**Owner:** James Okafor, ISSO

Cognito password policy: minimum 14 characters, uppercase, lowercase,
number, and special character required. 90-day expiry. 24-password
history enforced. Temporary passwords expire in 24 hours. Users
receive automated reminder 14 days before expiry.

**Evidence:** evidence/IA/IA-5-cognito-password-policy.png

---

## SC — System and Communications Protection

### SC-7 — Boundary Protection
**Status:** Implemented
**Owner:** Priya Nair, ISSE

Bundle operates in a dedicated AWS VPC. Public subnet contains only
the Load Balancer and WAF. Application servers and database are in
private subnets with no public IP addresses. Security groups act as
virtual firewalls. All flows logged to VPC Flow Logs.

**Evidence:** evidence/SC/SC-7-vpc-architecture.png |
evidence/SC/SC-7-security-group-rules.png

---

### SC-28 — Protection of Information at Rest
**Status:** Implemented
**Owner:** Priya Nair, ISSE

All PHI encrypted at rest. RDS uses AES-256 via AWS KMS with a
customer-managed key. Annual key rotation enforced. S3 buckets use
SSE-KMS. EC2 EBS volumes encrypted with AWS-managed KMS keys.
No unencrypted storage exists in Bundle's environment.
Verified monthly via AWS Config rules.

**Evidence:** evidence/SC/SC-28-rds-encryption.png |
evidence/SC/SC-28-s3-encryption.png |
evidence/SC/SC-28-aws-config-rule.png

---

## IR — Incident Response

### IR-4 — Incident Handling
**Status:** Implemented
**Owner:** James Okafor, ISSO

Bundle follows the NIST SP 800-61 six-phase IR lifecycle: Preparation,
Detection and Analysis, Containment, Eradication, Recovery, and
Post-Incident Review. Immediate containment includes isolating affected
EC2 instances, revoking suspicious sessions, and blocking malicious IPs
at the WAF. Systems are rebuilt from clean AMIs rather than cleaned in
place.

**Evidence:** evidence/IR/IR-4-incident-response-procedure.md |
evidence/IR/IR-4-incident-tracker-template.xlsx

---

### IR-8 — Incident Response Plan
**Status:** Implemented
**Owner:** James Okafor, ISSO

Written IRP includes scope, roles and responsibilities, detection and
escalation procedures, and playbooks for Ransomware Attack, PHI Data
Breach, and Unauthorised Insider Access. Reviewed and tested annually
via tabletop exercise.

**Evidence:** evidence/IR/IR-8-incident-response-plan.md |
evidence/IR/IR-8-tabletop-exercise-report.md

---

## SI — System and Information Integrity

### SI-2 — Flaw Remediation
**Status:** Implemented
**Owner:** Priya Nair, ISSE

AWS Inspector performs automated monthly vulnerability scans of all
EC2 instances. Remediation SLAs: Critical within 15 days, High within
30 days, Medium within 90 days, Low within 180 days. All findings
tracked in the vulnerability tracker and POA&M.

**Evidence:** evidence/SI/SI-2-inspector-scan-report.pdf |
evidence/SI/SI-2-vulnerability-tracker.xlsx

---

### SI-3 — Malware Protection
**Status:** Implemented
**Owner:** Priya Nair, ISSE

CrowdStrike Falcon EDR deployed on all EC2 instances. Real-time
protection enabled. Definition updates every 4 hours. Any detection
triggers immediate PagerDuty alert to ISSO.

**Evidence:** evidence/SI/SI-3-crowdstrike-deployment.png

---

## CP — Contingency Planning

### CP-9 — System Backup
**Status:** Implemented
**Owner:** Priya Nair, ISSE

AWS RDS automated backups run daily. 35-day retention. Point-in-time
recovery enabled. Backups replicated cross-region to AWS US West.
S3 documents replicated via S3 Cross-Region Replication. Backup
completion verified daily by automated Lambda function.

**Evidence:** evidence/CP/CP-9-rds-backup-config.png |
evidence/CP/CP-9-restoration-test-report.md

---

## RA — Risk Assessment

### RA-5 — Vulnerability Scanning
**Status:** Implemented
**Owner:** Priya Nair, ISSE

AWS Inspector scans all EC2 instances monthly. OWASP ZAP quarterly
web application scans against Bundle HTTPS endpoints. All findings
entered into Vulnerability Tracker and POA&M. Scan reports retained
as evidence.

**Evidence:** evidence/RA/RA-5-inspector-report.pdf |
evidence/RA/RA-5-owasp-zap-report.pdf

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 | Priya Nair | All implementation statements completed |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

