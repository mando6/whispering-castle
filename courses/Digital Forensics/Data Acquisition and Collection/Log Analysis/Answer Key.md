### Part A: Multiple Choice

1. **B** - To establish timelines and reconstruct events for investigations
2. **C** - 4624
3. **B** - Maintaining forensic soundness and chain of custody
4. **B** - `grep "Failed password" auth.log | grep "192.168.1.100" | wc -l`
5. **C** - Successful request
6. **B** - It enables accurate correlation of events across multiple systems
7. **C** - Normal GET requests for image files
8. **B** - To verify integrity and detect tampering
9. **B** - An attacker moving between systems within a network after initial compromise
10. **C** - Plaso/Log2Timeline
11. **C** - Audit log cleared (potential evidence destruction)
12. **B** - /var/log/auth.log or /var/log/secure
13. **B** - It provides centralized log collection, correlation, and real-time analysis
14. **C** - Page not found
15. **C** - Preserve them untouched and work on copies
16. **B** - Multiple failed login attempts in rapid succession from the same source
17. **B** - Automatically archiving old logs and creating new log files to manage disk space
18. **C** - User passwords
19. **B** - To build a complete picture of an incident by combining evidence from different systems
20. **A** - Get-EventLog or Get-WinEvent

### Part B: Short Answer

**21. UTC Timestamp Normalization

Expected Answer:
Normalizing timestamps to UTC is critical because:
- Different systems may be configured in different time zones
- Daylight Saving Time changes can create ambiguous timestamps
- UTC provides a consistent reference point for correlating events across global systems
- Prevents errors in timeline reconstruction when events appear out of order
- Essential for accurate determination of attack progression and event causation

**22. Three Log Types for Data Breach Investigation**

Expected Answer:
- **Firewall Logs:** Show network connections (source/destination IPs, ports, protocols) to identify unauthorized external connections and potential data exfiltration paths
- **Authentication Logs (Windows Security/Linux auth.log):** Reveal user account activity, failed login attempts, privilege escalation, and can identify compromised credentials
- **Database/Application Logs:** Show what data was accessed, by whom, and when - critical for determining scope of data exposure and identifying specific records compromised

**23. Data Exfiltration Indicators**

Expected Answer:
- Large outbound network transfers, especially to unusual or external IP addresses
- Access to sensitive directories or databases followed by network activity
- Use of file compression tools (zip, tar, rar) before network transfers
- Connections to file-sharing services, cloud storage, or encrypted communication channels
- Unusual outbound traffic during off-hours
- Multiple file read operations (Event ID 4663) on sensitive data

**24. Chain of Custody**

Expected Answer:
Chain of custody is the documented chronological record of who collected, accessed, handled, analyzed, or transferred evidence. It is critical because:
- Ensures evidence admissibility in legal proceedings
- Proves evidence hasn't been tampered with or contaminated
- Establishes accountability for all evidence handling
- Documents the complete history from collection to presentation
- Demonstrates proper procedures were followed throughout investigation

**25. Linux Command-Line Tools**

Expected Answer:
- **grep:** Searches for patterns in text files; essential for finding specific events, IP addresses, or error messages in logs
- **awk:** Extracts and processes specific fields from logs; useful for parsing structured log formats and performing calculations
- **sed:** Stream editor for transforming text; used for extracting portions of log entries or reformatting data
- **sort/uniq:** Sort log entries and identify unique values; useful for finding unique IP addresses, counting occurrences, and identifying anomalies

### Part C: Practical Scenario

**26. Investigation Plan**

Expected Answer should include:

**Step-by-step approach:**
1. **Preserve Evidence:** Create forensic copies of all logs with hash verification
2. **Identify Baseline:** Establish the incident detection time (14:30 UTC) and work backward
3. **Firewall Analysis First:** Identify unusual outbound connections, large data transfers, connections to suspicious IPs
4. **Windows Event Log Analysis:** Look for process creation (4688), file access (4663), logon events (4624), privilege escalation
5. **Web Proxy Analysis:** Identify websites visited, especially suspicious domains or file downloads
6. **Antivirus Log Review:** Check for malware detections, quarantine actions, suspicious behavior alerts
7. **Correlation:** Use usernames, IP addresses, and timestamps to connect events across logs
8. **Timeline Construction:** Create chronological sequence from initial compromise to data exfiltration

**Timeline to construct:**
- Initial compromise/infection time
- Privilege escalation or credential theft
- Reconnaissance and lateral movement
- Access to sensitive data
- Data staging and compression
- Exfiltration events

**27. Attack Analysis**

Expected Answer:

**Attack Vector:** Phishing email with malicious attachment (invoice_Oct.exe)

**Timeline:**
- 13:45:23 - Initial HTTPS connection to malicious domain (likely C2 server)
- 13:45:25 - Proxy shows connection to malicious-domain.com
- 13:47:15 - User executes malicious file (invoice_Oct.exe) from Downloads folder
- 13:47:18 - Antivirus detects suspicious behavior but appears malware executed successfully
- 14:25:10 - Access to confidential documents directory (READ operations)
- 14:30:45 - Large data transfer (2GB) to external IP (data exfiltration)

**Indicators of Compromise:**
- IP address: 203.0.113.50 (external C2 server)
- Domain: malicious-domain.com
- File hash of invoice_Oct.exe (should be calculated)
- File path: C:\Users\jsmith\Downloads\invoice_Oct.exe
- Compromised user account: jsmith

**Data Exfiltration Analysis:**
- Malware accessed C:\Users\jsmith\Documents\Confidential\
- 2GB of data transferred to external IP
- Likely confidential business documents were stolen
- Transfer occurred via encrypted HTTPS connection (harder to detect content)

**Additional Log Sources:**
- Email logs (to identify phishing email source and delivery)
- DNS logs (to identify domain resolution for malicious-domain.com)
- File system access audit logs (complete list of files accessed)
- Network packet captures (if available, for detailed traffic analysis)
- Endpoint Detection and Response (EDR) logs
- Web server logs (if internal servers were accessed)
- Database logs (if databases were compromised)
