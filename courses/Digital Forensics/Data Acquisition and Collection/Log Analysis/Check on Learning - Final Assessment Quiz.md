### Part A: Multiple Choice Questions

**1. What is the primary purpose of log analysis in digital forensics?**
   - A) To improve system performance
   - B) To establish timelines and reconstruct events for investigations
   - C) To reduce storage costs
   - D) To replace antivirus software

**2. Which Windows Event ID indicates a successful user logon?**
   - A) 4625
   - B) 4720
   - C) 4624
   - D) 7045

**3. What is the most important principle when collecting logs for forensic purposes?**
   - A) Speed of collection
   - B) Maintaining forensic soundness and chain of custody
   - C) Deleting unnecessary logs
   - D) Converting all logs to PDF format

**4. Which command would you use to count the number of failed SSH login attempts from a specific IP in a Linux auth.log file?**
   - A) `cat auth.log | count 192.168.1.100`
   - B) `grep "Failed password" auth.log | grep "192.168.1.100" | wc -l`
   - C) `find auth.log -ip 192.168.1.100`
   - D) `search auth.log --failed-logins`

**5. What does the HTTP status code 200 indicate in web server logs?**
   - A) Page not found
   - B) Server error
   - C) Successful request
   - D) Unauthorized access

**6. Why is time synchronization critical in log analysis?**
   - A) It makes logs easier to read
   - B) It enables accurate correlation of events across multiple systems
   - C) It reduces file sizes
   - D) It prevents malware infections

**7. Which of the following is NOT a common indicator of a SQL injection attempt in web logs?**
   - A) Presence of UNION SELECT statements in URLs
   - B) Single quotes (') followed by OR clauses
   - C) Normal GET requests for image files
   - D) Double dashes (--) in query parameters

**8. What is the purpose of creating cryptographic hashes (MD5/SHA256) during log collection?**
   - A) To compress the log files
   - B) To verify integrity and detect tampering
   - C) To encrypt sensitive information
   - D) To speed up analysis

**9. In a forensic investigation, what does "lateral movement" typically refer to?**
   - A) Physical movement of evidence between locations
   - B) An attacker moving between systems within a network after initial compromise
   - C) Transferring logs to external storage
   - D) Rotating log files to prevent overflow

**10. Which tool is specifically designed for creating timelines from multiple log sources in forensic investigations?**
   - A) Microsoft Excel
   - B) Notepad++
   - C) Plaso/Log2Timeline
   - D) Adobe Acrobat

**11. What does the Windows Event ID 1102 typically indicate?**
   - A) Successful logon
   - B) System boot
   - C) Audit log cleared (potential evidence destruction)
   - D) User account created

**12. Which Linux log file typically contains authentication-related events?**
   - A) /var/log/syslog
   - B) /var/log/auth.log or /var/log/secure
   - C) /var/log/kern.log
   - D) /var/log/dpkg.log

**13. What is the primary advantage of using a SIEM (Security Information and Event Management) platform?**
   - A) It eliminates the need for log storage
   - B) It provides centralized log collection, correlation, and real-time analysis
   - C) It automatically fixes security vulnerabilities
   - D) It replaces the need for firewalls

**14. In Apache access logs, what does a 404 HTTP status code indicate? **
   - A) Successful request
   - B) Server error
   - C) Page not found
   - D) Unauthorized access

**15. What is the best practice for handling original log files during a forensic investigation?**
   - A) Edit them directly to highlight important information
   - B) Delete redundant entries to save space
   - C) Preserve them untouched and work on copies
   - D) Convert them all to a single format

**16. Which of the following is a key indicator of a brute force attack in logs?**
   - A) Single successful login
   - B) Multiple failed login attempts in rapid succession from the same source
   - C) Regular scheduled tasks running
   - D) System updates being installed

**17. What does the term "log rotation" mean?**
   - A) Physically rotating storage devices
   - B) Automatically archiving old logs and creating new log files to manage disk space
   - C) Changing log file permissions
   - D) Encrypting log files

**18. In firewall logs, what information is typically NOT included?**
   - A) Source and destination IP addresses
   - B) Port numbers and protocols
   - C) User passwords
   - D) Action taken (allow/deny)

**19. What is the primary purpose of correlating logs from multiple sources?**
   - A) To reduce storage requirements
   - B) To build a complete picture of an incident by combining evidence from different systems
   - C) To simplify log formatting
   - D) To eliminate duplicate entries

**20. Which PowerShell cmdlet is used to retrieve Windows Event Logs?**
   - A) Get-EventLog or Get-WinEvent
   - B) Read-Logs
   - C) Show-Events
   - D) Export-WindowsLog

### Part B: Short Answer Questions

**21. Explain why normalizing timestamps to UTC is important when analyzing logs from multiple systems.**

**22. Describe three different types of logs you would examine when investigating a suspected data breach, and explain what information each type provides.**

**23. What are three indicators you would look for in logs to detect potential data exfiltration?**

**24. Explain the concept of "chain of custody" and why it is critical in forensic log analysis.**

**25. List and briefly describe four command-line tools commonly used for log analysis in Linux environments.**

### Part C: Practical Scenario

**Scenario:**
You are investigating a security incident at a company. The security team detected unusual outbound network traffic on October 6, 2025, at approximately 14:30 UTC. You have access to the following logs:
- Firewall logs
- Windows Security Event Logs from the affected workstation
- Web proxy logs
- Antivirus logs

**26. Outline a step-by-step investigation plan. Include:**
   - What specific information you would look for in each log type
   - The order in which you would analyze the logs
   - How you would correlate findings across different log sources
   - What timeline you would attempt to construct

**27. Based on the following log excerpts, identify the most likely attack vector and explain your reasoning:**

```
Firewall Log (10/06/2025 13:45:23 UTC):
ALLOW src=192.168.1.105 dst=203.0.113.50 proto=TCP dport=443

Web Proxy Log (10/06/2025 13:45:25 UTC):
192.168.1.105 CONNECT malicious-domain.com:443 - - [200]

Windows Security Event Log (10/06/2025 13:47:15 UTC):
Event ID: 4688 (New Process Created)
Process: C:\Users\jsmith\Downloads\invoice_Oct.exe
Creator: jsmith

Antivirus Log (10/06/2025 13:47:18 UTC):
WARNING: Suspicious behavior detected - invoice_Oct.exe
Registry modification detected
Network connection attempt to 203.0.113.50

Firewall Log (10/06/2025 14:30:45 UTC):
ALLOW src=192.168.1.105 dst=203.0.113.50 proto=TCP dport=443
bytes_out=2,147,483,648 (2GB transferred)

Windows Security Event Log (10/06/2025 14:25:10 UTC):
Event ID: 4663 (Object Access)
Object: C:\Users\jsmith\Documents\Confidential\*
Access: READ
```

In your answer:
- Identify the attack vector (how the system was compromised)
- Construct a timeline of events
- Identify indicators of compromise (IoCs)
- Explain what data may have been exfiltrated and how
- Suggest additional log sources to examine