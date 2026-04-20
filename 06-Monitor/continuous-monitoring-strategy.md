# Continuous Monitoring Strategy

**System:** Bundle — Electronic Healthcare Management System
**Document:** Continuous Monitoring Strategy
**Step:** Step 6 — Monitor
**ATO Reference:** BUNDLE-ATO-2025-001
**Version:** 1.0
**Prepared By:** James Okafor, ISSO
**Date:** 2025

---

## Purpose

This document defines the continuous monitoring programme that
Bundle's team will run throughout the three-year authorization period.
It ensures that Bundle's security controls remain effective as the
system, its users, and the threat landscape evolve over time.

If monitoring stops, the ATO can be revoked.

---

## Monitoring Objectives

- Maintain ongoing awareness of Bundle's security posture
- Detect new vulnerabilities and security incidents quickly
- Ensure all ATO conditions are met and POA&M items are remediated
- Provide the AO with timely accurate information
- Detect changes that may affect Bundle's security posture

---

## Monitoring Activities Schedule

| Activity | Frequency | Owner | Tool |
|----------|-----------|-------|------|
| Audit log review | Weekly | James Okafor (ISSO) | AWS CloudWatch |
| GuardDuty review | Weekly | James Okafor (ISSO) | AWS GuardDuty |
| Vulnerability scanning (EC2) | Monthly | Priya Nair (ISSE) | AWS Inspector |
| POA&M review and report to AO | Monthly | James Okafor (ISSO) | POA&M tracker |
| Security Hub review | Monthly | Priya Nair (ISSE) | AWS Security Hub |
| AWS Config compliance review | Monthly | Priya Nair (ISSE) | AWS Config |
| Patch currency check | Monthly | Priya Nair (ISSE) | AWS Systems Manager |
| Training completion tracking | Monthly | James Okafor (ISSO) | LMS Platform |
| Web application scanning | Quarterly | Priya Nair (ISSE) | OWASP ZAP |
| Control spot-check (5 controls) | Quarterly | James Okafor (ISSO) | SSP and evidence |
| Posture report to AO | Quarterly | James Okafor (ISSO) | This folder |
| Full control assessment | Annually | External Assessor | NIST SP 800-53A |
| Vendor and BAA review | Annually | James Okafor (ISSO) | Vendor contracts |
| Annual security review | Annually | James Okafor (ISSO) | All RMF documents |
| Reauthorization preparation | Month 18 (2027) | James Okafor (ISSO) | Full RMF lifecycle |

---

## Escalation Thresholds

| Trigger | Response Time | Action |
|---------|--------------|--------|
| Critical CVE on any EC2 instance | Immediate | ISSE notified within 1 hour. Patch within 15 days. |
| GuardDuty HIGH severity finding | 2 hours | ISSO investigates. IR invoked if active compromise. |
| Confirmed PHI breach | Immediate | IR invoked. AO notified. HIPAA notification activated. |
| POA&M item overdue by 7+ days | 1 business day | Escalated to System Owner. Written explanation to AO. |
| AWS Config non-compliant 48+ hours | 48 hours | ISSE investigates. POA&M raised if not resolved in 5 days. |
| Failed backup 2 consecutive days | 24 hours | ISSE investigates. AO notified if recovery at risk. |
| Significant system change proposed | Before implementation | ISSO security impact assessment. AO notified within 5 days. |

---

## Monitoring Tools

| Tool | Purpose |
|------|---------|
| AWS Inspector | Monthly automated vulnerability scanning of EC2 instances |
| AWS GuardDuty | ML-based continuous threat detection |
| AWS Security Hub | Aggregated findings dashboard |
| AWS Config | Continuous configuration compliance monitoring |
| AWS CloudWatch | Log aggregation and metric alarms |
| AWS CloudTrail | Complete record of all AWS API calls |
| CrowdStrike Falcon | Real-time endpoint detection and response |
| OWASP ZAP | Quarterly web application vulnerability scanning |
| AWS Systems Manager | Patch management and configuration enforcement |
| LMS Platform | Security awareness training completion tracking |

---

## Reporting Schedule

| Report | Frequency | Recipient | Due Date |
|--------|-----------|-----------|---------|
| POA&M status report | Monthly | AO — Linda Reyes | First business day of each month |
| Vulnerability scan summary | Monthly | ISSO | Within 3 days of scan completion |
| Security posture summary | Quarterly | AO — Linda Reyes | End of each quarter |
| Annual security review | Annually | AO and System Owner | Year anniversary of ATO |

---

## Year-One Results Summary

| Metric | Result |
|--------|--------|
| Original POA&M items | 6 — all closed within target dates |
| New post-ATO findings | 2 — both closed within SLA |
| Confirmed security incidents | 0 |
| Monthly scans completed | 12 of 12 |
| Quarterly posture reports | 4 of 4 submitted on time |
| ATO Condition 1 (IR training) | Satisfied Day 28 |
| Annual security review | Complete — no material changes |

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 | James Okafor | Initial ConMon strategy completed |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

