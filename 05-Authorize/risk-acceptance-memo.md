# Risk Acceptance Memorandum

---

**TO:** Bundle RMF Programme Team
**FROM:** Linda Reyes, Chief Information Officer — Authorizing Official
**SUBJECT:** Risk Acceptance for Bundle Electronic Healthcare Management System
**DATE:** 2025
**REFERENCE:** BUNDLE-ATO-2025-001

---

## 1. Purpose

I have completed my review of the authorization package for Bundle
(BUNDLE-EHMS-001). This memorandum documents my formal acceptance of
the residual risks associated with authorizing Bundle to operate and
my decision regarding its Authorization to Operate.

---

## 2. Documents Reviewed

I have reviewed the following documents in reaching this decision:

- System Security Plan (Final), Version 1.0
- Security Assessment Report, ClearPath Security LLC, 2025
- Plan of Action and Milestones, Version 1.0 (6 open items)
- FIPS 199 Security Categorization (HIGH impact)
- Risk Executive Summary
- AWS HIPAA Business Associate Agreement
- AWS SOC 2 Type II Report (most recent)

---

## 3. Summary of Security Posture

Based on the independent assessment conducted by ClearPath Security
LLC, I am satisfied that Bundle's core technical controls are robustly
implemented and operating effectively.

The assessment identified no critical technical failures in Bundle's
PHI protection mechanisms. The cryptographic controls, identity and
authentication mechanisms, and monitoring capabilities are of a
standard I consider adequate for the sensitivity of the data
Bundle processes.

---

## 4. Residual Risks Accepted

I formally acknowledge and accept the following residual risks,
subject to the conditions stated in Section 5:

| ID | Risk | Severity | Decision |
|----|------|----------|---------|
| RR-001 | 193 staff untrained in IR | HIGH | Accepted CONDITIONALLY — 30-day completion required |
| RR-002 | 4 Lambda functions outside Config baseline | MODERATE | Accepted — POA&M-002 within 60 days |
| RR-003 | 12 staff without background checks | MODERATE | Accepted — POA&M-003 within 45 days |
| RR-004 | Online training module incomplete | MODERATE | Accepted — POA&M-004 within 60 days |
| RR-005 | 3 Lambda accounts using static API keys | LOW | Accepted — POA&M-005 within 90 days |
| RR-006 | Audit review log unstructured | LOW | Accepted — POA&M-006 within 30 days |

---

## 5. Conditions of Authorization

This authorization is granted subject to the following conditions.
Failure to meet any condition will result in immediate ATO review
and potential suspension:

**Condition 1 — IR Training:** Evidence of 100% completion for all
500 staff within 30 days. This is a mandatory HIGH priority condition.

**Condition 2 — POA&M Compliance:** All six items resolved by their
stated dates. Monthly status reports to the AO.

**Condition 3 — Continuous Monitoring:** Full ConMon programme
maintained. Quarterly posture summaries to the AO.

**Condition 4 — Change Notification:** Significant changes reported
within 5 business days.

**Condition 5 — Breach Notification:** Any PHI breach reported
immediately.

---

## 6. AO Decision

Based on my review and the residual risk profile above, I have
determined that the residual risk associated with operating Bundle
is ACCEPTABLE to this organisation, subject to the conditions above.

I hereby accept the residual risk and direct the ISSO and System
Owner to proceed with issuing the formal Authorization to Operate
for Bundle EHMS.

```
Signed:  Linda Reyes
Title:   CIO — Authorizing Official
Org:     Bundle Hospital Network
Date:    2025
```

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

