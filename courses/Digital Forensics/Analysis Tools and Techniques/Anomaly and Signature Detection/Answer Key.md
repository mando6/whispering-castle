
### Section A: Multiple Choice

1. **B** - Anomaly-based detection (can identify unknown threats through behavioral deviations)
2. **B** - Anomaly-based detection of potential C2 communication (significant deviation from baseline)
3. **C** - Cannot detect unknown or novel threats (requires existing signatures)
4. **B** - Detecting a specific Nmap TCP SYN scan pattern (known attack signature)
5. **C** - Time series analysis (examines patterns over time)
6. **B** - Establishing a baseline of normal behavior (foundation for anomaly detection)
7. **C** - Signature-based detection (hash matching against known malware)
8. **B** - Large file downloads during business hours that would be suspicious at midnight (context matters)
9. **C** - Comprehensive coverage against both known and unknown threats
10. **B** - Regular, periodic communication at fixed intervals with a C2 server

### Section B: Short Answer (Sample Answers)

**Question 11:**
- **Point Anomaly**: A single data point that is anomalous. Example: A single user account attempting 500 failed logins in one minute.
- **Collective Anomaly**: A collection of data points that together form an anomaly. Example: A series of small, incremental privilege escalations over several days that individually seem normal but collectively indicate an attack progression.

**Question 12:**
Three signature indicators for ransomware:
1. **File hash matches**: Known ransomware family hash in threat database
2. **Registry modifications**: Creation of specific registry keys (e.g., encryption key storage locations)
3. **File extension changes**: Mass renaming of files with specific extensions (.encrypted, .locked, .wncry)
4. (Bonus) Ransom note file signatures, specific mutex names, or known C2 domains

**Question 13:**
- **Anomaly approach**: The 5 TB transfer is 10x normal daily volume and occurred during weekend (outside baseline). Investigate source systems, user accounts, destination IP, and timing patterns.
- **Signature approach**: Check if destination IP is in threat intelligence feeds, examine packet payloads for known exfiltration tool signatures, analyze DNS queries for known C2 domains, check for known data staging techniques.
- **Combined**: Correlate the anomalous volume with any signature matches to confirm malicious intent and identify attack tools used.

**Question 14:**
Polymorphic malware constantly changes its code/signature to avoid hash-based detection. Each instance has a different signature even though functionality remains the same. **Anomaly-based behavioral detection** would be more effective because it focuses on what the malware does (behavioral patterns) rather than what it looks like (static signatures).

**Question 15:**
Three evasion techniques:
1. **Slow and low attacks**: Spreading malicious activity over extended periods to blend with normal behavior and avoid threshold triggers
2. **Mimicking legitimate behavior**: Making malicious traffic appear similar to normal business operations
3. **Baseline poisoning**: Gradually introducing malicious activity during baseline establishment to make it part of "normal" behavior

### Section C: Practical Scenario Analysis (Sample Answers)

**Question 16:**
Four anomalies:
1. **Time anomaly**: Login at 02:15 AM vs. baseline of 8:30 AM-5:30 PM
2. **Volume anomaly**: 847 files accessed vs. baseline of 25-30 files per day
3. **Access anomaly**: Accessing finance department files with no previous access history
4. **Data transfer anomaly**: 25 GB transfer vs. baseline <100 MB per day
5. (Bonus) **Destination anomaly**: Transfer to unknown external IP on non-standard port vs. approved cloud storage

**Question 17:**
Signature indicators to investigate:
- Check authentication logs for: multiple failed attempts before success (brute force signature), impossible travel (login from geographic locations user couldn't reach), use of known credential stuffing tools
- Examine endpoint for: keylogger signatures, credential dumping tool artifacts (Mimikatz), persistence mechanisms
- Review network traffic for: known C2 communication patterns, malware hash signatures on the endpoint
- Check threat intelligence: Is the external IP associated with known threat actors?

**Question 18:**
This would be **signature-based detection**. The external IP appearing in a threat intelligence feed represents a known indicator of compromise (IOC) - a signature of malicious infrastructure. However, the unusual volume and timing that led you to investigate the IP would be anomaly-based detection. This demonstrates how both methods work together in real investigations.

**Question 19:**
Next three investigative steps:
1. **Preserve evidence**: Create forensic images of jsmith's workstation, capture memory dump, preserve relevant logs before they rotate
2. **Validate account compromise**: Interview user jsmith to confirm they did not perform these actions; check for signs of credential theft on their systems
3. **Scope the incident**: Check logs for other potentially compromised accounts, identify all affected systems, determine if data was successfully exfiltrated and what data was taken

**Question 20:**
This most likely represents **data exfiltration via compromised credentials** or **insider threat**. 

Supporting evidence:
- Successful authentication with valid credentials (either stolen or malicious insider)
- Systematic access to sensitive data outside normal working hours
- Creation of compressed archive (common data staging technique)
- Transfer to external IP on non-standard port (exfiltration)
- Access to departments outside user's normal scope

The combination of behavioral anomalies suggests either an external attacker using compromised credentials or a malicious insider. Further investigation of the endpoint and user interview would distinguish between these scenarios.

### Section D: Critical Thinking (Sample Framework Answers)

**Question 21:**
**Recommendation**: Implement signature-based detection first, then gradually add anomaly capabilities.

**Reasoning**:
- Signature-based detection provides immediate value with fewer resources (lower false positives, easier to manage)
- Can leverage community threat intelligence feeds (many free options available)
- Provides foundation for demonstrating security value to stakeholders
- As program matures, add anomaly detection for comprehensive coverage

**Trade-offs**:
- Initial gap in zero-day protection
- May miss sophisticated attacks in early stages
- Need to balance quick wins with long-term comprehensive strategy

**Question 22:**
**How ML enhances anomaly detection**:
- Processes massive datasets to identify subtle patterns humans would miss
- Adapts to evolving baselines automatically
- Handles high-dimensional data with complex relationships
- Can identify multivariate anomalies across multiple features simultaneously

**Risks and limitations**:
- "Black box" problem: Difficult to explain why ML flagged something
- Training data bias can lead to systematic blind spots
- Adversarial ML: Attackers can manipulate inputs to evade detection
- Requires significant computational resources and expertise
- False confidence: May miss attacks that weren't in training data
- Requires ongoing retraining to remain effective

**Question 23:**
**Defense strategies against baseline shifting**:
1. **Multiple baselines**: Maintain historical baselines from different time periods; compare current behavior against multiple references
2. **Rate of change monitoring**: Alert on significant baseline drift itself, not just threshold violations
3. **Hybrid detection**: Combine with signature detection that isn't baseline-dependent
4. **Peer group analysis**: Compare user/system behavior against peer groups rather than just individual history
5. **Manual baseline review**: Periodic human review of baseline assumptions and anomaly thresholds
6. **External threat intelligence**: Incorporate IOCs from outside sources that aren't influenced by your local baseline