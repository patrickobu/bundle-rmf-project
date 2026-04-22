# Hardware and Software Inventory

![System](https://img.shields.io/badge/System-Bundle%20EHMS-blue)
![Step](https://img.shields.io/badge/RMF%20Step-1%20Categorize-blue)
![Last Updated](https://img.shields.io/badge/Last%20Updated-2025-orange)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## Purpose

This document provides a complete inventory of all hardware
and software components within the Bundle EHMS authorization
boundary. Maintaining an accurate inventory is required by
NIST SP 800-53 CM-8 and HIPAA 45 CFR 164.310(d)(1).

An up-to-date inventory is essential for vulnerability
management — you cannot patch what you do not know you have.

---

## AWS Infrastructure Components (Hardware)

These components run on AWS GovCloud physical infrastructure.
The physical hardware is managed by AWS under the Shared
Responsibility Model. Bundle is responsible for what runs
on this infrastructure.

| Component ID | Resource Type | Configuration | Purpose | Subnet |
|-------------|--------------|--------------|---------|-------|
| EC2-APP-001 | EC2 Instance | t3.large, 2 vCPU, 8GB RAM | Application server — primary | Private App |
| EC2-APP-002 | EC2 Instance | t3.large, 2 vCPU, 8GB RAM | Application server — secondary | Private App |
| EC2-API-001 | EC2 Instance | t3.medium, 2 vCPU, 4GB RAM | API server — primary | Private App |
| EC2-API-002 | EC2 Instance | t3.medium, 2 vCPU, 4GB RAM | API server — secondary | Private App |
| RDS-DB-001 | RDS PostgreSQL | db.r6g.large, Multi-AZ | Primary database | Private DB |
| RDS-DB-002 | RDS PostgreSQL | db.r6g.large, standby | Standby database (automatic failover) | Private DB |
| ALB-001 | Application Load Balancer | HTTPS only | Traffic distribution | Public |
| WAF-001 | AWS WAF | Managed rule groups | Web application firewall | Public |
| S3-DOCS-001 | S3 Bucket | Versioning enabled, SSE-KMS | Document and image storage | N/A |
| S3-BACKUP-001 | S3 Bucket | Object Lock enabled | Audit log archive | N/A |
| S3-DR-001 | S3 Bucket | Cross-region replica | Disaster recovery backup | US West |

---

## Operating System Inventory

| Component | OS | Version | Patch Level | Notes |
|-----------|----|---------|-----------|----|
| EC2-APP-001 | Amazon Linux | 2023.3 | Current | CIS Level 2 hardened |
| EC2-APP-002 | Amazon Linux | 2023.3 | Current | CIS Level 2 hardened |
| EC2-API-001 | Amazon Linux | 2023.3 | Current | CIS Level 2 hardened |
| EC2-API-002 | Amazon Linux | 2023.3 | Current | CIS Level 2 hardened |

All EC2 instances are patched monthly using AWS Systems Manager
Patch Manager. All instances must be at current patch level
within 30 days of release for High and Critical patches.

---

## Application Software Inventory

| Software | Version | Vendor | Purpose | Licence |
|----------|---------|--------|---------|--------|
| Bundle EHMS Application | 3.2.2 | GovCloud Solutions (fictional) | Core EHR application | Proprietary |
| Node.js | 20.11.0 LTS | OpenJS Foundation | Application runtime | MIT |
| Express.js | 4.18.2 | OpenJS Foundation | Web framework | MIT |
| React | 18.2.0 | Meta | Front-end framework | MIT |
| PostgreSQL Client | 16.1 | PostgreSQL Global Dev Group | Database client | PostgreSQL |
| AWS SDK for JavaScript | 3.x | Amazon | AWS service integration | Apache 2.0 |
| Passport.js | 0.6.0 | Jared Hanson | Authentication middleware | MIT |
| Helmet.js | 7.1.0 | Evan Hahn | HTTP security headers | MIT |
| Winston | 3.11.0 | Charlie Robbins | Application logging | MIT |
| Jest | 29.7.0 | Meta | Automated testing | MIT |
| CrowdStrike Falcon Sensor | 7.x | CrowdStrike | Endpoint detection and response | Commercial |

---

## AWS Service Inventory

| Service | Version / Config | Purpose |
|---------|-----------------|---------|
| AWS IAM | N/A | Identity and access management |
| Amazon Cognito | N/A | User authentication and MFA |
| AWS KMS | FIPS 140-2 Level 3 | Encryption key management |
| AWS CloudWatch | N/A | Log aggregation and monitoring |
| AWS CloudTrail | N/A | API audit trail |
| AWS GuardDuty | N/A | Threat detection |
| AWS Security Hub | N/A | Security posture management |
| AWS Inspector v2 | N/A | Vulnerability scanning |
| AWS Config | N/A | Configuration compliance monitoring |
| AWS Systems Manager | N/A | Patch management and configuration |
| AWS Backup | N/A | Automated backup |
| AWS Shield Standard | N/A | DDoS protection |

---

## Third-Party Software and Libraries

| Library | Version | Purpose | Vulnerability Status |
|---------|---------|---------|---------------------|
| OpenSSL | 3.2.0 | TLS cryptography | Current — no known CVEs |
| libcurl | 8.5.0 | HTTP client | Current — no known CVEs |
| zlib | 1.3.1 | Compression | Current — no known CVEs |
| libpng | 1.6.40 | Image handling | Current — no known CVEs |
| Lodash | 4.17.21 | JavaScript utilities | Current — patched against prototype pollution |
| Axios | 1.6.2 | HTTP client | Current — no known CVEs |
| bcrypt | 5.1.1 | Password hashing | Current — no known CVEs |
| jsonwebtoken | 9.0.2 | JWT handling | Current — no known CVEs |
| multer | 1.4.5 | File upload handling | Current — no known CVEs |

---

## Inventory Management Process

This inventory is maintained by the ISSE (Priya Nair) and is
updated in the following circumstances:

- When any new component is added to the environment
- When any component is upgraded or patched
- When any component is decommissioned and removed
- Reviewed and verified as complete monthly during the
  continuous monitoring review cycle

AWS Systems Manager Inventory is used to automatically collect
software version information from all EC2 instances and feed
it into this record.

---

## Document Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025 | Priya Nair, ISSE | Initial inventory completed |

---

*This document is part of the Bundle RMF portfolio project.
All names, data, and scenarios are fictional and used for
learning and career development purposes only.*

