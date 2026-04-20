# Step 6 — Monitor

![Status](https://img.shields.io/badge/Status-Active%20%E2%80%94%20Ongoing-brightgreen)
![RMF Step](https://img.shields.io/badge/RMF%20Step-6%20Monitor-blue)
![ATO](https://img.shields.io/badge/ATO-BUNDLE--ATO--2025--001-blue)
![Valid Until](https://img.shields.io/badge/Valid%20Until-2028-orange)
![POA&M](https://img.shields.io/badge/POA%26M-6%2F6%20Original%20Closed-brightgreen)
![Incidents](https://img.shields.io/badge/Confirmed%20Incidents-0-brightgreen)

---

## What is the Monitor Step?

Getting the ATO is not the finish line — it is the starting gun for ongoing security operations.

The Monitor step runs continuously for the entire **three-year life of the Authorization to Operate**. It ensures that:

- Security controls remain effective as the system and threats evolve
- New vulnerabilities are detected and remediated within defined timeframes
- The AO is kept informed through regular posture reports
- The POA&M is actively managed — not filed away and forgotten
- System changes are assessed for security impact before they go live

> **If monitoring stops, the ATO can be revoked.** The Authorizing Official's trust in Bundle's security posture depends entirely on the quality of this programme.

---

## Documents in This Folder

| File | Description |
|------|-------------|
| `README.md` | This file — full monitoring programme, scan reports, and POA&M updates |
| `continuous-monitoring-strategy.md` | Full ConMon strategy with activities, frequencies, and thresholds |
| `scan-reports/` | Monthly vulnerability scan report summaries |
| `poam-updates.md` | Living POA&M — all findings with current status |
| `quarterly-posture-reports/` | Q1–Q4 posture reports submitted to AO |
| `change-management-log.md` | Record of all system changes with security assessments |
| `audit-review-log.md` | Weekly structured audit log review records |
| `conmon-metrics-dashboard.md` | Year-one monitoring metrics summary |

---

## Monitoring Activities at a Glance

| Activity | Frequency | Owner | Tool |
|----------|-----------|-------|------|
| Vulnerability Scanning (EC2) | Monthly | Priya Nair (ISSE) | AWS Inspector |
| Web Application Scanning | Quarterly | Priya Nair (ISSE) | OWASP ZAP |
| Audit Log Review | Weekly | James Okafor (ISSO) | AWS CloudWatch |
| GuardDuty Review | Weekly | James Okafor (ISSO) | AWS GuardDuty |
| POA&M Review + Report to AO | Monthly | James Okafor (ISSO) | POA&M tracker |
| Security Hub Review | Monthly | Priya Nair (ISSE) | AWS Security Hub |
| AWS Config Compliance | Monthly | Priya Nair (ISSE) | AWS Config |
| Training Completion Tracking | Monthly | James Okafor (ISSO) | LMS Platform |
| Spot-Check Control Assessment | Quarterly | James Okafor (ISSO) | SSP + Evidence |
| Patch Currency Review | Monthly | Priya Nair (ISSE) | AWS Systems Manager |
| Third-Party Vendor Review | Annually | James Okafor (ISSO) | Vendor contracts |
| Full Control Assessment | Annually | External Assessor | NIST SP 800-53A |
| Quarterly Posture Report to AO | Quarterly | James Okafor (ISSO) | This folder |
| Annual Security Review | Annually | James Okafor (ISSO) | All RMF docs |
| Reauthorization Preparation | Month 18 (2027) | James Okafor (ISSO) | Full RMF lifecycle |

![Continuous monitoring calendar](10-conmon-calendar.svg)

---

## Escalation Thresholds

| Trigger | Response Time | Action |
|---------|--------------|--------|
| Critical CVE on any EC2 instance | Immediate | ISSE notified within 1hr. Patch within 15 days. AO notified if downtime required. |
| GuardDuty HIGH severity finding | 2 hours | ISSO investigates. IR invoked if active compromise. AO notified within 24hrs. |
| Confirmed PHI breach | Immediate | IR invoked. AO notified immediately. HIPAA notification activated. |
| POA&M item overdue > 7 days | 1 business day | Escalated to System Owner. Written explanation to AO. Revised date agreed. |
| AWS Config non-compliant > 48hrs | 48 hours | ISSE investigates. POA&M raised if remediation > 5 days. |
| Failed backup 2 consecutive days | 24 hours | ISSE investigates. AO notified if recovery capability at risk. |
| 20+ failed logins from single IP in 10 min | Immediate (automated) | CloudWatch alarm triggers. ISSO investigates. IP blocked at WAF if confirmed attack. |
| Significant system change proposed | Before implementation | ISSO conducts security impact assessment. AO notified within 5 business days. |

---

## Monthly Vulnerability Scan Reports

### Month 1 Post-ATO
| Severity | Count |
|----------|-------|
| 🔴 Critical | 0 |
| 🟠 High | 0 |
| 🟡 Medium | 3 |
| ⚪ Low | 7 |

**Summary:** Clean first scan. Three Medium CVEs in Amazon Linux kernel — all within 90-day SLA. Seven Low findings carried from pre-ATO baseline. No immediate action required.

---

### Month 2 Post-ATO
| Severity | Count |
|----------|-------|
| 🔴 Critical | 0 |
| 🟠 High | 1 ← New |
| 🟡 Medium | 2 |
| ⚪ Low | 6 |

**Summary:** One new High CVE (Node.js runtime, CVSS 7.4). Patch available. Scheduled within 30-day SLA. Two Low findings closed. Quarterly OWASP ZAP scan conducted — 1 Medium (missing CSP header), 3 Low findings.

**OWASP ZAP Q1 Summary:** High: 0 | Medium: 1 (CSP header) | Low: 3 (verbose server headers)

---

### Month 3 Post-ATO
| Severity | Count |
|----------|-------|
| 🔴 Critical | 0 |
| 🟠 High | 0 ← Patched |
| 🟡 Medium | 2 |
| ⚪ Low | 5 |

**Summary:** Month 2 High CVE patched and verified closed. CSP header remediated ahead of schedule. Three Low findings closed. Downward trend — improving posture. POA&M-002 (Lambda Config) completed.

### Three-Month Scan Trend

| Month | Critical | High | Medium | Low | Total Open | Closed |
|-------|----------|------|--------|-----|------------|--------|
| Month 1 | 0 | 0 | 3 | 7 | 10 | 0 |
| Month 2 | 0 | 1 | 2 | 6 | 9 + ZAP | 2 |
| Month 3 | 0 | 0 | 2 | 5 | 7 | 3 |

---

## POA&M — Month 3 Status

### Summary

| ID | Title | Risk | Status | Closed |
|----|-------|------|--------|--------|
| POA&M-001 | IR Training Gap | 🔴 HIGH | ✅ Closed | Day 28 post-ATO |
| POA&M-002 | Lambda Config Baseline | 🟠 MODERATE | ✅ Closed | Month 3 |
| POA&M-003 | Background Checks | 🟠 MODERATE | ✅ Closed | Month 2 |
| POA&M-004 | Security Training Module | 🟠 MODERATE | ✅ Closed | Month 2 |
| POA&M-005 | Static API Keys | 🟡 LOW | 🔄 In Progress | Target: Month 4 |
| POA&M-006 | Audit Review Log Format | 🟡 LOW | ✅ Closed | Month 1 Week 2 |
| POA&M-007 (new) | Node.js CVE | 🟠 MODERATE | ✅ Closed | Month 3 Week 2 |
| POA&M-008 (new) | CSP Header Missing | 🟡 LOW | ✅ Closed | Month 3 Week 1 |

> ✅ 4 of 6 original findings closed within 3 months. The HIGH finding (IR Training) was the first to close — Day 28, within the 30-day ATO condition deadline.

### Key Updates

**POA&M-001 — IR Training (HIGH) — CLOSED Day 28**
All 193 outstanding staff completed mandatory IR training by Day 26. LMS completion report (500/500) submitted to AO Day 28. AO confirmed Condition 1 satisfied.

**POA&M-002 — Lambda Config (MODERATE) — CLOSED Month 3**
ISSE discovered one Lambda had overly permissive S3 access during audit — corrected immediately. Custom AWS Config rules deployed covering all 4 Lambda functions. All now compliant.

**POA&M-003 — Background Checks (MODERATE) — CLOSED Month 2**
All 12 retrospective checks completed. All clear — no adverse findings. HR process updated to require check completion before access granted.

**POA&M-004 — Training Module (MODERATE) — CLOSED Month 2**
Online module completed and deployed. All 500 staff completed within 21-day window. LMS completion archived as HIPAA evidence.

**POA&M-005 — Static API Keys (LOW) — IN PROGRESS**
IAM roles created. Staging migration tested successfully. Production migration scheduled Month 4 Week 1. On track within 90-day SLA.

**POA&M-006 — Audit Log Format (LOW) — CLOSED Month 1 Week 2**
Structured template implemented Week 2. All subsequent reviews using new format. Three months backfilled.

---

## Quarterly Security Posture Reports

### Q1 (Months 1–3) — Overall Posture: ⚠️ MODERATE

| Metric | Value |
|--------|-------|
| Top Risk | IR training gap — resolved Day 28 |
| POA&M Closed | 4 of 6 |
| POA&M Open | 2 + 2 new post-ATO findings |
| Security Incidents | 0 confirmed. 1 GuardDuty MEDIUM (port scan) — blocked at WAF |
| Key Action | ATO Condition 1 satisfied. Four POA&M items closed. |

---

### Q2 (Months 4–6) — Overall Posture: ✅ STRONG

| Metric | Value |
|--------|-------|
| Top Risk | POA&M-005 (static API keys) — closed Month 4 |
| POA&M Closed | 6 of 8 (all original + new 007, 008) |
| POA&M Open | 0 original. 1 new Low (verbose HTTP headers) |
| Security Incidents | 0 confirmed. 2 GuardDuty LOW — false positives (maintenance windows) |
| Key Action | All original POA&M items closed. Full OWASP ZAP scan clean. STRONG posture achieved. |

---

### Q3 (Months 7–9) — Overall Posture: ✅ STRONG

| Metric | Value |
|--------|-------|
| Top Risk | 3 open Low CVEs — all within 180-day SLA |
| POA&M Closed | 1 new Low (HTTP headers) |
| POA&M Open | 3 Low CVEs (within SLA) |
| Security Incidents | 0 confirmed. 1 phishing attempt on ISSO email — contained, no breach. |
| Key Action | Spot-check assessment — 5 controls, all passed. Annual training renewal launched — 89% completion. |

---

### Q4 (Months 10–12) — Overall Posture: ✅ STRONG

| Metric | Value |
|--------|-------|
| Top Risk | Annual training — 96% completion (4% on approved extension) |
| POA&M Open | 2 Low CVEs (within SLA) |
| Security Incidents | 0 confirmed |
| Key Action | Annual security review complete. SSP reviewed — no changes required. All vendor BAAs renewed. Reauthorization planning begins Month 18. |

---

## Year-One Metrics Summary

| Metric | Value |
|--------|-------|
| Original POA&M Items | 6 |
| Original Items Closed | ✅ 6 of 6 (100%) |
| New Post-ATO Items | 2 |
| New Items Closed | ✅ 2 of 2 (100%) |
| Current Open Items | 2 Low CVEs (within SLA) |
| Confirmed Security Incidents | 0 |
| GuardDuty Findings Investigated | 4 (3 false positives, 1 contained) |
| Monthly Scans Completed | 12 of 12 |
| Quarterly Reports to AO | 4 of 4 (all on time) |
| ATO Condition 1 | ✅ Satisfied Day 28 |
| Annual Security Review | ✅ Complete |
| Avg AWS Config Non-Compliant Resources | 0.3/month (all resolved within threshold) |

---

## Change Management Log

| ID | Month | Change | Impact | AO Action |
|----|-------|--------|--------|-----------|
| CHG-001 | Month 2 | Bundle app update v3.2.1 → v3.2.2 | Low | No notification required |
| CHG-002 | Month 3 | Node.js security patch (CVE-2025-XXXX) | Low | No notification — risk reduction |
| CHG-003 | Month 4 | Lambda IAM role migration (POA&M-005) | Low | No notification — risk reduction |
| CHG-004 | Month 6 | 350 new users from merged satellite clinic | **MODERATE** | **AO notified — no reauth required** |
| CHG-005 | Month 8 | RDS PostgreSQL minor version upgrade | Low | No notification required |
| CHG-006 | Month 10 | CrowdStrike Falcon sensor update | Low | No notification required |

---

## The RMF is a Cycle — Not a Finish Line

Bundle has completed all 7 steps of the NIST RMF. But the framework cycles:

| What Changes | What Happens |
|-------------|-------------|
| New system feature added | Update Step 1 boundary → Step 2 control review → Step 3 implementation → AO report |
| New vulnerability discovered | POA&M entry → reassessment if severe → risk acceptance update |
| ATO expires in 2028 | Full RMF cycle begins again |
| PHI breach occurs | IR invoked → AO notified → root cause assessed → reauth triggered |
| Threat landscape shifts | Risk assessment refreshed → control selection reviewed → gaps addressed |

---

## Monitor Step Checklist

| Task | NIST Task ID | Status |
|------|-------------|--------|
| ConMon strategy documented | M-1 | ✅ Complete |
| Monthly scan reports produced (12) | M-2 | ✅ Complete |
| Weekly audit log reviews (52) | M-3 | ✅ Complete |
| POA&M managed — all original items closed | M-4 | ✅ Complete |
| Quarterly posture reports to AO (4) | M-5 | ✅ Complete |
| Change management log maintained | M-6 | ✅ Complete |
| ATO Condition 1 (IR Training) satisfied | M-7 | ✅ Complete |
| Annual security review completed | M-8 | ✅ Complete |
| Annual vendor review + BAA renewals | M-9 | ✅ Complete |
| Reauthorization planning initiated | M-10 | 🔄 In Progress — Month 18 |

---

## Project Complete 🎉

**Bundle EHMS has successfully completed all 7 steps of the NIST SP 800-37 Rev. 2 Risk Management Framework.**

| Step | Name | Status |
|------|------|--------|
| Step 0 | Prepare | ✅ Complete |
| Step 1 | Categorize | ✅ Complete |
| Step 2 | Select | ✅ Complete |
| Step 3 | Implement | ✅ Complete |
| Step 4 | Assess | ✅ Complete |
| Step 5 | Authorize | ✅ Complete — ATO Issued |
| Step 6 | Monitor | ✅ Active — Year 1 Complete |

**ATO Reference:** BUNDLE-ATO-2025-001
**Valid Until:** 2028
**Next Reauthorization:** 2027 (preparation begins Month 18)

➡️ [Back to Project Home](../README.md)
⬅️ [Back to Step 5 — Authorize](../05-authorize/README.md)

---

## Document Information

| Field | Value |
|-------|-------|
| Document Version | 1.0 |
| ConMon Owner | James Okafor, ISSO |
| Technical Owner | Priya Nair, ISSE |
| Reporting To | Linda Reyes, Authorizing Official |
| NIST Reference | NIST SP 800-37 Rev. 2 — Monitor Step |
| Supporting Reference | NIST SP 800-137 (Continuous Monitoring) |

---

*This document is part of the Bundle RMF portfolio project. All names, data, and scenarios are fictional and used for learning and career development purposes only.*

