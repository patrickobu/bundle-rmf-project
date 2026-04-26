# Tailoring Decisions

![System](https://img.shields.io/badge/System-Bundle%20EHMS-blue)
![Step](https://img.shields.io/badge/RMF%20Step-2%20Select-blue)
![Baseline](https://img.shields.io/badge/Baseline-NIST%20800--53%20HIGH-red)
![Decisions](https://img.shields.io/badge/Tailoring%20Decisions-8-orange)
![Status](https://img.shields.io/badge/Status-Approved-brightgreen)

---

## What is Tailoring?

Tailoring is the process of adjusting the selected
control baseline to make it more appropriate for
Bundle's specific environment, mission, and risk
profile.

NIST SP 800-53B allows organisations to:
- **Add controls** that are not in the baseline but
  are needed for the specific system
- **Remove controls** that do not apply to the system
- **Modify parameters** to fit the organisation's
  specific requirements

Every tailoring decision must be documented and
justified. The Authorizing Official reviews and
approves all tailoring decisions before the SSP
is finalised.

---

## Tailoring Decisions Summary

| ID | Control | Decision | Type | Approved By |
|----|---------|---------|------|-------------|
| TD-001 | AC-2(4) | ADDED | Addition | Priya Nair, ISSE |
| TD-002 | AC-11(1) | ADDED | Addition | Priya Nair, ISSE |
| TD-003 | IA-2(6) | ADDED | Addition | Priya Nair, ISSE |
| TD-004 | SC-28(1) | ADDED | Addition | Priya Nair, ISSE |
| TD-005 | SI-4(2) | ADDED | Addition | Priya Nair, ISSE |
| TD-006 | PT-2 | ADDED | Addition | Marcus Webb |
| TD-007 | MA-3 | REMOVED | Removal | James Okafor, ISSO |
| TD-008 | PE-1 to PE-20 | INHERITED | Removal | James Okafor, ISSO |

---

## Detailed Tailoring Decisions

---

### TD-001 — AC-2(4) Added — Automated Account Disabling

**Control:** AC-2(4) — Automated Permanent Removal of
Temporary and Emergency Accounts

**Decision:** ADDED to the HIGH baseline

**Justification:**
Bundle stores highly sensitive PHI for thousands of
patients. The risk of former employees or contractors
retaining active accounts is unacceptable. Automated
disabling removes the possibility of human error in
the off-boarding process.

If a nurse or administrator leaves and their account
is not manually disabled promptly, they could
potentially access patient records from outside the
hospital. Automated disabling prevents this entirely.

**Implementation:**
AWS Cognito is configured to automatically disable
any account that has not logged in for 35 consecutive
days. An automated Lambda function runs nightly and
checks all accounts against the HR active staff list.
Any account not on the list is immediately disabled
and the ISSO is notified.

**Who approved:** Priya Nair, ISSE

---

### TD-002 — AC-11(1) Added — Pattern-Hiding on Session Lock

**Control:** AC-11(1) — Pattern-Hiding Displays

**Decision:** ADDED to the HIGH baseline

**Justification:**
Bundle is used on shared clinical workstations in
hospital wards, nurses stations, and consultation
rooms. When a session locks, the screen must not
display any patient information or hint at what
was being viewed.

Without this control, a locked screen on a shared
workstation could reveal partial patient information
to anyone walking past, violating HIPAA minimum
necessary standards.

**Implementation:**
When the 15-minute inactivity timeout triggers, the
screen displays a blank lock screen with only the
Bundle logo and a login prompt. No patient name,
record content, or navigation state is visible.

**Who approved:** Priya Nair, ISSE

---

### TD-003 — IA-2(6) Added — Separate MFA Device for Admins

**Control:** IA-2(6) — Access to Accounts Using Separate
Device

**Decision:** ADDED to the HIGH baseline

**Justification:**
IT administrators have elevated privileges that could
allow them to access all patient records, modify
system configurations, or disable security controls.
If an admin uses the same device for their MFA token
as they use to access the system, a compromised device
could defeat the MFA protection entirely.

Requiring a separate physical hardware token for
admin accounts ensures that a single device compromise
cannot grant full administrative access.

**Implementation:**
All 15 IT administrators are issued a YubiKey hardware
security key. This physical device must be present
and inserted to complete admin authentication.
Software TOTP apps are not permitted for any
privileged account.

**Who approved:** Priya Nair, ISSE

---

### TD-004 — SC-28(1) Added — Mandatory Encryption at Rest

**Control:** SC-28(1) — Cryptographic Protection

**Decision:** ADDED to the HIGH baseline as a mandatory
requirement rather than organisation-defined

**Justification:**
HIPAA requires encryption of PHI at rest as an
addressable safeguard. Given Bundle's HIGH impact
classification and the sensitivity of patient health
records, encryption at rest is treated as mandatory
rather than discretionary.

A data breach involving unencrypted PHI would expose
the hospital network to maximum HIPAA penalties and
cause severe harm to patients.

**Implementation:**
All RDS PostgreSQL databases encrypted with AES-256
using AWS KMS customer-managed keys. Annual key
rotation enforced. All S3 buckets use SSE-KMS. All
EC2 EBS volumes encrypted. No unencrypted storage
exists anywhere in Bundle's environment.

**Who approved:** Priya Nair, ISSE

---

### TD-005 — SI-4(2) Added — Automated Threat Detection

**Control:** SI-4(2) — Automated Tools and Mechanisms
for Real-Time Analysis

**Decision:** ADDED to the HIGH baseline

**Justification:**
Healthcare systems are the most targeted sector for
ransomware and data theft attacks. Waiting for manual
log review to detect an intrusion is unacceptable
given the sensitivity of patient PHI. Automated
detection reduces the window between a breach
occurring and being detected from days or weeks
to minutes.

**Implementation:**
AWS GuardDuty is enabled across all Bundle AWS
accounts. It analyses CloudTrail logs, VPC Flow
Logs, and DNS logs using machine learning to detect
unusual behaviour. Any HIGH severity finding triggers
an immediate PagerDuty alert to the ISSO. CrowdStrike
Falcon EDR provides real-time endpoint detection
on all EC2 instances.

**Who approved:** Priya Nair, ISSE

---

### TD-006 — PT-2 Added — PII Processing Controls

**Control:** PT-2 — Authority to Process Personally
Identifiable Information

**Decision:** ADDED to the HIGH baseline

**Justification:**
HIPAA requires explicit documentation of the legal
basis for processing patient PHI and PII. Bundle
processes some of the most sensitive categories of
personal information including mental health records,
HIV status, and substance abuse records.

Adding PT-2 ensures that all PII processing has
explicit documented authority and that patients
are informed of how their data is used.

**Implementation:**
Privacy Impact Assessment completed. Patient privacy
notice published and presented at point of care.
All PHI processing documented with its legal basis
under HIPAA. Privacy Officer reviews all new
data flows for PT-2 compliance before go-live.

**Who approved:** Marcus Webb, Privacy Officer

---

### TD-007 — MA-3 Removed — Physical Maintenance Tools

**Control:** MA-3 — Maintenance Tools

**Decision:** REMOVED from the HIGH baseline

**Justification:**
MA-3 requires controls over physical maintenance
tools used on information system components. Bundle
is entirely cloud-hosted on AWS with no on-premises
physical servers, workstations, or hardware that
Bundle staff would physically maintain.

There are no physical maintenance tools to control.
AWS is responsible for physical hardware maintenance
under the Shared Responsibility Model.

**Implementation:**
Not applicable. AWS FedRAMP High authorization
covers physical maintenance of all underlying
hardware. Evidence retained in
evidence/aws-compliance/.

**Who approved:** James Okafor, ISSO

---

### TD-008 — PE-1 to PE-20 Inherited — All Physical Controls

**Control:** PE Family — Physical and Environmental
Protection (all 20 controls)

**Decision:** FULLY INHERITED from AWS — removed from
Bundle's system-specific requirements

**Justification:**
Bundle has no physical data centres, server rooms,
or hardware facilities. All physical infrastructure
is managed by Amazon Web Services in their GovCloud
data centres.

AWS maintains ISO 27001 certification, SOC 2 Type II
reports, FedRAMP High authorization, and a signed
HIPAA Business Associate Agreement — all of which
provide comprehensive evidence of physical security
controls.

Implementing duplicate physical controls for a
cloud-only system is not meaningful and would create
false assurance.

**Implementation:**
All PE controls inherited from AWS. Evidence package
retained in evidence/aws-compliance/ folder and
includes:
- AWS SOC 2 Type II Report
- AWS ISO 27001 Certificate
- AWS FedRAMP High Authorization Package Summary
- AWS HIPAA Business Associate Agreement (BAA)

**Who approved:** James Okafor, ISSO

---

## Tailoring Approval Record

All eight tailoring decisions were reviewed and
approved before the control selection was finalised.

| Role | Name | Action | Date |
|------|------|--------|------|
| ISSE | Priya Nair | Proposed and reviewed | 2025 |
| ISSO | James Okafor | Reviewed and accepted | 2025 |
| Privacy Officer | Marcus Webb | Reviewed TD-006 | 2025 |
| System Owner | Dr. Sarah Mitchell | Approved all decisions | 2025 |

---

## Navigation

[Back to Step 2 Overview](README.md)

[Go to Step 3 — Implement](../03-implement/README.md)

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

