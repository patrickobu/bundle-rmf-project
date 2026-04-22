# Step 0 — Prepare

![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![RMF Step](https://img.shields.io/badge/RMF%20Step-0%20Prepare-blue)
![NIST](https://img.shields.io/badge/NIST-SP%20800--37%20Rev.2-blue)
![HIPAA](https://img.shields.io/badge/Compliance-HIPAA-green)

---

## What is the Prepare Step?

The Prepare step is the foundation of the entire RMF process. Before any security work begins, this step establishes:

- **Who** is responsible for security (roles and responsibilities)
- **Why** the system exists and what it supports (mission context)
- **What** risks the organisation is willing to accept (risk management strategy)
- **Which** laws and standards apply (regulatory context)

> NIST SP 800-37 Revision 2 added the Prepare step specifically because programmes that skipped this foundation consistently struggled to complete the RMF process. Every other step depends on what is documented here.

---

## Documents in This Folder


| File | Description |
|------|-------------|
| [README.md](README.md) | This file — overview of the Prepare step |
| [roles-and-responsibilities.md](roles-and-responsibilities.md) | RMF role assignments and RACI matrix |
| [risk-management-strategy.md](risk-management-strategy.md) | Risk tolerance, assessment approach, and risk response options |
---

## System: Bundle EHMS

Bundle is a cloud-based Electronic Healthcare Management System (EHMS) used by clinical staff at a mid-sized hospital network. It processes, stores, and transmits Protected Health Information (PHI) including:

- Patient Electronic Health Records (EHR)
- Clinical scheduling and resource management
- Billing and insurance claims data
- Staff access credentials and role assignments

**Hosting:** Amazon Web Services (AWS) — EC2, RDS, S3, CloudWatch, IAM, KMS  
**Users:** ~500 (doctors, nurses, administrators, billing staff)  
**Impact Level:** HIGH (determined in Step 1 — Categorize)

---

## RMF Roles Assigned

| Role | Person | Title |
|------|--------|-------|
| Authorizing Official (AO) | Linda Reyes | Chief Information Officer |
| System Owner | Dr. Sarah Mitchell | Chief Medical Officer |
| ISSO | James Okafor | IT Security Manager |
| ISSE | Priya Nair | Senior Cloud Security Engineer |
| Control Assessor | TBC — External Auditor | Third-Party Assessment Organisation |
| Privacy Officer | Marcus Webb | Chief Privacy Officer |
| Common Control Provider | AWS Security Team | Amazon Web Services |

> All names are fictional and used for portfolio simulation purposes only.

---

## Risk Management Strategy Summary

Bundle operates in a healthcare environment where a security failure can directly harm patients. Risk tolerance is defined as follows:

| Risk Level | Response |
|------------|----------|
| **HIGH** | Not accepted without immediate compensating controls. Must be reported to AO. Remediation within 30 days. |
| **MODERATE** | Accepted temporarily with a documented POA&M entry. Remediation within 90 days. |
| **LOW** | Accepted and tracked in POA&M. Reviewed quarterly. |

**Risk Assessment Approach:** Qualitative — Likelihood × Impact matrix  
**Risk Review Cadence:** Annual full assessment + monthly POA&M review + event-triggered reviews

---

## Applicable Laws and Standards

| Law / Standard | Relevance |
|----------------|-----------|
| HIPAA Security Rule | Requires specific safeguards for electronic PHI |
| HITECH Act | Strengthens HIPAA enforcement; extends requirements to vendors |
| NIST SP 800-37 Rev. 2 | The RMF process this project follows |
| NIST SP 800-53 Rev. 5 | Security control catalogue used for control selection |
| FIPS 199 | System categorisation standard |
| FIPS 200 | Minimum security requirements |
| AWS Shared Responsibility Model | Defines split between AWS and Bundle team responsibilities |

---

## Preliminary Threat Assessment

Top risks identified before formal categorisation:

| Threat | Likelihood | Impact | Risk Rating |
|--------|------------|--------|-------------|
| Ransomware Attack | High | High | **HIGH** |
| PHI Data Breach | Moderate | High | **HIGH** |
| Unauthorised Access | Moderate | High | **HIGH** |
| Phishing / Social Engineering | High | Moderate | **HIGH** |
| Third-Party Vendor Compromise | Low | High | **MODERATE** |
| System Misconfiguration (AWS) | Moderate | Moderate | **MODERATE** |
| Availability Disruption (DDoS) | Low | Moderate | **LOW** |

> Full formal risk assessment will be conducted in Step 4 — Assess.

---

## Prepare Step Checklist

| Task | NIST Task ID | Status |
|------|-------------|--------|
| RMF roles assigned with named individuals | P-1 | ✅ Complete |
| Risk management strategy documented | P-2 | ✅ Complete |
| Preliminary risk assessment conducted | P-3 | ✅ Complete |
| Applicable laws and standards identified | P-4 | ✅ Complete |
| AWS inherited controls identified | P-5 | ✅ Complete |
| Mission-critical functions documented | P-6 | ✅ Complete |
| High-level monitoring approach defined | P-7 | 🔄 In Progress — full strategy in Step 6 |

---

## Next Step

With the Prepare step complete, the project moves to **Step 1 — Categorize**.

In that step, the team will formally assess Bundle's data sensitivity using FIPS 199 and assign an overall system impact level (Low, Moderate, or High).

➡️ [Go to Step 1 — Categorize](../01-categorize/README.md)

---

## Document Information

| Field | Value |
|-------|-------|
| Document Version | 1.0 |
| Prepared By | James Okafor, ISSO |
| Reviewed By | Dr. Sarah Mitchell, System Owner |
| Approved By | Linda Reyes, Authorizing Official |
| NIST Reference | NIST SP 800-37 Rev. 2, Chapter 2 — Prepare Step |

---

*This document is part of the Bundle RMF portfolio project. All names, data, and scenarios are fictional and used for learning and career development purposes only.*

