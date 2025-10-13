### Part 1: Foundational Concepts (Multiple Choice)

**Question 1:** What is the primary purpose of establishing a network traffic baseline?
- A) To maximize network bandwidth utilization
- B) To provide a reference point for identifying abnormal network behavior
- C) To comply with industry regulations
- D) To reduce network latency

<details>
<summary>Answer</summary>
<strong>B) To provide a reference point for identifying abnormal network behavior</strong>

Explanation: While baselines may support compliance and optimization efforts, their primary purpose in digital forensics is establishing normal behavior patterns that enable identification of anomalies and potential security incidents.
</details>

---

**Question 2:** What is the minimum recommended time period for establishing an initial network traffic baseline?
- A) 24 hours
- B) One week
- C) 2-4 weeks
- D) One year

<details>
<summary>Answer</summary>
<strong>C) 2-4 weeks</strong>

Explanation: A minimum of 2-4 weeks captures weekday/weekend variations and begins to show patterns, though 90 days is recommended for capturing more complete business cycles.
</details>

---

**Question 3:** Which of the following is NOT typically a component of a network traffic baseline?
- A) Protocol distribution
- B) Source code of applications
- C) Traffic volume metrics
- D) Endpoint communication patterns

<details>
<summary>Answer</summary>
<strong>B) Source code of applications</strong>

Explanation: Baselines focus on observable network behavior metrics, not application internals. Source code analysis is a separate security activity.
</details>

---

**Question 4:** What does "beaconing behavior" typically indicate?
- A) Normal DNS queries
- B) Regular backup operations
- C) Potential command-and-control (C2) communications
- D) Standard web browsing activity

<details>
<summary>Answer</summary>
<strong>C) Potential command-and-control (C2) communications</strong>

Explanation: Beaconing refers to regular, periodic connections often used by malware to communicate with C2 servers, representing a deviation from normal baseline patterns.
</details>

---

**Question 5:** In statistical baseline analysis, what does a deviation of >3 standard deviations (σ) from the mean typically represent?
- A) Normal variation
- B) A statistically significant anomaly
- C) Network optimization opportunity
- D) Required threshold for investigation

<details>
<summary>Answer</summary>
<strong>B) A statistically significant anomaly</strong>

Explanation: Values beyond 3σ from the mean are considered statistically unusual (occurring less than 0.3% of the time in normal distributions) and warrant investigation.
</details>

---

### Part 2: Technical Application (Multiple Choice)

**Question 6:** Which tool is specifically designed for high-performance NetFlow analysis and long-term storage?
- A) Wireshark
- B) SiLK (System for Internet-Level Knowledge)
- C) Nmap
- D) Metasploit

<details>
<summary>Answer</summary>
<strong>B) SiLK (System for Internet-Level Knowledge)</strong>

Explanation: SiLK is purpose-built for efficient storage and analysis of flow data at scale, making it ideal for baseline establishment and historical analysis.
</details>

---

**Question 7:** What is the primary advantage of NetFlow data over full packet capture (PCAP) for baseline analysis?
- A) More detailed payload information
- B) Lower storage requirements while capturing connection metadata
- C) Better protocol decoding capabilities
- D) Real-time alerting features

<details>
<summary>Answer</summary>
<strong>B) Lower storage requirements while capturing connection metadata</strong>

Explanation: NetFlow captures metadata about connections (who talked to whom, when, how much) without storing payloads, dramatically reducing storage needs while providing sufficient data for baseline analysis.
</details>

---

**Question 8:** In the context of baseline analysis, what does "lateral movement" refer to?
- A) Normal user authentication to domain controllers
- B) Movement of data between cloud storage services
- C) Attackers spreading between systems within a network
- D) Load balancing across multiple servers

<details>
<summary>Answer</summary>
<strong>C) Attackers spreading between systems within a network</strong>

Explanation: Lateral movement describes adversary behavior of moving from one compromised system to others, often visible as unusual workstation-to-workstation traffic that deviates from baseline patterns.
</details>

---

**Question 9:** Which machine learning approach is best suited for identifying previously unknown attack patterns?
- A) Supervised learning with labeled malicious data
- B) Unsupervised anomaly detection
- C) Reinforcement learning
- D) Transfer learning

<details>
<summary>Answer</summary>
<strong>B) Unsupervised anomaly detection</strong>

Explanation: Unsupervised methods like Isolation Forest or autoencoders learn normal behavior patterns and flag deviations without requiring prior knowledge of specific attacks, making them effective for zero-day detection.
</details>

---

**Question 10:** How often should network traffic baselines be updated in a typical enterprise environment?
- A) Never, once established they remain constant
- B) Only when security incidents occur
- C) Regularly (monthly adjustments, quarterly reviews, annual major updates)
- D) Every 24 hours

<details>
<summary>Answer</summary>
<strong>C) Regularly (monthly adjustments, quarterly reviews, annual major updates)</strong>

Explanation: Networks evolve with business changes; baselines require regular updates to remain accurate. Minor monthly adjustments, quarterly reviews for seasonal changes, and annual major refreshes are recommended.
</details>

---

### Part 3: Scenario-Based Questions

**Question 11:** You observe that a database server typically sends 10GB outbound per day, but on a Sunday night it transferred 180GB to an IP address in a country your organization doesn't do business with. What type of anomaly is this, and what attack might it indicate?

- A) Protocol anomaly; indicates port scanning
- B) Volume and geographic anomaly; indicates potential data exfiltration
- C) Temporal anomaly only; indicates scheduled maintenance
- D) Behavioral anomaly; indicates normal backup operation

<details>
<summary>Answer</summary>
<strong>B) Volume and geographic anomaly; indicates potential data exfiltration</strong>

Explanation: This scenario presents multiple red flags: 18× normal volume, unusual timing (weekend), and unexpected geographic destination—all classic indicators of data exfiltration that deviate significantly from the baseline.
</details>

---

**Question 12:** During baseline analysis, you notice HTTP traffic on port 8080 between workstations and a server. Previously, all HTTP traffic used port 80. What should be your first investigative step?

- A) Immediately block port 8080 traffic
- B) Verify if a new legitimate application or service was deployed
- C) Ignore it as port numbers don't matter for HTTP
- D) Report it as confirmed malicious activity

<details>
<summary>Answer</summary>
<strong>B) Verify if a new legitimate application or service was deployed</strong>

Explanation: While non-standard ports can indicate malicious activity (proxy evasion, C2 communications), they may also result from legitimate business changes. Investigation should confirm whether this is authorized before taking action.
</details>

---

**Question 13:** You're establishing a baseline for a hospital network. Which consideration is MOST critical for this specific environment?

- A) High gaming traffic during night shifts
- B) 24/7 operational requirements with less predictable "off-hours"
- C) Minimal use of medical devices on the network
- D) Standard 9-to-5 business hour patterns

<details>
<summary>Answer</summary>
<strong>B) 24/7 operational requirements with less predictable "off-hours"</strong>

Explanation: Healthcare environments operate continuously with shift work, emergency scenarios, and critical systems that don't follow typical business hours, requiring baselines that account for constant legitimate activity.
</details>

---

**Question 14:** In a forensic investigation, you need to prove that observed traffic was anomalous. What documentation from your baseline would provide the strongest evidence?

- A) Verbal testimony about what's "normally" seen
- B) Statistical analysis showing the behavior is >3σ from documented mean with timestamped baseline data
- C) General industry standards for network traffic
- D) Screenshots of current traffic dashboards

<details>
<summary>Answer</summary>
<strong>B) Statistical analysis showing the behavior is >3σ from documented mean with timestamped baseline data</strong>

Explanation: Forensic evidence requires documented, objective, quantifiable proof. Statistical deviation from a properly documented baseline with chain-of-custody provides legally defensible evidence of anomalous behavior.
</details>

---

**Question 15:** You observe regular connections every 60 minutes from multiple workstations to the same external IP, with each connection lasting exactly 3 seconds and transferring minimal data. What does this pattern most likely indicate?

- A) Normal user web browsing
- B) Scheduled system updates
- C) Beaconing pattern consistent with C2 communications
- D) Cloud service synchronization

<details>
<summary>Answer</summary>
<strong>C) Beaconing pattern consistent with C2 communications</strong>

Explanation: Regular periodic connections at fixed intervals with minimal data transfer from multiple hosts to a single external IP is a classic C2 beaconing pattern—a significant deviation from normal baseline behavior that warrants immediate investigation.
</details>

---

### Part 4: Short Answer Questions

**Question 16:** Explain why understanding temporal patterns (time-based behavior) is important in traffic baseline analysis. Provide two specific examples of legitimate temporal variations you might see in a corporate network.

<details>
<summary>Sample Answer</summary>

Temporal patterns are critical because they help distinguish between normal scheduled/authorized activity and potentially malicious behavior occurring at unusual times. Understanding when activity should occur enables detection of compromise indicators like after-hours data exfiltration or off-schedule system access.

Two examples of legitimate temporal variations:
1. <strong>Business Hours Traffic:</strong> Significantly higher traffic volumes Monday-Friday 8 AM-6 PM due to user activity, with dramatic drops during evenings, nights, and weekends when most users are offline.

2. <strong>Scheduled Maintenance Windows:</strong> Predictable traffic patterns during designated maintenance periods (e.g., Sunday 2-4 AM) including backup operations, system updates, and database maintenance that would be anomalous if occurring at other times.

<em>Grading criteria: Answer should explain the value of temporal analysis and provide two realistic, specific examples with appropriate detail.</em>
</details>

---

**Question 17:** You are creating a baseline for a newly merged network environment that combines two companies' infrastructures. What specific challenges does this present, and how would you address them in your baseline methodology?

<details>
<summary>Sample Answer</summary>

<strong>Challenges:</strong>
- Different security policies and acceptable use standards between organizations
- Duplicate or overlapping IP addressing schemes
- Disparate technology stacks and applications
- Cultural differences in work patterns (different business hours, remote work policies)
- Incomplete visibility during integration phase
- Legitimate inter-company traffic that may appear anomalous initially

<strong>Methodology Approaches:</strong>
1. <strong>Segmented Baselines:</strong> Initially create separate baselines for each legacy network, then gradually merge as integration progresses
2. <strong>Extended Collection Period:</strong> Use longer baseline periods (90+ days) to capture integration changes and stabilization
3. <strong>Collaborative Documentation:</strong> Work with IT teams from both organizations to understand legitimate traffic patterns and business processes
4. <strong>Incremental Integration:</strong> Document each phase of network integration and adjust baselines accordingly
5. <strong>Enhanced Change Management:</strong> Implement rigorous tracking of all infrastructure changes during merger period
6. <strong>Flexible Thresholds:</strong> Use wider statistical thresholds initially, tightening as the merged environment stabilizes

<em>Grading criteria: Answer should identify at least 3 specific challenges and propose practical solutions that demonstrate understanding of baseline principles.</em>
</details>

---

**Question 18:** Describe the difference between NetFlow data and full packet capture (PCAP). In what situations would you prefer one over the other for baseline analysis and forensic investigation?

<details>
<summary>Sample Answer</summary>

<strong>NetFlow Data:</strong>
- Captures metadata about network flows: source/destination IPs, ports, protocols, byte counts, timestamps
- Does NOT capture actual packet payloads or content
- Significantly lower storage requirements (typically 0.5-5% of full capture)
- Provides high-level view of "who talked to whom, when, and how much"
- Suitable for long-term retention and large-scale analysis

<strong>Full Packet Capture (PCAP):</strong>
- Captures complete packets including headers AND payloads
- Enables deep protocol analysis and content inspection
- Very high storage requirements
- Allows reconstruction of sessions and extraction of files
- Provides complete forensic detail

<strong>Usage Preferences:</strong>

<em>Prefer NetFlow for baseline establishment:</em>
- Long-term baseline creation (months/years of data)
- Identifying communication patterns and relationships
- Volume and bandwidth analysis
- Initial anomaly detection across entire network
- Resource-constrained environments

<em>Prefer PCAP for forensic investigation:</em>
- Deep-dive analysis of identified anomalies
- Malware analysis and artifact extraction
- Protocol-level investigation
- Evidence collection requiring payload data
- Reconstructing attacker actions
- Short-term targeted capture around incidents

<em>Best Practice:</em> Use NetFlow for continuous baseline monitoring and initial anomaly detection, then selectively capture PCAP data when investigating specific incidents or suspicious activity.

<em>Grading criteria: Answer should clearly differentiate both technologies, explain their respective strengths, and demonstrate understanding of appropriate use cases for each.</em>
</details>

---

**Question 19:** Why is documentation critical in traffic baseline analysis from a forensic standpoint? List at least four specific elements that must be documented for a baseline to be forensically sound.

<details>
<summary>Sample Answer</summary>

<strong>Importance of Documentation:</strong>
Documentation is critical for several forensic reasons:
- <strong>Legal Admissibility:</strong> Courts require evidence of proper methodology and chain of custody
- <strong>Reproducibility:</strong> Other analysts must be able to verify findings using the same methodology
- <strong>Credibility:</strong> Documented baselines provide objective, defensible proof of normal vs. anomalous behavior
- <strong>Continuity:</strong> Ensures baselines can be maintained and updated consistently over time
- <strong>Expert Testimony:</strong> Detailed documentation supports expert witness testimony in legal proceedings

<strong>Essential Documentation Elements:</strong>

1. <strong>Methodology:</strong> Detailed description of data collection methods, tools used (with version numbers), collection points, sampling rates, and analysis techniques employed

2. <strong>Time Period and Scope:</strong> Exact dates/times of data collection, which network segments were included, what was excluded and why, business context during collection period

3. <strong>Quantitative Metrics:</strong> Statistical measurements including means, standard deviations, percentiles, threshold definitions, with supporting tables and graphs

4. <strong>Chain of Custody:</strong> Who collected data, when, where stored, hash values of data files, access logs, transfer records maintaining evidence integrity

5. <strong>Tool Configurations:</strong> Exact configurations of collection and analysis tools, filters applied, any data transformations performed

6. <strong>Analyst Qualifications:</strong> Credentials and training of personnel who created the baseline

7. <strong>Version Control:</strong> Baseline version number, date created, approval signatures, change history

8. <strong>Assumptions and Limitations:</strong> Known gaps in visibility, assumptions made, acknowledged limitations of the baseline

<em>Grading criteria: Answer should explain WHY documentation matters forensically and list at least 4 specific, appropriate documentation elements.</em>
</details>

---

**Question 20:** You've identified an anomaly: a workstation is communicating with 50 different internal servers over SMB protocol in a 10-minute period, which has never been observed before. Walk through your investigation process using baseline analysis principles. What would you check, and what might this indicate?

<details>
<summary>Sample Answer</summary>

<strong>Investigation Process:</strong>

<strong>Step 1: Baseline Comparison</strong>
- Check baseline for this specific workstation: What is its normal SMB communication pattern?
- Review organizational baseline: Is workstation-to-server SMB common? (Usually limited)
- Check the 50 servers: Do they normally receive SMB connections from workstations?
- Result: Likely confirms this is highly anomalous behavior

<strong>Step 2: Context Gathering</strong>
- Identify the workstation user and their role
- Check authentication logs: Who was logged in during the activity?
- Review change management: Any authorized scans, inventory tools, or administration tasks scheduled?
- Check with IT staff: Was this authorized administrative activity?

<strong>Step 3: Detailed Traffic Analysis</strong>
- Examine specific SMB operations: Was it reading, writing, executing, or enumerating?
- Check for patterns: Sequential server access vs. random? All servers in same subnet?
- Review connection success rate: How many connections succeeded vs. failed?
- Analyze timing: Rapid automated pattern vs. human-paced?
- Check other protocols: Any other anomalous traffic from this workstation?

<strong>Step 4: Correlation</strong>
- Cross-reference with other security data: IDS/IPS alerts, antivirus logs, proxy logs
- Check for prior anomalies from this workstation
- Review the 50 target servers: Any commonality? (All file servers, all domain controllers, etc.)
- Look for subsequent activity: Data transfers, privilege escalation, additional lateral movement

<strong>Step 5: Artifact Collection</strong>
- Extract all relevant NetFlow/PCAP data for preservation
- Collect system logs from the workstation
- Document timeline with references to baseline
- Prepare evidence with proper chain of custody

<strong>What This Likely Indicates:</strong>

<em>Primary Concern - Lateral Movement/Reconnaissance:</em>
- This pattern is consistent with an attacker or malware conducting network reconnaissance
- Rapidly connecting to multiple servers suggests automated scanning for accessible shares
- Common post-compromise activity for attackers mapping the environment
- May precede data theft, ransomware deployment, or further propagation

<em>Attack Techniques Potentially Observed:</em>
- SMB enumeration for accessible shares
- Credential validation across multiple systems
- Searching for sensitive data locations
- Preparing for ransomware deployment across servers

<em>Alternative (Less Likely) Explanations:</em>
- Misconfigured or unauthorized administrative tool
- Legitimate but undocumented IT inventory scan
- User error with poorly configured backup software

<strong>Immediate Actions:</strong>
- Isolate the workstation from the network pending investigation
- Reset credentials for any accounts that authenticated from that workstation
- Monitor the 50 contacted servers for any subsequent anomalies
- Escalate to incident response team

<em>Grading criteria: Answer should demonstrate systematic investigative approach, reference baseline comparisons, describe relevant checks, correctly identify this as likely malicious lateral movement, and recommend appropriate response actions.</em>
</details>
