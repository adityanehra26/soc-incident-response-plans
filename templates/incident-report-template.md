# Incident Response Plan – [Incident Type]

---

## 1. Overview

### Objective
Define the purpose of this Incident Response Plan and the goals of responding to this specific incident type.


### Scope & Definition of [Incident Type]
Describe what is considered in-scope for this incident.
Include:
- Types of attacks covered
- Assets or systems affected
- What is explicitly out of scope (if applicable)



### Assumptions & Limitations
Document assumptions and constraints that may impact incident handling, such as:
- Delayed user reporting
- Partial or missing logs
- Limited endpoint visibility
- Dependency on third-party systems


### Outcome
Describe the expected outcome of executing this IRP, such as:
- Reduced business impact
- Containment of the threat
- Recovery of affected systems
- Improved detection and prevention


### Document Usage
Explain how and when this document should be used:
- During active incidents
- As a reference during investigations
- For training and tabletop exercises


### Roles & Responsibilities

| Role | Responsibility |
|----|---------------|
| SOC Analyst | Initial triage and investigation |
| Incident Response Lead | Incident coordination and decision-making |
| IT / Infrastructure Team | System remediation and recovery |
| Identity / IAM Team | Account containment and recovery |
| Management / Stakeholders | Oversight and communication |

---

## 2. Response Plan

### 2.1 Preparation

#### Technical Controls
List technical controls required for readiness, such as:
- Email security controls
- Endpoint protection
- SIEM / log collection
- Network monitoring


#### User Awareness & Training
Document user-facing preparedness measures:
- Security awareness training
- Phishing simulations (if applicable)
- Incident reporting procedures


#### Communication Channels
Define communication methods used during incidents:
- SOC ticketing system
- Email or messaging platforms
- Incident bridge or war room


#### Logging & Monitoring Requirements
Specify required logs and telemetry:
- Authentication logs
- Endpoint telemetry
- Network logs
- Application or cloud logs


#### Access & Escalation Contacts
List access requirements and escalation paths:
- Privileged access requirements
- On-call contacts
- Escalation thresholds


### 2.2 Detection & Analysis

#### Detection Sources
Identify how incidents may be detected:
- SIEM alerts
- EDR alerts
- User reports
- Threat intelligence
- Automated detections


#### Initial Triage Steps
Provide step-by-step triage actions:
1. Validate alert legitimacy
2. Identify affected user(s) or system(s)
3. Determine whether interaction occurred
4. Preserve relevant evidence


#### Analysis Methodology / Checklist
Outline investigation activities such as:
- Log analysis
- Endpoint review
- Email or file analysis
- IOC extraction and enrichment
- Threat intelligence correlation


#### Impact Assessment
Assess the scope and severity of the incident:
- Number of affected users
- Systems impacted
- Data exposure risk
- Business impact


#### Incident Classification / Severity Levels
Define severity criteria:
- Low: No user interaction, no impact
- Medium: Limited exposure or user impact
- High: Credential compromise, malware execution, or lateral movement


### 2.3 Containment, Eradication & Recovery

#### Immediate Containment Actions
List containment steps based on confirmed impact:
- Account suspension or restriction
- Email or file quarantine
- Network isolation
- Blocking confirmed malicious indicators


#### User Account Recovery Steps
Describe actions for compromised identities:
- Password resets
- MFA enforcement
- Session revocation
- User validation


#### System & Endpoint Remediation
Outline remediation actions:
- Malware removal
- System reimaging (if required)
- Patch verification
- Configuration hardening


#### Verification of Successful Recovery
Define validation steps:
- No further malicious activity
- Clean endpoint scans
- Normal user access restored
- Monitoring for reoccurrence


### 2.4 Post-Incident Activity

#### Reporting & Documentation
Document:
- Incident timeline
- Root cause
- Actions taken
- Final resolution


#### Lessons Learned
Identify improvement areas:
- Detection gaps
- Response delays
- Process improvements


#### Communication to Stakeholders
Outline communication requirements:
- Internal teams
- Management
- Affected users (if applicable)


#### Policy / Control Updates
Document updates required:
- Security controls
- Detection rules
- Awareness training
- IR procedures

---

## 3. Resources

### Preparation Resources
List tools and documentation used for readiness:
- Security policies
- Training material
- Architecture diagrams


### Detection & Analysis Resources
Include:
- Log analysis tools
- Threat intelligence platforms
- Investigation guides


### Containment, Eradication & Recovery Resources
List:
- EDR tools
- IAM management tools
- Recovery procedures


### Post-Incident Resources
Include:
- Reporting templates
- Audit documentation
- Improvement tracking


### Useful Tools & References
Provide relevant tools and external references:
- Analysis utilities
- Documentation links
- Framework references


### Glossary (Optional)
Define important terms and abbreviations used in this document.

---
