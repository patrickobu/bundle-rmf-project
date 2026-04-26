# Inherited Controls

![System](https://img.shields.io/badge/System-Bundle%20EHMS-blue)
![Step](https://img.shields.io/badge/RMF%20Step-2%20Select-blue)
![Provider](https://img.shields.io/badge/Provider-AWS-orange)
![Inherited](https://img.shields.io/badge/Controls%20Inherited-26-brightgreen)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## What Are Inherited Controls?

Inherited controls are security controls that are
implemented and managed by another organisation on
behalf of Bundle. Bundle does not need to implement
these controls itself but must retain evidence that
the provider has implemented them correctly.

For Bundle, the inherited control provider is
**Amazon Web Services (AWS)**. Because Bundle runs
entirely on AWS infrastructure, AWS is responsible
for a significant number of physical and environmental
controls under the AWS Shared Responsibility Model.

---

## The AWS Shared Responsibility Model

AWS and Bundle share responsibility for security
but in clearly defined areas.

| Responsibility | AWS Manages | Bundle Manages |
|---------------|------------|---------------|
| Physical data centres | YES | NO |
| Hardware and servers | YES | NO |
| Hypervisor and virtualisation | YES | NO |
| Network infrastructure | YES | NO |
| Operating system on EC2 | NO | YES |
| Application code | NO | YES |
| Data encryption | PARTIAL | PARTIAL |
| Identity and access | PARTIAL | PARTIAL |
| Network configuration (VPC) | NO | YES |
| Security group rules | NO | YES |

---

## Evidence of AWS Compliance

Bundle retains the following AWS compliance documents
as evidence that inherited controls are implemented.
These are stored in the evidence/aws-compliance/ folder.

| Document | What it proves | Obtained from |
|----------|---------------|--------------|
| AWS SOC 2 Type II Report | AWS security controls independently audited | AWS Artifact portal |
| AWS ISO 27001 Certificate | International security management standard | AWS Artifact portal |
| AWS FedRAMP High Authorization | US government security authorization | marketplace.fedramp.gov |
| AWS HIPAA Business Associate Agreement | HIPAA compliance and PHI handling | AWS console |
| AWS Shared Responsibility Model | Defines exactly what AWS vs Bundle owns | aws.amazon.com |

---

## Full List of Inherited Controls

### PE — Physical and Environmental Protection
All 20 PE controls are fully inherited from AWS.

| Control | Title | Why Inherited |
|---------|-------|--------------|
| PE-1 | Physical and Environmental Protection Policy | AWS manages all physical facilities |
| PE-2 | Physical Access Authorizations | AWS controls who enters its data centres |
| PE-3 | Physical Access Control | Badge readers, security guards at AWS facilities |
| PE-4 | Access Control for Transmission | AWS manages physical network cabling |
| PE-5 | Access Control for Output Devices | AWS manages physical output devices |
| PE-6 | Monitoring Physical Access | CCTV and access logging at AWS data centres |
| PE-7 | Visitor Access Records | AWS logs all visitor access |
| PE-8 | Visitor Access Records | AWS retains visitor logs |
| PE-9 | Power Equipment and Cabling | AWS manages all power infrastructure |
| PE-10 | Emergency Shutoff | AWS manages emergency power systems |
| PE-11 | Emergency Power | AWS provides UPS and backup generators |
| PE-12 | Emergency Lighting | AWS data centres have emergency lighting |
| PE-13 | Fire Protection | AWS data centres have fire suppression systems |
| PE-14 | Environmental Controls | AWS manages temperature and humidity |
| PE-15 | Water Damage Protection | AWS protects against water damage |
| PE-16 | Delivery and Removal | AWS manages hardware delivery and disposal |
| PE-17 | Alternate Work Site | AWS supports remote access capabilities |
| PE-18 | Location of System Components | AWS chooses secure facility locations |
| PE-19 | Information Leakage | AWS controls electromagnetic interference |
| PE-20 | Asset Monitoring and Tracking | AWS tracks all physical hardware assets |

**Evidence:** AWS SOC 2 Type II Report covers all PE
controls. AWS FedRAMP High authorization package
documents physical security in detail.

---

### MA — Maintenance (Partially Inherited)

| Control | Title | Status | Notes |
|---------|-------|--------|-------|
| MA-4 | Nonlocal Maintenance | Inherited | AWS manages remote maintenance of physical hardware |
| MA-6 | Timely Maintenance | Inherited | AWS hardware maintenance SLAs documented in SOC 2 |

**Evidence:** AWS SOC 2 Type II Report, Section on
Hardware Maintenance.

---

### MP — Media Protection (Partially Inherited)

| Control | Title | Status | Notes |
|---------|-------|--------|-------|
| MP-6 | Media Sanitization | Inherited | AWS manages secure disposal of physical storage media |
| MP-7 | Media Use | Inherited | AWS controls physical media within data centres |
| MP-8 | Media Downgrading | Inherited | AWS manages media declassification processes |

**Evidence:** AWS SOC 2 Type II Report, Section on
Media Handling. AWS data destruction certification.

---

### SC — System and Communications (Partially Inherited)

| Control | Title | Status | Notes |
|---------|-------|--------|-------|
| SC-39 | Process Isolation | Inherited | AWS hypervisor provides isolation between tenants |

**Evidence:** AWS FedRAMP High authorization package
documents hypervisor isolation. AWS SOC 2 covers
virtualisation security.

---

### AU — Audit and Accountability (Partially Inherited)

| Control | Title | Status | Notes |
|---------|-------|--------|-------|
| AU-3(2) | Centralised Management | Inherited | AWS CloudTrail centralised across all regions |
| AU-6(7) | Permitted Actions | Inherited | AWS IAM enforces permitted audit actions |

**Evidence:** AWS CloudTrail documentation. AWS
Config compliance evidence.

---

## Inherited Controls Summary Count

| Control Family | Total Inherited | Type |
|---------------|----------------|------|
| PE — Physical and Environmental | 20 | Fully inherited |
| MA — Maintenance | 2 | Partially inherited |
| MP — Media Protection | 3 | Partially inherited |
| SC — System Communications | 1 | Partially inherited |
| AU — Audit | 0 | Not inherited — Bundle manages |
| **Total** | **26** | |

---

## How Inherited Controls Are Verified

Bundle cannot test AWS controls directly. Instead
verification is done through:

**Step 1 — Obtain current AWS compliance documents**
The ISSO downloads the latest AWS SOC 2 Type II
report and ISO 27001 certificate from the AWS
Artifact portal at the start of each assessment
cycle.

**Step 2 — Review the relevant control sections**
The ISSE reviews the sections of the SOC 2 report
that correspond to the inherited controls and
confirms the controls are covered.

**Step 3 — Retain the evidence**
All documents are stored in evidence/aws-compliance/
with the date they were obtained. This demonstrates
that Bundle actively monitors AWS compliance rather
than relying on outdated documents.

**Step 4 — Annual review**
The ISSO reviews and refreshes all inherited control
evidence annually as part of the continuous
monitoring programme.

---

## Important Note on Inherited Controls

Inheriting controls from AWS does not mean Bundle
has no responsibility for those areas. Bundle is
still responsible for:

- Correctly configuring the AWS services it uses
- Ensuring its VPC, security groups, and IAM
  policies are set up securely
- Monitoring its own usage of AWS services
- Reporting any AWS service incidents that affect
  Bundle to the AO

The Shared Responsibility Model means both parties
have obligations — AWS for the infrastructure,
Bundle for everything it builds on top of it.

---

## Navigation

[Back to Step 2 Overview](README.md)

[Go to Tailoring Decisions](tailoring-decisions.md)

[Go to Step 3 — Implement](../03-implement/README.md)

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

