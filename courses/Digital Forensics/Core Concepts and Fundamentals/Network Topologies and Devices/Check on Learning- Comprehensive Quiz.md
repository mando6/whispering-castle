### Section 1: Network Topologies (20 points)

**Question 1:** You are investigating a suspected data exfiltration incident in a corporate network using a hybrid topology (star topology at access layer, mesh at core). What is the PRIMARY advantage of the star topology configuration at the access layer for your forensic investigation?

A) It provides multiple data paths for redundancy  
B) It creates a single collision domain for easy packet capture  
C) It centralizes evidence at the switch level, simplifying port-level isolation and traffic capture  
D) It allows promiscuous mode capture across all network segments

**Question 2:** During a forensic examination, you discover that a legacy industrial control system uses a bus topology. What is the MOST significant forensic limitation of this topology?

A) Difficult to physically access the network cable  
B) Limited logging capabilities and difficulty isolating specific device communications  
C) Too many devices create excessive network traffic  
D) Requires specialized forensic tools not commonly available

**Question 3:** You need to map both physical and logical topologies during an investigation. Which statement BEST describes why both are necessary?

A) Physical topology is only needed for wireless networks  
B) Logical topology shows cable routes while physical topology shows data flow  
C) Physical topology reveals device locations and physical access points, while logical topology shows how data actually travels and where it can be intercepted  
D) Logical topology is only relevant for cloud-based infrastructure

**Question 4:** In a mesh topology network, you're investigating possible lateral movement by an attacker. What is the PRIMARY forensic challenge this topology presents?

A) Lack of centralized logging  
B) Multiple data paths complicate traffic reconstruction and require analyzing multiple evidence sources  
C) Inability to capture network traffic  
D) No redundancy for evidence preservation

**Question 5:** An organization's DMZ uses a dedicated topology with dual firewalls. From a forensic perspective, what is the PRIMARY benefit of this configuration?

A) Faster network performance  
B) Reduced hardware costs  
C) Enhanced monitoring and logging at critical network boundaries, with layered evidence sources 
D) Simplified network management

### Section 2: Network Devices (40 points)

**Question 6:** You are examining a switch's MAC address table during an incident investigation. Which of the following forensic insights can you derive from this artifact?

A) Complete packet contents of historical communications  
B) Device locations, port associations, VLAN memberships, and device movement patterns  
C) User authentication credentials  
D) Encrypted traffic contents

**Question 7:** During a data breach investigation, you need to correlate internal private IP addresses with external public IP communications. Which router artifact is MOST critical for this task?

A) Routing table  
B) Access Control Lists (ACLs)  
C) NAT/PAT tables  
D) Interface statistics

**Question 8:** You're investigating unauthorized remote access. The firewall logs show VPN connections with user attribution. What additional firewall artifact would provide the MOST valuable information about what the user did during the session?

A) Firewall rule base configuration  
B) Connection logs showing destination IPs, ports, protocols, bytes transferred, and session duration  
C) Firewall software version  
D) Administrator login history

**Question 9:** An IDS has generated 1,500 alerts during a suspected APT intrusion. What is the MOST important first step in analyzing these alerts from a forensic perspective?

A) Immediately examine every alert in chronological order  
B) Ignore all alerts flagged as low severity  
C) Prioritize high-severity alerts and look for multi-stage attack patterns or lateral movement indicators  
D) Delete false positives to reduce workload

**Question 10:** You need to capture live network traffic from a specific switch port without disrupting operations. Which switch feature should you configure, and what is its primary limitation from a forensic perspective?

A) Port security; it may block legitimate traffic  
B) VLAN tagging; it only works on trunk ports  
C) Port mirroring (SPAN); it may drop packets under high traffic load  
D) MAC flooding; it crashes the switch

**Question 11:** During an investigation, you discover that a router's NetFlow data is configured to export to a collector every 5 minutes. What type of forensic information does NetFlow provide, and what is its primary limitation?

A) Full packet captures; limited storage duration  
B) Summarized connection records (5-tuple metadata); lacks packet payload contents  
C) Only DNS queries; doesn't capture other protocols  
D) Complete application-layer data; excessive processing overhead

**Question 12:** You're investigating a potential VLAN hopping attack. Which switch artifacts would be MOST relevant to your investigation?

A) Power supply logs and temperature sensors  
B) VLAN configuration, trunk port settings, and port security violation logs  
C) CPU utilization statistics  
D) SNMP community strings

**Question 13:** A next-generation firewall (NGFW) detected and blocked a potential command-and-control (C2) communication. Which forensic artifacts from the NGFW would provide the MOST comprehensive evidence?

A) Only the block decision and timestamp  
B) Alert log with threat classification, packet captures of the attempted connection, and threat intelligence correlation  
C) Firewall throughput statistics  
D) License expiration date

**Question 14:** You're investigating an insider threat case where an employee allegedly accessed unauthorized file servers. The firewall has user identity integration with Active Directory. Why is this capability particularly valuable for your investigation?

A) It encrypts all network traffic  
B) It provides direct attribution of network activity to specific user accounts, strengthening evidence  
C) It automatically blocks suspicious users  
D) It increases network performance

**Question 15:** During incident response, you need to determine if an attack was successful or blocked. Which device type would typically provide the MOST definitive evidence of whether malicious traffic reached the target?

A) Hub activity logs  
B) IPS logs showing inline blocking actions and session termination  
C) Unmanaged switch  
D) Repeater status

### Section 3: Integration and Investigation Planning (20 points)

**Question 16:** You're planning evidence collection after a ransomware incident. What is the correct order of priority for collecting network device evidence, considering volatility?

A) Archived logs → Configuration files → Active connections → Switch MAC tables  
B) Configuration files → Archived logs → Switch MAC tables → Active connections  
C) Active connections and NAT tables → Time-sensitive logs → Configuration snapshots → Archived logs  
D) Archived logs only, as they contain all necessary information

**Question 17:** You're investigating suspected data exfiltration where firewall logs show a large outbound data transfer. Which additional device evidence would BEST help you identify the source device and confirm the activity?

A) Router NetFlow data for connection details, switch MAC/port logs for device location, and DHCP logs for IP-to-device mapping  
B) Only firewall logs are sufficient  
C) Physical security camera footage  
D) Email server logs

**Question 18:** During an investigation, you need to understand lateral movement after initial compromise. Which combination of device logs would provide the MOST complete picture?

A) Only firewall logs  
B) IDS/IPS alerts for exploitation, switch logs for port-to-port traffic patterns, and router ACLs for cross-segment access  
C) DNS logs exclusively  
D) Web proxy logs only

**Question 19:** You're documenting the chain of evidence for network device logs. Which practice is MOST critical for maintaining evidence integrity?

A) Printing all logs immediately  
B) Hashing configuration files, documenting topology, preserving timestamps, and photographing physical connections  
C) Deleting redundant logs to save space  
D) Only collecting data from the newest devices

### Section 4: Applied Scenarios 

**Question 20 (10 points - Short Answer):** You're investigating a multi-stage attack where the attacker gained initial access via a phishing email, moved laterally to a file server, and exfiltrated sensitive data over several days. Describe the specific network device artifacts you would collect from at least THREE different device types and explain how each artifact contributes to reconstructing the attack timeline and identifying the attacker's actions. Your answer should demonstrate understanding of how different devices provide complementary evidence.

**Question 21 (10 points - Short Answer):** A suspected insider threat involves an employee who allegedly accessed confidential files outside of business hours and transferred them to an external cloud storage service. The organization has the following infrastructure: managed switches, routers with NetFlow, NGFWs with user identity integration, and IPS at the perimeter. Design a forensic investigation plan that identifies: (a) which devices you would target for evidence, (b) what specific artifacts you would collect from each device, and (c) how you would correlate evidence across devices to prove or disprove the allegation.
