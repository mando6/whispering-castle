### Section 1: Fundamental Concepts (Questions 1-5)

**Question 1:** What is the primary difference between Full Packet Capture and Flow Data?

A) FPC captures only metadata, while Flow Data captures complete packets  
B) FPC captures complete packets including payload, while Flow Data captures aggregated metadata  
C) FPC is cheaper to implement than Flow Data  
D) Flow Data provides more detailed information than FPC

---

**Question 2:** Which of the following is NOT typically included in a NetFlow/IPFIX record?

A) Source and destination IP addresses  
B) Number of packets in the flow  
C) Email message content  
D) Source and destination port numbers

---

**Question 3:** A network security team needs to investigate a suspected data breach from 6 months ago. Which approach would most likely still have data available?

A) Full Packet Capture  
B) Flow Data  
C) Both would have equal availability  
D) Neither would have data that old

---

**Question 4:** What does the "7-tuple" refer to in flow data collection?

A) Seven different collection tools  
B) Seven types of network attacks  
C) Seven packet characteristics that define a unique flow  
D) Seven analysis techniques

---

**Question 5:** Which statement about IPFIX is correct?

A) IPFIX is a proprietary Cisco protocol  
B) IPFIX is the IETF standardization of NetFlow v9  
C) IPFIX captures full packet payloads  
D) IPFIX is incompatible with NetFlow

---

### Section 2: Practical Application (Questions 6-10)

**Question 6:** An investigator needs to extract a malware sample that was downloaded during an incident. Which collection method is required?

A) Flow Data is sufficient  
B) Full Packet Capture is required  
C) Either method would work equally well  
D) Neither method can extract malware samples

---

**Question 7:** Your organization has a 10 Gbps internet connection running at 40% utilization. Approximately how much storage would Full Packet Capture require per day?

A) 4 GB  
B) 400 GB  
C) 4 TB  
D) 40 TB

---

**Question 8:** A security analyst notices unusual traffic patterns indicating potential lateral movement in the network. They have flow data showing connections between internal hosts over several weeks. What can they determine from this flow data alone?

A) Which files were transferred between systems  
B) The exact commands executed by the attacker  
C) Which systems communicated, when, and how much data was transferred  
D) The contents of encrypted communications

---

**Question 9:** Which scenario represents the BEST use case for a hybrid approach (both FPC and Flow Data)?

A) A small business with limited budget monitoring a single office  
B) An enterprise with critical infrastructure requiring both broad visibility and deep investigation capability  
C) A home user protecting their personal network  
D) A research network with no security concerns

---

**Question 10:** Flow data shows a workstation established 15,000 DNS queries to different domains over 24 hours, which is highly unusual. What can an investigator determine from this flow data, and what would require packet capture?

A) Flow data can identify the malicious domain names; packet capture isn't needed  
B) Flow data shows the anomalous pattern; packet capture would reveal the actual DNS responses and payload  
C) Packet capture is required to see DNS traffic; flow data cannot capture it  
D) Neither method can analyze DNS effectively

---

### Section 3: Advanced Understanding (Questions 11-15)

**Question 11:** How does the increasing prevalence of encrypted traffic (TLS 1.3, QUIC) affect the value proposition of FPC versus Flow Data?

A) FPC becomes more valuable because it can decrypt traffic  
B) Flow Data becomes more valuable because it's unaffected by encryption  
C) Both are equally affected and lose all value  
D) FPC maintains value for metadata/behavior analysis; Flow Data's relative value increases but both face challenges

---

**Question 12:** What is "sampling" in the context of flow data, and what is its impact on forensic investigations?

A) Sampling increases the amount of data collected  
B) Sampling means only a subset of packets (e.g., 1 in 100) are used to generate flow records, potentially missing low-volume connections  
C) Sampling is a technique to improve accuracy of flow data  
D) Sampling only applies to packet capture, not flow data

---

**Question 13:** Your incident response team discovers an attacker used DNS tunneling to exfiltrate data. Which collection method would provide the most complete evidence of what data was stolen?

A) NetFlow data showing DNS query counts  
B) IPFIX records with DNS port information  
C) Full Packet Capture with DNS protocol dissection  
D) Any flow data is sufficient for DNS tunneling analysis

---

**Question 14:** Which factor would most likely make Full Packet Capture legally problematic in a corporate environment?

A) The storage costs are too high  
B) FPC captures employee communications and potentially sensitive personal information  
C) Network equipment doesn't support FPC  
D) FPC creates too much data to analyze

---

**Question 15:** An organization wants to detect network reconnaissance activities (port scanning, vulnerability scanning) across their entire enterprise network. Which approach is most practical and effective?

A) Full Packet Capture at every network segment  
B) Flow Data collection with anomaly detection for unusual port access patterns  
C) Manual log review only  
D) Physical network monitoring at each switch
