# Step 1 — Categorize

![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![RMF Step](https://img.shields.io/badge/RMF%20Step-1%20Categorize-blue)
![FIPS 199](https://img.shields.io/badge/Standard-FIPS%20199-blue)
![Impact Level](https://img.shields.io/badge/Impact%20Level-HIGH-red)

---

## What is the Categorize Step?

The Categorize step determines how sensitive Bundle's information is and how serious it would be if something went wrong. Every system must be rated across three security objectives using **FIPS 199**:

| Security Objective | Question Asked |
|--------------------|----------------|
| **Confidentiality** | How bad would it be if unauthorised people could read Bundle's data? |
| **Integrity** | How bad would it be if Bundle's data were altered incorrectly? |
| **Availability** | How bad would it be if Bundle went offline and staff could not access it? |

Each objective is rated **Low**, **Moderate**, or **High**. The highest rating across all three becomes the overall system impact level.

> The overall impact level determines which security control baseline applies in Step 2. A HIGH system requires significantly more security controls than a Low or Moderate one.

---

## Documents in This Folder

| File | Description |
|------|-------------|
| `README.md` | This file — overview of the Categorize step and key outputs |
| `system-description.md` | Detailed description of Bundle including users, architecture, and AWS services |
| `information-types.md` | All information types processed by Bundle with regulatory basis |
| `fips199-impact-analysis.md` | Full FIPS 199 categorization with ratings and justifications |
| `system-boundary.md` | What is inside and outside the RMF authorization scope |
| `hardware-software-inventory.md` | Inventory of key system components and software versions |
| `data-flow-description.md` | How PHI and other data move through Bundle |
| `data-flow-diagram.png` | Visual diagram of system data flows *(to be added)* |
| `categorization-decision-record.md` | Formal categorization statement and approval record |

---

## System Summary: Bundle EHMS

| Field | Value |
|-------|-------|
| System Name | Bundle |
| System Type | Electronic Healthcare Management System (EHMS) |
| Hosting | AWS — EC2, RDS, S3, CloudWatch, IAM, KMS, WAF |
| Users | ~500 (doctors, nurses, administrators, billing staff) |
| Primary Data | PHI, PII, billing records, scheduling data, audit logs |
| Regulatory Requirements | HIPAA Security Rule, HITECH Act |
| Third-Party Connections | Insurance APIs, Laboratory Information System, Pharmacy System, Hospital Active Directory |

---

## FIPS 199 Categorization Results

### Confidentiality — HIGH

Bundle contains PHI for thousands of patients. A breach would expose sensitive medical records including diagnoses, medications, and treatment history.

**Potential consequences of a confidentiality failure:**
- HIPAA violations with fines up to $1.9 million per violation category per year
- Patient identity theft and discrimination based on health conditions
- Reputational damage to the hospital network
- Potential patient harm if sensitive diagnoses are exposed
- Possible criminal liability for responsible individuals

---

### Integrity — HIGH

Clinical staff make life-or-death decisions based on data in Bundle. If records were altered — by an attacker, a software bug, or human error — the consequences could be directly harmful to patients.

**Potential consequences of an integrity failure:**
- A patient's medication dosage changed to a dangerous level
- An allergy record deleted, causing an adverse reaction
- A diagnosis altered, leading to incorrect treatment
- Fraudulent billing records submitted to insurance companies

---

### Availability — MODERATE

If Bundle goes offline, clinical staff can revert to documented manual paper-based emergency procedures for a limited period. Prolonged unavailability is serious but not immediately life-threatening.

**Potential consequences of an availability failure:**
- Significant operational disruption and patient care delays
- Inability to access historical medication and allergy records in emergencies
- Billing and insurance claims backlog affecting hospital revenue
- Increased error risk during manual operation

---

## Formal Categorization Statement

```
SC Bundle = {(confidentiality, HIGH), (integrity, HIGH), (availability, MODERATE)}

Overall System Impact Level: HIGH
```

> Per FIPS 199, the overall system impact level is the **highest** rating across all three security objectives. This is known as the high-water mark principle.

---

## System Boundary

### Inside the Boundary (In Scope)
- All AWS EC2 application and API servers running Bundle
- AWS RDS PostgreSQL database (all patient and operational data)
- AWS S3 buckets for document and image storage
- AWS CloudWatch logging for Bundle
- AWS IAM roles and user accounts for Bundle
- AWS KMS encryption keys for Bundle
- Bundle VPC, subnets, security groups, and network ACLs
- AWS WAF protecting Bundle's public endpoints
- All Bundle application code and configuration

### Outside the Boundary (Inherited from AWS)
These are covered by AWS compliance reports (SOC 2, ISO 27001, HIPAA BAA):

| Component | AWS Responsibility |
|-----------|-------------------|
| Physical data centre security | Facility access, environmental controls, hardware security |
| Hypervisor and virtualisation layer | Underlying infrastructure security |
| Physical network infrastructure | AWS backbone and regional connectivity |
| Hardware maintenance and disposal | Physical hardware lifecycle management |

---

## Information Types

| Information Type | Sensitivity | Regulatory Basis |
|-----------------|-------------|-----------------|
| Protected Health Information (PHI) | **CRITICAL** | HIPAA Security Rule, HITECH |
| Personally Identifiable Information (PII) | **HIGH** | HIPAA, State Privacy Laws |
| Financial and Billing Data | **HIGH** | HIPAA, PCI-DSS |
| Scheduling and Operational Data | **MODERATE** | Internal Policy |
| System and Audit Logs | **MODERATE** | NIST 800-53 AU Controls |
| Management and Compliance Reports | **LOW** | Internal / Regulatory Reporting |

---

## Key Data Flows

| Flow | Description |
|------|-------------|
| Staff Login | User → WAF → Load Balancer → App Server → Active Directory (LDAPS) |
| Patient Record Access | App Server → VPC Private Subnet → RDS Database |
| Document Upload | App Server → S3 Bucket (KMS encrypted) |
| Lab Results Receipt | Lab System → API Gateway → API Server → RDS |
| Insurance Claim Submission | App Server → RDS → API Server → Insurance API |
| Daily Backup | RDS → AWS Backup → S3 US East → S3 US West (cross-region) |
| Audit Logging | All EC2 instances → CloudWatch Logs (90-day retention) |

> See `data-flow-diagram.png` for the visual representation of these flows.

---

## Categorize Step Checklist

| Task | NIST Task ID | Status |
|------|-------------|--------|
| System description documented | C-1 | ✅ Complete |
| Information types identified | C-2 | ✅ Complete |
| FIPS 199 ratings assigned with justification | C-3 | ✅ Complete |
| System boundary defined | C-4 | ✅ Complete |
| Hardware inventory completed | C-5 | ✅ Complete |
| Software inventory completed | C-6 | ✅ Complete |
| Data flows documented | C-7 | ✅ Complete |
| Data flow diagram created | C-8 | 🔄 In Progress |
| Categorization formally approved by AO | C-9 | ✅ Complete |

---

## Approval Record

| Role | Name | Action |
|------|------|--------|
| ISSO | James Okafor | Prepared and documented |
| System Owner | Dr. Sarah Mitchell | Reviewed — confirmed system description |
| ISSE | Priya Nair | Reviewed — confirmed technical architecture |
| Privacy Officer | Marcus Webb | Reviewed — confirmed PHI data types |
| **Authorizing Official** | **Linda Reyes** | **Approved — authorised progression to Step 2** |

---

## Next Step

Bundle is formally categorised as a **HIGH impact system**.

In **Step 2 — Select**, the team will choose the HIGH baseline security controls from NIST SP 800-53 Rev. 5, tailor them for Bundle's healthcare environment, and begin drafting the System Security Plan (SSP).

➡️ [Go to Step 2 — Select](../02-select/README.md)  
⬅️ [Back to Step 0 — Prepare](../00-prepare/README.md)

---

## Document Information

| Field | Value |
|-------|-------|
| Document Version | 1.0 |
| Categorization Standard | FIPS 199 |
| Supporting Reference | NIST SP 800-60 Vol. I & II |
| Prepared By | James Okafor, ISSO |
| Approved By | Linda Reyes, Authorizing Official |
| NIST Reference | NIST SP 800-37 Rev. 2 — Categorize Step |

---

*This document is part of the Bundle RMF portfolio project. All names, data, and scenarios are fictional and used for learning and career development purposes only.*

