# System Security Plan — Final Version

**System Name:** Bundle — Electronic Healthcare Management System
**System Identifier:** BUNDLE-EHMS-001
**Version:** 1.0 — Final
**Status:** Complete
**Prepared By:** James Okafor, ISSO
**Approved By:** Dr. Sarah Mitchell, System Owner
**Date:** 2025

---

## Section 1 — System Information

| Field | Value |
|-------|-------|
| System Name | Bundle EHMS |
| System Identifier | BUNDLE-EHMS-001 |
| System Categorization | HIGH (Confidentiality: HIGH, Integrity: HIGH, Availability: MODERATE) |
| System Owner | Dr. Sarah Mitchell, CMO |
| ISSO | James Okafor, IT Security Manager |
| Authorizing Official | Linda Reyes, CIO |
| Hosting Environment | AWS — US East and US West |
| Operating Status | Authorized to Operate |
| ATO Reference | BUNDLE-ATO-2025-001 |

---

## Section 2 — System Purpose and Description

Bundle is a cloud-based Electronic Healthcare Management System (EHMS)
serving approximately 500 clinical and administrative staff across a
mid-sized hospital network. It manages Electronic Health Records (EHR),
patient scheduling, medication tracking, insurance billing, and staff
access control.

Bundle processes Protected Health Information (PHI) and is subject to
HIPAA and HITECH regulations. It is hosted on Amazon Web Services (AWS)
using EC2, RDS, S3, CloudWatch, IAM, KMS, and WAF.

---

## Section 3 — System Environment and Architecture

Bundle runs entirely on AWS. Key components:

- EC2 application servers in a private subnet
- RDS PostgreSQL database in a separate private subnet
- S3 for document and image storage
- AWS WAF and Application Load Balancer in the public subnet
- CloudWatch for logging and monitoring
- KMS for encryption key management
- IAM for access control

All components sit inside a dedicated AWS VPC. No application server
or database has a public IP address.

---

## Section 4 — System Boundary

**Inside the boundary (Bundle team responsible):**
All AWS services listed above, Bundle application code,
user accounts, and configuration.

**Outside the boundary (AWS responsible):**
Physical data centres, hypervisor, hardware maintenance.
Evidence: AWS SOC 2 Type II report, ISO 27001, HIPAA BAA.

**External connections:**
Insurance billing API, Laboratory Information System,
Pharmacy system, Hospital Active Directory.

---

## Section 5 — Applicable Laws and Regulations

- HIPAA Security Rule
- HITECH Act
- NIST SP 800-37 Rev. 2 (RMF process)
- NIST SP 800-53 Rev. 5 (security controls)
- FIPS 199 (categorization)
- AWS Shared Responsibility Model

---

## Section 6 — Control Implementation Statements

All control implementation statements are documented in:

[Control Implementation Statements](control-implementation-statements.md)

Key controls implemented:

| Control | Name | Status |
|---------|------|--------|
| AC-2 | Account Management | Implemented |
| AC-3 | Access Enforcement | Implemented |
| AU-2 | Event Logging | Implemented |
| IA-2 | Multi-Factor Authentication | Implemented |
| SC-7 | Boundary Protection | Implemented |
| SC-28 | Encryption at Rest | Implemented |
| IR-4 | Incident Handling | Implemented |
| SI-2 | Flaw Remediation | Implemented |
| CP-9 | System Backup | Implemented |
| RA-5 | Vulnerability Scanning | Implemented |

---

## Section 7 — Roles and Responsibilities

| Role | Person | Title |
|------|--------|-------|
| Authorizing Official | Linda Reyes | CIO |
| System Owner | Dr. Sarah Mitchell | CMO |
| ISSO | James Okafor | IT Security Manager |
| ISSE | Priya Nair | Senior Cloud Security Engineer |
| Privacy Officer | Marcus Webb | Chief Privacy Officer |
| Control Assessor | ClearPath Security LLC | External Assessor |

---

## Section 8 — Interconnections and Interfaces

| System | Connection Type | Protocol |
|--------|----------------|----------|
| Insurance billing API | Outbound API | TLS 1.2+ |
| Laboratory Information System | Bidirectional | TLS 1.2+ |
| Pharmacy system | Bidirectional | TLS 1.2+ |
| Hospital Active Directory | Inbound authentication | LDAPS |

---

## Section 9 — Information Types and Categorization

| Information Type | Sensitivity |
|-----------------|-------------|
| Protected Health Information (PHI) | CRITICAL |
| Personally Identifiable Information (PII) | HIGH |
| Financial and Billing Data | HIGH |
| Scheduling and Operational Data | MODERATE |
| Audit Logs | MODERATE |

**FIPS 199 Result:**

| Security Objective | Rating |
|-------------------|--------|
| Confidentiality | HIGH |
| Integrity | HIGH |
| Availability | MODERATE |
| Overall System Impact Level | HIGH |

---

## Section 10 — Control Selection and Tailoring

Full control selection documented in:
[Control Selection](../02-select/control-selection.md)

- Baseline: NIST SP 800-53 Rev. 5 — HIGH impact
- Total controls selected: approximately 140
- Tailoring decisions: 8 documented additions and removals
- Inherited from AWS: Physical environment controls (PE family)

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 | James Okafor | Final SSP completed and approved |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*
