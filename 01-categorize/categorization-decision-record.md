# Categorization Decision Record

![System](https://img.shields.io/badge/System-Bundle%20EHMS-blue)
![Step](https://img.shields.io/badge/RMF%20Step-1%20Categorize-blue)
![Result](https://img.shields.io/badge/Impact%20Level-HIGH-red)
![Standard](https://img.shields.io/badge/Standard-FIPS%20199-orange)
![Status](https://img.shields.io/badge/Approved-Yes-brightgreen)

---

## Purpose

This document is the formal record of Bundle's security
categorization decision. It summarises the analysis from
all supporting documents in this folder and records the
official approval by all required parties.

This document is required by NIST SP 800-37 Rev. 2
(Task C-1) and serves as the authoritative reference
for the impact level used throughout the rest of the
RMF process.

---

## Formal Categorization Statement

In accordance with FIPS 199 (Standards for Security
Categorization of Federal Information and Information
Systems) and NIST SP 800-60 (Guide for Mapping Types
of Information and Information Systems to Security
Categories), the security categorization of Bundle
is formally stated as:

```
Security Category Bundle =
{(Confidentiality, HIGH), (Integrity, HIGH), (Availability, MODERATE)}

Overall System Impact Level = HIGH
```

The overall impact level of HIGH is determined by applying
the high-water mark rule — the overall level equals the
highest rating across all three security objectives.

---

## Summary of Analysis

The full analysis supporting this decision is documented
in the following files in this folder:

| File | Analysis Performed |
|------|--------------------|
| `information-types.md` | All six information types identified and rated |
| `fips199-impact-analysis.md` | Full FIPS 199 analysis with justifications |
| `system-boundary.md` | Authorization boundary defined |
| `system-description.md` | System purpose and architecture documented |
| `hardware-software-inventory.md` | All components inventoried |
| `data-flow-description.md` | All data flows mapped and described |

---

## Impact Ratings — Final Determination

### Confidentiality — HIGH

**Reason:** Bundle stores and processes Protected Health
Information (PHI) for thousands of patients. PHI is
classified as HIGH confidentiality because its unauthorised
disclosure would cause severe harm to patients — including
discrimination, identity theft, psychological harm, and
potential physical harm in cases involving mental health
or infectious disease status.

Unauthorised disclosure would also cause severe harm to
the organisation through HIPAA penalties of up to
$1.9 million per violation category per year and
potential criminal liability for responsible individuals.

**Supporting reference:** information-types.md — PHI
section, Confidentiality rating HIGH

---

### Integrity — HIGH

**Reason:** Clinical staff make treatment decisions based
on data stored in Bundle. If patient records were
tampered with — for example a medication dosage changed,
a drug allergy removed, or a diagnosis altered — the
consequence could be serious patient harm or death.

The integrity of audit logs is also rated HIGH because
tampered logs would destroy forensic capability and
constitute a HIPAA violation.

**Supporting reference:** information-types.md — PHI
section and Audit Logs section, Integrity rating HIGH

---

### Availability — MODERATE

**Reason:** While Bundle is critical to hospital operations,
the hospital has documented manual emergency procedures
that clinical staff can use for a limited period if
Bundle becomes unavailable. The system is not life-critical
in the sense that its absence alone would cause immediate
patient harm.

However, extended unavailability would cause serious
operational disruption, patient care delays, and
potential regulatory concerns. MODERATE is the
appropriate rating.

**Supporting reference:** information-types.md — PHI
section, Availability rating MODERATE

---

## Impact Level Comparison

| Objective | Rating | What this means for control selection |
|-----------|--------|---------------------------------------|
| Confidentiality | HIGH | Most stringent access controls, encryption requirements |
| Integrity | HIGH | Strong integrity checking, audit logging, change management |
| Availability | MODERATE | Backup and recovery, reasonable RTO/RPO targets |
| **Overall** | **HIGH** | Full NIST SP 800-53 HIGH impact baseline required |

---

## Implications of HIGH Impact

Because Bundle is rated HIGH impact, it must:

- Implement the NIST SP 800-53 Rev. 5 HIGH control baseline
  (approximately 325+ controls)
- Undergo independent assessment by qualified assessors
  before the Authorizing Official can issue an ATO
- Maintain more rigorous continuous monitoring than a
  MODERATE or LOW system would require
- Comply with all HIPAA technical safeguard requirements
- Maintain FIPS-validated encryption for all PHI

---

## Approval Record

This categorization was reviewed and approved by all required
parties before the RMF process proceeded to Step 2 (Select).

| Role | Name | Action | Date |
|------|------|--------|------|
| ISSO | James Okafor | Prepared and reviewed | 2025 |
| ISSE | Priya Nair | Technical review | 2025 |
| Privacy Officer | Marcus Webb | Privacy impact review | 2025 |
| System Owner | Dr. Sarah Mitchell | Approved | 2025 |
| Authorizing Official | Linda Reyes | Acknowledged | 2025 |

**Official categorization approved by System Owner:**
Dr. Sarah Mitchell, Chief Medical Officer
Date: 2025

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 | James Okafor | Initial categorization decision recorded and approved |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

