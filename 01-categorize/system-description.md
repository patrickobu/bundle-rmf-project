# System Description

![System](https://img.shields.io/badge/System-Bundle%20EHMS-blue)
![Step](https://img.shields.io/badge/RMF%20Step-1%20Categorize-blue)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## System Overview

Bundle is a cloud-based Electronic Healthcare Management System
(EHMS) that serves as the central platform for all clinical and
administrative operations across a mid-sized hospital network.

It enables clinical staff to manage patient records, schedule
appointments, track medications, process insurance billing,
and communicate internally — all in a single integrated system.

---

## System Identification

| Field | Value |
|-------|-------|
| System Name | Bundle — Electronic Healthcare Management System |
| System Identifier | BUNDLE-EHMS-001 |
| System Abbreviation | Bundle EHMS |
| System Version | 3.2.2 |
| Operating Status | Operational |
| System Type | Major Application |
| Deployment Model | Cloud-hosted SaaS (AWS) |

---

## Organisational Context

| Field | Value |
|-------|-------|
| Organisation | Bundle Hospital Network |
| System Owner | Dr. Sarah Mitchell, Chief Medical Officer |
| ISSO | James Okafor, IT Security Manager |
| Primary Users | Clinical and administrative hospital staff |
| Number of Users | Approximately 500 |
| User Locations | Hospital main site + 2 satellite clinics |

---

## System Purpose and Mission

Bundle supports the hospital network's core clinical mission
by providing secure, reliable access to patient health
information at the point of care.

**Critical functions Bundle performs:**

Electronic Health Records (EHR) management — doctors and nurses
use Bundle to view and update patient records, diagnoses,
medication lists, and clinical notes during consultations and
ward rounds.

Patient scheduling — all outpatient appointments, procedure
bookings, and follow-up scheduling is managed through Bundle.
Without Bundle the hospital cannot book or track appointments.

Medication management — nursing staff use Bundle to record
medication administration and verify prescriptions. The system
integrates with the pharmacy to ensure accuracy.

Insurance billing — the billing team uses Bundle to submit
insurance claims and track reimbursements. The hospital's
revenue depends on this function.

Staff access management — Bundle controls which staff can
see which patient records, enforcing the principle that
staff only access records relevant to their clinical role.

---

## Technical Architecture

Bundle uses a three-tier web application architecture hosted
entirely on Amazon Web Services (AWS) in the US East region.

### Presentation Tier
Staff access Bundle through a web browser using HTTPS.
There is no desktop application to install. The web
interface is built with React and served over HTTPS
through an Application Load Balancer protected by AWS WAF.

### Application Tier
The Bundle application logic runs on Amazon EC2 instances
using Amazon Linux 2023. The application is built with
Node.js. EC2 instances run in a private subnet with no
direct internet access. All traffic flows through the
load balancer.

### Data Tier
Patient records and all operational data are stored in an
Amazon RDS PostgreSQL database. Documents and medical images
are stored in Amazon S3. Both the database and S3 are
encrypted at rest using AWS KMS with customer-managed keys.

---

## AWS Services Used

| AWS Service | Purpose | Location |
|-------------|---------|---------|
| EC2 (Amazon Linux 2023) | Application servers | Private subnet — no public IP |
| RDS PostgreSQL | Patient records database | Private database subnet |
| S3 | Document and image storage | Encrypted — SSE-KMS |
| Application Load Balancer | Traffic distribution | Public subnet |
| AWS WAF | Web application firewall | Public subnet — protects load balancer |
| AWS CloudWatch | Logging and monitoring | All regions |
| AWS CloudTrail | API audit trail | All regions |
| AWS KMS | Encryption key management | US East |
| AWS IAM | Access control and identity | All regions |
| AWS GuardDuty | Threat detection | US East |
| AWS Security Hub | Security posture management | US East |
| AWS Inspector | Vulnerability scanning | US East |
| AWS Backup | Automated backup | US East + US West (cross-region) |
| AWS Systems Manager | Patch management | US East |
| Amazon Cognito | User authentication and MFA | US East |

---

## Network Architecture

Bundle operates within a dedicated AWS Virtual Private Cloud (VPC).
The VPC is divided into subnets that enforce separation between
public-facing and private components.

**Public subnet** — contains only the Application Load Balancer
and AWS WAF. These receive traffic from the internet on port 443
(HTTPS). No application servers or databases are in this subnet.

**Private application subnet** — contains the EC2 application
servers. These cannot be reached directly from the internet.
They receive traffic only from the load balancer.

**Private database subnet** — contains the RDS PostgreSQL
database. This subnet accepts connections only from the
application servers. No direct internet access is possible.

Security groups act as virtual firewalls at every layer,
permitting only the specific traffic flows required.

---

## External Connections

Bundle integrates with three external systems to support
clinical workflows:

| System | Type | Direction | Data Exchanged | Protocol |
|--------|------|-----------|---------------|---------|
| Laboratory Information System | Third party | Inbound | Lab results | HL7 over TLS |
| Pharmacy Management System | Third party | Bidirectional | Prescriptions | API over TLS |
| Insurance Billing API | Third party | Outbound | Claims data | HTTPS/TLS |
| Hospital Active Directory | Internal | Inbound | Staff credentials | LDAPS |

All external connections use encrypted protocols.
Business Associate Agreements (BAAs) are in place for
all connections that involve PHI.

---

## User Population

| User Type | Count | Access Level | Authentication |
|-----------|-------|-------------|---------------|
| Doctors | 45 | Full EHR read and write | MFA via Cognito |
| Nurses | 120 | EHR read, medication write | MFA via Cognito |
| Administrative staff | 280 | Scheduling and admin only | MFA via Cognito |
| Billing staff | 40 | Financial records only | MFA via Cognito |
| IT administrators | 15 | Full system (separate account) | MFA + hardware token |
| **Total** | **500** | | |

---

## Operating Hours

Bundle is expected to be available 24 hours a day, 7 days a
week to support clinical staff on all shifts. Planned
maintenance windows are scheduled between 02:00 and 04:00
on Sunday mornings and communicated to all staff at least
72 hours in advance.

Target availability: 99.5% measured monthly
(allows approximately 3.6 hours of downtime per month)

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

