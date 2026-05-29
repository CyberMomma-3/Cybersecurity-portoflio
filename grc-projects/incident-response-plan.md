# Incident Response Plan

## Bright Smile Family Dentistry — Mock Organization

**Document Date:** May 2026
**Prepared By:** Melissa Gaither, CompTIA Security+
**Document Version:** 1.0
**Classification:** Confidential
**Framework:** NIST SP 800-61 & HIPAA Security Rule

-----

## Table of Contents

1. [Purpose and Scope](#1-purpose-and-scope)
1. [Incident Response Team](#2-incident-response-team)
1. [Incident Classification](#3-incident-classification)
1. [Phase 1 — Preparation](#4-phase-1--preparation)
1. [Phase 2 — Identification](#5-phase-2--identification)
1. [Phase 3 — Containment](#6-phase-3--containment)
1. [Phase 4 — Eradication](#7-phase-4--eradication)
1. [Phase 5 — Recovery](#8-phase-5--recovery)
1. [Phase 6 — Lessons Learned](#9-phase-6--lessons-learned)
1. [Ransomware Scenario Walkthrough](#10-ransomware-scenario-walkthrough)
1. [HIPAA Notification Requirements](#11-hipaa-notification-requirements)
1. [Document Review and Maintenance](#12-document-review-and-maintenance)

-----

## 1. Purpose and Scope

This Incident Response Plan (IRP) establishes procedures for detecting, responding to, and recovering from cybersecurity incidents affecting electronic Protected Health Information (ePHI) at **Bright Smile Family Dentistry**. It is designed to minimize damage, reduce recovery time, and ensure compliance with the HIPAA Security Rule (45 CFR § 164.308(a)(6)).

This plan applies to all staff, systems, and business associates that create, receive, maintain, or transmit ePHI, including clinical workstations, practice management software, digital imaging systems, email platforms, and backup systems.

> **Regulatory Basis:** The HIPAA Security Rule requires covered entities to implement policies and procedures to address security incidents, including identifying and responding to suspected or known incidents, mitigating harmful effects, and documenting incidents and outcomes (§164.308(a)(6)(ii)).

-----

## 2. Incident Response Team

|Role                                   |Responsibility                          |Contact                 |
|---------------------------------------|----------------------------------------|------------------------|
|Incident Response Lead (Office Manager)|Overall coordination and decision-making|[Office Manager Phone]  |
|Security Officer                       |HIPAA compliance and documentation      |[Security Officer Phone]|
|IT MSP                                 |Technical response and remediation      |[MSP Emergency Line]    |
|Practice Owner / Lead Dentist          |Final authority on major decisions      |[Owner Phone]           |
|Legal Counsel                          |Legal guidance on breach notification   |[Attorney Phone]        |
|HHS / OCR                              |Breach reporting portal                 |ocrportal.hhs.gov       |

### Chain of Command

1. **Any Staff Member** — Detects suspicious activity → immediately reports to Office Manager. Do not attempt to investigate or fix independently.
1. **Office Manager** — Receives report → contacts IT MSP emergency line → notifies Security Officer → begins incident log.
1. **IT MSP** — Assesses technical scope → advises on containment → begins remediation.
1. **Security Officer** — Determines if ePHI was involved → initiates HIPAA breach assessment → coordinates notification if required.
1. **Practice Owner / Legal** — Notified for High or Critical incidents → approves patient notification decisions.

-----

## 3. Incident Classification

|Level     |Description                                 |Examples                                                         |Response                                   |
|----------|--------------------------------------------|-----------------------------------------------------------------|-------------------------------------------|
|🟢 Low     |Minimal impact, no ePHI involved            |Spam email, failed login attempt                                 |Log and monitor                            |
|🟡 Medium  |Potential ePHI exposure, limited scope      |Lost unencrypted USB, phishing click (no confirmed data theft)   |Activate IRT, investigate within 24 hrs    |
|🟠 High    |Confirmed ePHI exposure or system compromise|Confirmed phishing breach, unauthorized access by former employee|Full IRT activation, begin HIPAA assessment|
|🔴 Critical|Major system compromise or mass ePHI breach |Ransomware attack, large-scale data theft                        |Full IRT + Legal + possible law enforcement|

-----

## 4. Phase 1 — Preparation

> Preparation is the most important phase. A practice that is well-prepared responds faster, recovers faster, and faces less regulatory exposure when an incident occurs.

### Preparation Checklist

- [ ] This Incident Response Plan is documented, approved, and accessible to all IRT members
- [ ] All IRT members have been trained on this plan and know their roles
- [ ] Annual tabletop exercise conducted to simulate an incident scenario
- [ ] All staff have completed HIPAA security awareness training including phishing recognition
- [ ] Clean, tested data backups exist and are stored securely offsite or in the cloud
- [ ] All staff have individual login credentials (no shared accounts)
- [ ] All laptops and workstations have full-disk encryption enabled
- [ ] Antivirus and endpoint protection software is installed and up to date on all devices
- [ ] All software patches are applied on a regular schedule
- [ ] Business Associate Agreements are in place with all vendors who handle ePHI
- [ ] IRT contact list is printed and posted in the office (not only stored digitally)
- [ ] Incident log template is ready and accessible

-----

## 5. Phase 2 — Identification

> Identification begins the moment something suspicious is noticed. Speed matters — the faster an incident is identified and reported, the less damage it causes.

### Common Warning Signs in a Dental Office

- Computers are unresponsive, unusually slow, or programs will not open
- A pop-up appears demanding payment to unlock files (ransomware)
- Staff receive emails asking them to click a link or enter their password
- A patient calls to report a suspicious email that appears to be from the office
- A staff member’s login is showing activity while they are not at their workstation
- The insurance clearinghouse reports unusual activity on the practice’s account
- Files are missing, renamed, or cannot be opened
- Antivirus software generates an alert or shuts down unexpectedly

### Identification Checklist

- [ ] Staff member reports suspicious activity to Office Manager immediately — do not investigate independently
- [ ] Office Manager opens incident log and records: date, time, who reported it, and what was observed
- [ ] Office Manager contacts IT MSP to assess whether a real incident has occurred
- [ ] IT MSP confirms incident and classifies severity (Low / Medium / High / Critical)
- [ ] Security Officer notified if ePHI may be involved
- [ ] Practice Owner notified for High or Critical incidents

-----

## 6. Phase 3 — Containment

> **⚠️ Critical Rule: Do Not Touch the Affected System.** The first instinct is to click around and try to fix it. This almost always makes things worse. Leave the affected computer exactly as it is.

### Immediate Containment (First 15 Minutes)

- [ ] Do not click anything on the affected computer — leave it exactly as found
- [ ] Do not turn off the affected computer unless directed by IT MSP (turning it off may destroy evidence)
- [ ] Disconnect the affected computer from the network — unplug the ethernet cable and/or disable WiFi
- [ ] Shut down or disconnect other workstations from the network to prevent spread
- [ ] Do not log into any systems using potentially compromised credentials
- [ ] Contact IT MSP emergency line immediately

### Short-Term Containment (First Few Hours)

- [ ] IT MSP assesses full scope of compromise across all systems
- [ ] Isolate any additional affected systems identified during assessment
- [ ] Change passwords for all staff accounts from an unaffected device
- [ ] Determine whether ePHI was accessed or exfiltrated
- [ ] Preserve all logs and evidence — do not delete anything
- [ ] Consider whether to continue operating on paper records temporarily
- [ ] Notify legal counsel if ePHI breach is confirmed or suspected

-----

## 7. Phase 4 — Eradication

> Eradication ensures the threat is fully removed before any systems are brought back online. Rushing this phase risks reinfection.

- [ ] IT MSP performs full forensic scan of all affected systems
- [ ] Identify the root cause — how did the attacker get in?
- [ ] Remove all malware, ransomware, or malicious files from affected systems
- [ ] Reimage (wipe and rebuild) any systems that cannot be fully cleaned
- [ ] Apply all outstanding software patches and security updates
- [ ] Remove or disable any unauthorized user accounts created during the incident
- [ ] Verify all systems are clean before proceeding to Recovery
- [ ] Document all findings and actions taken during eradication

-----

## 8. Phase 5 — Recovery

> Recovery is not just about turning computers back on — it requires careful validation to ensure everything is working correctly and securely before patients are seen.

- [ ] Restore patient data and records from the most recent clean backup
- [ ] Reinstall all practice software — Dentrix, Eaglesoft, imaging software, and billing platforms
- [ ] Calibrate digital X-ray sensors and imaging equipment after system restoration
- [ ] Test all systems thoroughly before returning to patient care
- [ ] Verify patient data integrity — confirm records are complete and accurate
- [ ] Reset all staff passwords and enforce new strong password requirements
- [ ] Re-enable multi-factor authentication on all accounts if applicable
- [ ] Monitor all systems closely for 30 days post-recovery for signs of reinfection
- [ ] Communicate with staff about the return to normal operations
- [ ] Document the date and time systems were restored and declared clean

-----

## 9. Phase 6 — Lessons Learned

> The Lessons Learned phase should occur within 2 weeks of the incident being resolved. Skipping this phase means the practice is likely to experience the same incident again.

- [ ] Hold a formal after-action meeting with all IRT members within 14 days of resolution
- [ ] Review the full incident log and timeline as a team
- [ ] Answer: What happened? How did it start? How was it detected?
- [ ] Answer: What did we do well? What could have been faster or better?
- [ ] Identify the root cause and confirm it has been fully addressed
- [ ] Update this Incident Response Plan based on lessons learned
- [ ] Conduct targeted staff training based on how the incident occurred
- [ ] Implement any new technical or administrative controls identified
- [ ] Produce a written after-action report and file with incident documentation

-----

## 10. Ransomware Scenario Walkthrough

> **Scenario:** A front desk staff member arrives Monday morning and finds a full-screen pop-up stating all files are encrypted and demanding $50,000 in Bitcoin. Dentrix will not open.

|Timeframe                   |Actions                                                                                                                                         |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
|0–15 Minutes                |Do not touch or click anything. Staff notifies Office Manager. Office Manager calls IT MSP. All staff told not to log into computers.           |
|15–60 Minutes               |IT MSP advises disconnecting all workstations from network. Practice moves to paper records. Security Officer notified. Incident log opened.    |
|Hours 1–4                   |IT MSP assesses scope. Determines which systems are encrypted and how ransomware entered. Practice Owner and Legal Counsel notified.            |
|Days 1–3                    |IT MSP wipes and reimages all affected systems. Removes ransomware. Applies patches. Changes all passwords. Verifies network is clean.          |
|Days 3–5                    |Patient data restored from clean backups. Software reinstalled. X-ray sensors calibrated. Systems tested. Practice returns to normal operations.|
|Within 60 Days              |If ePHI confirmed accessed — notify affected patients, HHS OCR, and media (if 500+ patients). File all documentation.                           |
|Within 14 Days of Resolution|After-action meeting held. IRP updated. Staff retrained on phishing. New controls implemented. Written report filed.                            |

-----

## 11. HIPAA Notification Requirements

|Who to Notify              |Deadline                                     |Method                            |Trigger                              |
|---------------------------|---------------------------------------------|----------------------------------|-------------------------------------|
|Affected Patients          |Within 60 days of discovery                  |Written notice by first-class mail|Any confirmed ePHI breach            |
|HHS Office for Civil Rights|Within 60 days (500+) or annually (under 500)|ocrportal.hhs.gov                 |Any confirmed ePHI breach            |
|Prominent Local Media      |Within 60 days of discovery                  |Press release                     |500+ patients in a single state      |
|Business Associates        |Without unreasonable delay                   |Per BAA terms                     |If BA caused or discovered the breach|


> **Important:** Paying a ransom does NOT eliminate the notification requirement. HIPAA requires notification unless a forensic investigation proves ePHI was not accessed or exfiltrated. When in doubt, notify.

-----

## 12. Document Review and Maintenance

|Activity                         |Frequency     |Owner                     |
|---------------------------------|--------------|--------------------------|
|Full IRP review and update       |Annual        |Security Officer          |
|Tabletop exercise / simulation   |Annual        |Security Officer + All IRT|
|Staff security awareness training|Annual        |Office Manager            |
|IRT contact list verification    |Semi-Annual   |Office Manager            |
|Backup restoration test          |Quarterly     |IT MSP                    |
|Review after any real incident   |Within 14 days|Security Officer          |

-----

> **Note:** This is a mock Incident Response Plan created as a cybersecurity career portfolio project. Bright Smile Family Dentistry is a fictional organization. All procedures are based on real HIPAA Security Rule requirements and NIST SP 800-61 methodology.

## References

- NIST SP 800-61 Rev 2 — Computer Security Incident Handling Guide. <https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final>
- HHS Office for Civil Rights — Breach Notification Rule. <https://www.hhs.gov/hipaa/for-professionals/breach-notification/index.html>
- HHS OCR — Ransomware and HIPAA Guidance. <https://www.hhs.gov/hipaa/for-professionals/security/guidance/ransomware/index.html>
- CompTIA Security+ Study Guide, Exam SY0-701

-----

*Prepared by: Melissa Gaither | CompTIA Security+ | GitHub: CyberMomma-3*
*This document is part of a cybersecurity career transition portfolio.*