
**Question 1: Fundamentals**  
Which OSI layer is most relevant for analyzing HTTP traffic during user action reconstruction?
- A) Layer 2 (Data Link)
- B) Layer 3 (Network)
- C) Layer 4 (Transport)
- D) Layer 7 (Application)

---

**Question 2: Protocol Analysis**  
You discover a TCP three-way handshake (SYN, SYN-ACK, ACK) in your packet capture. What does this indicate?
- A) The end of a TCP session
- B) The beginning of a TCP session
- C) A failed connection attempt
- D) A packet retransmission

---

**Question 3: File Transfer Identification**  
Which of the following is the BEST indicator of a file download via HTTP?
- A) Multiple small HTTP GET requests
- B) A large HTTP POST request
- C) A sustained HTTP response with significant data transfer
- D) DNS queries for file hosting domains

---

**Question 4: Email Forensics**  
When analyzing SMTP traffic, which command indicates the sender of an email?
- A) RCPT TO
- B) DATA
- C) MAIL FROM
- D) HELO

---

**Question 5: Encryption Challenges**  
You need to decrypt HTTPS traffic in Wireshark. Which method will NOT work for TLS connections using Perfect Forward Secrecy (PFS)?
- A) Using the server's private RSA key
- B) Using session keys from SSLKEYLOGFILE
- C) Deploying an SSL inspection proxy
- D) Using pre-master secrets

---

**Question 6: Timeline Creation**  
You are building a timeline of a suspected data exfiltration event. Which sequence of events is MOST suspicious?
- A) Login → Check email → Browse internet → Logout
- B) Login → Access HR files → Send email → Logout
- C) Login → Download 2GB from file server → Upload 2GB to cloud storage → Clear browser history → Logout
- D) Login → Attend video conference → Access database → Logout

---

**Question 7: Network Flow Analysis**  
What is the primary advantage of using NetFlow data over full packet captures?
- A) NetFlow provides more detailed packet payload information
- B) NetFlow requires significantly less storage space
- C) NetFlow captures encrypted traffic in plaintext
- D) NetFlow provides better timestamp accuracy

---

**Question 8: Application Analysis**  
You observe regular connections every 5 minutes from an internal host to an external IP address, with small packet sizes (~150 bytes). What does this pattern suggest?
- A) Normal web browsing behavior
- B) Streaming video playback
- C) Possible malware beaconing/command-and-control
- D) Large file download in progress

---

**Question 9: Authentication Events**  
Multiple HTTP POST requests to a login endpoint from the same source IP, each with different usernames, followed by HTTP 401 responses, indicates:
- A) Successful user authentication
- B) Possible brute force attack
- C) Normal user behavior (forgot username)
- D) Server misconfiguration

---

**Question 10: Tool Selection**  
Which tool would be MOST appropriate for automatically extracting files transferred over HTTP from a packet capture?
- A) tcpdump
- B) nmap
- C) Wireshark or NetworkMiner
- D) netstat

---

**Question 11: DNS Analysis**  
An investigator notices DNS queries for domain names with high entropy (random-looking characters) and no human-readable patterns. This could indicate:
- A) Normal CDN (Content Delivery Network) usage
- B) Possible DNS tunneling for data exfiltration
- C) IPv6 adoption
- D) DNSSEC implementation

---

**Question 12: Legal Considerations**  
Before conducting network forensics on employee traffic, what is the MOST important prerequisite?
- A) Installing the latest version of Wireshark
- B) Obtaining proper authorization and ensuring compliance with legal requirements
- C) Upgrading network infrastructure
- D) Training all employees on security awareness

---

**Question 13: Remote Access**  
You identify RDP traffic (port 3389) in a packet capture. What information can you reliably extract?
- A) The exact commands typed by the remote user
- B) The files opened during the session
- C) Connection timing, duration, and endpoints
- D) Screenshots of the user's desktop

---

**Question 14: Protocol Anomalies**  
HTTP traffic is observed on port 8443, which is typically used for HTTPS. What should an investigator consider?
- A) This is normal behavior and requires no further investigation
- B) This could be legitimate alternative configuration or potential protocol tunneling
- C) The capture is corrupted
- D) This is always malicious activity

---

**Question 15: Session Reconstruction**  
When following a TCP stream in Wireshark, you see alternating red and blue text. What do these colors represent?
- A) Encrypted and unencrypted data
- B) Data from client to server (red) and server to client (blue), or vice versa
- C) Malicious and benign traffic
- D) IPv4 and IPv6 packets

---

### Scenario-Based Questions

**Scenario 1 (Questions 16-18):**  
An employee's workstation shows signs of compromise. You capture network traffic and observe the following sequence:

1. 10:15 AM: HTTP download of "document.pdf.exe" (2.3 MB)
2. 10:16 AM: DNS query for "c2-server-1923.dyndns.org"
3. 10:17 AM: HTTPS connection established to 198.51.100.42
4. 10:17 AM - 11:30 AM: Small encrypted packets (~100 bytes) every 60 seconds to 198.51.100.42
5. 11:35 AM: Larger encrypted download (500 KB) from 198.51.100.42
6. 11:40 AM - 12:30 PM: SMB connections to multiple internal hosts
7. 01:00 PM: Large HTTPS upload (800 MB) to 198.51.100.42

**Question 16:**  
What is the most likely initial infection vector?
- A) Phishing email with malicious attachment
- B) SQL injection attack
- C) Physical USB drive
- D) Malicious email attachment downloaded via HTTP (document.pdf.exe)

---

**Question 17:**  
What does the pattern of small packets every 60 seconds most likely represent?
- A) Normal Windows update checks
- B) Command-and-control beaconing/heartbeat
- C) User browsing activity
- D) Background DNS queries

---

**Question 18:**  
Based on the complete timeline, what malicious activities likely occurred? (Select all that apply)
- A) Initial malware infection
- B) Command-and-control communication
- C) Lateral movement/network reconnaissance
- D) Data exfiltration
- E) All of the above

---

**Scenario 2 (Questions 19-20):**  
During a routine security audit, you analyze packet captures and find the following for user ID "jsmith":

- Day 1-10: Regular work hours (8 AM - 5 PM), accessing internal resources, email, and approved cloud services
- Day 11: 11:30 PM - Large SMB transfers from \\FileServer\Finance\Confidential (3.2 GB)
- Day 11: 11:45 PM - DNS queries and HTTPS traffic to mega.nz (cloud storage)
- Day 11: 11:50 PM - 12:30 AM - Large HTTPS POST requests totaling 3.2 GB to mega.nz
- Day 12: Resume normal work pattern

**Question 19:**  
What makes the Day 11 activity suspicious?
- A) The use of HTTPS encryption
- B) The timing (late night), volume of data, and sequence of file access followed by external upload
- C) The use of SMB protocol
- D) DNS queries to a cloud service

---

**Question 20:**  
What should be the investigator's FIRST step after identifying this activity?
- A) Immediately confront the user
- B) Delete the cloud storage account
- C) Preserve evidence, document findings, and follow incident response procedures
- D) Reset the user's password