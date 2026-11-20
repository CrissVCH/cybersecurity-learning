# HTB Academy — Incident Handling Process

> **Status:** In progress · **Completed:** Sections 1–2 of 11 — *Incident Handling* and *Cyber Kill Chain*
>
> **Learning path:** Linux Fundamentals → Incident Handling Process → Security Monitoring & SIEM Fundamentals
>
> **Last update:** 2026-11-20

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

## Section 2/11 — Cyber Kill Chain

### 1. The seven stages of the Cyber Kill Chain

The **Cyber Kill Chain** is a high-level model for understanding how an intrusion develops. Identifying the adversary's current stage can help defenders interrupt the attack before further damage.

| Stage | Meaning | Example |
| --- | --- | --- |
| **1. Reconnaissance** | Gather information about a target. | Public research or scanning exposed services. |
| **2. Weaponization** | Prepare the malicious capability or payload. | Build an exploit and malicious payload. |
| **3. Delivery** | Get malicious content to the intended target. | Phishing email or malicious link. |
| **4. Exploitation** | Trigger a vulnerability or malicious execution. | Victim opens a malicious attachment. |
| **5. Installation** | Install malicious software or establish access. | Dropper, backdoor, or rootkit. |
| **6. Command and Control (C2)** | Maintain communication with compromised systems. | Infected host checks in with attacker infrastructure. |
| **7. Actions on Objectives** | Carry out the attacker's intended goal. | Data theft, espionage, or disruption. |

**Passive reconnaissance** uses publicly available information (websites, job ads, social profiles). **Active reconnaissance** interacts directly with the target (port scans or service identification).

The stages are a helpful model, **not a rigid sequence**: real attacks can skip stages, repeat activities, or pursue multiple objectives.

### 2. MITRE ATT&CK: Tactics, Techniques, and Sub-techniques

[MITRE ATT&CK](https://attack.mitre.org/) describes observed adversary behavior at a more detailed level than the Cyber Kill Chain.

| Concept | Core question | Example |
| --- | --- | --- |
| **Tactic** | *Why / for what objective?* | Credential Access or Lateral Movement |
| **Technique** | *How is the objective achieved?* | T1003 — OS Credential Dumping |
| **Sub-technique** | *Which more specific method?* | T1003.001 — LSASS Memory |
| **Procedure** | *What exactly did this attacker do?* | The actual commands and sequence seen in an incident |

**TTPs** stands for *Tactics, Techniques, and Procedures*: a useful way to describe attacker behavior beyond isolated indicators.

Other examples from the module:

- **T1105 — Ingress Tool Transfer:** bringing tools or payloads into an environment, sometimes through utilities such as `curl` or `wget`.
- **T1021 — Remote Services:** use of remote access services in an attack.
- **T1021.002 — SMB/Windows Admin Shares:** a more specific remote-services sub-technique.
- **T1059.001 — PowerShell:** a sub-technique of command and scripting interpreter.

### 3. Pyramid of Pain

The Pyramid of Pain illustrates how much disruption different kinds of detection can cause for an adversary, from generally easier to change to more difficult:

1. Hash values.
2. IP addresses.
3. Domain names.
4. Network and host artifacts.
5. Tools.
6. TTPs (attacker behaviors and methods).

**IOC (Indicator of Compromise)** examples: a suspicious hash, IP address, domain, or filename. **TTP** examples: credential dumping, lateral movement over RDP, or persistence using Windows services.

**Takeaway:** IOC detections are valuable, but behavior-focused detection can remain useful when attackers rotate hashes, addresses, and domains.

### 4. Connecting an incident to ATT&CK

The module showed how one incident can involve several ATT&CK techniques:

| Observed behavior | ATT&CK example |
| --- | --- |
| Exploitation of a public-facing application | T1190 |
| PowerShell execution | T1059.001 |
| Persistence through a Windows service | T1543.003 |
| LSASS memory credential dumping | T1003.001 |
| Lateral movement through RDP | T1021.001 |
| Data encryption for impact | T1486 |

A **whole-incident ATT&CK mapping** summarizes multiple behaviors. An **individual TheHive alert** may describe only one part of that incident or have no ATT&CK mapping at all.

### 5. Practical lab — Investigating alerts in TheHive

**TheHive** helps SOC analysts organize alerts, observables, investigation tasks, and cases. In HTB, the web application used the format:

```text
http://TARGET_IP:9000
```

`TARGET_IP` is a **placeholder**: replace it with the IP assigned to the running HTB lab. TheHive's application credentials are distinct from SSH credentials unless the lab explicitly states otherwise.

**Connectivity troubleshooting used in the lab:**

```bash
ping -c 3 TARGET_IP
nc -vz TARGET_IP 9000
curl -v http://TARGET_IP:9000
```

| Test | What it helps answer | Observed result |
| --- | --- | --- |
| `ping -c 3` | Can the target respond to ICMP? | Received responses. |
| `nc -vz IP 9000` | Is TCP port 9000 accepting connections? | Connection succeeded. |
| `curl -v http://IP:9000` | Is the HTTP application responding? | HTTP 200 and TheHive HTML. |

**Important distinction:** `ping` can be blocked by ICMP rules even when a service is healthy, and an open TCP port does not prove the application is functioning correctly.

In the lab, the host and HTTP service responded, but Firefox initially failed to load TheHive due to a **browser/proxy (FoxyProxy) configuration issue**. Checking each network layer helped isolate a local browser problem from a server problem.

### 6. Finding an alert and interpreting its fields

The exercise involved locating an alert using its **Reference** (example from the lab: `67c202`) and inspecting its detailed fields.

| Field | Meaning |
| --- | --- |
| **Reference** | Identifier used to find the specific TheHive alert. |
| **`rule.id`** | Detection rule identifier from the source tool (such as Wazuh). |
| **`rule.mitre.id`** | MITRE ATT&CK technique/sub-technique ID associated with that detection. |
| **`rule.mitre.tactic`** | Associated ATT&CK tactic, when supplied. |
| **`rule.level`** | Rule severity/level from the source detection system. |

The lab alert related to **LSASS access and possible credential dumping**, connecting the hands-on evidence with the **Credential Access** tactic and ATT&CK mapping.

**Practical lesson:** Searching for every MITRE technique ID using `Ctrl+F` on the alerts list did not work reliably. The list may not show hidden alert details, and some alerts have no TTP mapping.

Better workflow:

1. Locate the exact alert using its Reference.
2. Open the alert details and read the event description.
3. Inspect `rule.mitre.id` and `rule.mitre.tactic` if available.
4. Compare the evidence with the overall incident timeline.
5. Decide whether it requires escalation, further investigation, or case creation.

### 7. Key takeaways for SOC and SIEM

- Cyber Kill Chain gives a broad view of an attack's progression; ATT&CK gives more granular behavior mappings.
- A tactic is an adversary objective; a technique is a method; a sub-technique is a more specific method.
- Behavioral evidence can be more durable than a single hash, IP, or domain indicator.
- A case or incident may contain many alerts, with different ATT&CK mappings.
- Alert identifiers and MITRE IDs serve different purposes.
- `ping`, `nc`, and `curl` answer different troubleshooting questions.
- An alert is **evidence to investigate**, not automatic proof of malicious activity.

**My takeaway:** Understanding attacker behavior helps a SOC analyst make sense of SIEM alerts and respond to the broader incident instead of treating each alert in isolation.

---

## Progress log

- [x] **1/11 — Incident Handling:** Definition, scope, lifecycle, real-world cases, and introduction to the scenario.
- [x] **2/11 — Cyber Kill Chain:** Attack stages, MITRE ATT&CK, Pyramid of Pain, TheHive alert analysis, and network troubleshooting.
- [ ] **3–11:** Continue the module. Add notes after completing each section rather than marking material as learned prematurely.

## Upcoming topics / questions

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
