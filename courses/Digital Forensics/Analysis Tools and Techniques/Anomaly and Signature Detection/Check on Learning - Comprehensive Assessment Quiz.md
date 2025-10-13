### Section A: Multiple Choice Questions

**Question 1:** Which detection method is MOST effective at identifying zero-day exploits?
- A) Signature-based detection
- B) Anomaly-based detection
- C) Hash-based detection
- D) Pattern matching detection

**Question 2:** A forensic investigator notices that a workstation has made DNS queries to 50 different newly-registered domains with random-looking names in the past hour. The baseline for this workstation is 10-15 known domain queries per hour. This is an example of:
- A) Signature-based detection of known malware
- B) Anomaly-based detection of potential C2 communication
- C) False positive from legitimate software updates
- D) Normal behavior requiring no investigation

**Question 3:** What is the PRIMARY limitation of signature-based detection?
- A) High false positive rates
- B) Cannot detect known threats
- C) Cannot detect unknown or novel threats
- D) Requires extensive baseline profiling

**Question 4:** In the context of port scanning detection, which of the following is a signature-based indicator?
- A) A single host attempting connections to significantly more ports than the established baseline
- B) Detecting a specific Nmap TCP SYN scan pattern with characteristic timing
- C) Unusual connection attempts during off-hours
- D) Higher than normal failed connection rate

**Question 5:** Which anomaly detection technique would be MOST appropriate for identifying irregular data exfiltration patterns over time?
- A) Hash comparison
- B) String matching
- C) Time series analysis
- D) Static pattern recognition

**Question 6:** What is the FIRST critical step in implementing anomaly-based detection?
- A) Deploying machine learning algorithms
- B) Establishing a baseline of normal behavior
- C) Creating signature databases
- D) Installing intrusion prevention systems

**Question 7:** A file has a hash value that matches a known malware variant in your threat intelligence database. This is an example of:
- A) Behavioral anomaly
- B) Contextual anomaly
- C) Signature-based detection
- D) Statistical outlier detection

**Question 8:** Which of the following scenarios represents a "contextual anomaly"?
- A) A user accessing 10,000 files at once
- B) Large file downloads during business hours that would be suspicious at midnight
- C) A completely unknown file hash
- D) Multiple failed login attempts followed by successful login

**Question 9:** In a hybrid detection approach, why are both signature and anomaly detection used together?
- A) To reduce the cost of security tools
- B) To meet compliance requirements
- C) To provide comprehensive coverage against both known and unknown threats
- D) To eliminate all false positives

**Question 10:** What is "beaconing" behavior in malware communication?
- A) Broadcasting messages to all network hosts
- B) Regular, periodic communication at fixed intervals with a C2 server
- C) One-time connection to download malicious payload
- D) Random sporadic connections to multiple servers

### Section B: Short Answer Questions

**Question 11:** Explain the difference between a "point anomaly" and a "collective anomaly" in the context of network forensics. Provide an example of each.

**Question 12:** Describe three specific signature indicators you would look for when investigating suspected ransomware on a system.

**Question 13:** A company's network typically transfers 500 GB of data outbound per day. Over a weekend, you observe 5 TB was transferred to an external IP address. Explain how you would investigate this using both anomaly and signature-based approaches.

**Question 14:** Why might polymorphic malware evade signature-based detection? What alternative detection method would be more effective?

**Question 15:** List and briefly describe three evasion techniques attackers use to avoid anomaly detection systems.

### Section C: Practical Scenario Analysis

**Scenario for Questions 16-20:**

You are investigating a potential security incident. You have the following information:

```
Timeline of Events:
- 02:15 AM: User account "jsmith" logs in remotely via VPN
- 02:18 AM: Access to file server \\fileserver01\finance
- 02:20-03:45 AM: 847 files accessed from various departments
- 03:50 AM: 25 GB compressed archive created
- 04:15 AM: Archive transferred to external IP 203.0.113.45 via HTTPS on port 8443
- 04:30 AM: User logs off

Baseline for "jsmith":
- Typical login times: 8:30 AM - 5:30 PM, Monday-Friday
- Average file access: 25-30 files per day
- Typical data transfers: <100 MB per day to approved cloud storage
- No previous after-hours access
- No previous access to finance department files
```

**Question 16:** Identify at least four anomalies in this scenario. For each, explain why it deviates from the baseline.

**Question 17:** What signature-based indicators would you look for to determine if this was compromised credentials versus insider threat?

**Question 18:** If you found that the external IP address 203.0.113.45 appeared in a threat intelligence feed associated with data exfiltration, would this be signature-based or anomaly-based detection? Explain.

**Question 19:** Describe the next three investigative steps you would take to validate this as a confirmed security incident.

**Question 20:** Based on the available information, what type of incident does this most likely represent, and what evidence supports your conclusion?

### Section D: Critical Thinking

**Question 21:** An organization wants to implement detection capabilities but has limited budget and staff. They are debating between focusing exclusively on signature-based or anomaly-based detection. What would you recommend and why? Discuss the trade-offs.

**Question 22:** Explain how machine learning enhances anomaly detection capabilities. What are the potential risks or limitations of relying heavily on ML-based detection systems?

**Question 23:** A skilled attacker aware of your detection capabilities slowly increases their malicious activity over several weeks to shift the baseline and avoid anomaly detection. How would you defend against this technique?