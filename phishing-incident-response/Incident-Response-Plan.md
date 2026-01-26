# Overview

## Objective

This document outlines a structured response plan designed to guide Analysts and the Incident Response (IR) team through all stages of the incident lifecycle. It defines the necessary preparatory actions required to reduce the likelihood and impact of phishing incidents and ensures that appropriate resources are available for effective analysis and response.

The plan provides clear guidance for evaluating phishing alerts, documenting findings, determining root causes, and executing consistent response actions. It also includes a consolidated set of resources—tools, reference documents, and links—relevant to each phase of the incident response lifecycle.

## Scope & Definition of Phishing Attacks

This document applies to phishing incidents targeting the organization’s users, systems, or data.

It covers common phishing categories including, but not limited to:

- Credential-harvesting emails
- Malware or payload-delivering emails
- Spear-phishing and targeted attacks
- Business Email Compromise (BEC) attempts
- Phishing URLs distributed through corporate email channels

## Assumptions & Limitations

- All users are expected to follow the organization’s security awareness guidelines and report suspicious emails promptly.
- Logging, mailbox auditing, and security tools (e.g., email gateway, SIEM, EDR) are assumed to be operational and correctly configured.
- Incident Response actions depend on the availability of accurate data such as message traces, sign-in logs, and endpoint telemetry.
- This playbook provides general guidance; variations in technology, tools, or business requirements may require adjustments by the IR team.
- External factors such as vendor outages, delayed log availability, or incomplete user reports may limit the accuracy of analysis.

## Outcome

Effective application of this response plan enables the organization to:

- Rapidly detect and validate phishing incidents
- Contain and remediate malicious emails across affected mailboxes
- Protect compromised users by resetting credentials and securing accounts
- Identify the root cause, attack vector, and extent of impact
- Restore normal operations with minimal disruption
- Document findings to strengthen defenses and prevent recurrence

## Document Usage

This document serves as a practical guide for Analysts, Incident Responders, and IT personnel during suspected or confirmed phishing incidents.

It should be used:

- During triage of phishing alerts or user-reported emails
- When performing containment, eradication, and recovery actions
- For documenting incident details, impact, and lessons learned
- As a reference for approved tools, workflows, and communication procedures

The document is a **living reference** and must be updated following significant incidents, tool changes, or process enhancements.

## Roles & Responsibilities

| Role | Description | SPOC |
| --- | --- | --- |
| **Security Analyst** | • Perform initial alert triage and phishing email analysis<br>• Escalate incidents according to severity and defined thresholds<br>• Document findings and maintain timelines | Contact Info |
| **Incident Response Lead** | • Coordinate response efforts across teams<br>• Approve containment and recovery actions<br>• Communicate with management and stakeholders | Contact Info |
| **IT / Email Administration Team** | • Remove malicious emails from mailboxes<br>• Verify account security, reset credentials, revoke sessions<br>• Assist with system or mailbox log retrieval | Contact Info |
| **Security Awareness / Training Team** | • Notify users if needed and provide follow-up education<br>• Track user reporting effectiveness | Contact Info |
| **Management** | • Support escalation decisions and communication requirements<br>• Approve major recovery actions when business impact exists | Contact Info |

---
<br><br>
# Response Plan

## Preparation

The Preparation phase ensures that the organization has the necessary controls, visibility, and processes in place to effectively detect and respond to email phishing incidents. Proper preparation reduces response time, limits impact, and enables consistent execution of the response plan.

### **Technical Controls**

The following technical controls should be implemented and maintained:

- Secure Email Gateway with anti-phishing, anti-spoofing, and attachment scanning capabilities
- SPF, DKIM, and DMARC configured and enforced
- Endpoint Detection and Response (EDR) deployed on user endpoints
- Multi-Factor Authentication (MFA) enforced for user and privileged accounts
- Secure Web Gateway / DNS filtering for malicious URL blocking
- Centralized log collection and retention
- Automated email quarantine and message purge capabilities

### **User Awareness & Training**

- Mandatory security awareness training covering phishing and social engineering
- Regular phishing simulation exercises
- Clear and easy-to-use phishing reporting mechanism (button, mailbox, or ticket)
- Guidance for users on immediate actions after suspected interaction
- Periodic communication on emerging phishing trends and campaigns

### **Communication Channels**

The following communication channels must be defined and tested:

- Dedicated SOC or security incident mailbox
- Internal ticketing or case management system
- Secure internal messaging platform for IR coordination
- Escalation communication paths to IT, HR, Legal, and Management
- Pre-approved templates for user and stakeholder notifications

### **Logging & Monitoring Requirements**

To support detection, investigation, and response:

- Email message trace and delivery logs
- Mailbox audit logs (rule creation, forwarding, delegation)
- Authentication and sign-in logs
- EDR telemetry and endpoint activity logs
- Network and web access logs
- Log retention aligned with organizational and regulatory requirements

### **Access & Escalation Contacts**

- Defined roles with access to:
    - Email administration consoles
    - IAM and identity platforms
    - SIEM and EDR systems
- 24/7 escalation contact list for:
    - Incident Response Lead
    - IT / Email Administration Team
    - Endpoint Security Team
- Clearly documented escalation thresholds and approval authority
<br></br>
## Detection & Analysis

### Detection Sources

Phishing incidents may be detected through any of the following channels:

- **User Reports:** Suspicious emails reported via the phishing-reporting button, helpdesk, or security mailbox.
- **Email Security Gateway Alerts:** Notifications from EOP, Defender, Mimecast, Proofpoint, or equivalent tools regarding malicious URLs, spoofing attempts, or malware.
- **SIEM Alerts:** Indicators such as abnormal sign-in attempts, password spray patterns, or repeated failed authentication.
- **Threat Intelligence Feeds:** External intelligence identifying malicious sender domains, URLs, or attachment hashes.
- **Endpoint or Network Alerts:** Detected execution of malicious attachments, suspicious processes, or outbound connections.

### Initial Triage Steps

Upon receiving a suspected phishing alert, analysts must:

- Conduct a rapid assessment to determine potential severity and urgency.
- Validate whether the email is truly suspicious or a false positive.
- Check whether the user **clicked**, opened an attachment, or provided credentials.
- Identify whether multiple users received the same email.
- Gather relevant artifacts (email sample, headers, URLs, attachments).

Incidents involving credential compromise, malware execution, or organization-wide distribution must be escalated immediately.

### Email Analysis Methodology

Analysts must follow the established methodology to ensure thorough examination and consistency across all phishing investigations.

- **Header and Sender Examination**
    - Validate sender legitimacy by reviewing From, Reply-To, Return-Path, and sending domain.
    - Examine SPF, DKIM, and DMARC results.
    - Investigate message routing, IP origins, and anomalies in header metadata.
- **Content Examination**
    - Review email body for:
        - Urgency, fear, authority, or reward-based social engineering
        - Grammar anomalies or branding inconsistencies
        - Fraudulent requests such as password resets or payment instructions
- **Web and URL Artifacts**
    - Extract URLs and examine them safely using:
        - URL decode tools
        - Browserless scanning/sandboxing
        - Threat intelligence reputation checks
    - Identify redirections, domain age, hosting provider, and SSL certificate details.
- **Attachment Examination**
    - Analyze attachments in a secure sandbox or isolated environment.
    - Inspect:
        - File type mismatches
        - Macros or embedded scripts
        - Obfuscation indicators
        - Known malware signatures
- **Contextual Examination**
    - Determine whether the email fits patterns of:
        - Ongoing campaigns targeting the organization or industry
        - Known attacker techniques (TTPs)
        - Previously observed phishing activity
<br></br>
## Containment, Eradication & Recovery

### Immediate Containment Actions

Based on the findings from the Detection & Analysis phase:

- Remove the malicious email from all affected mailboxes using email security tools.
- Block associated sender addresses, domains, URLs, or attachments at the email gateway.
- Disable or lock affected user accounts if compromise is suspected.
- If credential theft is likely, force password reset and MFA re-registration.
- If malware download or execution is detected, **escalate to the Malware Incident Response Plan** immediately.

> Decision Point: If the analysis reveals a downloaded file, executed payload, or suspicious process → **trigger separate IR workflow** (Malware IR Plan, Ransomware IR Plan, etc.)

### User Account Recovery Steps

If user credentials may have been compromised:

- Reset the user’s password and revoke all active sessions.
- Check for abnormal sign-ins, MFA fraud alerts, or risky sign-in attempts.
- Review mailbox rules, forwarding rules, and account delegation for signs of attacker manipulation.
- Validate restoration of normal account activity.

### Email System Remediation

- Block malicious indicators (domains, URLs, hashes) across email gateway and security tools.
- Adjust anti-phishing rules, filters, and allow/block lists.
- Review email delivery logs to confirm no further spread or variants.
- Implement proactive detections (e.g., rule-based scanning) based on discovered TTPs.

### System & Endpoint Remediation

Triggered only when the Email Analysis finds endpoint interaction.

- Conduct endpoint scan using EDR to detect malware or suspicious activity.
- Isolate the device if malicious execution is confirmed.
- Remove malicious files, kill malicious processes, and clean persistence mechanisms.
- If required, escalate for forensic investigation.

> Note: This section remains *light* because the deeper remediation belongs in the **Malware IR Plan**.

### Verification of Successful Recovery

- Confirm malicious emails are fully removed organization-wide.
- Verify blocked indicators cannot be accessed.
- Ensure affected accounts are secure and not exhibiting abnormal activity.
- Confirm endpoints show no malicious behavior after remediation.
- Validate business operations are restored without residual risk.
<br></br>
## Post-Incident Activity

### Reporting & Documentation

Using the documentation created during the Email Analysis Methodology:

- Finalize the incident report summarizing timeline, indicators, impact, and actions taken.
- Include evidence collected during header, URL, attachment, and contextual analysis.
- Update SIEM/SOAR incident tickets with all findings and remediation notes.

### Lessons Learned

- Evaluate what worked well and what failed during detection or containment.
- Identify gaps in user awareness, logging, or email security.
- Determine whether new rules, alerts, or training are required.
- Feed findings back into the security awareness team.

### Communication to Stakeholders

- Notify management based on severity level.
- Communicate findings to affected users (e.g., additional training or follow-up guidance).
- Provide summaries to IT, SOC, and other relevant teams.

### Policy / Control Updates

- Update phishing detection rules, email gateway settings, and monitoring policies.
- Improve automated enrichment or triage processes based on incident findings.
- Add new indicators or patterns to threat intelligence watchlists.
- Update IR documentation if new steps were identified during the incident.

Using the documentation created during the Email Analysis Methodology:

- Finalize the incident report summarizing timeline, indicators, impact, and actions taken.
- Include evidence collected during header, URL, attachment, and contextual analysis.
- Update SIEM/SOAR incident tickets with all findings and remediation notes.

### Lessons Learned

- Evaluate what worked well and what failed during detection or containment.
- Identify gaps in user awareness, logging, or email security.
- Determine whether new rules, alerts, or training are required.
- Feed findings back into the security awareness team.

### Communication to Stakeholders

- Notify management based on severity level.
- Communicate findings to affected users (e.g., additional training or follow-up guidance).
- Provide summaries to IT, SOC, and other relevant teams.

### Policy / Control Updates

- Update phishing detection rules, email gateway settings, and monitoring policies.
- Improve automated enrichment or triage processes based on incident findings.
- Add new indicators or patterns to threat intelligence watchlists.
- Update IR documentation if new steps were identified during the incident.
---
