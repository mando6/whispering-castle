
### Lab 1: Signature Detection Exercise

**Objective**: Create and test file hash signatures

**Materials Needed**: Virtual machine, hash calculation tools

**Steps**:
1. Download sample malware from theZoo or VirusShare (in isolated VM)
2. Calculate MD5, SHA-1, and SHA-256 hashes
3. Create YARA rules for detection
4. Test rules against clean and malicious files
5. Document false positive/negative rates

### Lab 2: Network Anomaly Detection

**Objective**: Identify port scanning through anomaly analysis

**Materials Needed**: Wireshark, Nmap, test network

**Steps**:
1. Capture baseline network traffic (30 minutes normal activity)
2. Calculate normal connection metrics
3. Perform various port scans (SYN, NULL, FIN scans)
4. Analyze captured traffic for anomalies
5. Calculate deviation from baseline
6. Create detection rules based on findings

### Lab 3: Malware Communication Analysis

**Objective**: Detect C2 communication patterns

**Materials Needed**: Malware-traffic-analysis.net PCAPs

**Steps**:
1. Download sample PCAP with known malware traffic
2. Establish baseline of normal traffic patterns
3. Identify beaconing behavior
4. Extract IOCs (IPs, domains, ports)
5. Create both signature and anomaly-based detection rules
6. Test rules against clean and malicious PCAPs

### Lab 4: Log Analysis with SIEM

**Objective**: Configure detection rules in Splunk/ELK

**Materials Needed**: SIEM platform, sample logs

**Steps**:
1. Ingest authentication logs
2. Create baseline for normal login patterns
3. Configure signature detection for known attack patterns
4. Create anomaly detection for unusual login behavior
5. Generate test alerts
6. Tune thresholds to reduce false positives