# Control Selection

**System:** Bundle — Electronic Healthcare Management System
**Document:** Security Control Selection and Tailoring
**Step:** Step 2 — Select
**Baseline:** NIST SP 800-53 Rev. 5 — HIGH Impact
**Version:** 1.0
**Prepared By:** Priya Nair, ISSE
**Reviewed By:** James Okafor, ISSO
**Approved By:** Dr. Sarah Mitchell, System Owner
**Date:** 2025

---

## What This Document Covers

This document records which security controls have been selected for
Bundle, why they were selected, and any tailoring decisions made to
adjust the HIGH impact baseline for Bundle's specific environment.

---

## Control Selection Approach

**Stage 1 — Start with the HIGH baseline**
Because Bundle is rated HIGH impact, the starting point is the HIGH
control baseline from NIST SP 800-53B.

**Stage 2 — Tailor the baseline**
Adjust for Bundle's healthcare and AWS cloud environment by adding
controls, removing controls, or modifying requirements.

**Stage 3 — Classify each control**
Every control is classified as System-Specific, Inherited, or Hybrid.

---

## Control Type Definitions

| Type | Meaning |
|------|---------|
| System-Specific | Implemented and managed entirely by Bundle's team |
| Inherited | Implemented by AWS under the Shared Responsibility Model |
| Hybrid | Partially Bundle's team, partially AWS |

---

## Selected Controls by Family

### AC — Access Control

| Control | Name | Type | Owner |
|---------|------|------|-------|
| AC-1 | Access Control Policy | System-Specific | James Okafor |
| AC-2 | Account Management | System-Specific | James Okafor |
| AC-3 | Access Enforcement | Hybrid | Priya Nair |
| AC-6 | Least Privilege | System-Specific | Priya Nair |
| AC-7 | Unsuccessful Login Attempts | System-Specific | Priya Nair |
| AC-11 | Session Lock | System-Specific | Priya Nair |
| AC-17 | Remote Access | System-Specific | James Okafor |
| AC-22 | Publicly Accessible Content | System-Specific | James Okafor |

### AU — Audit and Accountability

| Control | Name | Type | Owner |
|---------|------|------|-------|
| AU-1 | Audit Policy | System-Specific | James Okafor |
| AU-2 | Event Logging | Hybrid | Priya Nair |
| AU-3 | Content of Audit Records | Hybrid | Priya Nair |
| AU-6 | Audit Record Review | System-Specific | James Okafor |
| AU-9 | Audit Record Protection | Hybrid | Priya Nair |
| AU-11 | Audit Record Retention | System-Specific | James Okafor |
| AU-12 | Audit Record Generation | Hybrid | Priya Nair |

### IA — Identification and Authentication

| Control | Name | Type | Owner |
|---------|------|------|-------|
| IA-1 | IA Policy | System-Specific | James Okafor |
| IA-2 | MFA for All Users | Hybrid | Priya Nair |
| IA-2(1) | Hardware MFA for Privileged Accounts | Hybrid | Priya Nair |
| IA-2(2) | Software MFA for Standard Accounts | Hybrid | Priya Nair |
| IA-4 | Identifier Management | System-Specific | James Okafor |
| IA-5 | Authenticator Management | System-Specific | James Okafor |
| IA-8 | Non-Organisational Users | System-Specific | James Okafor |

### SC — System and Communications Protection

| Control | Name | Type | Owner |
|---------|------|------|-------|
| SC-1 | SC Policy | System-Specific | James Okafor |
| SC-7 | Boundary Protection | Hybrid | Priya Nair |
| SC-8 | Transmission Encryption | System-Specific | Priya Nair |
| SC-12 | Cryptographic Key Management | Hybrid | Priya Nair |
| SC-13 | Cryptographic Protection | Hybrid | Priya Nair |
| SC-28 | Protection of Information at Rest | Hybrid | Priya Nair |
| SC-39 | Process Isolation | Inherited | AWS |

### IR — Incident Response

| Control | Name | Type | Owner |
|---------|------|------|-------|
| IR-1 | IR Policy | System-Specific | James Okafor |
| IR-2 | IR Training | System-Specific | James Okafor |
| IR-4 | Incident Handling | System-Specific | James Okafor |
| IR-5 | Incident Monitoring | System-Specific | James Okafor |
| IR-6 | Incident Reporting | System-Specific | James Okafor |
| IR-8 | Incident Response Plan | System-Specific | James Okafor |

### SI — System and Information Integrity

| Control | Name | Type | Owner |
|---------|------|------|-------|
| SI-1 | SI Policy | System-Specific | James Okafor |
| SI-2 | Flaw Remediation | System-Specific | Priya Nair |
| SI-3 | Malware Protection | System-Specific | Priya Nair |
| SI-4 | System Monitoring | Hybrid | Priya Nair |
| SI-5 | Security Alerts | Hybrid | James Okafor |
| SI-10 | Information Input Validation | System-Specific | Priya Nair |

### CP — Contingency Planning

| Control | Name | Type | Owner |
|---------|------|------|-------|
| CP-1 | CP Policy | System-Specific | James Okafor |
| CP-2 | Contingency Plan | System-Specific | James Okafor |
| CP-4 | Contingency Plan Testing | System-Specific | James Okafor |
| CP-9 | System Backup | Hybrid | Priya Nair |
| CP-10 | System Recovery | Hybrid | Priya Nair |

### RA — Risk Assessment

| Control | Name | Type | Owner |
|---------|------|------|-------|
| RA-1 | RA Policy | System-Specific | James Okafor |
| RA-3 | Risk Assessment | System-Specific | James Okafor |
| RA-5 | Vulnerability Scanning | Hybrid | Priya Nair |
| RA-7 | Risk Response | System-Specific | James Okafor |

---

## Tailoring Decisions

| Control | Decision | Justification | Approved By |
|---------|----------|--------------|-------------|
| AC-2(4) | ADDED — Automated account disabling | PHI risk from former employees | Priya Nair |
| AC-11(1) | ADDED — Pattern-hiding on session lock | Shared clinical workstations | Priya Nair |
| IA-2(6) | ADDED — Separate device for admin MFA | Prevents single device compromise | Priya Nair |
| MA-3 | REMOVED — Physical maintenance tools | Fully cloud-hosted — AWS responsibility | James Okafor |
| PE-1 to PE-20 | INHERITED — All physical controls | AWS SOC 2 and ISO 27001 cover these | James Okafor |
| SC-28(1) | ADDED — Mandatory encryption at rest | HIPAA requires PHI encryption | Priya Nair |
| SI-4(2) | ADDED — Automated threat detection | GuardDuty essential for healthcare | Priya Nair |
| PT-2 | ADDED — PII processing controls | HIPAA requires explicit PII controls | Marcus Webb |

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 | Priya Nair | Initial control selection completed |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

