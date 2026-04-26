# Control Responsibility Matrix

![System](https://img.shields.io/badge/System-Bundle%20EHMS-blue)
![Step](https://img.shields.io/badge/RMF%20Step-2%20Select-blue)
![Controls](https://img.shields.io/badge/Total%20Controls-325-orange)
![Status](https://img.shields.io/badge/Status-Approved-brightgreen)

---

## What is the Control Responsibility Matrix?

This document shows who is responsible for implementing
and maintaining every security control selected for
Bundle. Each control is assigned one of three types:

| Type | Meaning | Who implements it |
|------|---------|------------------|
| System-Specific | Bundle team fully responsible | James Okafor and Priya Nair |
| Hybrid | Shared between Bundle and AWS | Both teams |
| Inherited | AWS fully responsible | Amazon Web Services |

---

## Responsibility Summary

| Type | Count | Percentage |
|------|-------|-----------|
| System-Specific | 187 | 58% |
| Hybrid | 112 | 34% |
| Inherited | 26 | 8% |
| **Total** | **325** | **100%** |

---

## AC — Access Control (25 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| AC-1 | Access Control Policy | System-Specific | James Okafor |
| AC-2 | Account Management | System-Specific | James Okafor |
| AC-2(1) | Automated System Account Management | Hybrid | Priya Nair |
| AC-2(2) | Removal of Temporary Accounts | Hybrid | Priya Nair |
| AC-2(3) | Disable Inactive Accounts | Hybrid | Priya Nair |
| AC-2(4) | Automated Audit Actions | Hybrid | Priya Nair |
| AC-3 | Access Enforcement | Hybrid | Priya Nair |
| AC-4 | Information Flow Enforcement | Hybrid | Priya Nair |
| AC-5 | Separation of Duties | System-Specific | James Okafor |
| AC-6 | Least Privilege | System-Specific | Priya Nair |
| AC-6(1) | Authorise Access to Security Functions | System-Specific | Priya Nair |
| AC-6(2) | Non-Privileged Access | System-Specific | Priya Nair |
| AC-6(5) | Privileged Accounts | System-Specific | Priya Nair |
| AC-6(9) | Log Use of Privileged Functions | Hybrid | Priya Nair |
| AC-7 | Unsuccessful Logon Attempts | System-Specific | Priya Nair |
| AC-8 | System Use Notification | System-Specific | James Okafor |
| AC-11 | Session Lock | System-Specific | Priya Nair |
| AC-11(1) | Pattern-Hiding Displays | System-Specific | Priya Nair |
| AC-12 | Session Termination | System-Specific | Priya Nair |
| AC-14 | Permitted Actions Without Identification | System-Specific | James Okafor |
| AC-17 | Remote Access | System-Specific | James Okafor |
| AC-17(1) | Monitoring and Control | Hybrid | Priya Nair |
| AC-18 | Wireless Access | System-Specific | James Okafor |
| AC-19 | Access Control for Mobile Devices | System-Specific | James Okafor |
| AC-22 | Publicly Accessible Content | System-Specific | James Okafor |

---

## AT — Awareness and Training (5 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| AT-1 | Awareness and Training Policy | System-Specific | James Okafor |
| AT-2 | Literacy Training and Awareness | System-Specific | James Okafor |
| AT-2(2) | Insider Threat Awareness | System-Specific | James Okafor |
| AT-3 | Role-Based Training | System-Specific | James Okafor |
| AT-4 | Training Records | System-Specific | James Okafor |

---

## AU — Audit and Accountability (16 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| AU-1 | Audit and Accountability Policy | System-Specific | James Okafor |
| AU-2 | Event Logging | Hybrid | Priya Nair |
| AU-3 | Content of Audit Records | Hybrid | Priya Nair |
| AU-3(1) | Additional Audit Information | Hybrid | Priya Nair |
| AU-4 | Audit Log Storage Capacity | Hybrid | Priya Nair |
| AU-5 | Response to Audit Logging Process Failures | Hybrid | Priya Nair |
| AU-6 | Audit Record Review Analysis and Reporting | System-Specific | James Okafor |
| AU-6(1) | Automated Process Integration | Hybrid | Priya Nair |
| AU-7 | Audit Record Reduction and Report Generation | Hybrid | Priya Nair |
| AU-8 | Time Stamps | Hybrid | Priya Nair |
| AU-9 | Protection of Audit Information | Hybrid | Priya Nair |
| AU-9(4) | Access by Subset of Privileged Users | System-Specific | James Okafor |
| AU-10 | Non-Repudiation | Hybrid | Priya Nair |
| AU-11 | Audit Record Retention | System-Specific | James Okafor |
| AU-12 | Audit Record Generation | Hybrid | Priya Nair |
| AU-12(1) | System-Wide and Time-Correlated Audit Trail | Hybrid | Priya Nair |

---

## CA — Assessment Authorization and Monitoring (9 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| CA-1 | Policy and Procedures | System-Specific | James Okafor |
| CA-2 | Control Assessments | System-Specific | James Okafor |
| CA-2(1) | Independent Assessors | System-Specific | James Okafor |
| CA-3 | Information Exchange | System-Specific | James Okafor |
| CA-5 | Plan of Action and Milestones | System-Specific | James Okafor |
| CA-6 | Authorization | System-Specific | James Okafor |
| CA-7 | Continuous Monitoring | System-Specific | James Okafor |
| CA-7(1) | Independent Assessment | System-Specific | James Okafor |
| CA-9 | Internal System Connections | System-Specific | Priya Nair |

---

## CM — Configuration Management (11 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| CM-1 | Configuration Management Policy | System-Specific | James Okafor |
| CM-2 | Baseline Configuration | Hybrid | Priya Nair |
| CM-2(1) | Reviews and Updates | System-Specific | Priya Nair |
| CM-2(2) | Automation Support | Hybrid | Priya Nair |
| CM-3 | Configuration Change Control | System-Specific | Priya Nair |
| CM-4 | Impact Analyses | System-Specific | Priya Nair |
| CM-5 | Access Restrictions for Change | System-Specific | Priya Nair |
| CM-6 | Configuration Settings | Hybrid | Priya Nair |
| CM-7 | Least Functionality | System-Specific | Priya Nair |
| CM-7(1) | Periodic Review | System-Specific | Priya Nair |
| CM-8 | System Component Inventory | System-Specific | Priya Nair |

---

## CP — Contingency Planning (10 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| CP-1 | Contingency Planning Policy | System-Specific | James Okafor |
| CP-2 | Contingency Plan | System-Specific | James Okafor |
| CP-2(1) | Coordinate with Related Plans | System-Specific | James Okafor |
| CP-3 | Contingency Training | System-Specific | James Okafor |
| CP-4 | Contingency Plan Testing | System-Specific | James Okafor |
| CP-6 | Alternate Storage Site | Hybrid | Priya Nair |
| CP-7 | Alternate Processing Site | Hybrid | Priya Nair |
| CP-8 | Telecommunications Services | Hybrid | Priya Nair |
| CP-9 | System Backup | Hybrid | Priya Nair |
| CP-10 | System Recovery and Reconstitution | Hybrid | Priya Nair |

---

## IA — Identification and Authentication (12 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| IA-1 | Identification and Authentication Policy | System-Specific | James Okafor |
| IA-2 | Identification and Authentication | Hybrid | Priya Nair |
| IA-2(1) | MFA — Privileged Accounts | Hybrid | Priya Nair |
| IA-2(2) | MFA — Non-Privileged Accounts | Hybrid | Priya Nair |
| IA-2(6) | Separate Device for MFA | System-Specific | Priya Nair |
| IA-2(8) | Network Access — Replay Resistant | Hybrid | Priya Nair |
| IA-4 | Identifier Management | System-Specific | James Okafor |
| IA-5 | Authenticator Management | System-Specific | James Okafor |
| IA-5(1) | Password-Based Authentication | System-Specific | Priya Nair |
| IA-6 | Authentication Feedback | System-Specific | Priya Nair |
| IA-7 | Cryptographic Module Authentication | Hybrid | Priya Nair |
| IA-8 | Non-Organisational Users | System-Specific | James Okafor |

---

## IR — Incident Response (10 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| IR-1 | Incident Response Policy | System-Specific | James Okafor |
| IR-2 | Incident Response Training | System-Specific | James Okafor |
| IR-3 | Incident Response Testing | System-Specific | James Okafor |
| IR-4 | Incident Handling | System-Specific | James Okafor |
| IR-4(1) | Automated Incident Handling | Hybrid | Priya Nair |
| IR-5 | Incident Monitoring | System-Specific | James Okafor |
| IR-6 | Incident Reporting | System-Specific | James Okafor |
| IR-6(1) | Automated Reporting | Hybrid | Priya Nair |
| IR-7 | Incident Response Assistance | System-Specific | James Okafor |
| IR-8 | Incident Response Plan | System-Specific | James Okafor |

---

## PE — Physical and Environmental (20 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| PE-1 through PE-20 | All Physical Controls | **Inherited** | **Amazon Web Services** |

All 20 PE controls are fully inherited from AWS.
See inherited-controls.md for full details.

---

## RA — Risk Assessment (6 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| RA-1 | Risk Assessment Policy | System-Specific | James Okafor |
| RA-2 | Security Categorization | System-Specific | James Okafor |
| RA-3 | Risk Assessment | System-Specific | James Okafor |
| RA-5 | Vulnerability Monitoring and Scanning | Hybrid | Priya Nair |
| RA-5(2) | Update Vulnerabilities | Hybrid | Priya Nair |
| RA-7 | Risk Response | System-Specific | James Okafor |

---

## SC — System and Communications Protection (20 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| SC-1 | System and Communications Policy | System-Specific | James Okafor |
| SC-5 | Denial of Service Protection | Hybrid | Priya Nair |
| SC-7 | Boundary Protection | Hybrid | Priya Nair |
| SC-7(3) | Access Points | Hybrid | Priya Nair |
| SC-7(4) | External Telecommunications Services | Hybrid | Priya Nair |
| SC-7(5) | Deny by Default | Hybrid | Priya Nair |
| SC-8 | Transmission Confidentiality and Integrity | System-Specific | Priya Nair |
| SC-8(1) | Cryptographic Protection | System-Specific | Priya Nair |
| SC-10 | Network Disconnect | System-Specific | Priya Nair |
| SC-12 | Cryptographic Key Management | Hybrid | Priya Nair |
| SC-13 | Cryptographic Protection | Hybrid | Priya Nair |
| SC-15 | Collaborative Computing Devices | System-Specific | Priya Nair |
| SC-17 | Public Key Infrastructure Certificates | System-Specific | Priya Nair |
| SC-18 | Mobile Code | System-Specific | Priya Nair |
| SC-20 | Secure Name Resolution | Hybrid | Priya Nair |
| SC-21 | Secure Name Resolution | Hybrid | Priya Nair |
| SC-22 | Architecture and Provisioning | Hybrid | Priya Nair |
| SC-28 | Protection of Information at Rest | Hybrid | Priya Nair |
| SC-28(1) | Cryptographic Protection | System-Specific | Priya Nair |
| SC-39 | Process Isolation | **Inherited** | **Amazon Web Services** |

---

## SI — System and Information Integrity (13 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| SI-1 | System and Information Integrity Policy | System-Specific | James Okafor |
| SI-2 | Flaw Remediation | System-Specific | Priya Nair |
| SI-2(2) | Automated Flaw Remediation | Hybrid | Priya Nair |
| SI-3 | Malicious Code Protection | System-Specific | Priya Nair |
| SI-3(1) | Central Management | Hybrid | Priya Nair |
| SI-4 | System Monitoring | Hybrid | Priya Nair |
| SI-4(2) | Automated Tools for Real-Time Analysis | Hybrid | Priya Nair |
| SI-4(4) | Inbound and Outbound Traffic | Hybrid | Priya Nair |
| SI-4(5) | System Generated Alerts | Hybrid | Priya Nair |
| SI-5 | Security Alerts Advisories and Directives | Hybrid | James Okafor |
| SI-7 | Software Firmware and Information Integrity | Hybrid | Priya Nair |
| SI-10 | Information Input Validation | System-Specific | Priya Nair |
| SI-12 | Information Management and Retention | System-Specific | James Okafor |

---

## PS — Personnel Security (8 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| PS-1 | Personnel Security Policy | System-Specific | James Okafor |
| PS-2 | Position Risk Designation | System-Specific | James Okafor |
| PS-3 | Personnel Screening | System-Specific | James Okafor |
| PS-4 | Personnel Termination | System-Specific | James Okafor |
| PS-5 | Personnel Transfer | System-Specific | James Okafor |
| PS-6 | Access Agreements | System-Specific | James Okafor |
| PS-7 | External Personnel Security | System-Specific | James Okafor |
| PS-8 | Personnel Sanctions | System-Specific | James Okafor |

---

## SA — System and Services Acquisition (10 controls)

| Control | Title | Type | Primary Owner |
|---------|-------|------|--------------|
| SA-1 | System and Services Acquisition Policy | System-Specific | James Okafor |
| SA-2 | Allocation of Resources | System-Specific | James Okafor |
| SA-3 | System Development Life Cycle | System-Specific | Priya Nair |
| SA-4 | Acquisition Process | System-Specific | James Okafor |
| SA-4(1) | Functional Properties of Controls | System-Specific | Priya Nair |
| SA-4(2) | Design and Implementation Information | System-Specific | Priya Nair |
| SA-5 | System Documentation | System-Specific | James Okafor |
| SA-9 | External System Services | System-Specific | James Okafor |
| SA-10 | Developer Configuration Management | System-Specific | Priya Nair |
| SA-11 | Developer Testing and Evaluation | System-Specific | Priya Nair |

---

## Approval Record

| Role | Name | Action | Date |
|------|------|--------|------|
| ISSE | Priya Nair | Prepared matrix | 2025 |
| ISSO | James Okafor | Reviewed and approved | 2025 |
| System Owner | Dr. Sarah Mitchell | Final approval | 2025 |

---

## Navigation

[Back to Step 2 Overview](README.md)

[Back to Tailoring Decisions](tailoring-decisions.md)

[Go to Step 3 — Implement](../03-implement/README.md)

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

