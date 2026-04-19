# Step 3 — Implement

![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![RMF Step](https://img.shields.io/badge/RMF%20Step-3%20Implement-blue)
![SSP](https://img.shields.io/badge/SSP-Final-brightgreen)
![Controls](https://img.shields.io/badge/Controls-Documented-brightgreen)

---

## What is the Implement Step?

In Step 2 we chose which security controls Bundle needs. In Step 3 we prove they are actually switched on and working.

For every selected control this step provides:

- A detailed **implementation statement** — exactly what was done, how it was configured, and where it runs in Bundle's environment
- An **implementation status** — Implemented, Partially Implemented, Planned, or Inherited
- Named **evidence** — the specific files, screenshots, and documents that prove the control is in place

This step also **finalises the System Security Plan (SSP)** — the master security document that will be handed to the Authorizing Official in Step 5.

> The quality of Step 3 directly affects how smoothly the assessment in Step 4 goes. Clear, specific, evidence-backed statements make the assessor's work straightforward and demonstrate a mature security programme.

---

## Documents in This Folder

| File | Description |
|------|-------------|
| `README.md` | This file — overview and implementation status summary |
| `control-implementation-statements.md` | Full implementation statements for all controls |
| `system-security-plan-final.md` | Completed SSP — all ten sections |
| `implementation-status-tracker.xlsx` | Control status tracker with POA&M references |
| `evidence/` | Folder containing all supporting evidence by control family |

---

## Implementation Status Definitions

| Status | Meaning |
|--------|---------|
| ✅ **Implemented** | Fully in place and operating. Evidence available. |
| 🔄 **Partially Implemented** | In place but not fully meeting requirements. POA&M entry raised. |
| 📋 **Planned** | Not yet implemented. POA&M entry with target date exists. |
| 🏢 **Inherited** | Implemented by AWS. Bundle team has verified compliance docs. |

---

## Control Implementation Statements

### AC — Access Control

---

#### AC-2 — Account Management
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** James Okafor (ISSO)

All Bundle user accounts are provisioned through AWS IAM following receipt of a completed and signed Access Request Form approved by the relevant department head. The ISSO creates accounts within one business day of approval. Role-Based Access Control (RBAC) is applied at account creation. Accounts are reviewed quarterly against the current HR active staff list. Any account not on the active list is disabled immediately. When a staff member leaves, HR notifies the ISSO within the same business day and the account is disabled within 24 hours. Shared and generic accounts are prohibited. All account management actions are logged in AWS CloudTrail.

**Evidence:** `evidence/AC/AC-2-account-request-form-template.pdf` | `evidence/AC/AC-2-quarterly-review-log.xlsx` | `evidence/AC/AC-2-cloudtrail-screenshot.png`

---

#### AC-3 — Access Enforcement (RBAC)
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

Role-Based Access Control is enforced at two layers. At the application layer, the Bundle web application checks the user's assigned role on every request. At the database layer, RDS PostgreSQL users are granted permissions matching their application role. The six roles are: Clinical Doctor (full EHR read/write), Clinical Nurse (EHR read, medication write), Administrator (scheduling/registration), Billing Staff (financial records only), IT Admin (full system, separate privileged account), and Read-Only Management (dashboards only).

**Evidence:** `evidence/AC/AC-3-rbac-role-definitions.md` | `evidence/AC/AC-3-access-control-matrix.xlsx` | `evidence/AC/AC-3-db-permissions-screenshot.png`

---

#### AC-6 — Least Privilege
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** Priya Nair (ISSE)

All IAM policies follow least privilege — service accounts have only the permissions required for their specific function. No IAM user has AdministratorAccess attached. IT administrators use separate privileged accounts only when elevated access is genuinely required. Privileged account usage is logged and reviewed monthly by the ISSO.

**Evidence:** `evidence/AC/AC-6-iam-policy-review-screenshot.png` | `evidence/AC/AC-6-privileged-account-usage-log.xlsx`

---

#### AC-7 — Unsuccessful Login Attempts
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** Priya Nair (ISSE)

AWS Cognito locks accounts after 5 consecutive failed login attempts. Lockout period is 30 minutes. All lockout events generate an automated SNS alert to the ISSO. Failed logins are recorded in CloudWatch with timestamp, username, and source IP. GuardDuty flags repeated failures across multiple accounts as potential brute force.

**Evidence:** `evidence/AC/AC-7-cognito-lockout-config-screenshot.png` | `evidence/AC/AC-7-cloudwatch-failed-login-sample.png`

---

#### AC-11 — Session Lock
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** Priya Nair (ISSE)

Bundle sessions automatically time out after 15 minutes of inactivity. Screen content is hidden and re-authentication (password + MFA) is required to resume. Timeout is enforced server-side and cannot be overridden by the client. Critical in Bundle's clinical environment where shared workstations are common.

**Evidence:** `evidence/AC/AC-11-session-timeout-config-screenshot.png` | `evidence/AC/AC-11-session-lock-ui-mockup.png`

---

#### AC-17 — Remote Access
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** James Okafor (ISSO)

Remote administrative access requires VPN connection before any AWS console or SSH access is possible. VPN itself requires MFA. Clinical and administrative staff access Bundle only via HTTPS web application — no direct backend access for standard users. VPN accounts reviewed quarterly. All VPN connections logged.

**Evidence:** `evidence/AC/AC-17-vpn-access-policy.md` | `evidence/AC/AC-17-vpn-account-review.xlsx` | `evidence/AC/AC-17-vpn-log-sample.png`

---

### AU — Audit and Accountability

---

#### AU-2 — Event Logging
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

Bundle logs the following in real time to AWS CloudWatch: all authentication events; all patient record access and modification; all administrative actions; all system errors; all failed access attempts; all AWS API calls via CloudTrail; all infrastructure changes. CloudWatch agent is installed on all EC2 instances and deployed via AWS Systems Manager.

**Evidence:** `evidence/AU/AU-2-cloudwatch-log-groups-screenshot.png` | `evidence/AU/AU-2-cloudwatch-agent-config.json` | `evidence/AU/AU-2-sample-log-entries.png`

---

#### AU-6 — Audit Record Review
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** James Okafor (ISSO)

The ISSO conducts manual log review every Monday covering the preceding 7 days. Focus areas: failed login patterns, mass record access events, admin actions outside business hours, GuardDuty HIGH findings. Results recorded in the Audit Review Log. Automated CloudWatch alarms alert the ISSO immediately for: 10+ failed logins from a single IP in 5 minutes, logins from unexpected geographies, and any attempt to access the audit logs themselves.

**Evidence:** `evidence/AU/AU-6-weekly-audit-review-log.xlsx` | `evidence/AU/AU-6-cloudwatch-alarm-config-screenshot.png`

---

#### AU-9 — Audit Record Protection
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

IAM policy restricts CloudWatch log access to ISSO and designated backup security officer only. An explicit IAM deny policy prevents log deletion by any user including administrators. CloudTrail log file validation creates a hash of every log file — tampering is detectable. Audit log access is itself audited in a separate CloudTrail log.

**Evidence:** `evidence/AU/AU-9-iam-log-protection-policy.json` | `evidence/AU/AU-9-cloudtrail-validation-screenshot.png`

---

#### AU-11 — Audit Record Retention
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** James Okafor (ISSO)

CloudWatch logs retained 90 days (active). Then exported automatically to S3 (bundle-audit-archive) with S3 Object Lock for 12 further months. After 15 months total, transitioned to S3 Glacier Deep Archive for long-term storage. Meets and exceeds HIPAA audit log retention requirements. Retention configuration reviewed annually.

**Evidence:** `evidence/AU/AU-11-cloudwatch-retention-screenshot.png` | `evidence/AU/AU-11-s3-lifecycle-policy.json` | `evidence/AU/AU-11-s3-object-lock-screenshot.png`

---

### IA — Identification and Authentication

---

#### IA-2 — Multi-Factor Authentication (All Users)
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

All Bundle users authenticate via AWS Cognito with two factors: (1) username + password, (2) TOTP code from an authenticator app. MFA enforced at the Cognito User Pool level — cannot be bypassed by any user. Integrated with Bundle application via OAuth 2.0 / OIDC. Session tokens expire after 8 hours.

**Evidence:** `evidence/IA/IA-2-cognito-mfa-config-screenshot.png` | `evidence/IA/IA-2-mfa-enforcement-policy.md`

---

#### IA-2(1) — MFA for Privileged Accounts
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

IT administrators and ISSO require hardware MFA tokens (YubiKey 5 FIDO2/WebAuthn) for all privileged access. Software TOTP is not accepted for privileged accounts. Lost/stolen tokens are reported immediately and the account locked pending replacement.

**Evidence:** `evidence/IA/IA-2-1-yubikey-registration-log.xlsx` | `evidence/IA/IA-2-1-privileged-mfa-policy.md`

---

#### IA-5 — Authenticator Management (Passwords)
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** James Okafor (ISSO)

Cognito password policy: minimum 14 characters, uppercase + lowercase + number + special character required, 90-day expiry, 24-password history, temporary passwords expire in 24 hours. Users receive automated reminder 14 days before expiry. Password resets require MFA verification before reset link is sent.

**Evidence:** `evidence/IA/IA-5-cognito-password-policy-screenshot.png` | `evidence/IA/IA-5-password-policy-document.md`

---

### SC — System and Communications Protection

---

#### SC-7 — Boundary Protection
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

Bundle operates in a dedicated AWS VPC with layered architecture. Public subnet: Load Balancer + WAF only — no app servers or databases are internet-accessible. Private app subnet: EC2 instances (no public IPs). Private DB subnet: RDS PostgreSQL. Security groups act as virtual firewalls per component. NACLs provide secondary subnet-level filtering. All flows logged to VPC Flow Logs.

**Evidence:** `evidence/SC/SC-7-vpc-architecture-diagram.png` | `evidence/SC/SC-7-security-group-rules-screenshot.png` | `evidence/SC/SC-7-vpc-flow-logs-sample.png`

---

#### SC-8 — Transmission Encryption
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** Priya Nair (ISSE)

All user-to-Bundle traffic encrypted using TLS 1.2 minimum (TLS 1.3 preferred). TLS 1.0 and 1.1 explicitly disabled on the Application Load Balancer. Certificate managed by AWS ACM with automatic renewal. Internal RDS traffic encrypted in transit (require_ssl = on). TLS configuration achieves A rating on SSL Labs. Reviewed quarterly.

**Evidence:** `evidence/SC/SC-8-alb-tls-policy-screenshot.png` | `evidence/SC/SC-8-rds-ssl-config-screenshot.png` | `evidence/SC/SC-8-ssl-labs-result.png`

---

#### SC-28 — Protection of Information at Rest
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

All PHI encrypted at rest: RDS uses AES-256 via AWS KMS (customer-managed key, annual rotation). S3 buckets use SSE-KMS — bucket policies deny unencrypted PutObject requests. EBS volumes encrypted with AWS-managed KMS keys. No unencrypted storage exists in Bundle's environment. Verified monthly via AWS Config rules.

**Evidence:** `evidence/SC/SC-28-rds-encryption-screenshot.png` | `evidence/SC/SC-28-s3-encryption-screenshot.png` | `evidence/SC/SC-28-aws-config-rule-screenshot.png`

---

### IR — Incident Response

---

#### IR-4 — Incident Handling
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** James Okafor (ISSO)

Bundle follows the NIST SP 800-61 six-phase IR lifecycle: (1) Preparation — plan documented, staff trained, tools ready. (2) Detection — GuardDuty, CloudWatch alarms, weekly log reviews. (3) Containment — isolate EC2 instances, revoke sessions, block IPs at WAF. (4) Eradication — root cause removed; systems rebuilt from clean AMIs. (5) Recovery — restored from clean backup, monitored 72hrs post-recovery. (6) Post-Incident Review — lessons learned within 5 business days.

**Evidence:** `evidence/IR/IR-4-incident-response-procedure.md` | `evidence/IR/IR-4-incident-tracker-template.xlsx` | `evidence/IR/IR-4-sample-incident-report.md`

---

#### IR-6 — Incident Reporting
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** James Okafor (ISSO)

All users must report suspected incidents to ISSO within 1 hour via dedicated email or direct call. ISSO acknowledges within 30 minutes. For HIPAA reportable breaches: affected individuals notified within 60 days; HHS notified within 60 days; media notification required if breach affects 500+ patients. All reports retained for 6 years per HIPAA.

**Evidence:** `evidence/IR/IR-6-incident-reporting-procedure.md` | `evidence/IR/IR-6-hipaa-breach-notification-template.md`

---

#### IR-8 — Incident Response Plan
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** James Okafor (ISSO)

Written IRP includes: scope and objectives, roles and responsibilities, detection and escalation procedures, and three specific playbooks: Ransomware Attack, PHI Data Breach, and Unauthorised Insider Access. Reviewed and tested annually via tabletop exercise. Most recent tabletop exercise report retained as evidence.

**Evidence:** `evidence/IR/IR-8-incident-response-plan.md` | `evidence/IR/IR-8-ransomware-playbook.md` | `evidence/IR/IR-8-tabletop-exercise-report-2025.md`

---

### SI — System and Information Integrity

---

#### SI-2 — Flaw Remediation
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** Priya Nair (ISSE)

AWS Inspector scans all EC2 instances monthly. Remediation SLAs: Critical (CVSS 9+) → 15 days, High (CVSS 7-8.9) → 30 days, Medium → 90 days, Low → 180 days. Amazon Linux 2023 automatic security patching enabled for OS patches. OWASP Dependency Check integrated into CI/CD pipeline blocks deployment if known vulnerable dependencies are detected. All open CVEs tracked in POA&M.

**Evidence:** `evidence/SI/SI-2-aws-inspector-scan-report-sample.pdf` | `evidence/SI/SI-2-vulnerability-tracker.xlsx` | `evidence/SI/SI-2-patch-management-policy.md`

---

#### SI-3 — Malware Protection
**Status:** ✅ Implemented | **Type:** System-Specific | **Owner:** Priya Nair (ISSE)

CrowdStrike Falcon EDR deployed on all EC2 instances. Real-time protection enabled — cannot be disabled by any application user. Definition updates every 4 hours. Any detection triggers immediate PagerDuty alert to ISSO. Behavioural detection monitors for ransomware indicators (mass file encryption) and lateral movement. Monthly CrowdStrike reports reviewed by ISSE.

**Evidence:** `evidence/SI/SI-3-crowdstrike-deployment-screenshot.png` | `evidence/SI/SI-3-monthly-report-sample.pdf`

---

#### SI-4 — System Monitoring
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

Three-layer monitoring: CloudWatch (infrastructure metrics and alarms), GuardDuty (ML-based threat detection across CloudTrail, VPC Flow Logs, DNS — identifies unusual API patterns, malicious IPs, credential exfiltration), Security Hub (aggregates findings from GuardDuty, Inspector, Config into single dashboard). ISSO reviews Security Hub weekly. All HIGH/CRITICAL GuardDuty findings generate immediate alerts.

**Evidence:** `evidence/SI/SI-4-cloudwatch-dashboard-screenshot.png` | `evidence/SI/SI-4-guardduty-findings-screenshot.png` | `evidence/SI/SI-4-security-hub-screenshot.png`

---

### CP — Contingency Planning

---

#### CP-9 — System Backup
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

RDS automated backups run daily (02:00-03:00 UTC), 35-day retention, point-in-time recovery enabled (max 5-minute data loss). Backups replicated cross-region to AWS US West via AWS Backup. S3 documents replicated via S3 Cross-Region Replication. Backup completion verified daily by automated Lambda function — ISSO alerted on failure. Restoration capability tested quarterly.

**Evidence:** `evidence/CP/CP-9-rds-backup-config-screenshot.png` | `evidence/CP/CP-9-cross-region-backup-screenshot.png` | `evidence/CP/CP-9-restoration-test-report-Q1-2025.md`

---

#### CP-10 — System Recovery
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

Full AWS infrastructure defined as code in AWS CloudFormation templates — stored in S3 and version-controlled in GitHub. Full environment rebuild achievable in under 2 hours. Tested Recovery Runbook documents: database restore from RDS backup, EC2 relaunch from golden AMI, DNS failover to DR region, user communication procedures. RTO: 4 hours (validated). RPO: 24 hours (validated). Annual DR test conducted.

**Evidence:** `evidence/CP/cloudformation-templates/` | `evidence/CP/CP-10-recovery-runbook.md` | `evidence/CP/CP-10-dr-test-report-2025.md`

---

### RA — Risk Assessment

---

#### RA-5 — Vulnerability Scanning
**Status:** ✅ Implemented | **Type:** Hybrid | **Owner:** Priya Nair (ISSE)

Two scan tracks: (1) Infrastructure — AWS Inspector monthly on all EC2 instances, results reviewed within 3 business days. (2) Web application — OWASP ZAP quarterly in authenticated scan mode testing OWASP Top 10, run against staging before production. All findings entered into Vulnerability Tracker and POA&M. Scan reports retained for Step 4 assessment evidence.

**Evidence:** `evidence/RA/RA-5-inspector-monthly-report-sample.pdf` | `evidence/RA/RA-5-owasp-zap-report-Q1-2025.pdf` | `evidence/RA/RA-5-vulnerability-tracker.xlsx`

---

## Implementation Status Summary

| Control | Name | Status | POA&M |
|---------|------|--------|-------|
| AC-2 | Account Management | ✅ Implemented | — |
| AC-3 | Access Enforcement | ✅ Implemented | — |
| AC-6 | Least Privilege | ✅ Implemented | — |
| AC-7 | Unsuccessful Login Attempts | ✅ Implemented | — |
| AC-11 | Session Lock | ✅ Implemented | — |
| AC-17 | Remote Access | ✅ Implemented | — |
| AU-2 | Event Logging | ✅ Implemented | — |
| AU-6 | Audit Record Review | ✅ Implemented | — |
| AU-9 | Audit Record Protection | ✅ Implemented | — |
| AU-11 | Audit Record Retention | ✅ Implemented | — |
| IA-2 | MFA — All Users | ✅ Implemented | — |
| IA-2(1) | MFA — Privileged Accounts | ✅ Implemented | — |
| IA-5 | Authenticator Management | ✅ Implemented | — |
| SC-7 | Boundary Protection | ✅ Implemented | — |
| SC-8 | Transmission Encryption | ✅ Implemented | — |
| SC-28 | Protection of Information at Rest | ✅ Implemented | — |
| IR-4 | Incident Handling | ✅ Implemented | — |
| IR-6 | Incident Reporting | ✅ Implemented | — |
| IR-8 | Incident Response Plan | ✅ Implemented | — |
| SI-2 | Flaw Remediation | ✅ Implemented | — |
| SI-3 | Malware Protection | ✅ Implemented | — |
| SI-4 | System Monitoring | ✅ Implemented | — |
| CP-9 | System Backup | ✅ Implemented | — |
| CP-10 | System Recovery | ✅ Implemented | — |
| RA-5 | Vulnerability Scanning | ✅ Implemented | — |
| AT-2 | Security Awareness Training | 🔄 Partially Implemented | POA&M-003 |
| CM-6 | Configuration Settings | 🔄 Partially Implemented | POA&M-004 |
| PS-3 | Personnel Screening | 🔄 Partially Implemented | POA&M-005 |
| PE Controls | Physical Protection | 🏢 Inherited (AWS) | AWS SOC 2 + ISO 27001 |
| SC-39 | Process Isolation | 🏢 Inherited (AWS) | AWS Shared Responsibility docs |

---

## Evidence Folder Structure

```
evidence/
├── AC/          Access Control — request forms, RBAC matrix, review logs
├── AU/          Audit — CloudWatch samples, retention configs, review logs
├── IA/          Identity and Authentication — Cognito configs, MFA policy, YubiKey logs
├── SC/          System and Communications — VPC diagram, TLS config, encryption screenshots
├── IR/          Incident Response — IR plan, playbooks, tabletop exercise report
├── SI/          System Integrity — Inspector reports, CrowdStrike reports, GuardDuty screenshots
├── CP/          Contingency Planning — backup configs, restoration tests, DR test report
├── RA/          Risk Assessment — vulnerability scan reports, tracker
├── aws-compliance/   AWS SOC 2, ISO 27001, HIPAA BAA
└── policies/    All Bundle security policies
```

---

## SSP Final Status

| SSP Section | Status |
|-------------|--------|
| 1 — System Information | ✅ Complete |
| 2 — System Purpose and Description | ✅ Complete |
| 3 — System Environment and Architecture | ✅ Complete |
| 4 — System Boundary | ✅ Complete |
| 5 — Applicable Laws and Regulations | ✅ Complete |
| 6 — Control Implementation Statements | ✅ Complete |
| 7 — Roles and Responsibilities | ✅ Complete |
| 8 — Interconnections and Interfaces | ✅ Complete |
| 9 — Information Types and Categorization | ✅ Complete |
| 10 — Control Selection and Tailoring | ✅ Complete |

> The Bundle SSP is complete and ready to be included in the Step 5 authorization package.

---

## Implement Step Checklist

| Task | NIST Task ID | Status |
|------|-------------|--------|
| Implementation statements written for all controls | I-1 | ✅ Complete |
| Implementation status assigned to each control | I-2 | ✅ Complete |
| Evidence items identified and named per control | I-3 | ✅ Complete |
| Evidence folder structure created in repository | I-4 | ✅ Complete |
| Partially implemented / planned controls in POA&M | I-5 | ✅ Complete |
| SSP finalised and saved | I-6 | ✅ Complete |
| System Owner approval granted | I-7 | ✅ Complete |

---

## Next Step

With the SSP finalised and all controls documented, the project moves to **Step 4 — Assess**.

An independent assessor will test each control, identify any gaps, and produce the Security Assessment Report (SAR). Any new findings will be added to the POA&M.

➡️ [Go to Step 4 — Assess](../04-assess/README.md)  
⬅️ [Back to Step 2 — Select](../02-select/README.md)

---

## Document Information

| Field | Value |
|-------|-------|
| Document Version | 1.0 |
| Prepared By | Priya Nair, ISSE |
| Reviewed By | James Okafor, ISSO |
| Approved By | Dr. Sarah Mitchell, System Owner |
| NIST Reference | NIST SP 800-37 Rev. 2 — Implement Step |
| Supporting Reference | NIST SP 800-53A Rev. 5 (Assessment Procedures) |

---

*This document is part of the Bundle RMF portfolio project. All names, data, and scenarios are fictional and used for learning and career development purposes only.*

