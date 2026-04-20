# FIPS 199 Security Categorization

**System:** Bundle — Electronic Healthcare Management System
**Document:** FIPS 199 Impact Analysis
**Step:** Step 1 — Categorize
**Standard:** FIPS 199 — Standards for Security Categorization
**Version:** 1.0
**Prepared By:** James Okafor, ISSO
**Approved By:** Linda Reyes, Authorizing Official
**Date:** 2025

---

## What is FIPS 199?

FIPS 199 is the Federal Information Processing Standard that defines
how to categorise information systems based on the potential harm
a security failure could cause. Every system is rated across three
security objectives. Each objective receives a rating of Low,
Moderate, or High.

The overall system impact level is the HIGHEST rating across all
three objectives. This is called the high-water mark principle.

---

## System Description Summary

Bundle is a cloud-based Electronic Healthcare Management System
processing Protected Health Information (PHI) for approximately
500 clinical and administrative staff at a mid-sized hospital network.

Bundle stores and processes:
- Patient Electronic Health Records including diagnoses and medications
- Patient demographic and insurance information
- Clinical scheduling and resource data
- Billing and insurance claims records
- Staff access credentials and audit logs

---

## Security Categorization Results

### Confidentiality — HIGH

Confidentiality means protecting information from being accessed
by unauthorised individuals.

**Rating: HIGH**

**Justification:**
Bundle contains PHI for thousands of patients. A confidentiality
breach would expose sensitive medical records including diagnoses,
medications, mental health records, and insurance information.

Consequences of a confidentiality failure:
- HIPAA violations with fines up to $1.9 million per violation per year
- Patient identity theft and discrimination based on health conditions
- Irreversible reputational damage to the hospital network
- Potential patient harm if sensitive diagnoses are exposed
- Possible criminal liability for responsible individuals

---

### Integrity — HIGH

Integrity means ensuring information is accurate and has not been
altered without authorisation.

**Rating: HIGH**

**Justification:**
Clinical staff make life-or-death decisions based on data in Bundle.
If Bundle's data were altered the consequences could be directly
life-threatening.

Examples of integrity failure consequences:
- A patient medication dosage changed to a dangerous level
- An allergy record deleted causing an adverse drug reaction
- A diagnosis altered leading to incorrect treatment
- Fraudulent billing records submitted to insurance companies

---

### Availability — MODERATE

Availability means ensuring authorised users can access the system
when they need it.

**Rating: MODERATE**

**Justification:**
If Bundle becomes unavailable, clinical staff can revert to
documented manual paper-based emergency procedures for a limited
period. Prolonged unavailability is serious but not immediately
life-threatening if fallback procedures are followed.

Consequences of an availability failure:
- Significant operational disruption and patient care delays
- Inability to access medication records in emergencies
- Billing and claims backlog affecting hospital revenue
- Increased error risk during manual operation

---

## Formal Categorization Statement

In accordance with FIPS 199 and NIST SP 800-60, the security
categorization for Bundle EHMS is formally stated as:

```
SC Bundle = {(confidentiality, HIGH), (integrity, HIGH), (availability, MODERATE)}

Overall System Impact Level: HIGH
```

---

## Impact Level Summary Table

| Security Objective | Rating | Primary Reason |
|-------------------|--------|----------------|
| Confidentiality | HIGH | PHI breach causes severe patient and organisational harm |
| Integrity | HIGH | Data tampering could directly harm or kill patients |
| Availability | MODERATE | Manual fallback procedures exist |
| **Overall Impact Level** | **HIGH** | Driven by HIGH ratings for Confidentiality and Integrity |

---

## What HIGH Impact Means for Bundle

Because Bundle is rated HIGH, it must be protected using the HIGH
security control baseline from NIST SP 800-53 Rev. 5. This is the
most rigorous baseline available and includes significantly more
controls than the Moderate or Low baselines.

This means:
- Stronger access control requirements including mandatory MFA
- More frequent monitoring and scanning obligations
- Independent third-party assessment required before ATO
- More detailed documentation and evidence requirements

---

## Approval Record

| Action | Name | Role | Date |
|--------|------|------|------|
| Prepared | James Okafor | ISSO | 2025 |
| Reviewed | Dr. Sarah Mitchell | System Owner | 2025 |
| Reviewed | Priya Nair | ISSE | 2025 |
| Reviewed | Marcus Webb | Privacy Officer | 2025 |
| Approved | Linda Reyes | Authorizing Official | 2025 |

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 | James Okafor | Initial FIPS 199 analysis completed and approved |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

