# Security Assessment Report

**System:** Bundle — Electronic Healthcare Management System
**Document:** Security Assessment Report (SAR)
**Step:** Step 4 — Assess
**Assessment Organisation:** ClearPath Security LLC
**Version:** 1.0
**Date:** 2025

---

## Executive Summary

ClearPath Security LLC conducted a comprehensive security assessment
of Bundle EHMS. The assessment covered 30 system-specific and hybrid
controls across nine NIST SP 800-53 control families.

**Overall Assessment Result: CONDITIONAL**

Bundle demonstrates a generally strong security posture appropriate
for a HIGH impact healthcare system. The majority of controls are
implemented correctly and operating as intended. Six findings were
identified: one HIGH severity, three MODERATE severity, and two LOW
severity. None of the findings represent an immediate critical risk
to patient safety or PHI confidentiality. All findings have documented
corrective actions in the POA&M.

---

## Results Summary

| Metric | Value |
|--------|-------|
| Total Controls Assessed | 30 |
| Controls — Pass | 24 (80%) |
| Controls — Partial Pass | 4 (13%) |
| Controls — Fail | 2 (7%) |
| HIGH Severity Findings | 1 |
| MODERATE Severity Findings | 3 |
| LOW Severity Findings | 2 |
| Informational Observations | 3 |

---

## Findings

### FINDING-001 — IR Training Not Completed (HIGH)
**Control:** IR-2 / IR-8
**Method:** Interview and Examine
**Status:** Open — POA&M-001

Only 61% of Bundle users (307 of 500) have completed mandatory annual
IR awareness training. This includes 24 doctors and 37 nurses with
clinical PHI access. Under HIPAA, failure to train workforce members
is a direct Security Rule violation (45 CFR 164.308(a)(5)).

**Recommendation:** Complete training for all 193 outstanding staff
within 30 days.

---

### FINDING-002 — Lambda Functions Not in Config Baseline (MODERATE)
**Control:** CM-6
**Method:** Examine and Test
**Status:** Open — POA&M-002

Four AWS Lambda functions are not covered by any AWS Config rule and
have not been assessed against the configuration baseline.

**Recommendation:** Extend AWS Config coverage to Lambda functions
within 60 days.

---

### FINDING-003 — Background Checks Incomplete (MODERATE)
**Control:** PS-3
**Method:** Examine and Interview
**Status:** Open — POA&M-003

12 staff members hired before the current background check policy
have not had retrospective checks completed. 9 of these have PHI
access.

**Recommendation:** Complete retrospective checks within 45 days.
Prioritise the 9 staff with PHI access.

---

### FINDING-004 — Online Training Module Incomplete (MODERATE)
**Control:** AT-2
**Method:** Examine
**Status:** In Progress — POA&M-004

The online security awareness training module is still under
development. Current in-person delivery lacks automated tracking.

**Recommendation:** Complete and deploy the online module within
60 days.

---

### FINDING-005 — API Service Account Static Keys (LOW)
**Control:** AC-11
**Method:** Test
**Status:** Open — POA&M-005

Three Lambda integration service accounts use static long-lived
API keys instead of IAM role-based temporary credentials.

**Recommendation:** Migrate to IAM roles with STS credentials
within 90 days.

---

### FINDING-006 — Audit Review Log Format (LOW)
**Control:** AU-6
**Method:** Examine
**Status:** Open — POA&M-006

Weekly audit reviews are conducted correctly but documented in
unstructured free-text format.

**Recommendation:** Implement a structured template within 30 days.

---

## Controls That Passed Assessment

| Control | Name | Result |
|---------|------|--------|
| AC-2 | Account Management | Pass |
| AC-3 | Access Enforcement | Pass |
| AC-6 | Least Privilege | Pass |
| AC-7 | Login Attempt Limits | Pass |
| AC-17 | Remote Access | Pass |
| AU-2 | Event Logging | Pass |
| AU-9 | Audit Record Protection | Pass |
| AU-11 | Audit Record Retention | Pass |
| IA-2 | MFA — All Users | Pass |
| IA-2(1) | MFA — Privileged Accounts | Pass |
| IA-5 | Password Management | Pass |
| SC-7 | Boundary Protection | Pass |
| SC-8 | Transmission Encryption | Pass |
| SC-28 | Encryption at Rest | Pass |
| IR-4 | Incident Handling | Pass |
| IR-6 | Incident Reporting | Pass |
| IR-8 | Incident Response Plan | Pass |
| SI-2 | Flaw Remediation | Pass |
| SI-3 | Malware Protection | Pass |
| SI-4 | System Monitoring | Pass |
| CP-9 | System Backup | Pass |
| CP-10 | System Recovery | Pass |
| RA-5 | Vulnerability Scanning | Pass |
| AC-11 | Session Lock (human sessions) | Partial Pass |

---

## Assessor Conclusion

Bundle EHMS demonstrates a commendable security posture for a HIGH
impact healthcare information system. The core technical controls
protecting PHI are robustly implemented. The identified findings are
primarily workforce and configuration items, not fundamental technical
failures.

**Bundle is suitable for ATO issuance** subject to the AO reviewing
and accepting the six POA&M findings, with particular attention to
FINDING-001 (IR training completion).

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

