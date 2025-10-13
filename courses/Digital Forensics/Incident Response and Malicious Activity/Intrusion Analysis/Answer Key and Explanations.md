**Question 1: C**  
Intrusion analysis fundamentally seeks to determine who conducted the attack, how they accomplished it, and the full scope of the compromise (what systems/data were affected).

**Question 2: B**  
TTPs describe behavioral patterns and methods (more resilient to change), while IoCs are specific observable artifacts like hashes, IPs, or domains (easier for attackers to change).

**Question 3: B**  
Dwell time is the critical metric representing how long an attacker remained undetected in the environment from initial compromise to detection.

**Question 4: A**  
The correct Kill Chain order is: Reconnaissance → Weaponization → Delivery → Exploitation → Installation → Command and Control → Actions on Objectives. The question includes stages 5, 3, 1, 4, 2.

**Question 5: B**  
Weaponization is when attackers create the malicious payload, typically occurring in their own infrastructure before targeting the victim.

**Question 6: B**  
Registry persistence is the Installation stage, and C2 communication is the Command and Control stage.

**Question 7: B**  
In ATT&CK, tactics represent the adversary's goal (the "why"), techniques are methods to achieve that goal (the "how"), and procedures are specific implementations by particular threat actors.

**Question 8: B**  
Executing PowerShell is the Execution tactic (T1059.001), and dumping credentials from LSASS is Credential Access (T1003).

**Question 9: B**  
Lateral Movement (TA0008) specifically describes techniques for moving between systems within a compromised network.

**Question 10: A**  
T1003 is OS Credential Dumping, one of the most common techniques in intrusions.

**Question 11: B**  
MITRE ATT&CK provides much more granular, technique-specific detail with hundreds of techniques and sub-techniques, while Kill Chain provides a higher-level 7-stage framework.

**Question 12: B**  
Memory (RAM) is volatile and lost when power is removed, so it must be collected first. Follow the order of volatility.

**Question 13: B**  
MACB represents Modified, Accessed, Changed (metadata), and Born (created) timestamps.

**Question 14: C**  
Regular, periodic connections to an external IP suggest C2 beaconing, where malware checks in with its controller at consistent intervals.

**Question 15: B**  
Event ID 4624 indicates a successful logon, while 4625 is failed logon, 4688 is process creation, and 4720 is user account created.

**Question 16: C**  
Unexplained gaps in security logs often indicate log deletion, a common defense evasion technique (T1070).

**Question 17: B**  
Dwell time is from initial compromise (Day 1) until detection (Day 8 when ransomware was discovered), but it's really 7 days of undetected access.

**Question 18: B**  
Credential dumping specifically falls under the Credential Access tactic (TA0006).

**Question 19: A**  
Archiving data is Collection (TA0009), and sending it out of the network is Exfiltration (TA0010).

**Question 20: D**  
While early detection is always better, organizations have multiple opportunities at each stage. The best answer is stopping before Actions on Objectives (data exfiltration and ransomware), particularly during the Command and Control stage where monitoring could detect the ongoing compromise.

**Question 21: B**  
A super timeline aggregates all time-stamped events from various sources (file systems, logs, registry, etc.) into a single chronological sequence for comprehensive analysis.

**Question 22: B**  
Attribution is difficult because attackers use false flags, compromised infrastructure, stolen tools, and other techniques to mislead investigators about their true identity.

**Question 23: B**  
AWS CloudTrail provides comprehensive logging of API calls and account activities for forensic analysis.

**Question 24: B**  
Threat hunting is proactive (searching for unknown threats), while intrusion analysis is typically reactive (investigating known or suspected incidents).

**Question 25: D**  
The analysis tool (REPL) is for executing JavaScript code, data analysis, and complex calculations—not for creating presentation materials.

**Question 26: B**  
The Cyber Kill Chain provides a simpler, more narrative-friendly framework for executive communication, while ATT&CK is better for technical details.

**Question 27: B**  
Chain of custody documentation ensures evidence integrity and admissibility by tracking every person who handled it and when.

**Question 28: C**  
Executive summaries should focus on business impact, key findings, and actionable recommendations rather than technical details.

**Question 29: B**  
Volatility is specifically designed for analyzing memory dumps to extract processes, network connections, and other volatile artifacts.

**Question 30: B**  
ATT&CK Navigator is a web application for visualizing and annotating ATT&CK matrices, useful for documenting which techniques were observed in an attack.