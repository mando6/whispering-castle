## Course Overview

**Duration:** 8-10 hours  
**Level:** Intermediate to Advanced  
**Prerequisites:** Basic understanding of networking, operating systems, and security concepts

### Learning Objectives

By the end of this course, you will be able to:
- Understand the fundamentals of intrusion analysis within digital forensics
- Apply the Cyber Kill Chain and MITRE ATT&CK frameworks to analyze attacker behavior
- Identify and characterize attacker tactics, techniques, and procedures (TTPs)
- Reconstruct attack timelines and determine scope of compromise
- Document findings effectively for incident response and legal proceedings

---

## Module 1: Introduction to Intrusion Analysis

### 1.1 What is Intrusion Analysis?

Intrusion analysis is the systematic process of examining digital evidence to identify, characterize, and document the activities of an attacker within a compromised network or system. It answers critical questions:

- **Who** conducted the attack?
- **What** systems and data were compromised?
- **When** did the intrusion occur?
- **Where** did the attacker gain access?
- **Why** was the organization targeted?
- **How** did the attacker achieve their objectives?

### 1.2 The Role in Digital Forensics

Intrusion analysis connects to digital forensics as a specialized discipline focused on:

- **Post-incident investigation**: Examining what happened after a security breach
- **Evidence collection**: Gathering artifacts that demonstrate attacker behavior
- **Timeline reconstruction**: Building chronological sequences of events
- **Attribution**: Identifying indicators that may reveal attacker identity or motivation
- **Remediation support**: Providing actionable intelligence to prevent future attacks

**Connection to Main Topic:** Digital forensics provides the methodological foundation and evidence handling procedures that ensure intrusion analysis findings are legally defensible and technically sound.

### 1.3 Key Concepts

**Indicators of Compromise (IoCs)**
- Observable artifacts suggesting malicious activity (IP addresses, file hashes, domains)
- Used to detect and investigate security incidents

**Tactics, Techniques, and Procedures (TTPs)**
- Behavioral patterns that describe how adversaries operate
- More resilient to changes than simple IoCs

**Lateral Movement**
- Techniques attackers use to move through a network after initial compromise
- Critical for understanding scope of breach

**Persistence Mechanisms**
- Methods attackers use to maintain access to compromised systems
- Essential for complete remediation

---

## Module 2: The Cyber Kill Chain Framework

### 2.1 Framework Overview

Developed by Lockheed Martin, the Cyber Kill Chain describes the stages of a cyber attack from reconnaissance to achieving objectives. Understanding this framework allows analysts to:

- Identify which stage of an attack occurred
- Determine defensive gaps
- Predict attacker next moves
- Disrupt attacks in progress

**Connection to Main Topic:** The Kill Chain provides a structured approach to intrusion analysis by breaking complex attacks into discrete, analyzable phases.

### 2.2 The Seven Stages

#### Stage 1: Reconnaissance
**What happens:** Attackers research and identify targets, gathering information about the organization, employees, and technical infrastructure.

**Analysis Focus:**
- Review web server logs for unusual scanning activity
- Examine DNS queries for reconnaissance patterns
- Check for social media harvesting or OSINT gathering

**Artifacts to Examine:**
- Web server access logs
- DNS logs
- Email server logs (for email harvesting attempts)
- Perimeter firewall logs

#### Stage 2: Weaponization
**What happens:** Attackers create malicious payloads (malware, exploits) tailored to the target environment.

**Analysis Focus:**
- This stage typically occurs off-network
- Look for evidence of customized malware in later stages
- Identify exploit kits or tools used

**Artifacts to Examine:**
- Malware samples recovered from systems
- Exploit code characteristics
- Packer/obfuscation signatures

#### Stage 3: Delivery
**What happens:** Attackers transmit the weaponized payload to the target through various vectors (email, web, USB, etc.).

**Analysis Focus:**
- Identify delivery method used
- Determine which users or systems were targeted
- Timeline when delivery occurred

**Artifacts to Examine:**
- Email headers and attachments
- Web proxy logs
- Email gateway logs
- Endpoint detection logs
- USB device connection logs

#### Stage 4: Exploitation
**What happens:** The malicious code exploits vulnerabilities to execute on the target system.

**Analysis Focus:**
- Identify which vulnerability was exploited
- Determine if exploitation was successful
- Assess scope of initial compromise

**Artifacts to Examine:**
- Application crash logs
- System event logs (Event ID 1000, 1001, 1002)
- Security software alerts
- Memory dumps
- Exploit artifacts in browser cache

#### Stage 5: Installation
**What happens:** Attackers install malware and establish persistence mechanisms to maintain access.

**Analysis Focus:**
- Identify all persistence mechanisms
- Locate malware installation paths
- Determine privileges obtained

**Artifacts to Examine:**
- Registry Run keys (HKLM/HKCU\Software\Microsoft\Windows\CurrentVersion\Run)
- Scheduled tasks
- Service installations
- WMI event subscriptions
- Startup folder contents
- DLL hijacking indicators

#### Stage 6: Command and Control (C2)
**What happens:** Malware establishes communication channels with attacker-controlled infrastructure.

**Analysis Focus:**
- Identify C2 servers and domains
- Characterize communication protocols
- Determine frequency and timing of beaconing

**Artifacts to Examine:**
- Network traffic captures (PCAP files)
- Firewall logs
- Proxy logs
- DNS query logs
- NetFlow data
- HTTP/HTTPS connection logs

#### Stage 7: Actions on Objectives
**What happens:** Attackers achieve their goals (data exfiltration, system destruction, espionage, etc.).

**Analysis Focus:**
- Determine what data was accessed or stolen
- Identify lateral movement paths
- Assess overall impact

**Artifacts to Examine:**
- File access logs
- Database query logs
- Large outbound data transfers
- Authentication logs showing lateral movement
- Encryption/destruction evidence

### 2.3 Using the Kill Chain in Analysis

**Step-by-Step Application:**

1. **Map discovered artifacts to kill chain stages** - Organize your findings by which phase they represent
2. **Identify gaps** - Missing stages may indicate incomplete evidence or stealthy techniques
3. **Build timeline** - Sequence events chronologically within each stage
4. **Determine defenses that failed** - Analyze where security controls should have stopped the attack
5. **Recommend improvements** - Suggest controls for each stage to prevent recurrence

---

## Module 3: MITRE ATT&CK Framework

### 3.1 Framework Overview

MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) is a globally-accessible knowledge base of adversary tactics and techniques based on real-world observations. It provides:

- Comprehensive taxonomy of attacker behaviors
- Platform-specific technique descriptions
- Detection and mitigation guidance
- Common adversary procedures

**Connection to Main Topic:** ATT&CK provides granular detail for intrusion analysis, allowing analysts to precisely categorize attacker techniques and cross-reference with known threat actor behaviors.

### 3.2 ATT&CK Structure

The framework is organized hierarchically:

- **Tactics** (the "why") - Adversary's tactical goals (14 enterprise tactics)
- **Techniques** (the "how") - Methods used to achieve tactical goals
- **Sub-techniques** - More specific variations of techniques
- **Procedures** - Specific implementations by threat actors

### 3.3 The 14 Enterprise Tactics

#### TA0043: Reconnaissance
Gathering information to plan future operations.

**Key Techniques:**
- T1595: Active Scanning
- T1592: Gather Victim Host Information
- T1589: Gather Victim Identity Information

**Analysis Application:** Review logs for scanning, OSINT gathering, and information disclosure.

#### TA0042: Resource Development
Establishing resources to support operations (domains, infrastructure, capabilities).

**Key Techniques:**
- T1583: Acquire Infrastructure
- T1588: Obtain Capabilities
- T1586: Compromise Accounts

**Analysis Application:** Identify attacker-controlled infrastructure and stolen credentials.

#### TA0001: Initial Access
Techniques used to gain entry into the network.

**Key Techniques:**
- T1566: Phishing (with sub-techniques for spearphishing attachment, link, via service)
- T1190: Exploit Public-Facing Application
- T1133: External Remote Services
- T1078: Valid Accounts

**Analysis Application:** Determine the initial compromise vector by examining email, web, and authentication logs.

**Connection to Kill Chain:** Maps directly to Delivery and Exploitation stages.

#### TA0002: Execution
Techniques for running malicious code.

**Key Techniques:**
- T1059: Command and Scripting Interpreter (PowerShell, cmd, bash)
- T1204: User Execution
- T1047: Windows Management Instrumentation
- T1053: Scheduled Task/Job

**Analysis Application:** Examine process creation logs, script execution evidence, and task scheduler artifacts.

#### TA0003: Persistence
Techniques to maintain access across restarts and credential changes.

**Key Techniques:**
- T1547: Boot or Logon Autostart Execution
- T1053: Scheduled Task/Job
- T1543: Create or Modify System Process
- T1136: Create Account
- T1098: Account Manipulation

**Analysis Application:** Thoroughly examine all persistence locations to ensure complete remediation.

**Connection to Kill Chain:** Maps to Installation stage.

#### TA0004: Privilege Escalation
Techniques to gain higher-level permissions.

**Key Techniques:**
- T1068: Exploitation for Privilege Escalation
- T1078: Valid Accounts
- T1134: Access Token Manipulation
- T1055: Process Injection

**Analysis Application:** Review security event logs for privilege changes and unusual access patterns.

#### TA0005: Defense Evasion
Techniques to avoid detection.

**Key Techniques:**
- T1562: Impair Defenses (disable antivirus, logging)
- T1070: Indicator Removal (clear logs, delete files)
- T1027: Obfuscated Files or Information
- T1055: Process Injection
- T1218: System Binary Proxy Execution

**Analysis Application:** Look for gaps in logs, disabled security tools, and code obfuscation.

#### TA0006: Credential Access
Techniques for stealing credentials.

**Key Techniques:**
- T1003: OS Credential Dumping (LSASS, SAM, etc.)
- T1110: Brute Force
- T1056: Input Capture (keylogging)
- T1558: Steal or Forge Kerberos Tickets

**Analysis Application:** Examine credential access events, LSASS interaction, and authentication anomalies.

#### TA0007: Discovery
Techniques for gaining knowledge about the system and network.

**Key Techniques:**
- T1083: File and Directory Discovery
- T1087: Account Discovery
- T1018: Remote System Discovery
- T1049: System Network Connections Discovery
- T1082: System Information Discovery

**Analysis Application:** Review command history, network enumeration, and reconnaissance activity.

#### TA0008: Lateral Movement
Techniques for moving through the network.

**Key Techniques:**
- T1021: Remote Services (RDP, SMB, SSH)
- T1570: Lateral Tool Transfer
- T1080: Taint Shared Content
- T1550: Use Alternate Authentication Material

**Analysis Application:** Analyze authentication logs, remote access sessions, and file transfers between systems.

**Critical for Intrusion Analysis:** Lateral movement reveals the full scope of compromise.

#### TA0009: Collection
Techniques for gathering information of interest.

**Key Techniques:**
- T1560: Archive Collected Data
- T1005: Data from Local System
- T1039: Data from Network Shared Drive
- T1113: Screen Capture
- T1114: Email Collection

**Analysis Application:** Look for staged data, compression activities, and unusual file access patterns.

#### TA0011: Command and Control
Techniques for communicating with compromised systems.

**Key Techniques:**
- T1071: Application Layer Protocol (HTTP, DNS, email)
- T1573: Encrypted Channel
- T1090: Proxy
- T1095: Non-Application Layer Protocol
- T1571: Non-Standard Port

**Analysis Application:** Analyze network traffic for C2 beaconing, unusual protocols, and encrypted channels.

**Connection to Kill Chain:** Maps to Command and Control stage.

#### TA0010: Exfiltration
Techniques for stealing data from the network.

**Key Techniques:**
- T1041: Exfiltration Over C2 Channel
- T1048: Exfiltration Over Alternative Protocol
- T1567: Exfiltration Over Web Service
- T1020: Automated Exfiltration

**Analysis Application:** Identify large outbound transfers, uploads to cloud services, and data staging.

**Connection to Kill Chain:** Part of Actions on Objectives stage.

#### TA0040: Impact
Techniques for disrupting availability or compromising integrity.

**Key Techniques:**
- T1486: Data Encrypted for Impact (ransomware)
- T1485: Data Destruction
- T1490: Inhibit System Recovery
- T1498: Network Denial of Service

**Analysis Application:** Document destruction, encryption, or disruption activities.

**Connection to Kill Chain:** Part of Actions on Objectives stage.

### 3.4 Using ATT&CK in Intrusion Analysis

**Practical Application Process:**

1. **Document observed attacker activities** - List all suspicious or confirmed malicious actions
2. **Map to ATT&CK techniques** - Identify which technique(s) each activity represents
3. **Use ATT&CK Navigator** - Visualize the attack path using the ATT&CK Navigator tool
4. **Cross-reference with threat intelligence** - Compare TTPs with known threat actors
5. **Identify detection gaps** - Determine which techniques you couldn't detect
6. **Generate mitigations** - Use ATT&CK's mitigation guidance for each technique

**Example Mapping:**

```
Observed Activity: PowerShell script executed from temporary directory
ATT&CK Mapping:
  - Tactic: Execution (TA0002)
  - Technique: Command and Scripting Interpreter (T1059)
  - Sub-technique: PowerShell (T1059.001)

Observed Activity: Registry Run key modified to execute malware at startup
ATT&CK Mapping:
  - Tactic: Persistence (TA0003)
  - Technique: Boot or Logon Autostart Execution (T1547)
  - Sub-technique: Registry Run Keys / Startup Folder (T1547.001)
```

### 3.5 ATT&CK vs Kill Chain

**When to Use Each Framework:**

**Kill Chain:**
- High-level attack narrative
- Executive reporting
- Strategic defense planning
- Linear attack progression

**MITRE ATT&CK:**
- Detailed technical analysis
- Specific technique identification
- Detection engineering
- Threat actor attribution
- Comprehensive TTPs documentation

**Best Practice:** Use both frameworks together. Map detailed ATT&CK techniques to Kill Chain stages for complete analysis.

---

## Module 4: Intrusion Analysis Methodology

### 4.1 Preparation Phase

**Before Investigation Begins:**

1. **Establish legal authority** - Ensure proper authorization for investigation
2. **Define scope** - Determine which systems and timeframes to analyze
3. **Assemble tools** - Prepare forensic software and hardware
4. **Document chain of custody** - Establish procedures for evidence handling
5. **Create analysis environment** - Set up isolated systems for examination

**Connection to Main Topic:** Proper preparation ensures intrusion analysis findings are admissible and defensible.

### 4.2 Evidence Collection

**Key Artifacts for Intrusion Analysis:**

**System-Level Artifacts:**
- Memory dumps (volatile data)
- Disk images (non-volatile data)
- Registry hives
- Event logs (System, Security, Application)
- Prefetch files
- Shimcache/AmCache
- SRUM database
- File system timeline

**Network-Level Artifacts:**
- Packet captures (PCAP)
- NetFlow data
- Firewall logs
- Proxy logs
- DNS logs
- IDS/IPS alerts
- Network device configurations

**Application-Level Artifacts:**
- Web server logs
- Database logs
- Email server logs
- Application-specific logs
- Cloud service logs

**Best Practices:**
- Collect volatile data first (memory, active connections)
- Use write-blockers for disk imaging
- Document collection process thoroughly
- Maintain cryptographic hashes for integrity

### 4.3 Timeline Analysis

**Creating a Comprehensive Timeline:**

Timeline analysis is fundamental to understanding attack progression.

**Steps:**

1. **Aggregate time-stamped artifacts** from multiple sources
2. **Normalize timestamps** to single timezone (usually UTC)
3. **Create supertimeline** using tools like log2timeline/Plaso
4. **Filter for relevant events** based on initial indicators
5. **Identify temporal clusters** of suspicious activity
6. **Build attack narrative** chronologically

**File System Timestamps (MACB):**
- **M**odified - Content changed
- **A**ccessed - File read
- **C**hanged - Metadata changed
- **B**orn - File created

**Critical Analysis Points:**
- First evidence of attacker presence
- Privilege escalation events
- Lateral movement timing
- Data staging and exfiltration windows
- Persistence installation timeframes

### 4.4 Network Traffic Analysis

**Analyzing Network Evidence:**

1. **Identify baseline behavior** - Understand normal network patterns
2. **Detect anomalies** - Look for deviations from baseline
3. **Follow connections** - Trace attacker communication flows
4. **Extract artifacts** - Carve files, credentials, commands from packets
5. **Reconstruct sessions** - Build complete picture of attacker actions

**Key Indicators:**
- Unusual outbound connections
- Uncommon protocols or ports
- Large data transfers
- Beaconing patterns (regular C2 check-ins)
- Geographical anomalies
- Failed authentication attempts

**Tools:** Wireshark, NetworkMiner, Zeek (Bro), tcpdump

### 4.5 Malware Analysis

**When malware is discovered during intrusion analysis:**

**Basic/Static Analysis:**
- File properties (size, timestamps, hashes)
- Strings extraction
- PE header analysis
- Packer detection
- VirusTotal/threat intelligence lookup

**Behavioral/Dynamic Analysis:**
- Execute in sandbox environment
- Monitor file system changes
- Track registry modifications
- Capture network communications
- Observe process creation

**Goal:** Understand malware capabilities, persistence mechanisms, and C2 infrastructure to complete the intrusion picture.

### 4.6 Log Analysis

**Windows Event Logs:**

**Security Log - Key Event IDs:**
- 4624: Successful logon
- 4625: Failed logon
- 4672: Special privileges assigned
- 4688: Process creation
- 4697: Service installed
- 4720: User account created
- 4732: User added to privileged group

**System Log:**
- 7045: Service installation
- 7036: Service state change
- 1074: System shutdown/restart
- 6005/6006: Event log service started/stopped

**PowerShell Logs:**
- Event ID 4104: Script block logging
- Event ID 4103: Module logging

**Linux/Unix Logs:**
- /var/log/auth.log - Authentication
- /var/log/syslog - System messages
- /var/log/apache2/ - Web server
- ~/.bash_history - Command history

**Analysis Tips:**
- Look for time gaps (possible log deletion)
- Correlate events across systems
- Identify unusual user behaviors
- Track privilege escalations

### 4.7 Scoping the Compromise

**Determining Full Breach Extent:**

1. **Identify patient zero** - First compromised system
2. **Map lateral movement** - Track attacker's path through network
3. **List all compromised accounts** - User and service accounts used
4. **Document affected systems** - All hosts the attacker accessed
5. **Assess data exposure** - What information was accessed or exfiltrated
6. **Identify persistence mechanisms** - All ways attacker maintained access

**Scope Expansion Triggers:**
- Discovery of additional compromised credentials
- Evidence of privilege escalation
- New C2 communications detected
- Additional malware families identified

### 4.8 Attribution Analysis

**Identifying Attacker Characteristics:**

While definitive attribution is challenging, analysts can identify:

**Technical Indicators:**
- Malware families used (linked to specific groups)
- Infrastructure patterns (hosting choices, domains)
- Operational security mistakes (exposed IPs, usernames)
- Code artifacts (language, time zones in timestamps)

**Behavioral Indicators:**
- Targeting patterns (industry, geography)
- Sophistication level
- Motivations (financial, espionage, disruption)
- Dwell time and patience

**Caution:** Attribution is extremely difficult and often requires extensive intelligence. False flags are common. Focus on TTPs rather than attribution for remediation purposes.

---

## Module 5: Documentation and Reporting

### 5.1 Importance of Documentation

**Why Thorough Documentation Matters:**

- **Legal admissibility** - Courts require detailed evidence handling records
- **Repeatability** - Others must be able to verify your findings
- **Knowledge transfer** - Team members need complete context
- **Incident response** - Guides remediation efforts
- **Lessons learned** - Improves future defenses

**Connection to Main Topic:** Documentation transforms intrusion analysis from data to actionable intelligence.

### 5.2 Elements of Analysis Documentation

**What to Document:**

1. **Chain of custody** - Every person who handled evidence
2. **Collection methods** - Tools and procedures used
3. **Analysis steps** - All examinations performed
4. **Findings** - What was discovered
5. **Timeline** - Chronological attack sequence
6. **Indicators of Compromise** - Hashes, IPs, domains, file paths
7. **Attacker TTPs** - Techniques used (mapped to frameworks)
8. **Scope assessment** - Systems and data affected
9. **Recommendations** - Remediation and prevention steps

### 5.3 Report Structure

**Technical Intrusion Analysis Report:**

**1. Executive Summary**
- Incident overview
- Key findings
- Impact assessment
- Critical recommendations

**2. Incident Overview**
- Initial detection
- Investigation scope
- Timeline summary

**3. Technical Analysis**
- Attack vector (Initial Access)
- Attack progression (Kill Chain/ATT&CK mapping)
- Systems compromised
- Data accessed/exfiltrated
- Malware analysis summary
- Network analysis findings

**4. Timeline of Events**
- Detailed chronological sequence
- Key milestones highlighted

**5. Indicators of Compromise**
- File hashes
- Network indicators (IPs, domains)
- Registry keys
- File paths
- Account names

**6. Attacker TTPs**
- Kill Chain mapping
- ATT&CK technique listing
- Behavioral analysis

**7. Impact Assessment**
- Business impact
- Data loss
- System availability
- Regulatory implications

**8. Recommendations**
- Immediate containment steps
- Eradication procedures
- Recovery actions
- Long-term improvements

**9. Appendices**
- Detailed technical evidence
- Tool outputs
- Screenshots
- Log excerpts

### 5.4 Presenting to Different Audiences

**Executive Audience:**
- Focus on business impact
- Use Kill Chain for narrative structure
- Highlight risk and recommendations
- Minimize technical jargon

**Technical Audience:**
- Detailed ATT&CK mappings
- Complete IoC lists
- Technical evidence
- Detection and prevention specifics

**Legal Audience:**
- Chain of custody emphasis
- Methodology justification
- Evidence integrity
- Compliance implications

---

## Module 6: Tools and Resources

### 6.1 Essential Forensic Tools

**Disk and Memory Analysis:**
- **Autopsy/The Sleuth Kit** - Open-source digital forensics platform
- **FTK Imager** - Free disk imaging and analysis
- **Volatility** - Memory forensics framework
- **Rekall** - Memory analysis framework
- **X-Ways Forensics** - Commercial forensics suite

**Network Analysis:**
- **Wireshark** - Packet analyzer
- **NetworkMiner** - Network forensic analysis
- **Zeek (Bro)** - Network security monitoring
- **tcpdump** - Command-line packet capture

**Log Analysis:**
- **Splunk** - Security information and event management (SIEM)
- **ELK Stack** (Elasticsearch, Logstash, Kibana) - Open-source log management
- **Graylog** - Log management platform
- **Chainsaw** - Windows event log analysis

**Timeline Creation:**
- **log2timeline/Plaso** - Super timeline generation
- **Timesketch** - Timeline analysis and collaboration

**Malware Analysis:**
- **Remnux** - Linux distribution for malware analysis
- **FLARE VM** - Windows-based malware analysis environment
- **Cuckoo Sandbox** - Automated malware analysis
- **IDA Pro/Ghidra** - Disassemblers for reverse engineering

**ATT&CK Tools:**
- **ATT&CK Navigator** - Visualize and annotate ATT&CK techniques
- **Atomic Red Team** - Test detection coverage
- **MITRE Caldera** - Automated adversary emulation

### 6.2 Reference Documentation

**MITRE ATT&CK Resources:**
- Official ATT&CK Website: https://attack.mitre.org/
- ATT&CK Navigator: https://mitre-attack.github.io/attack-navigator/
- Getting Started with ATT&CK: https://attack.mitre.org/resources/getting-started/
- ATT&CK for CTI: https://attack.mitre.org/resources/attackcon/
- ATT&CK Workbench: https://mitre-engenuity.org/cybersecurity/center-for-threat-informed-defense/our-work/attck-workbench/

**Cyber Kill Chain Resources:**
- Lockheed Martin Kill Chain Paper: https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html
- Kill Chain Analysis Guide: Search for "Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains"

**Digital Forensics Standards:**
- NIST Computer Forensics Tool Testing (CFTT): https://www.nist.gov/itl/ssd/software-quality-group/computer-forensics-tool-testing-program-cftt
- SWGDE Best Practices: https://www.swgde.org/
- ISO/IEC 27037 - Digital Evidence Guidelines

**Windows Forensics:**
- SANS Windows Forensic Analysis Poster: https://www.sans.org/posters/
- 13Cubed YouTube Channel: Excellent Windows forensics tutorials
- Windows Event Log Encyclopedia: https://www.ultimatewindowssecurity.com/

**Linux Forensics:**
- Linux LEO: https://linuxleo.com/
- SANS Linux Forensics Blog: https://www.sans.org/blog/

**Network Forensics:**
- Wireshark Documentation: https://www.wireshark.org/docs/
- Zeek Documentation: https://docs.zeek.org/

**Memory Forensics:**
- Volatility Documentation: https://volatility3.readthedocs.io/
- The Art of Memory Forensics (Book by Ligh, Case, Levy)

**Learning Platforms:**
- SANS FOR508: Advanced Incident Response, Threat Hunting, and Digital Forensics
- SANS FOR610: Reverse-Engineering Malware
- Cybrary: Free cybersecurity courses
- TryHackMe: Hands-on cybersecurity training
- HackTheBox: Penetration testing labs

**Threat Intelligence:**
- VirusTotal: https://www.virustotal.com/
- AlienVault OTX: https://otx.alienvault.com/
- MISP: https://www.misp-project.org/
- Recorded Future: Threat intelligence platform

**Community Resources:**
- Reddit r/computerforensics
- Digital Forensics Discord communities
- DFIR.training website
- AboutDFIR.com - Tool listings and resources

---

## Module 7: Practical Case Study

### 7.1 Scenario: Healthcare Provider Ransomware Attack

**Background:**
A regional healthcare provider with 500 employees detects ransomware encryption on multiple file servers. Your team is called to investigate.

**Initial Information:**
- Detection: Monday, 8:45 AM - IT staff notices encrypted files
- Affected systems: 3 file servers, 25 workstations
- Ransom note: Demands $500,000 in Bitcoin, threatens data leak
- Business impact: Critical patient records encrypted

### 7.2 Investigation Process

**Phase 1: Initial Triage**

**Actions Taken:**
1. Isolated affected systems from network
2. Captured memory dumps from key systems
3. Collected disk images
4. Preserved network logs (firewall, proxy, DNS)
5. Interviewed IT staff about first detection

**Initial Findings:**
- Ransomware note references "LockBit 3.0"
- Encryption started approximately Sunday, 11:30 PM
- Some backups also encrypted

**Phase 2: Timeline Development**

**Key Timeline Events Discovered:**

**15 days ago, Wednesday, 2:47 PM:**
- Email received by HR staff member with resume attachment "Resume_JohnDoe.pdf.exe"
- Event Log: Successful logon (Event ID 4624) for user "hradmin"
- Email gateway log shows email passed SPF/DKIM checks

**Kill Chain Stage:** Delivery
**ATT&CK:** Initial Access - T1566.001 (Phishing: Spearphishing Attachment)

**15 days ago, Wednesday, 2:51 PM:**
- Process creation: outlook.exe spawned cmd.exe
- PowerShell executed with encoded command
- Event ID 4688: Process creation

**Kill Chain Stage:** Exploitation, Execution
**ATT&CK:** 
- Execution - T1059.001 (PowerShell)
- Execution - T1059.003 (Windows Command Shell)

**15 days ago, Wednesday, 2:52 PM:**
- Outbound connection to 185.220.101.XX:443
- DNS query for "legitupdate[.]com"
- Malware dropped: C:\Users\hradmin\AppData\Local\Temp\svchost.exe

**Kill Chain Stage:** Installation, Command and Control
**ATT&CK:**
- Command and Control - T1071.001 (Web Protocols)
- Defense Evasion - T1036.005 (Match Legitimate Name)

**15 days ago, Wednesday, 2:55 PM:**
- Registry modification: HKCU\Software\Microsoft\Windows\CurrentVersion\Run
- Persistence established
- Event ID 13 (Registry value set) in Sysmon logs

**Kill Chain Stage:** Installation
**ATT&CK:** Persistence - T1547.001 (Registry Run Keys)

**14 days ago, Thursday, 8:15 AM:**
- LSASS memory access by svchost.exe
- Event ID 10 (Process Access) in Sysmon logs
- Credential dumping detected

**ATT&CK:** Credential Access - T1003.001 (LSASS Memory)

**14 days ago, Thursday, 9:30 AM:**
- Successful logon from hradmin to DC01 (domain controller)
- Event ID 4624, Logon Type 3 (Network)
- Lateral movement initiated

**ATT&CK:** Lateral Movement - T1021.002 (SMB/Windows Admin Shares)

**13 days ago, Friday, 11:20 AM:**
- Multiple systems queried via "net view" and "nltest" commands
- Domain enumeration activities

**ATT&CK:** Discovery - T1018 (Remote System Discovery), T1482 (Domain Trust Discovery)

**7 days ago, Saturday, 3:40 AM:**
- Archive created: backup_data.7z (45 GB)
- Located in \\FileServer01\IT\Temp\

**ATT&CK:** Collection - T1560.001 (Archive via Utility)

**6 days ago, Sunday, 4:15 AM:**
- Large outbound transfer to cloud storage service (mega[.]nz)
- 47 GB uploaded over 6 hours
- Proxy logs show sustained HTTPS connections

**Kill Chain Stage:** Actions on Objectives
**ATT&CK:** Exfiltration - T1567.002 (Exfiltration to Cloud Storage)

**Sunday, 11:30 PM:**
- Ransomware executable dropped across network: "update.exe"
- Windows Defender disabled via Group Policy
- Event ID 5001 (Antivirus disabled)
- Scheduled task created to execute ransomware

**ATT&CK:** 
- Defense Evasion - T1562.001 (Disable or Modify Tools)
- Execution - T1053.005 (Scheduled Task)
- Persistence - T1053.005 (Scheduled Task)

**Sunday, 11:45 PM:**
- Mass file encryption begins across network
- Shadow copies deleted: "vssadmin delete shadows /all /quiet"
- Backup deletion: VSS snapshots removed

**Kill Chain Stage:** Actions on Objectives
**ATT&CK:** 
- Impact - T1486 (Data Encrypted for Impact)
- Impact - T1490 (Inhibit System Recovery)

**Monday, 12:30 AM:**
- Ransom notes deployed: "README_TO_DECRYPT.txt"
- Encryption complete on primary targets

**ATT&CK:** Impact - T1486 (Data Encrypted for Impact)

### 7.3 Analysis Summary

**Attack Vector:** Spearphishing email with malicious executable attachment

**Dwell Time:** 15 days (from initial compromise to ransomware deployment)

**Attacker Objectives:**
1. Data exfiltration (double extortion)
2. Financial gain through ransom
3. Maximum business disruption

**Scope of Compromise:**
- Initial access: 1 workstation (HR department)
- Lateral movement: 8 additional workstations, 2 servers
- Domain controller compromised
- Total affected: 28 systems
- Credentials compromised: 12 user accounts, 2 service accounts
- Data exfiltrated: 47 GB (patient records, financial data, employee information)

**Kill Chain Analysis:**

| Stage | Evidence Found | Date/Time |
|-------|---------------|-----------|
| Reconnaissance | Targeted email to HR | Occurred off-network |
| Weaponization | Custom malware | Occurred off-network |
| Delivery | Spearphishing email | 15 days ago, 2:47 PM |
| Exploitation | Malicious executable run | 15 days ago, 2:51 PM |
| Installation | Malware + persistence | 15 days ago, 2:52-2:55 PM |
| Command & Control | C2 communication | 15 days ago, 2:52 PM onward |
| Actions on Objectives | Credential theft, lateral movement, data exfiltration, ransomware | 14 days ago through incident |

**ATT&CK Technique Summary:**
- Initial Access: T1566.001
- Execution: T1059.001, T1059.003, T1053.005
- Persistence: T1547.001, T1053.005
- Defense Evasion: T1036.005, T1562.001
- Credential Access: T1003.001
- Discovery: T1018, T1482
- Lateral Movement: T1021.002
- Collection: T1560.001
- Command and Control: T1071.001
- Exfiltration: T1567.002
- Impact: T1486, T1490

### 7.4 Key Findings and IoCs

**Network Indicators:**
- C2 Domain: legitupdate[.]com
- C2 IP: 185.220.101.XX
- Exfiltration destination: mega[.]nz
- User agent: Mozilla/5.0 (custom variant)

**File Indicators:**
- Initial payload: Resume_JohnDoe.pdf.exe
  - SHA256: a1b2c3d4e5f6...
- Dropped malware: svchost.exe
  - SHA256: f6e5d4c3b2a1...
  - Path: C:\Users\hradmin\AppData\Local\Temp\
- Ransomware binary: update.exe
  - SHA256: 1a2b3c4d5e6f...

**Registry Indicators:**
- HKCU\Software\Microsoft\Windows\CurrentVersion\Run\WindowsUpdate
- Value: C:\Users\hradmin\AppData\Local\Temp\svchost.exe

**Compromised Accounts:**
- hradmin (initial)
- Domain Admin account (escalated)
- 10 additional user accounts
- 2 service accounts

### 7.5 Recommendations

**Immediate Actions:**
1. Reset all compromised credentials
2. Rebuild affected systems from clean backups
3. Block IoCs at firewall/proxy level
4. Implement application whitelisting
5. Enable enhanced logging (PowerShell, process creation)

**Short-term Improvements:**
1. Deploy EDR solution across all endpoints
2. Implement email security training
3. Enable MFA for all accounts
4. Segregate backup systems from production network
5. Deploy deception technology (honeypots)

**Long-term Strategy:**
1. Implement zero-trust architecture
2. Regular purple team exercises
3. Threat hunting program
4. Security awareness program enhancement
5. Incident response plan updates

**Detection Improvements by Kill Chain Stage:**

| Stage | Current Gap | Recommended Control |
|-------|-------------|---------------------|
| Delivery | Email passed filters | Advanced email security with sandboxing |
| Exploitation | Delayed detection | Behavioral analysis, EDR |
| Installation | Registry change undetected | Enhanced registry monitoring |
| C&C | Outbound traffic allowed | DNS filtering, TLS inspection |
| Actions | No exfiltration alert | DLP, network traffic anomaly detection |

---

## Module 8: Advanced Topics

### 8.1 Cloud Intrusion Analysis

Modern attacks increasingly target cloud environments. Key differences:

**Unique Challenges:**
- Shared responsibility model
- Ephemeral resources
- API-based access
- Multi-tenant environments
- Limited network visibility

**Cloud-Specific Artifacts:**
- CloudTrail logs (AWS)
- Azure Activity logs
- Google Cloud Audit logs
- API access logs
- Identity and access management logs
- Container logs

**Cloud ATT&CK Considerations:**
- T1078.004: Valid Accounts (Cloud Accounts)
- T1550: Use Alternate Authentication Material
- T1530: Data from Cloud Storage Object
- T1537: Transfer Data to Cloud Account

**Connection to Main Topic:** Cloud intrusion analysis requires adapting traditional forensic methodologies to distributed, virtualized environments.

### 8.2 Threat Hunting

Proactive searching for threats not detected by automated tools.

**Hypothesis-Driven Hunting:**
1. Form hypothesis based on TTPs
2. Identify data sources needed
3. Query and analyze data
4. Document findings
5. Improve detections

**Hunt Methodologies:**
- **Intelligence-driven:** Based on threat intelligence
- **Situational awareness:** Based on organizational changes
- **Domain expertise:** Based on analyst knowledge
- **ATT&CK-driven:** Systematic coverage of techniques

**Connection to Main Topic:** Threat hunting uses intrusion analysis skills proactively to find compromises before major incidents occur.

### 8.3 Adversary Emulation

Testing defenses by simulating attacker behaviors.

**Purpose:**
- Validate detection capabilities
- Identify gaps in visibility
- Train incident responders
- Improve threat models

**Frameworks:**
- MITRE Caldera (automated)
- Atomic Red Team (technique testing)
- Purple team exercises

**Connection to Main Topic:** Understanding how attacks work through emulation improves intrusion analysis skills.

### 8.4 Machine Learning in Intrusion Analysis

AI/ML applications in forensics:

**Use Cases:**
- Anomaly detection in large datasets
- Malware classification
- Behavioral analysis
- Timeline optimization
- Pattern recognition

**Limitations:**
- Requires quality training data
- Can produce false positives
- Not a replacement for human analysis
- Explainability challenges

### 8.5 Legal and Ethical Considerations

**Chain of Custody:**
- Document every evidence transfer
- Maintain integrity through hashing
- Store securely with access logs
- Prepare for testimony

**Privacy Concerns:**
- Minimize collection of personal data
- Follow organizational policies
- Understand regulatory requirements (GDPR, HIPAA)
- Protect sensitive information in reports

**Ethical Guidelines:**
- Report findings objectively
- Don't exceed authorization
- Maintain professional integrity
- Consider impact on individuals

**Connection to Main Topic:** Legal and ethical compliance ensures intrusion analysis results are usable in all contexts.

---

## Module 9: Building an Intrusion Analysis Program

### 9.1 Skills Development

**Core Competencies for Intrusion Analysts:**

**Technical Skills:**
- Operating system internals (Windows, Linux, macOS)
- Network protocols and analysis
- Malware analysis fundamentals
- Scripting/programming (Python, PowerShell, Bash)
- Digital forensics tools proficiency
- Log analysis and SIEM usage

**Analytical Skills:**
- Critical thinking
- Pattern recognition
- Attention to detail
- Problem-solving
- Hypothesis testing

**Communication Skills:**
- Technical writing
- Executive presentation
- Visualization
- Collaboration

**Continuous Learning:**
- Follow threat intelligence blogs
- Participate in CTFs and challenges
- Attend conferences (SANS DFIR Summit, Black Hat, RSA)
- Obtain certifications (GCFA, GCFE, GNFA, OSCP)

### 9.2 Building Detection Capabilities

**Detection Engineering Process:**

1. **Understand attack technique** using ATT&CK
2. **Identify telemetry sources** needed
3. **Develop detection logic** (rules, queries)
4. **Test detection** using emulation
5. **Tune for false positives**
6. **Document and maintain**

**Detection Maturity:**
- Level 1: Signature-based (IoCs)
- Level 2: Behavioral (TTPs)
- Level 3: Analytics (anomalies)
- Level 4: Intelligence (contextual)

### 9.3 Incident Response Integration

**IR Lifecycle:**
1. **Preparation** - Plans, tools, training
2. **Detection & Analysis** - Where intrusion analysis begins
3. **Containment** - Informed by analysis findings
4. **Eradication** - Guided by scope assessment
5. **Recovery** - Based on impact analysis
6. **Lessons Learned** - Documented in analysis reports

**Connection to Main Topic:** Intrusion analysis is the technical foundation of effective incident response.

### 9.4 Metrics and KPIs

**Measuring Analysis Effectiveness:**

**Time Metrics:**
- Time to detect
- Time to analyze
- Time to contain
- Dwell time reduction

**Quality Metrics:**
- Detection accuracy (true/false positives)
- Scope assessment completeness
- Report quality scores
- Recommendation implementation rate

**Operational Metrics:**
- Cases analyzed per month
- Average case complexity
- Tool utilization
- Analyst training hours

---

## Course Summary

### Key Takeaways

**Core Concepts:**
1. **Intrusion analysis** is the systematic examination of digital evidence to understand attacker activities
2. **Kill Chain** provides a strategic framework for understanding attack progression
3. **MITRE ATT&CK** offers detailed tactical and technical categorization of adversary behaviors
4. **Timeline analysis** is fundamental to reconstructing attack sequences
5. **Proper documentation** ensures findings are actionable and defensible

**Framework Application:**
- Use Kill Chain for high-level attack narrative and communication
- Use ATT&CK for detailed technical analysis and detection engineering
- Combine both frameworks for comprehensive intrusion analysis

**Analysis Process:**
1. Prepare with proper authorization and tools
2. Collect evidence systematically
3. Analyze using structured frameworks
4. Document findings thoroughly
5. Present appropriately to different audiences
6. Provide actionable recommendations

**Success Factors:**
- Technical proficiency with forensic tools
- Understanding of attacker TTPs
- Methodical approach to investigation
- Clear communication skills
- Continuous learning mindset
- Ethical and legal compliance

### Further Learning Paths

**Certifications:**
- GIAC Certified Forensic Analyst (GCFA)
- GIAC Certified Forensic Examiner (GCFE)
- GIAC Network Forensic Analyst (GNFA)
- Certified Information Systems Security Professional (CISSP)
- Certified Computer Examiner (CCE)

**Specialization Areas:**
- Malware reverse engineering
- Memory forensics
- Network forensics
- Cloud forensics
- Mobile device forensics
- Threat intelligence

**Practical Experience:**
- Participate in CTF competitions
- Build home lab environments
- Analyze public malware samples
- Contribute to open-source tools
- Join DFIR community forums
