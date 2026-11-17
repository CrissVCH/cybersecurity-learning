# HTB Academy — Incident Handling Process

> **Status:** In progress · **Completed:** Section 1 of 11 — *Incident Handling*  
> **Learning path:** Linux Fundamentals → Incident Handling Process → Security Monitoring & SIEM Fundamentals  
> **Last update:** 2026-11-16

## Learning goals

- Understand how organizations identify, investigate, contain, and recover from security incidents.
- Distinguish normal events, suspicious activity, and confirmed security incidents.
- Learn how incident response teams, SOC analysts, SIEM platforms, and case-management tools work together.
- Connect theory to real-world attack timelines and defensive monitoring.

---

## Section 1/11 — Incident Handling

### 1. Key concepts

| Term | Meaning | Example |
| --- | --- | --- |
| **Event** | An observable action or occurrence on a system or network. | A user signs in; a firewall allows a connection. |
| **Suspicious event** | Activity that needs investigation because it may indicate a threat. | Repeated failed logins followed by an unusual successful login. |
| **Security incident** | An event or series of events that compromises, or threatens to compromise, security. | Unauthorized access to a privileged account or deployment of malware. |
| **Incident handling (IH)** | A structured set of procedures for managing and responding to security incidents. | Investigating unauthorized access, containing the affected systems, and restoring operations. |
| **Incident response (IR) team** | People responsible for coordinating and performing the response. | SOC analysts, responders, system owners, and an incident manager. |

**Important:** Not every event is an incident. Some suspicious events only become confirmed incidents after analysis. An incident does **not** necessarily require malicious intent: accidental data exposure and availability failures can also require incident response.

### 2. Incident response lifecycle

1. **Preparation:** Define procedures and responsibilities, improve logging, establish communications, test backups, and prepare tools.
2. **Detection & Analysis:** Review alerts and evidence, determine what happened, assess the scope, and prioritize the incident.
3. **Containment, Eradication & Recovery:** Limit damage, remove the cause or attacker foothold, fix affected systems, and restore safe operations.
4. **Post-Incident Activity:** Document findings, conduct lessons learned, and improve defenses and response procedures.

The lifecycle is **iterative**: new evidence may send responders back to analysis or require another containment action.

### 3. Why incident handling matters

- Reduces damage, downtime, data loss, and recovery time.
- Creates a consistent response process instead of improvised reactions.
- Helps prioritize incidents according to their severity and business impact.
- Preserves information needed for investigation, reporting, and future prevention.

The **incident manager** coordinates the response, tracks actions, and ensures the relevant teams communicate and act on time.

### 4. Examples of incident causes

| Category | Example | Defensive lesson |
| --- | --- | --- |
| Exposed or stolen credentials | Compromised VPN account | Enforce MFA, review access, and monitor unusual logins. |
| Default or weak passwords | Unchanged `admin/admin` | Change defaults and enforce strong authentication. |
| Unpatched software | Exploitation of known vulnerabilities | Maintain an asset inventory and patch process. |
| Insider misuse | Abuse of legitimate employee permissions | Apply least privilege and review activity logs. |
| Phishing / social engineering | Employee tricked into granting access | Combine user awareness with technical controls. |
| Supply-chain compromise | Malicious software update | Assess suppliers and monitor unexpected behavior. |

### 5. Reading incident reports

Professional reports explain an attack **chronologically**: entry point → execution or persistence → lateral movement → impact → detection and response. Useful references include:

- [The DFIR Report](https://thedfirreport.com/) — real intrusion investigations.
- [Example: Confluence Exploit Leads to LockBit Ransomware](https://thedfirreport.com/2025/02/24/confluence-exploit-leads-to-lockbit-ransomware/).
- [MITRE ATT&CK](https://attack.mitre.org/) — a reference for adversary tactics and techniques, to study in later sections.

When reading a case, ask:

1. How did the attacker gain initial access?
2. Which systems and accounts were affected?
3. Which evidence or logs could reveal the activity?
4. What actions would contain the damage?
5. What control could prevent or detect a similar incident?

### 6. HTB scenario — Insight Nexus

The module presents a fictional company, **Insight Nexus**, with internet-facing applications and internal Windows systems. One threat actor used an unchanged default administrator password on an exposed ManageEngine application. The scenario describes reconnaissance, creation of privileged Active Directory accounts, further movement through an exposed RDP service, and spyware deployment through Group Policy.

**Environment and monitoring flow:**

```text
Web applications / Windows endpoints / Domain Controller / Servers
                       ↓ security events and logs
                      SIEM
                       ↓ alert or integration
               TheHive (case management)
                       ↓
                 SOC analyst
                       ↓
             Investigation and response
```

- **SIEM (Security Information and Event Management):** Collects and correlates logs to help identify potentially malicious activity.
- **TheHive:** A platform for managing investigations, alerts, tasks, and cases. Integrations must be configured; not every SIEM alert automatically becomes a case.
- **SOC analyst:** Reviews context and evidence, validates alerts, and escalates or investigates when necessary.

**Potential detection opportunities** (examples to investigate, not confirmed detections from the scenario):

- Successful administrator logins from unusual sources.
- Unexpected creation of privileged Active Directory accounts.
- RDP connections that do not match normal access patterns.
- Unusual GPO changes or software deployment across many endpoints.

The scenario mentions two threat actors; the available Section 1 material mainly details the first. More facts can be added as the module progresses.

### 7. How this connects to SIEM

Incident handling explains **what defenders must do** when a threat appears. SIEM helps with one critical part of that process: **collecting and analyzing security evidence**.

**My takeaway:** A SIEM alert is a starting point for investigation, not automatically proof of an attack. Analysts need to understand the context, verify the evidence, determine impact, and follow an incident response process.

---

## Progress log

- [x] **1/11 — Incident Handling:** Definition, scope, lifecycle, real-world cases, and introduction to the scenario.
- [ ] **2–11:** Continue the module. Add notes after completing each section rather than marking material as learned prematurely.

## Upcoming topics / questions

- How do the Cyber Kill Chain and MITRE ATT&CK help organize an investigation?
- How should incidents be categorized and prioritized?
- What evidence should be collected and preserved during an investigation?
- Which SIEM alerts and log sources are useful for detecting the scenario's activities?
- How do we document an incident from detection through lessons learned?

## Repository organization

```text
htb/
├── linux-fundamentals.md
├── incident-handling-process.md     ← this file
└── soc-fundamentals.md              ← create when starting SIEM
```

> **Portfolio note:** Record findings in your own words. Avoid uploading HTB flags, lab credentials, session tokens, or sensitive machine details to a public repository.
