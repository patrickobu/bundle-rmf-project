# Security Assessment Plan

**System:** Bundle — Electronic Healthcare Management System
**Document:** Security Assessment Plan (SAP)
**Step:** Step 4 — Assess
**Version:** 1.0
**Prepared By:** James Okafor, ISSO
**Assessment Conducted By:** ClearPath Security LLC
**Date:** 2025

---

## Assessment Objectives

- Determine whether Bundle's security controls are implemented correctly
- Identify any security weaknesses or gaps
- Assess the overall security posture and residual risk
- Provide the AO with information to support the authorization decision
- Produce a POA&M documenting all findings with remediation actions

---

## Assessment Scope

This assessment covers all security controls selected for Bundle in
Step 2, including system-specific, hybrid, and verification of
inherited AWS controls.

**Out of scope:**
- AWS physical infrastructure (covered by AWS SOC 2 and ISO 27001)
- Third-party systems (insurance APIs, lab system, pharmacy system)
- Controls marked Not Applicable in Step 2 tailoring decisions

---

## Assessment Team

| Role | Name | Organisation |
|------|------|-------------|
| Lead Assessor | Sarah Chen | ClearPath Security LLC |
| Technical Assessor | David Osei | ClearPath Security LLC |
| Privacy Assessor | Dr. Amara Diallo | ClearPath Security LLC |
| ISSO Observer | James Okafor | Bundle Hospital Network |
| Technical Liaison | Priya Nair | Bundle Hospital Network |

---

## Assessment Methods

NIST SP 800-53A defines three assessment methods:

| Method | Description |
|--------|-------------|
| Examine | Review documentation, policies, and system records |
| Interview | Speak with personnel responsible for controls |
| Test | Directly interact with the system to verify behaviour |

---

## Assessment Schedule

| Week | Activity |
|------|----------|
| Week 1 | Document review — SSP, implementation statements, evidence |
| Week 2 | Interviews — ISSO, ISSE, System Owner, Privacy Officer |
| Week 3 | Technical testing — AWS configuration, application, network |
| Week 4 | Findings analysis and SAR drafting |
| Week 5 | SAR review with Bundle team and final SAR production |
| Week 6 | POA&M development |

---

## Rules of Engagement

- All technical testing conducted against a staging environment
- No testing conducted against live production during clinical hours
- Assessment team does not retain or copy any real patient data
- ISSO notified immediately if a critical vulnerability is discovered
- All assessment activities logged and submitted with the final SAR

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

