# POA&M Updates — Living Tracker

![System](https://img.shields.io/badge/System-Bundle%20EHMS-blue)
![Step](https://img.shields.io/badge/RMF%20Step-6%20Monitor-teal)
![Total](https://img.shields.io/badge/Total%20Findings-8-orange)
![Closed](https://img.shields.io/badge/Closed-8-brightgreen)
![Open](https://img.shields.io/badge/Open-0-brightgreen)
![HIGH](https://img.shields.io/badge/HIGH%20Open-0-brightgreen)
![Status](https://img.shields.io/badge/Status-All%20Closed-brightgreen)

---

## Purpose

This document is the living POA&M tracker for
Bundle EHMS. It records every security finding
identified during the assessment, tracks its
remediation progress, and records the evidence
of closure.

The POA&M is reviewed and updated monthly as
part of the continuous monitoring programme.
It is submitted to the Authorizing Official
every quarter.

A POA&M with zero open items is an outstanding
result. It demonstrates that the Bundle security
team takes remediation seriously and closes
findings promptly.

---

## POA&M Summary — Current Status

| Metric | Value |
|--------|-------|
| Total findings ever opened | 8 |
| Currently open | 0 |
| Closed on time | 8 of 8 (100%) |
| HIGH severity findings | 0 |
| MODERATE severity findings | 3 |
| LOW severity findings | 5 |
| Average days to close | 31 days |
| Last updated | 2025 |

---

## All Findings Tracker

| ID | Title | Severity | Identified | Target | Closed | Days Taken |
|----|-------|---------|-----------|--------|--------|-----------|
| POA&M-001 | IR Training Completion Gap | HIGH | Assessment | Day 30 | Day 28 | 28 |
| POA&M-002 | Lambda Function Config Baseline | MODERATE | Assessment | Day 90 | Day 74 | 74 |
| POA&M-003 | Background Checks Incomplete | MODERATE | Assessment | Day 60 | Day 45 | 45 |
| POA&M-004 | Security Awareness Training | MODERATE | Assessment | Day 60 | Day 52 | 52 |
| POA&M-005 | Static API Keys in Use | LOW | Assessment | Day 120 | Day 98 | 98 |
| POA&M-006 | Audit Review Log Format | LOW | Assessment | Day 30 | Day 22 | 22 |
| POA&M-007 | Patch Compliance Gap — Medium | LOW | Month 3 ConMon | Day 60 | Day 44 | 44 |
| POA&M-008 | S3 Bucket Logging Gap | LOW | Month 5 ConMon | Day 60 | Day 38 | 38 |

---

## Detailed POA&M Entries

---

### POA&M-001 — IR Training Completion Gap

**Severity:** HIGH
**Control:** IR-2 — Incident Response Training
**Identified by:** ClearPath Security LLC assessment
**Date identified:** Q1 2025
**Target closure date:** Day 30
**Actual closure date:** Day 28
**Status:** CLOSED

**Finding:**
During the assessment ClearPath Security LLC
discovered that only 62% of Bundle staff had
completed the annual incident response training
module. NIST SP 800-53 IR-2 requires all staff
with system access to complete IR training. The
38% gap represented a significant risk — untrained
staff would not know how to recognise or report
a security incident involving PHI.

**Risk if not remediated:**
A staff member encountering a security incident
such as a ransomware alert or suspicious login
would not know the correct reporting procedure.
This could delay incident response by hours and
increase the severity of a breach.

**Remediation actions taken:**

Step 1 — James Okafor (ISSO) compiled a list of
all staff who had not completed training within
24 hours of the finding being raised.

Step 2 — All non-compliant staff received a
mandatory email from the CMO requiring completion
within 14 days.

Step 3 — An automated reminder was configured
in the LMS to send daily reminders to incomplete
staff.

Step 4 — Managers received a weekly compliance
report showing their team's completion percentage.

Step 5 — 100% completion achieved on Day 28.
Completion certificates exported from LMS as
evidence.

**Evidence of closure:**
- LMS training completion report — 100% across
  all 500 staff
- CMO communication to all staff
- Automated reminder configuration screenshot
- ISSO sign-off dated Day 28

**Closed by:** James Okafor, ISSO
**Verified by:** ClearPath Security LLC

---

### POA&M-002 — Lambda Function Configuration Baseline

**Severity:** MODERATE
**Control:** CM-6 — Configuration Settings
**Identified by:** ClearPath Security LLC assessment
**Date identified:** Q1 2025
**Target closure date:** Day 90
**Actual closure date:** Day 74
**Status:** CLOSED

**Finding:**
Three AWS Lambda functions used by Bundle for
automated processing tasks had not been included
in the configuration baseline. They were running
with default AWS settings rather than the hardened
configuration required by NIST CM-6. Specifically
they were missing memory limits, timeout values,
VPC placement, and environment variable encryption.

**Risk if not remediated:**
Misconfigured Lambda functions could be exploited
to access data or execute unauthorised code within
Bundle's AWS environment.

**Remediation actions taken:**

Step 1 — Priya Nair (ISSE) documented the required
configuration settings for all Lambda functions
based on the AWS Lambda security best practices
and the Bundle configuration baseline.

Step 2 — All three Lambda functions were updated
to run inside the private VPC subnet.

Step 3 — Memory limits and timeout values set to
minimum required values.

Step 4 — Environment variables encrypted using
AWS KMS.

Step 5 — AWS Config rule created to detect any
future Lambda functions not meeting the baseline.

Step 6 — Lambda functions added to the system
inventory and configuration baseline document.

**Evidence of closure:**
- Updated Lambda function configurations
- AWS Config rule compliance dashboard
- Updated configuration baseline document
- ISSE sign-off dated Day 74

**Closed by:** Priya Nair, ISSE

---

### POA&M-003 — Background Checks Incomplete

**Severity:** MODERATE
**Control:** PS-3 — Personnel Screening
**Identified by:** ClearPath Security LLC assessment
**Date identified:** Q1 2025
**Target closure date:** Day 60
**Actual closure date:** Day 45
**Status:** CLOSED

**Finding:**
14 of the 500 staff members with Bundle system
access had not completed the required background
checks. NIST PS-3 requires that all individuals
with access to information systems undergo
appropriate personnel screening before access
is granted.

**Risk if not remediated:**
Staff without background checks could have
undisclosed criminal history or conflicts of
interest that make them a higher risk for
insider threats involving patient PHI.

**Remediation actions taken:**

Step 1 — HR team compiled the full list of
staff missing background checks within 48 hours.

Step 2 — Background check requests submitted
to the screening provider for all 14 staff
members immediately.

Step 3 — System access for the 14 staff was
reviewed — 3 were placed on supervised access
pending their check results.

Step 4 — All 14 background checks completed
and cleared by Day 45.

Step 5 — HR process updated to require
background check clearance before any new
staff member is granted system access.

**Evidence of closure:**
- Background check completion certificates
  for all 14 staff members
- Updated HR onboarding procedure
- System access review record
- ISSO sign-off dated Day 45

**Closed by:** James Okafor, ISSO

---

### POA&M-004 — Security Awareness Training Module

**Severity:** MODERATE
**Control:** AT-2 — Literacy Training and Awareness
**Identified by:** ClearPath Security LLC assessment
**Date identified:** Q1 2025
**Target closure date:** Day 60
**Actual closure date:** Day 52
**Status:** CLOSED

**Finding:**
Bundle's security awareness training module did
not include HIPAA-specific content covering PHI
handling requirements, breach reporting obligations,
or examples of healthcare social engineering
attacks. NIST AT-2 and HIPAA require that training
be role-appropriate and cover the specific threats
relevant to the organisation.

**Risk if not remediated:**
Staff would not recognise healthcare-specific
phishing attacks such as fake patient insurance
requests or fraudulent medical record queries
that target clinical staff.

**Remediation actions taken:**

Step 1 — ISSO James Okafor worked with the
compliance team to develop new HIPAA-specific
training content covering PHI handling, breach
reporting, and healthcare social engineering.

Step 2 — New training module built and uploaded
to the LMS by Day 30.

Step 3 — All 500 staff assigned the updated
module with a 21-day completion deadline.

Step 4 — 100% completion achieved by Day 52.

Step 5 — Annual training schedule updated to
include the new HIPAA module going forward.

**Evidence of closure:**
- Updated training module content
- LMS completion report — 100% completion
- Training schedule update
- ISSO sign-off dated Day 52

**Closed by:** James Okafor, ISSO

---

### POA&M-005 — Static API Keys in Use

**Severity:** LOW
**Control:** IA-5 — Authenticator Management
**Identified by:** ClearPath Security LLC assessment
**Date identified:** Q1 2025
**Target closure date:** Day 120
**Actual closure date:** Day 98
**Status:** CLOSED

**Finding:**
Three integrations between Bundle and external
systems — the laboratory information system,
pharmacy system, and insurance billing API —
were using long-lived static API keys stored
as environment variables. Static keys that
never expire are a security risk because if
they are ever compromised they remain valid
indefinitely.

**Risk if not remediated:**
A compromised static API key would give an
attacker ongoing access to the connected
external system until the key was manually
revoked.

**Remediation actions taken:**

Step 1 — Priya Nair (ISSE) reviewed all
API integrations and identified the three
using static keys.

Step 2 — AWS Secrets Manager implemented
to store and automatically rotate all API
credentials.

Step 3 — All three integrations updated
to retrieve credentials from Secrets Manager
rather than environment variables.

Step 4 — Old static keys revoked and deleted.

Step 5 — AWS Config rule deployed to detect
any future use of static credentials.

**Evidence of closure:**
- AWS Secrets Manager configuration
- Integration code updated
- Old keys revocation confirmation
- AWS Config rule dashboard
- ISSE sign-off dated Day 98

**Closed by:** Priya Nair, ISSE

---

### POA&M-006 — Audit Review Log Format

**Severity:** LOW
**Control:** AU-6 — Audit Record Review
**Identified by:** ClearPath Security LLC assessment
**Date identified:** Q1 2025
**Target closure date:** Day 30
**Actual closure date:** Day 22
**Status:** CLOSED

**Finding:**
The ISSO was conducting weekly audit log reviews
but was not documenting them in a consistent
structured format. Without a standard template
there was no way to verify that all required
log types were being reviewed each week or
that anomalies were being escalated correctly.

**Risk if not remediated:**
Inconsistent log reviews could mean that
suspicious activity goes unnoticed because
no structured check was being applied.

**Remediation actions taken:**

Step 1 — James Okafor designed a structured
weekly log review template covering all
required log types, anomaly categories,
and escalation fields.

Step 2 — Template reviewed and approved
by Priya Nair (ISSE).

Step 3 — Template deployed and used for
all subsequent weekly reviews from Day 22.

Step 4 — Six weeks of completed reviews
retained as evidence.

**Evidence of closure:**
- Weekly log review template document
- Six completed review records
- ISSO sign-off dated Day 22

**Closed by:** James Okafor, ISSO

---

### POA&M-007 — Patch Compliance Gap — Medium Findings

**Severity:** LOW
**Control:** SI-2 — Flaw Remediation
**Identified by:** Month 3 ConMon scan
**Date identified:** Month 3
**Target closure date:** Day 60 from identification
**Actual closure date:** Day 44 from identification
**Status:** CLOSED

**Finding:**
The Month 3 continuous monitoring vulnerability
scan identified that 4 Medium severity findings
from the Month 1 scan had not been patched
within the 60-day target. The patches existed
but had not been deployed due to a gap in the
patch management process for Medium findings.

**Risk if not remediated:**
Unpatched Medium vulnerabilities could be
exploited by an attacker to gain initial
access or escalate privileges within Bundle's
environment.

**Remediation actions taken:**

Step 1 — All 4 outstanding Medium patches
deployed within 5 days of finding being raised.

Step 2 — Patch management process reviewed
and updated to include automated deployment
for Medium findings within 45 days.

Step 3 — AWS Systems Manager Patch Manager
configured to automatically deploy Medium
patches to all EC2 instances.

Step 4 — Weekly patch compliance report
added to the ISSO dashboard.

**Evidence of closure:**
- Patch deployment confirmation from
  AWS Systems Manager
- Updated patch management procedure
- Systems Manager compliance dashboard
- ISSO sign-off

**Closed by:** Priya Nair, ISSE

---

### POA&M-008 — S3 Bucket Logging Gap

**Severity:** LOW
**Control:** AU-2 — Event Logging
**Identified by:** Month 5 ConMon review
**Date identified:** Month 5
**Target closure date:** Day 60 from identification
**Actual closure date:** Day 38 from identification
**Status:** CLOSED

**Finding:**
During the Month 5 ConMon review the ISSO
discovered that server access logging had
not been enabled on 2 of Bundle's S3 buckets.
All S3 buckets containing PHI or supporting
system operations must have server access
logging enabled so that all read and write
requests are captured in audit logs.

**Risk if not remediated:**
Any unauthorised access to data in those two
S3 buckets would not be captured in audit logs,
making forensic investigation of any incident
incomplete.

**Remediation actions taken:**

Step 1 — Server access logging enabled on
both affected S3 buckets within 24 hours.

Step 2 — AWS Config rule deployed to detect
any S3 bucket without logging enabled.

Step 3 — All S3 buckets audited to confirm
100% logging coverage.

Step 4 — S3 logging requirement added to
the new resource provisioning checklist.

**Evidence of closure:**
- S3 bucket logging configuration screenshots
- AWS Config rule showing 100% compliance
- Updated provisioning checklist
- ISSO sign-off

**Closed by:** James Okafor, ISSO

---

## Monthly POA&M Review Record

The POA&M is reviewed monthly and submitted
to the Authorizing Official quarterly.

| Month | Open at Start | Opened | Closed | Open at End | Submitted to AO |
|-------|-------------|--------|--------|------------|----------------|
| Month 1 | 6 | 0 | 2 | 4 | Quarterly |
| Month 2 | 4 | 0 | 2 | 2 | — |
| Month 3 | 2 | 1 | 1 | 2 | Quarterly |
| Month 4 | 2 | 0 | 2 | 0 | — |
| Month 5 | 0 | 1 | 0 | 1 | Quarterly |
| Month 6 | 1 | 0 | 1 | 0 | — |
| Month 7-12 | 0 | 0 | 0 | 0 | Quarterly |

---

## Key Lessons Learned

| Finding | Root Cause | Prevention Going Forward |
|---------|-----------|------------------------|
| IR training gap | No automated tracking of annual completion | LMS auto-reminder system deployed |
| Lambda config missing | New resources not added to baseline process | Config baseline checklist updated |
| Background checks gap | HR onboarding process not enforced | System access blocked until check cleared |
| Static API keys | No policy on credential rotation | Secrets Manager rotation mandatory |
| Patch compliance gap | Manual Medium patch process too slow | Automated patch deployment configured |
| S3 logging gap | New bucket provisioning checklist incomplete | Checklist updated and enforced |

---

## Navigation

[Back to Step 6 Overview](README.md)

[Back to Step 5 — Authorize](../05-authorize/README.md)

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

