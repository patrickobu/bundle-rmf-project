# Information Types

![System](https://img.shields.io/badge/System-Bundle%20EHMS-blue)
![Step](https://img.shields.io/badge/RMF%20Step-1%20Categorize-blue)
![Standard](https://img.shields.io/badge/Standard-NIST%20SP%20800--60-purple)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## Purpose

This document identifies every type of information that Bundle
creates, receives, maintains, or transmits. Each information
type is classified using NIST SP 800-60 Vol. II and assessed
for its confidentiality, integrity, and availability impact.

This is a required input to the FIPS 199 categorization process.
The overall system impact level is determined by the highest
impact rating across all information types and all three
security objectives — this is called the high-water mark rule.

---

## What is an Information Type?

An information type is a specific category of information
defined by its function, use, and the harm its compromise
would cause. NIST SP 800-60 provides a standard taxonomy
of government information types to ensure consistent
categorization across organisations.

---

## Information Types in Bundle

### 1. Protected Health Information (PHI)

**NIST SP 800-60 reference:** C.3.1.1 — Patient Health Information

**What this includes in Bundle:**
Patient diagnoses, clinical notes, medication records, laboratory
results, medical images, surgical records, mental health records,
HIV/AIDS status, substance abuse records, and any other
individually identifiable health information.

**Regulatory basis:** HIPAA Privacy Rule (45 CFR Part 164),
HITECH Act

| Security Objective | Impact Rating | Justification |
|-------------------|--------------|--------------|
| Confidentiality | HIGH | Unauthorised disclosure causes severe patient harm — discrimination, identity theft, reputational damage. HIPAA violations can result in criminal charges. |
| Integrity | HIGH | Corrupted or altered clinical data can cause misdiagnosis, wrong medication dosages, or patient death. |
| Availability | MODERATE | Short-term unavailability is manageable with paper backup procedures. Extended unavailability causes serious operational harm. |

---

### 2. Personally Identifiable Information (PII)

**NIST SP 800-60 reference:** C.3.1.3 — Personally Identifiable Information

**What this includes in Bundle:**
Patient names, dates of birth, addresses, phone numbers,
email addresses, Social Security Numbers, insurance member IDs,
and next-of-kin information.

**Regulatory basis:** HIPAA Privacy Rule, applicable state
privacy laws

| Security Objective | Impact Rating | Justification |
|-------------------|--------------|--------------|
| Confidentiality | HIGH | PII combined with PHI creates extreme identity theft risk. |
| Integrity | MODERATE | Incorrect PII causes billing errors and misidentification. |
| Availability | LOW | PII is needed for administrative functions. Clinical care can proceed without it in an emergency. |

---

### 3. Insurance and Billing Data

**NIST SP 800-60 reference:** C.3.1.6 — Financial Management Information

**What this includes in Bundle:**
Insurance policy numbers, claim submissions, payment records,
explanation of benefits documents, and billing codes.

**Regulatory basis:** HIPAA Transaction and Code Sets Rule,
applicable financial regulations

| Security Objective | Impact Rating | Justification |
|-------------------|--------------|--------------|
| Confidentiality | MODERATE | Financial data disclosure causes harm but is less sensitive than PHI. |
| Integrity | HIGH | Billing fraud or errors cause direct financial harm and regulatory violations. |
| Availability | MODERATE | Claims processing delays cause revenue disruption. |

---

### 4. Scheduling and Operational Data

**NIST SP 800-60 reference:** C.3.2.1 — Healthcare Management Information

**What this includes in Bundle:**
Appointment schedules, room bookings, staff duty rosters,
equipment availability, and procedure scheduling.

**Regulatory basis:** Operational requirement only

| Security Objective | Impact Rating | Justification |
|-------------------|--------------|--------------|
| Confidentiality | LOW | Scheduling information is not personally sensitive. |
| Integrity | MODERATE | Incorrect schedules cause operational disruption and patient care delays. |
| Availability | MODERATE | Unavailability disrupts hospital operations significantly. |

---

### 5. Audit and Security Logs

**NIST SP 800-60 reference:** C.2.1.3 — Audit and Monitoring Information

**What this includes in Bundle:**
User login and logout records, patient record access logs,
medication administration records, system error logs,
security alert logs, and administrator action logs.

**Regulatory basis:** HIPAA Security Rule (45 CFR 164.312(b)),
NIST SP 800-53 AU controls

| Security Objective | Impact Rating | Justification |
|-------------------|--------------|--------------|
| Confidentiality | MODERATE | Logs contain sensitive access patterns and system information. |
| Integrity | HIGH | Tampered logs would destroy forensic value and violate HIPAA audit requirements. |
| Availability | MODERATE | Real-time log availability is needed for security monitoring. |

---

### 6. Staff Credentials and Access Information

**NIST SP 800-60 reference:** C.2.8.12 — Identity and Authentication Information

**What this includes in Bundle:**
Staff usernames, hashed passwords, MFA configuration,
role assignments, and access rights.

**Regulatory basis:** NIST SP 800-53 IA and AC controls

| Security Objective | Impact Rating | Justification |
|-------------------|--------------|--------------|
| Confidentiality | HIGH | Compromised credentials enable unauthorised access to all PHI. |
| Integrity | HIGH | Modified access rights could grant unauthorised PHI access. |
| Availability | MODERATE | IAM unavailability prevents staff login and system use. |

---

## Information Type Impact Summary

| Information Type | Confidentiality | Integrity | Availability |
|-----------------|----------------|-----------|-------------|
| Protected Health Information | HIGH | HIGH | MODERATE |
| Personally Identifiable Information | HIGH | MODERATE | LOW |
| Insurance and Billing Data | MODERATE | HIGH | MODERATE |
| Scheduling and Operational Data | LOW | MODERATE | MODERATE |
| Audit and Security Logs | MODERATE | HIGH | MODERATE |
| Staff Credentials | HIGH | HIGH | MODERATE |

---

## Overall System Impact Determination

Applying the high-water mark rule across all information types
and all three security objectives:

| Security Objective | Highest Rating Across All Types |
|-------------------|---------------------------------|
| Confidentiality | **HIGH** (PHI, PII, Staff Credentials) |
| Integrity | **HIGH** (PHI, Billing, Logs, Credentials) |
| Availability | **MODERATE** (PHI, Billing, Scheduling, Logs, Credentials) |

This determination feeds directly into the FIPS 199
categorization documented in `fips199-impact-analysis.md`.

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

