# Roles and Responsibilities

**System:** Bundle — Electronic Healthcare Management System
**Document:** RMF Role Assignments and RACI Matrix
**Step:** Step 0 — Prepare
**Version:** 1.0
**Prepared By:** James Okafor, ISSO
**Date:** 2025

---

## What This Document Covers

This document assigns every RMF role required by NIST SP 800-37 Rev. 2
to a named individual at Bundle's hospital network. It also includes a
RACI matrix showing who is Responsible, Accountable, Consulted, and
Informed for each major RMF activity.

Without clear role assignments, the entire RMF process lacks direction
and accountability. This is why the Prepare step exists.

---

## RMF Role Assignments

| Role | Person | Title | Key Responsibility |
|------|--------|-------|--------------------|
| Authorizing Official (AO) | Linda Reyes | Chief Information Officer | Reviews the complete security package and issues the formal ATO. Accepts residual risk on behalf of the organisation. |
| System Owner | Dr. Sarah Mitchell | Chief Medical Officer | Responsible for the overall mission, function, and operation of Bundle. Approves all major changes. |
| ISSO | James Okafor | IT Security Manager | Day-to-day responsibility for Bundle's security posture. Maintains SSP and POA&M. Reports to the AO. |
| ISSE | Priya Nair | Senior Cloud Security Engineer | Provides technical security guidance. Responsible for selecting, configuring, and validating technical controls on AWS. |
| Control Assessor | ClearPath Security LLC | External Assessment Organisation | Independently tests and evaluates whether Bundle's security controls are working correctly. Produces the SAR. |
| Privacy Officer | Marcus Webb | Chief Privacy Officer | Ensures Bundle complies with HIPAA privacy requirements. Oversees breach notification procedures. |
| Common Control Provider | AWS Security Team | Amazon Web Services | Provides inherited security controls — physical security, hypervisor isolation, hardware maintenance. |

> All names are fictional and used for portfolio simulation purposes only.

---

## RACI Matrix

R = Responsible | A = Accountable | C = Consulted | I = Informed

| RMF Activity | AO | System Owner | ISSO | ISSE | Assessor | Privacy Officer |
|-------------|----|-----------|----|------|----------|----------------|
| Step 0 — Prepare | A | C | R | C | I | C |
| Step 1 — Categorize | I | A | R | C | I | C |
| Step 2 — Select | I | A | R | C | C | C |
| Step 3 — Implement | I | A | C | R | I | I |
| Step 4 — Assess | A | I | C | C | R | C |
| Step 5 — Authorize | A | C | C | I | I | I |
| Step 6 — Monitor | I | A | R | C | I | C |
| Incident Response | A | C | R | C | I | C |
| POA&M Management | I | I | R | C | I | I |
| ATO Reauthorization | A | C | R | C | R | C |

---

## Role Descriptions in Plain English

### Authorizing Official (AO) — Linda Reyes
The AO is the most senior decision maker in the RMF process. She reads
the complete security package at the end of Step 4 and decides whether
Bundle is safe enough to go live. When she signs the ATO letter she is
personally accepting responsibility for any residual risk. She also
receives monthly POA&M reports and quarterly posture summaries.

### System Owner — Dr. Sarah Mitchell
The System Owner owns Bundle from a business perspective. She decides
what Bundle does, who uses it, and what changes are made to it. She does
not manage the technical security details but she signs off on major
decisions and ensures the clinical team cooperates with security
requirements.

### ISSO — James Okafor
The ISSO is the day-to-day security manager for Bundle. He writes and
maintains the SSP, manages the POA&M, coordinates the assessment, runs
weekly log reviews, and reports to the AO. He is the first point of
contact for any security incident.

### ISSE — Priya Nair
The ISSE is the technical security expert. She designs and implements the
technical controls on AWS — the VPC architecture, IAM policies,
encryption configuration, GuardDuty setup, and patching process. She
works closely with the ISSO.

### Control Assessor — ClearPath Security LLC
An independent external organisation hired to test Bundle's security
controls. They cannot have been involved in designing or implementing
the controls. Their independence is required for HIGH impact systems.
They produce the Security Assessment Report (SAR).

### Privacy Officer — Marcus Webb
Responsible for HIPAA compliance. He reviews how Bundle handles patient
PHI, manages patient privacy rights, and leads the breach notification
process if a data breach occurs.

---

## Contact Directory

| Role | Person | Email | Phone |
|------|--------|-------|-------|
| AO | Linda Reyes | l.reyes@bundle-ehms.internal | Ext. 1001 |
| System Owner | Dr. Sarah Mitchell | s.mitchell@bundle-ehms.internal | Ext. 1002 |
| ISSO | James Okafor | j.okafor@bundle-ehms.internal | Ext. 1003 |
| ISSE | Priya Nair | p.nair@bundle-ehms.internal | Ext. 1004 |
| Privacy Officer | Marcus Webb | m.webb@bundle-ehms.internal | Ext. 1005 |
| Assessor | ClearPath Security LLC | assess@clearpathsec.example | 555-0199 |

> All contact details are fictional and used for simulation purposes only.

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 | James Okafor | Initial document created |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

