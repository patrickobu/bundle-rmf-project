# Plan of Action and Milestones (POA&M)

**System:** Bundle — Electronic Healthcare Management System
**Document:** Plan of Action and Milestones
**Step:** Step 4 — Assess (maintained through Step 6 — Monitor)
**Version:** 1.2 — Updated Month 3
**Maintained By:** James Okafor, ISSO
**Date:** 2025

---

## What is the POA&M?

The POA&M is Bundle's security to-do list. It tracks every security
weakness identified in the programme — whether discovered during
assessment, vulnerability scanning, or continuous monitoring.

A well-maintained POA&M is a sign of a mature security programme,
not a weak one. It shows the AO exactly what weaknesses exist and
what is being done about them.

---

## POA&M Summary

| ID | Title | Risk | Owner | Due | Status |
|----|-------|------|-------|-----|--------|
| POA&M-001 | IR Training Gap | HIGH | James Okafor | 30 days from ATO | CLOSED |
| POA&M-002 | Lambda Config Baseline | MODERATE | Priya Nair | 60 days from ATO | CLOSED |
| POA&M-003 | Background Checks | MODERATE | Marcus Webb | 45 days from ATO | CLOSED |
| POA&M-004 | Security Training Module | MODERATE | James Okafor | 60 days from ATO | CLOSED |
| POA&M-005 | Static API Keys | LOW | Priya Nair | 90 days from ATO | CLOSED |
| POA&M-006 | Audit Review Log Format | LOW | James Okafor | 30 days from ATO | CLOSED |
| POA&M-007 | Node.js CVE (new — Month 2) | MODERATE | Priya Nair | 30 days | CLOSED |
| POA&M-008 | CSP Header Missing (new — Month 2) | LOW | Priya Nair | 90 days | CLOSED |

---

## Detailed POA&M Entries

### POA&M-001 — IR Training Gap
**Risk:** HIGH
**Finding:** 193 of 500 staff had not completed mandatory IR training
including 24 doctors and 37 nurses with PHI access.
**Corrective Action:** Issue formal notices, enable automated
reminders, escalate to System Owner for non-completions, confirm
100% completion and provide evidence to AO.
**Owner:** James Okafor, ISSO
**Target Date:** 30 days from ATO
**Status:** CLOSED — Day 28
**Evidence:** LMS completion report showing 500/500. Submitted to AO.

---

### POA&M-002 — Lambda Configuration Baseline
**Risk:** MODERATE
**Finding:** 4 Lambda functions not covered by AWS Config rules.
One had overly permissive S3 access — corrected immediately.
**Corrective Action:** Audit Lambda IAM roles, develop custom Config
rules, deploy rules, update SSP.
**Owner:** Priya Nair, ISSE
**Target Date:** 60 days from ATO
**Status:** CLOSED — Month 3, Week 12
**Evidence:** AWS Config dashboard showing zero Lambda violations.

---

### POA&M-003 — Background Checks Incomplete
**Risk:** MODERATE
**Finding:** 12 staff without background check records.
9 had PHI access. No adverse findings.
**Corrective Action:** Engage vendor, prioritise PHI-access staff,
complete all checks, update HR policy.
**Owner:** Marcus Webb, Privacy Officer
**Target Date:** 45 days from ATO
**Status:** CLOSED — Month 2, Week 5
**Evidence:** Vendor completion certificates retained.

---

### POA&M-004 — Security Training Module
**Risk:** MODERATE
**Finding:** Online training module under development.
In-person delivery lacking automated tracking.
**Corrective Action:** Complete modules, QA review, deploy to all
500 staff, confirm 100% completion.
**Owner:** James Okafor, ISSO
**Target Date:** 60 days from ATO
**Status:** CLOSED — Month 2, Week 8
**Evidence:** LMS completion report archived as HIPAA evidence.

---

### POA&M-005 — Static API Keys
**Risk:** LOW
**Finding:** 3 Lambda service accounts using static long-lived
API keys instead of IAM role-based credentials.
**Corrective Action:** Create IAM execution roles, update Lambda
config, test, revoke static keys.
**Owner:** Priya Nair, ISSE
**Target Date:** 90 days from ATO
**Status:** CLOSED — Month 4
**Evidence:** IAM roles confirmed. Static keys revoked and deleted.

---

### POA&M-006 — Audit Review Log Format
**Risk:** LOW
**Finding:** Weekly reviews documented in unstructured free-text.
**Corrective Action:** Design structured template, get approval,
implement, backfill previous reviews.
**Owner:** James Okafor, ISSO
**Target Date:** 30 days from ATO
**Status:** CLOSED — Month 1, Week 2
**Evidence:** Completed structured review logs for all weeks.

---

### POA&M-007 — Node.js CVE
**Risk:** MODERATE (new finding — identified in Month 2 scan)
**Finding:** High CVE in Node.js runtime on Bundle API servers.
CVSS score 7.4. Patch available from AWS.
**Corrective Action:** Apply patch to staging, test, apply to
production.
**Owner:** Priya Nair, ISSE
**Target Date:** 30 days from discovery
**Status:** CLOSED — Month 3, Week 2
**Evidence:** AWS Inspector re-scan confirming remediation.

---

### POA&M-008 — Missing Content-Security-Policy Header
**Risk:** LOW (new finding — identified in Month 2 OWASP ZAP scan)
**Finding:** Content-Security-Policy header missing from login page.
**Corrective Action:** Add CSP header to Bundle login page.
**Owner:** Priya Nair, ISSE
**Target Date:** 90 days from discovery
**Status:** CLOSED — Month 3, Week 1
**Evidence:** ISSE verified via manual browser check and targeted
ZAP re-test.

---

## POA&M Review Process

| Activity | Frequency | Action |
|----------|-----------|--------|
| Monthly review | First business day each month | ISSO reviews all open items and submits report to AO |
| New findings | Within 5 business days | Any new finding entered into POA&M |
| Closure | Upon verified completion | ISSO verifies corrective action and retains evidence |
| Escalation | When overdue by 7+ days | ISSO escalates to System Owner immediately |

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 — Post-ATO | James Okafor | Initial POA&M with 6 original findings |
| 1.1 | Month 2 | James Okafor | Added POA&M-007 and POA&M-008. Closed 001, 003, 004, 006. |
| 1.2 | Month 3 | James Okafor | Closed POA&M-002, 007, 008. Updated 005 progress. |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

