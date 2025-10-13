
### Section A: Multiple Choice

**1. What is the primary difference between DoS and DDoS attacks?**
- A) DoS attacks are more sophisticated
- B) DDoS attacks originate from multiple sources
- C) DoS attacks target applications only
- D) DDoS attacks are always volume-based

**2. Which type of attack exploits the TCP three-way handshake?**
- A) UDP Flood
- B) SYN Flood
- C) HTTP Flood
- D) DNS Amplification

**3. What is an amplification factor in DDoS attacks?**
- A) The number of attacking systems
- B) The ratio of response size to request size
- C) The bandwidth increase over time
- D) The number of packets per second

**4. IP spoofing makes source attribution difficult because:**
- A) It encrypts the attack traffic
- B) It forges the source IP address in packets
- C) It uses multiple protocols simultaneously
- D) It randomizes packet timing

**5. Which tool is primarily used for packet-level analysis?**
- A) Splunk
- B) Wireshark
- C) Maltego
- D) Metasploit

**6. What does TTL analysis help forensic investigators determine?**
- A) Attack duration
- B) Potential IP spoofing through hop count
- C) Botnet size
- D) Attack bandwidth

**7. Slowloris is classified as which type of attack?**
- A) Volume-based
- B) Protocol-based
- C) Application layer
- D) Amplification

**8. What is the primary purpose of NetFlow data in DDoS forensics?**
- A) Capturing full packet payloads
- B) Analyzing traffic flow patterns and metadata
- C) Detecting malware signatures
- D) Performing memory forensics

**9. Which element is NOT part of proper evidence preservation?**
- A) Creating cryptographic hashes
- B) Maintaining chain of custody
- C) Modifying timestamps for consistency
- D) Working on copies, not originals

**10. BCP 38 refers to:**
- A) Incident response procedures
- B) Network ingress filtering
- C) Evidence handling standards
- D) Encryption requirements

**11. The Mirai botnet primarily compromised which type of devices?**
- A) Desktop computers
- B) Mobile phones
- C) IoT devices
- D) Web servers

**12. What is the "CIA triad" element primarily affected by DoS attacks?**
- A) Confidentiality
- B) Integrity
- C) Availability
- D) Authentication

**13. DNS amplification attacks exploit:**
- A) Weak passwords
- B) Open recursive DNS servers
- C) Unpatched web servers
- D) Misconfigured firewalls

**14. In forensic analysis, what is a "baseline"?**
- A) The minimum attack threshold
- B) Normal traffic patterns for comparison
- C) The first packet of an attack
- D) Legal evidence requirements

**15. Which layer of the OSI model do SYN floods target?**
- A) Layer 2 (Data Link)
- B) Layer 3 (Network)
- C) Layer 4 (Transport)
- D) Layer 7 (Application)

**16. What is the primary purpose of a scrubbing center?**
- A) Cleaning malware from infected systems
- B) Filtering attack traffic while allowing legitimate traffic
- C) Prosecuting attackers
- D) Storing forensic evidence

**17. Which organization maintains the MITRE ATT&CK framework?**
- A) SANS Institute
- B) NIST
- C) MITRE Corporation
- D) FBI

**18. Geolocation of IP addresses in forensic investigations provides:**
- A) Exact physical addresses
- B) Approximate geographic location
- C) Attacker identity
- D) Attack motivation

**19. What does PCAP stand for?**
- A) Protocol Capture Analysis Program
- B) Packet Capture
- C) Port Connection Access Point
- D) Primary Cybersecurity Assessment Protocol

**20. In DDoS forensics, what is "attribution"?**
- A) Measuring attack bandwidth
- B) Identifying the attacker or attack source
- C) Calculating financial damages
- D) Determining attack duration

---

### Section B: True/False

**21. Application layer attacks typically consume more bandwidth than volume-based attacks.**
- True / False

**22. All DDoS attacks use botnets.**
- True / False

**23. Memcached servers can provide amplification factors over 50,000x.**
- True / False

**24. Chain of custody is only important for criminal cases, not civil litigation.**
- True / False

**25. Protocol-based attacks target vulnerabilities in Layer 3 and Layer 4 of the OSI model.**
- True / False

**26. Forensic investigators should always work on original evidence to ensure accuracy.**
- True / False

**27. The knowledge cutoff date is less relevant for DDoS forensics since attack principles remain constant.**
- True / False

**28. Behavioral analysis in DDoS detection requires establishing baseline normal activity.**
- True / False

**29. IPv6 eliminates most DDoS attack vectors that exist in IPv4.**
- True / False

**30. Threat intelligence sharing can improve proactive defense against DDoS attacks.**
- True / False

---

### Section C: Short Answer

**31. Explain why documenting timestamps in UTC is important for DDoS forensic investigations.**

**32. List three challenges that make source attribution difficult in DDoS attacks.**

**33. Describe the difference between reflection and amplification in DDoS attacks.**

**34. What are two key differences between high-sophistication and low-sophistication DDoS attacks?**

**35. Explain what a "botnet" is and how it relates to DDoS attacks.**

**36. Name three types of log files that would be valuable evidence in a DDoS investigation.**

**37. Why is it important to calculate both technical and business impact in DDoS forensics?**

**38. What is the purpose of creating a forensic timeline in DDoS analysis?**

**39. Describe one way machine learning can be applied to DDoS forensics.**

**40. What is "defense in depth" and how does it relate to DDoS mitigation?**

---

### Section D: Scenario-Based Questions

**41. Scenario:** You discover that during a DDoS attack, your web server logs show thousands of HTTP GET requests from different IP addresses, all requesting the same resource-intensive page every second. The requests have varying User-Agent strings but similar timing patterns.

**Question:** What type of attack is this most likely, and what three forensic steps would you take to investigate the source?

**42. Scenario:** Network monitoring shows a sudden spike in UDP traffic to port 53 (DNS) from multiple external sources. The traffic volume is 100x normal levels, but your DNS server is handling the load. However, a customer reports their website is unreachable.

**Question:** What is likely happening, and how would you investigate to confirm your hypothesis?

**43. Scenario:** During forensic analysis, you find that attack traffic has source IP addresses from over 50 different countries, but all packets have identical TTL values of 64 and arrive with precise timing intervals.

**Question:** What might this indicate about the attack infrastructure, and what additional analysis would you perform?

**44. Scenario:** You need to present forensic findings to company executives who have no technical background. The attack caused 4 hours of downtime and affected 100,000 customers.

**Question:** What are the three most important points you would include in your executive summary?

**45. Scenario:** Legal counsel asks you to preserve evidence from a DDoS attack that occurred 3 days ago. Some logs have already rotated, and one firewall was rebooted during the incident.

**Question:** What immediate steps would you take to preserve remaining evidence, and how would you document gaps in the evidence?