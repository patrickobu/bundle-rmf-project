# Risk Management Strategy

**System:** Bundle — Electronic Healthcare Management System
**Document:** Organisational Risk Management Strategy
**Step:** Step 0 — Prepare
**Version:** 1.0
**Prepared By:** James Okafor, ISSO
**Approved By:** Linda Reyes, Authorizing Official
**Date:** 2025

---

## Purpose

This document defines how Bundle's organisation identifies, evaluates,
prioritises, and responds to security and privacy risks. It applies
throughout the entire RMF lifecycle and is reviewed annually or whenever
significant changes occur to the system or its operating environment.

---

## Risk Tolerance Statement

Bundle's organisation operates in a highly regulated healthcare
environment where the consequences of a security failure can be
life-threatening and legally catastrophic.

| Risk Level | Tolerance | Response Required |
|-----------|-----------|-------------------|
| HIGH | Not accepted without immediate compensating controls | Report to AO immediately. Remediate within 30 days. |
| MODERATE | Accepted temporarily with a documented plan | Enter into POA&M. Remediate within 90 days. |
| LOW | Accepted and tracked | Enter into POA&M. Review quarterly. |

> Bundle will never accept a HIGH risk to patient PHI without a
> compensating control and a written remediation plan approved by the AO.

---

## Risk Assessment Approach

Bundle uses a qualitative risk assessment approach based on two factors:

**Likelihood** — How probable is this risk occurring?
**Impact** — How serious would the consequences be?

### Likelihood Ratings

| Rating | Definition |
|--------|-----------|
| High | A known vulnerability exists, or similar incidents have occurred recently in healthcare |
| Moderate | A vulnerability exists but exploitation requires significant effort |
| Low | Exploitation would require highly specialised skills or insider access |

### Impact Ratings

| Rating | Definition |
|--------|-----------|
| High | Breach of PHI, system-wide outage, patient safety risk, or major regulatory penalties |
| Moderate | Limited PHI exposure, partial disruption, or moderate regulatory findings |
| Low | Minimal data exposure, brief interruption, no patient safety implications |

### Risk Rating Matrix

| | High Impact | Moderate Impact | Low Impact |
|-|------------|----------------|-----------|
| **High Likelihood** | HIGH | HIGH | MODERATE |
| **Moderate Likelihood** | HIGH | MODERATE | LOW |
| **Low Likelihood** | MODERATE | LOW | LOW |

---

## Risk Response Options

When a risk is identified the team selects one of these responses:

**Mitigate** — Implement a security control to reduce the risk.
This is the preferred response for HIGH and MODERATE risks.

**Accept** — Formally acknowledge the risk and choose not to act.
Only for LOW risks where remediation cost outweighs the impact.
Must be documented and approved by the AO.

**Transfer** — Shift responsibility to a third party such as through
cyber insurance or a vendor contractual arrangement.

**Avoid** — Change the system design to eliminate the risk entirely.
Used when a feature introduces unacceptable risk.

---

## Risk Review Cadence

| Activity | Frequency | Description |
|----------|-----------|-------------|
| Full Risk Assessment | Annually | Comprehensive review of all identified risks |
| POA&M Review | Monthly | ISSO reviews all open findings and updates status |
| Triggered Review | As needed | Following a security incident or significant system change |
| Continuous Monitoring | Ongoing | Automated scanning, log review, and anomaly detection |

---

## Applicable Regulations

The following laws and standards apply to Bundle and shape all risk
management decisions:

| Regulation | Relevance |
|-----------|-----------|
| HIPAA Security Rule | Requires specific safeguards for electronic PHI |
| HITECH Act | Strengthens HIPAA enforcement and increases penalties |
| NIST SP 800-37 Rev. 2 | The RMF process this project follows |
| NIST SP 800-53 Rev. 5 | The security control catalogue |
| FIPS 199 | System categorisation standard |
| AWS Shared Responsibility Model | Defines AWS vs Bundle team responsibilities |

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 | James Okafor | Initial strategy document created |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

