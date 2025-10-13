### Part 1: Fundamental Concepts (Questions 1-5)

**Question 1:** What are the three primary questions intrusion analysis seeks to answer during an investigation?

A) Who, What, and Where  
B) How, Why, and When  
C) Who attacked, how they did it, and what was the scope of compromise  
D) What malware was used, when was it deployed, and how much data was stolen  

**Question 2:** What is the key difference between Indicators of Compromise (IoCs) and Tactics, Techniques, and Procedures (TTPs)?

A) IoCs are more valuable than TTPs  
B) TTPs describe behavior patterns while IoCs are specific observable artifacts  
C) IoCs never change but TTPs change frequently  
D) TTPs are only used in malware analysis  

**Question 3:** In the context of intrusion analysis, what does "dwell time" refer to?

A) The time it takes to analyze an incident  
B) The time between initial compromise and detection  
C) The time spent by the analyst on the case  
D) The time malware remains dormant before executing  

---

### Part 2: Cyber Kill Chain (Questions 6-10)

**Question 4:** Place the following Cyber Kill Chain stages in the correct order:

1. Exploitation  
2. Command and Control  
3. Delivery  
4. Installation  
5. Reconnaissance  

A) 5, 3, 1, 4, 2  
B) 3, 1, 5, 4, 2  
C) 5, 1, 3, 4, 2  
D) 1, 3, 5, 2, 4  

**Question 5:** Which Kill Chain stage typically occurs off the target network and involves the attacker creating a malicious payload?

A) Reconnaissance  
B) Weaponization  
C) Delivery  
D) Exploitation  

**Question 6:** An analyst discovers that an attacker established persistence via a registry Run key and is communicating with an external C2 server. Which two Kill Chain stages are represented?

A) Delivery and Exploitation  
B) Installation and Command and Control  
C) Exploitation and Installation  
D) Command and Control and Actions on Objectives  

---

### Part 3: MITRE ATT&CK Framework (Questions 11-15)

**Question 7:** In the MITRE ATT&CK framework, what is the hierarchical relationship between tactics, techniques, and procedures?

A) Procedures contain tactics which contain techniques  
B) Tactics are the "why," techniques are the "how," and procedures are specific implementations  
C) Techniques are the highest level, followed by tactics and procedures  
D) All three terms are synonymous  

**Question 8:** An attacker uses PowerShell to execute a script that dumps credentials from LSASS memory. Which two ATT&CK tactics does this activity represent?

A) Initial Access and Execution  
B) Execution and Credential Access  
C) Persistence and Privilege Escalation  
D) Defense Evasion and Collection  

**Question 9:** Which ATT&CK tactic focuses on techniques attackers use to move from one system to another within a compromised network?

A) Discovery  
B) Lateral Movement  
C) Collection  
D) Command and Control  

**Question 10:** What is the ATT&CK technique ID for "OS Credential Dumping"?

A) T1003  
B) T1078  
C) T1059  
D) T1021  

**Question 11:** Which framework provides more granular, technique-specific detail: Kill Chain or MITRE ATT&CK?

A) Cyber Kill Chain  
B) MITRE ATT&CK  
C) They provide equal levels of detail  
D) Neither framework provides technique-level detail  

---

### Part 4: Analysis Methodology (Questions 16-20)

**Question 12:** When collecting digital evidence, which type of data should be collected FIRST due to its volatile nature?

A) Hard drive images  
B) System memory (RAM)  
C) Registry hives  
D) Event logs  

**Question 13:** What does MACB stand for in file system timestamp analysis?

A) Modified, Accessed, Created, Born  
B) Modified, Accessed, Changed, Born  
C) Metadata, Access, Creation, Backup  
D) Malware, Analysis, Collection, Baseline  

**Question 14:** An analyst notices network traffic from an internal host to an external IP on port 443 every 60 seconds. What type of activity does this regular pattern suggest?

A) Normal web browsing  
B) DNS tunneling  
C) C2 beaconing  
D) Port scanning  

**Question 15:** Which Windows Event ID indicates a successful user logon?

A) 4625  
B) 4624  
C) 4688  
D) 4720  

**Question 16:** When analyzing logs, what should an analyst suspect if there are unexplained time gaps in security event logs?

A) System was offline  
B) Normal log rotation  
C) Possible log deletion by attacker  
D) Timezone issues  

---

### Part 5: Case Study Application (Questions 21-25)

**Scenario for Questions 17-20:**
An organization detects ransomware on their network. Investigation reveals:
- Day 1: Phishing email received with malicious attachment
- Day 1: User opened attachment, malware executed
- Day 2: Attacker dumped credentials from memory
- Day 5: Attacker moved laterally to file server
- Day 7: Data archived and exfiltrated to cloud storage
- Day 8: Ransomware deployed

**Question 17:** What was the dwell time in this attack?

A) 1 day  
B) 7 days  
C) 8 days  
D) 2 days  

**Question 18:** Which ATT&CK tactic does "dumped credentials from memory" represent?

A) Privilege Escalation  
B) Credential Access  
C) Discovery  
D) Defense Evasion  

**Question 19:** The activity on Day 7 (data archived and exfiltrated) maps to which two ATT&CK tactics?

A) Collection and Exfiltration  
B) Command and Control and Impact  
C) Discovery and Collection  
D) Exfiltration and Impact  

**Question 20:** At which Kill Chain stage should the organization have had the best opportunity to detect and stop this attack before significant damage?

A) Delivery (Day 1)  
B) Installation (Day 1)  
C) Command and Control (Day 1-8)  
D) Any stage before Actions on Objectives  

---

### Part 6: Advanced Concepts (Questions 26-30)

**Question 21:** What is the primary purpose of creating a super timeline during intrusion analysis?

A) To create fancy visualizations for executives  
B) To aggregate time-stamped events from multiple sources into a single chronological view  
C) To identify the newest files on the system  
D) To measure how long the investigation took  

**Question 22:** Why is attribution (identifying who conducted an attack) considered extremely difficult in intrusion analysis?

A) Attackers always use encryption  
B) False flags, proxy infrastructure, and stolen tools can mislead analysts  
C) There are no technical indicators available  
D) Attribution is actually easy with the right tools  

**Question 23:** In cloud environment forensics, what AWS service provides audit logs of API calls and account activity?

A) CloudWatch  
B) CloudTrail  
C) S3 Logs  
D) VPC Flow Logs  

**Question 24:** What is the primary difference between threat hunting and traditional intrusion analysis?

A) Threat hunting is reactive while intrusion analysis is proactive  
B) Threat hunting is proactive searching for threats while intrusion analysis typically responds to known incidents  
C) There is no difference  
D) Threat hunting only uses automated tools  

**Question 25:** Which of the following is NOT a valid reason to use the analysis tool (REPL) during an investigation?

A) Processing a large CSV file with thousands of rows  
B) Performing complex mathematical calculations  
C) Reading and parsing uploaded forensic artifacts  
D) Creating a presentation slide deck  

---

### Part 7: Documentation and Reporting (Questions 31-35)

**Question 26:** When presenting intrusion analysis findings to executive leadership, which framework typically provides a better high-level narrative?

A) MITRE ATT&CK  
B) Cyber Kill Chain  
C) ISO 27001  
D) NIST CSF  

**Question 27:** What is the purpose of maintaining a chain of custody during a digital forensic investigation?

A) To track who analyzed the evidence  
B) To document every person who handled evidence and ensure its integrity  
C) To calculate investigation costs  
D) To create a timeline of events  

**Question 28:** In an intrusion analysis report, what should the Executive Summary emphasize?

A) Detailed technical ATT&CK mappings  
B) Complete IoC lists  
C) Business impact, key findings, and critical recommendations  
D) All forensic tool outputs  

---

### Part 8: Tools and Resources (Questions 36-38)

**Question 29:** Which tool is specifically designed for memory forensics analysis?

A) Autopsy  
B) Volatility  
C) Wireshark  
D) FTK Imager  

**Question 30:** What is the purpose of the ATT&CK Navigator tool?

A) To perform network scans  
B) To visualize and annotate ATT&CK techniques used in an attack  
C) To create malware  
D) To encrypt sensitive data  