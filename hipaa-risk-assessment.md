# HIPAA Security Risk Assessment
## Bright Smile Family Dentistry — Mock Organization
**Assessment Date:** May 2026
**Prepared By:** Melissa Gaither, CompTIA Security+
**Document Version:** 1.0
**Classification:** Confidential

---

## Table of Contents
1. [Executive Summary](#1-executive-summary)
2. [Organization Overview](#2-organization-overview)
3. [Scope and Methodology](#3-scope-and-methodology)
4. [Regulatory Framework](#4-regulatory-framework)
5. [Asset Inventory](#5-asset-inventory)
6. [Threat and Vulnerability Identification](#6-threat-and-vulnerability-identification)
7. [Risk Register](#7-risk-register)
8. [Current Controls Assessment](#8-current-controls-assessment)
9. [Gaps and Recommendations](#9-gaps-and-recommendations)
10. [Remediation Roadmap](#10-remediation-roadmap)
11. [Conclusion](#11-conclusion)

---

## 1. Executive Summary

This Security Risk Assessment was conducted for **Bright Smile Family Dentistry**, a fictional five-provider dental practice located in Columbus, Ohio. The purpose of this assessment is to identify risks to the confidentiality, integrity, and availability of electronic Protected Health Information (ePHI) in accordance with the HIPAA Security Rule (45 CFR §§ 164.302–318).

### Key Findings

| Risk Level | Count |
|------------|-------|
| Critical | 2 |
| High | 4 |
| Medium | 5 |
| Low | 3 |
| **Total Risks Identified** | **14** |

### Summary of Critical Issues
- **No formal encryption policy** for ePHI stored on workstations and portable devices
- **No documented incident response plan** for data breaches or ransomware events

Immediate remediation is recommended for all Critical and High findings. A full remediation roadmap is provided in Section 10.

---

## 2. Organization Overview

| Field | Detail |
|-------|--------|
| Organization Name | Bright Smile Family Dentistry (Mock) |
| Location | Columbus, Ohio |
| Practice Size | 5 Dentists, 12 Staff Members |
| Patient Volume | ~2,400 active patients |
| EHR System | Dentrix (cloud-assisted) |
| Practice Management | Eaglesoft |
| Billing | In-house + third-party clearinghouse |
| IT Support | Managed Service Provider (MSP) — outsourced |

Bright Smile handles ePHI across multiple systems including digital X-rays, scheduling software, billing platforms, and patient communication tools. As a covered entity under HIPAA, the practice is required to implement appropriate administrative, physical, and technical safeguards.

---

## 3. Scope and Methodology

### Scope
This assessment covers all systems, processes, and personnel that create, receive, maintain, or transmit ePHI, including:
- Clinical workstations and imaging systems
- Practice management and EHR software
- Email and patient communication platforms
- Physical office locations
- Business Associate relationships

### Methodology
This risk assessment follows guidance from:
- **NIST SP 800-30** — Guide for Conducting Risk Assessments
- **HHS Office for Civil Rights (OCR)** — HIPAA Security Risk Assessment Tool guidance
- **45 CFR Part 164** — HIPAA Security Rule

Risk scoring uses a **Likelihood × Impact** matrix:

| Score | Likelihood | Impact |
|-------|-----------|--------|
| 1 | Rare | Negligible |
| 2 | Unlikely | Minor |
| 3 | Possible | Moderate |
| 4 | Likely | Major |
| 5 | Almost Certain | Catastrophic |

**Risk Score = Likelihood × Impact**

| Score Range | Risk Level |
|-------------|------------|
| 1–4 | Low |
| 5–9 | Medium |
| 10–14 | High |
| 15–25 | Critical |

---

## 4. Regulatory Framework

This assessment is grounded in the HIPAA Security Rule, which requires covered entities to:

### Administrative Safeguards (§164.308)
- Conduct a risk analysis and implement a risk management plan
- Designate a Security Officer
- Implement workforce training and access management procedures
- Establish contingency and incident response plans

### Physical Safeguards (§164.310)
- Control facility access
- Implement workstation use policies
- Manage device and media controls (including disposal)

### Technical Safeguards (§164.312)
- Implement access controls (unique user IDs, automatic logoff)
- Implement audit controls and logging
- Ensure ePHI integrity controls
- Encrypt ePHI in transmission

### Breach Notification Rule (§164.400–414)
- Notify affected individuals within 60 days of discovery
- Notify HHS; notify media if breach affects 500+ individuals in a state

---

## 5. Asset Inventory

### ePHI-Containing Systems

| Asset ID | Asset Type | Location | ePHI Present | Owner |
|----------|-----------|----------|--------------|-------|
| A-001 | Dentrix EHR Server | Server Room | Yes | IT MSP |
| A-002 | Clinical Workstations (x8) | Operatories | Yes | Office Manager |
| A-003 | Digital X-Ray System | Operatories | Yes | Lead Dentist |
| A-004 | Front Desk Workstations (x3) | Reception | Yes | Office Manager |
| A-005 | Practice Management (Eaglesoft) | Cloud | Yes | IT MSP |
| A-006 | Billing Platform | Cloud | Yes | Billing Manager |
| A-007 | Staff Laptops (x4) | Various/Remote | Yes | Individual Staff |
| A-008 | Secure Email System | Cloud | Yes | IT MSP |
| A-009 | Patient Portal | Cloud | Yes | IT MSP |
| A-010 | Backup System (external drives) | Office/Offsite | Yes | Office Manager |

### Business Associates (BAs)

| BA Name | Service Provided | BAA in Place? |
|---------|-----------------|---------------|
| DentalXChange | Insurance clearinghouse | Yes |
| Weave | Patient communication/texting | Yes |
| Carestream | Digital imaging software | Yes |
| Shred-It | Physical document destruction | Yes |
| MSP Partner | IT management and support | **No — Gap Identified** |

---

## 6. Threat and Vulnerability Identification

### Threats Identified

| Threat ID | Threat Type | Category | Source |
|-----------|------------|---------|--------|
| T-001 | Ransomware attack | Cyber | External |
| T-002 | Phishing email leading to credential theft | Cyber | External |
| T-003 | Unauthorized access by terminated employee | Insider | Internal |
| T-004 | Lost or stolen laptop with unencrypted ePHI | Physical | Internal/External |
| T-005 | Accidental disclosure via unsecured email | Human Error | Internal |
| T-006 | Vendor/BA data breach | Third Party | External |
| T-007 | Natural disaster (flood, fire) causing data loss | Environmental | External |
| T-008 | Workstation left unattended with ePHI visible | Physical | Internal |
| T-009 | Outdated software with unpatched vulnerabilities | Technical | Internal |
| T-010 | Disposal of hard drives without proper sanitization | Physical | Internal |

### Vulnerabilities Identified

| Vuln ID | Description | Affected Asset(s) |
|---------|------------|------------------|
| V-001 | No whole-disk encryption on staff laptops | A-007 |
| V-002 | Shared login credentials among front desk staff | A-004 |
| V-003 | No automatic screen lock policy enforced | A-002, A-004 |
| V-004 | No formal security awareness training program | All staff |
| V-005 | Missing BAA with IT MSP | A-001, A-002, A-007 |
| V-006 | Backup drives stored in unlocked cabinet | A-010 |
| V-007 | No documented incident response plan | Organization-wide |
| V-008 | Software patches applied inconsistently | A-002, A-004 |
| V-009 | No process for revoking access upon termination | All systems |
| V-010 | Email platform not configured to block PHI transmission | A-008 |

---

## 7. Risk Register

| Risk ID | Threat | Vulnerability | Likelihood (1-5) | Impact (1-5) | Risk Score | Risk Level |
|---------|--------|--------------|-----------------|--------------|------------|------------|
| R-001 | Ransomware (T-001) | Unpatched software (V-008) | 4 | 5 | **20** | 🔴 Critical |
| R-002 | Lost/stolen laptop (T-004) | No encryption (V-001) | 4 | 5 | **20** | 🔴 Critical |
| R-003 | Credential theft (T-002) | Shared logins (V-002) | 4 | 4 | **16** | 🔴 Critical |
| R-004 | Terminated employee access (T-003) | No offboarding process (V-009) | 3 | 4 | **12** | 🟠 High |
| R-005 | PHI emailed insecurely (T-005) | Email not configured (V-010) | 4 | 3 | **12** | 🟠 High |
| R-006 | No incident response (T-001, T-002) | No IRP (V-007) | 3 | 4 | **12** | 🟠 High |
| R-007 | BA breach (T-006) | Missing BAA with MSP (V-005) | 3 | 4 | **12** | 🟠 High |
| R-008 | Workstation left unlocked (T-008) | No screen lock (V-003) | 4 | 3 | **12** | 🟠 High |
| R-009 | Staff phishing susceptibility (T-002) | No training program (V-004) | 3 | 3 | **9** | 🟡 Medium |
| R-010 | Backup theft (T-004) | Unlocked storage (V-006) | 2 | 4 | **8** | 🟡 Medium |
| R-011 | Improper device disposal (T-010) | No sanitization policy | 2 | 4 | **8** | 🟡 Medium |
| R-012 | Natural disaster data loss (T-007) | No offsite backup test | 2 | 4 | **8** | 🟡 Medium |
| R-013 | Vendor software breach (T-006) | No vendor review process | 2 | 3 | **6** | 🟡 Medium |
| R-014 | Unauthorized physical access (T-008) | No visitor log in server room | 1 | 4 | **4** | 🟢 Low |

---

## 8. Current Controls Assessment

### Administrative Controls

| Control | Required By | Status | Notes |
|--------|------------|--------|-------|
| Designated Security Officer | §164.308(a)(2) | ✅ In Place | Office Manager assigned |
| Risk Analysis conducted | §164.308(a)(1) | ⚠️ Partial | Last conducted 3+ years ago |
| Workforce training program | §164.308(a)(5) | ❌ Gap | No formal annual training |
| Access management policy | §164.308(a)(4) | ⚠️ Partial | No offboarding checklist |
| Business Associate Agreements | §164.308(b)(1) | ⚠️ Partial | MSP BAA missing |
| Incident Response Plan | §164.308(a)(6) | ❌ Gap | Not documented |
| Contingency / Disaster Recovery Plan | §164.308(a)(7) | ⚠️ Partial | Backup exists; no tested plan |

### Physical Controls

| Control | Required By | Status | Notes |
|--------|------------|--------|-------|
| Facility access controls | §164.310(a)(1) | ✅ In Place | Keypad entry at main door |
| Workstation use policy | §164.310(b) | ❌ Gap | No documented policy |
| Device and media controls | §164.310(d)(1) | ❌ Gap | No sanitization procedure |
| Workstation screen lock | §164.310(b) | ❌ Gap | Not enforced via policy |

### Technical Controls

| Control | Required By | Status | Notes |
|--------|------------|--------|-------|
| Unique user IDs | §164.312(a)(2)(i) | ❌ Gap | Front desk shares logins |
| Automatic logoff | §164.312(a)(2)(iii) | ❌ Gap | Not configured |
| Encryption — laptops | §164.312(a)(2)(iv) | ❌ Gap | Laptops unencrypted |
| Encryption — transmission | §164.312(e)(2)(ii) | ✅ In Place | EHR uses TLS |
| Audit logs / access tracking | §164.312(b) | ⚠️ Partial | EHR logs; email not logged |
| Patch management | §164.312(a)(2)(ii) | ⚠️ Partial | Inconsistent schedule |

---

## 9. Gaps and Recommendations

### Critical Gaps

**GAP-001: No encryption on staff laptops (R-002)**
> Staff laptops containing ePHI are unencrypted. A lost or stolen device would constitute a reportable HIPAA breach affecting potentially hundreds of patients.

*Recommendation:* Enable BitLocker (Windows) or FileVault (Mac) on all staff laptops immediately. Verify encryption status quarterly. Document encryption in asset inventory.

---

**GAP-002: No Incident Response Plan (R-006)**
> The practice has no documented procedure for responding to a ransomware attack, phishing incident, or data breach. HHS OCR expects documented and tested response procedures.

*Recommendation:* Develop a written Incident Response Plan (IRP) covering: identification, containment, eradication, recovery, and notification procedures. Train all staff annually. Test the plan via tabletop exercise.

---

### High Priority Gaps

**GAP-003: Shared login credentials (R-003)**
> Front desk staff share a single login for the practice management system, making audit trails unreliable and enabling unauthorized access post-termination.

*Recommendation:* Create individual user accounts for every staff member. Enforce unique credentials and role-based access controls (RBAC). Complete within 30 days.

---

**GAP-004: Missing BAA with IT MSP (R-007)**
> The managed service provider has access to systems containing ePHI but no Business Associate Agreement is in place, creating direct HIPAA liability for the practice.

*Recommendation:* Execute a BAA with the MSP immediately. Add BAA review to annual vendor management checklist.

---

**GAP-005: No workforce security training (R-009)**
> Staff have received no formal HIPAA security awareness training. Phishing is the leading cause of healthcare data breaches nationally.

*Recommendation:* Implement annual security awareness training covering phishing recognition, password hygiene, device security, and breach reporting. Document completion records.

---

**GAP-006: No employee offboarding process (R-004)**
> No checklist exists for revoking system access when employees are terminated or resign.

*Recommendation:* Create a formal offboarding checklist that includes immediate revocation of all system credentials. Assign HR and the Security Officer joint accountability.

---

## 10. Remediation Roadmap

### Phase 1 — Immediate (0–30 Days)

| Action Item | Owner | Priority | HIPAA Reference |
|-------------|-------|----------|----------------|
| Enable full-disk encryption on all laptops | IT MSP | 🔴 Critical | §164.312(a)(2)(iv) |
| Execute BAA with IT MSP | Office Manager | 🔴 Critical | §164.308(b)(1) |
| Create individual user accounts (end shared logins) | IT MSP | 🔴 Critical | §164.312(a)(2)(i) |
| Configure automatic screen lock (5-min timeout) | IT MSP | 🟠 High | §164.312(a)(2)(iii) |
| Create employee termination/offboarding checklist | Office Manager | 🟠 High | §164.308(a)(3) |

### Phase 2 — Short-Term (30–90 Days)

| Action Item | Owner | Priority | HIPAA Reference |
| ------------|-------|----------|----------------|
| Develop and document Incident Response Plan | Security Officer | 🟠 High | §164.308(a)(6) |
| Implement security awareness training program | Security Officer | 🟠 High | §164.308(a)(5) |
| Configure email system to flag outbound PHI | IT MSP | 🟠 High | §164.312(e) |
| Secure backup drive storage (locked cabinet/offsite) | Office Manager | 🟡 Medium | §164.310(d) |
| Establish patch management schedule | IT MSP | 🟡 Medium | §164.312(a)(2)(ii) |

### Phase 3 — Ongoing (90+ Days)

| Action Item | Owner | Frequency |
|-------------|-------|-----------|
| Repeat Security Risk Assessment | Security Officer | Annual |
| Security awareness training refresh | All Staff | Annual |
| BAA review for all vendors | Office Manager | Annual |
| Tabletop incident response exercise | Security Officer | Annual |
| Review and update asset inventory | IT MSP + Office Manager | Semi-Annual |
| Audit user access levels | Security Officer | Quarterly |
| Verify encryption status on all devices | IT MSP | Quarterly |

---

## 11. Conclusion

This risk assessment identified **14 risks** across administrative, physical, and technical safeguard domains, including **3 Critical** and **4 High** priority findings requiring immediate action.

The most significant vulnerabilities facing Bright Smile Family Dentistry are the lack of device encryption, absence of an incident response plan, shared login credentials, and a missing Business Associate Agreement with the primary IT vendor. Each of these represents direct regulatory exposure under the HIPAA Security Rule and could result in significant financial penalties and reputational harm in the event of a breach.

The remediation roadmap in Section 10 provides a structured, prioritized path to full compliance. With consistent implementation, the organization can significantly reduce its risk exposure within 90 days.

> **Note:** This is a mock risk assessment created as a cybersecurity portfolio project. Bright Smile Family Dentistry is a fictional organization. All findings and recommendations are based on real HIPAA Security Rule requirements and standard GRC methodology.

---

## References

- U.S. Department of Health & Human Services. (2022). *HIPAA Security Rule Guidance*. https://www.hhs.gov/hipaa/for-professionals/security/index.html
- National Institute of Standards and Technology. (2012). *NIST SP 800-30: Guide for Conducting Risk Assessments*. https://csrc.nist.gov/publications/detail/sp/800-30/rev-1/final
- HHS Office for Civil Rights. *Security Risk Assessment Tool*. https://www.healthit.gov/topic/privacy-security-and-hipaa/security-risk-assessment-tool
- CompTIA Security+ Study Guide, Exam SY0-701

---

*Prepared by: Melissa Gaither | CompTIA Security+ | GitHub: CyberMomma-3*
*This document is part of a cybersecurity career transition portfolio.*
