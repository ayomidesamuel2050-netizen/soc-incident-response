# SOC-INCIDENT-RESPONSE

A centralized repository for **Security Operations Center (SOC)** investigations, including **alert monitoring, incident triage, case analysis, and response workflows**.  
This project demonstrates the investigation and documentation of multiple SOC alerts using **Splunk** and supporting evidence.

---

## Project Overview

This repository contains a review of multiple security alerts assigned during a SOC investigation lab.  
The goal of this project is to:

- Investigate suspicious alerts
- Determine whether alerts are **true positives** or **false positives**
- Document findings clearly and professionally
- Practice SOC analyst workflows and case reporting

---

## Tools Used

- **Splunk**
- **Threat Intelligence / URL Reputation Checks**
- **Email Analysis**
- **Firewall / Proxy Log Review**

---

## Total Alerts

<img width="1495" height="485" alt="Total Alerts Dashboard" src="https://github.com/user-attachments/assets/3cfcadc5-1e8c-44d1-87e1-83acd62071e0" />

---

# Assigned Alerts Investigation

---

## Alert 8816 — Access to Blacklisted External URL Blocked by Firewall

**Severity:** High  
**Alert Type:** Web / Firewall  
**Status:** Investigated  

### Why This Alert Was Chosen
I selected **Alert 8816** because it had the **highest severity level**, making it the most critical alert to investigate first.

### Description
This alert was triggered when a user attempted to access an external URL that is listed in the organization's blacklist or threat intelligence feeds. The firewall or proxy successfully blocked the outbound request, preventing the connection.

> **Note:** Blacklists only protect against **known threats** and may not detect **new or unknown malicious domains**.

---

### Investigation in Splunk

#### Source IP
`10.20.2.17`

<img width="961" height="372" alt="Source IP Investigation" src="https://github.com/user-attachments/assets/83b6ec97-1a70-42ad-849c-767af7ed5b27" />

#### Suspicious URL
`http://bit.ly/3sHkX3da12340`

<img width="1184" height="660" alt="Malicious URL Evidence" src="https://github.com/user-attachments/assets/a2c6646b-3995-4575-8c6c-89fbe6d5fde6" />

### Findings
- The URL was identified as **malicious**
- The firewall **successfully blocked** the request
- No successful outbound connection was made

### Key Details
- **Action:** Blocked  
- **Timestamp:** `03/24/2026 12:40:00.965`

### Verdict
✅ **True Positive**

### Case Report Evidence

<img width="691" height="467" alt="Case Report 1" src="https://github.com/user-attachments/assets/5924b291-f4a4-462f-8319-fb121aa2d6ee" />
<img width="653" height="97" alt="Case Report 2" src="https://github.com/user-attachments/assets/7f29ed90-43eb-4759-9302-52f2f27fb43b" />

---

## Alert 8815 — Inbound Email Containing Suspicious External Link

**Severity:** Medium  
**Alert Type:** Email Security  
**Status:** Investigated  

### Description
This alert was triggered by an inbound email containing one or more external links with suspicious characteristics.  
As part of the investigation, firewall or proxy logs should be reviewed to determine whether any endpoints attempted to access the URLs and whether those connections were allowed or blocked.

---

### Investigation in Splunk

#### Email Details
- **Sender:** `urgents@amazon.biz`
- **Recipient:** `h.harris@thetrydaily.thm`
- **Subject:** `Your Amazon Package Couldn’t Be Delivered – Action Required`
- **URL:** `http://bit.ly/3sHkX3da`

<img width="1042" height="672" alt="Email Investigation 8815" src="https://github.com/user-attachments/assets/ab15f62d-f1c0-4e33-98ed-9d96c721e7d5" />

### Findings
- The embedded URL was identified as **malicious**
- The email appears to be a **phishing attempt**
- The sender domain is suspicious and impersonates a legitimate service

### Key Details
- **Timestamp:** `03/24/2026 12:38:46`

### Verdict
✅ **True Positive**

### Case Report Evidence

<img width="747" height="507" alt="Case Report 8815" src="https://github.com/user-attachments/assets/76400121-4ba0-4ec6-8711-d3f65ffc817e" />
<img width="737" height="101" alt="Case Report 8815 Additional" src="https://github.com/user-attachments/assets/5cfc7c06-6b40-4b76-989d-b0b2460fc08b" />

---

## Alert 8814 — Inbound Email Containing Suspicious External Link

**Severity:** Medium  
**Alert Type:** Email Security  
**Status:** Investigated  

### Description
This alert was triggered by an inbound email containing one or more external links with suspicious characteristics.  
The investigation focused on determining whether the email posed a real threat or was incorrectly flagged.

---

### Email Details
- **Datasource:** Email
- **Timestamp:** `03/24/2026 12:35:33`
- **Sender:** `onboarding@hrconnex.thm`
- **Recipient:** `j.garcia@thetrydaily.thm`
- **Subject:** `Action Required: Finalize Your Onboarding Profile`
- **Attachment:** None
- **Direction:** Inbound

<img width="963" height="636" alt="Alert 8814 Email Investigation" src="https://github.com/user-attachments/assets/008292a9-18c7-438b-9d76-1647dd60d563" />
<img width="427" height="468" alt="Alert 8814 Case Review" src="https://github.com/user-attachments/assets/45db982b-2fa5-4d25-a17d-9422f763d27b" />

### Findings
- The sender appears to be from a **legitimate internal onboarding process**
- No malicious payload or harmful redirection was confirmed
- The alert was likely triggered due to **automated link characteristics**

### Verdict
❌ **False Positive**

---

## Alert 8817 — Inbound Email Containing Suspicious External Link

**Severity:** Medium  
**Alert Type:** Email Security  
**Status:** Investigated  

### Description
This alert was triggered by an inbound email containing one or more external links with suspicious characteristics.  
The purpose of the investigation was to determine whether the email represented an actual phishing attempt or a non-malicious event.

---

### Email Details
- **Datasource:** Email
- **Timestamp:** `03/24/2026 12:41:04`
- **Sender:** `no-reply@m1crosoftsupport.co`
- **Recipient:** `c.allen@thetrydaily.thm`
- **Subject:** `Unusual Sign-In Activity on Your Microsoft Account`
- **Attachment:** None
- **Direction:** Inbound

<img width="1116" height="685" alt="Alert 8817 Email Investigation" src="https://github.com/user-attachments/assets/7b8908fa-95ab-47d8-8bac-98698c9d888d" />
<img width="435" height="456" alt="Alert 8817 Case Review" src="https://github.com/user-attachments/assets/5920b90a-6f0c-465f-a1cb-9df454c7d614" />

### Findings
- Although the sender domain appears suspicious, the investigation result classified this alert as non-malicious in the lab context
- No confirmed malicious execution or harmful interaction was observed

### Verdict
❌ **False Positive**

---

## Alert 8818 — Inbound Email Containing Suspicious External Link

**Severity:** Medium  
**Alert Type:** Email Security  
**Status:** Investigated  

### Description
This alert is similar in nature to **Alert 8814**, where the email triggered detection rules due to suspicious link characteristics.

<img width="437" height="421" alt="Alert 8818 Investigation" src="https://github.com/user-attachments/assets/b3fa6b35-7bd0-407d-82bd-d8b0fbe20f89" />

### Findings
- The alert matched suspicious email link behavior
- Further review showed no confirmed malicious activity
- This alert was determined to be another **false positive**

### Verdict
❌ **False Positive**

---

# Investigation Summary

| Alert ID | Alert Name | Verdict | Severity |
|---------|------------|---------|----------|
| 8816 | Access to Blacklisted External URL Blocked by Firewall | True Positive | High |
| 8815 | Inbound Email Containing Suspicious External Link | True Positive | Medium |
| 8814 | Inbound Email Containing Suspicious External Link | False Positive | Medium |
| 8817 | Inbound Email Containing Suspicious External Link | False Positive | Medium |
| 8818 | Inbound Email Containing Suspicious External Link | False Positive | Medium |

---

# Key Lessons Learned

Through this project, I practiced:

- SOC alert triage
- Identifying **true positives** vs **false positives**
- Investigating suspicious URLs and phishing emails
- Reviewing email metadata and security events in **Splunk**
- Writing structured incident reports

---

# Conclusion

This project demonstrates a practical **SOC analyst workflow** for handling and documenting security alerts.  
By investigating each alert and recording the evidence, I was able to improve my understanding of **incident response, phishing analysis, and threat validation** in a SOC environment.

---
 
_**Created as part of cybersecurity/SOC analyst learning and hands-on practice.**_
