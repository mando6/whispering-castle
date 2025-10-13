## Course Overview

**Duration:** 8-10 hours  
**Level:** Intermediate to Advanced  
**Prerequisites:** Basic understanding of TCP/IP, network protocols, and digital forensics fundamentals

### Learning Objectives

By the end of this course, you will be able to:
- Understand the principles of network event reconstruction in digital forensics
- Identify and extract relevant artifacts from packet captures
- Reconstruct user actions, file transfers, and application interactions from network data
- Apply appropriate tools and methodologies for network forensic analysis
- Document findings in a forensically sound manner

---

## Module 1: Foundations of Network Event Reconstruction

### 1.1 Introduction to Network Forensics

Network forensics involves capturing, recording, and analyzing network traffic to discover the source of security incidents, policy violations, or criminal activity. Unlike traditional forensics that focuses on storage media, network forensics deals with volatile, ephemeral data.

**Key Concepts:**
- **Network traffic** is the data transmitted across a network at any given time
- **Packet capture (PCAP)** is the process of intercepting and logging network traffic
- **Network artifacts** are remnants of network activity that can be analyzed

**Connection to Main Topic:** Network event reconstruction is the culmination of network forensic analysis—taking raw packet data and transforming it into a coherent timeline of events and user activities.

### 1.2 Legal and Ethical Considerations

Before conducting network forensics, investigators must understand:
- **Chain of custody** requirements for network evidence
- **Privacy laws** and wiretapping regulations (e.g., ECPA, GDPR)
- **Authorization requirements** for network monitoring
- **Data retention policies** and legal hold procedures

**Connection to Main Topic:** Proper legal framework ensures that reconstructed network events are admissible in court and ethically obtained.

### 1.3 The OSI Model and Protocol Analysis

Understanding network protocols across the OSI model layers is essential:

- **Layer 2 (Data Link):** MAC addresses, ARP, switches
- **Layer 3 (Network):** IP addressing, routing, ICMP
- **Layer 4 (Transport):** TCP, UDP, port numbers
- **Layer 7 (Application):** HTTP, FTP, DNS, SMTP, SSH

**Connection to Main Topic:** Different layers provide different types of evidence. Reconstruction often requires correlating information across multiple protocol layers to build a complete picture.

---

## Module 2: Packet Capture and Collection

### 2.1 Capture Methods and Tools

**Network Taps and SPAN Ports:**
- Physical taps provide complete visibility without dropping packets
- SPAN (Switch Port Analyzer) mirrors traffic to a monitoring port
- Each method has trade-offs in completeness and infrastructure impact

**Primary Capture Tools:**
- **tcpdump:** Command-line packet analyzer for Unix/Linux
- **Wireshark:** GUI-based protocol analyzer with deep inspection capabilities
- **tshark:** Command-line version of Wireshark for automation
- **NetworkMiner:** Windows-based tool for passive network sniffing

**Connection to Main Topic:** The quality and completeness of your packet capture directly determines the accuracy of event reconstruction. Incomplete captures lead to gaps in the timeline.

### 2.2 Capture Filters and Optimization

Effective filtering reduces data volume and focuses on relevant traffic:

```
# Capture only HTTP traffic
tcpdump -i eth0 'tcp port 80'

# Capture traffic from specific host
tcpdump -i eth0 'host 192.168.1.100'

# Capture DNS queries
tcpdump -i eth0 'udp port 53'
```

**Best Practices:**
- Use BPF (Berkeley Packet Filter) syntax for efficient filtering
- Balance between capturing too much (storage issues) and too little (missing evidence)
- Consider full packet capture vs. metadata-only capture based on investigation needs

**Connection to Main Topic:** Strategic filtering during capture ensures you have the right data for reconstruction without overwhelming storage or analysis capabilities.

### 2.3 Handling Large Packet Captures

**File Management Techniques:**
- Split large PCAP files using `editcap` or `tcpdump -C`
- Index PCAP files for faster searching
- Use compression to manage storage (e.g., gzip)

**Example splitting command:**
```bash
editcap -c 10000 large_capture.pcap split_capture.pcap
```

**Connection to Main Topic:** Large captures are common in enterprise environments. Proper file management enables efficient reconstruction even with terabytes of network data.

---

## Module 3: Rebuilding User Actions from Network Data

### 3.1 Session Reconstruction Fundamentals

User actions manifest as network sessions—sequences of related packets between endpoints.

**TCP Session Reconstruction:**
1. Identify TCP three-way handshake (SYN, SYN-ACK, ACK)
2. Follow sequence and acknowledgment numbers
3. Track data exchange
4. Identify session termination (FIN or RST)

**Wireshark Technique:**
- Right-click packet → Follow → TCP Stream
- Provides reassembled conversation view

**Connection to Main Topic:** Individual packets are meaningless without context. Session reconstruction transforms fragmented data into coherent user interactions.

### 3.2 HTTP/HTTPS Traffic Analysis

**HTTP Request Analysis:**
- **Method:** GET, POST, PUT, DELETE
- **URI:** Requested resource path
- **Headers:** User-Agent, Referer, Cookies
- **Body:** Form data, JSON payloads

**Example HTTP Reconstruction:**
A user visiting a website generates:
1. DNS query for domain name
2. TCP connection to server IP on port 80/443
3. HTTP GET request for webpage
4. Server response with HTML content
5. Subsequent requests for CSS, JavaScript, images
6. Cookie setting for session tracking

**HTTPS Considerations:**
- Encrypted payload prevents content inspection
- Metadata still visible: IP addresses, ports, SNI (Server Name Indication)
- May require SSL/TLS decryption with private keys (legal considerations apply)

**Connection to Main Topic:** Web browsing is the most common user activity. Reconstructing HTTP sessions reveals websites visited, searches performed, and data submitted.

### 3.3 Email Communication Reconstruction

**SMTP Analysis (Outbound Email):**
- Identify MAIL FROM and RCPT TO commands
- Extract email headers (From, To, Subject, Date)
- Reconstruct message body and attachments
- Track email relay path

**POP3/IMAP Analysis (Inbound Email):**
- User authentication (username visible in plaintext for unencrypted)
- Message retrieval commands
- Full email content in cleartext for non-encrypted connections

**Practical Example:**
```
# Filter for SMTP traffic
tcp.port == 25

# Look for email indicators
smtp.data.fragment
```

**Connection to Main Topic:** Email reconstruction reveals communication patterns, data exfiltration attempts, and social engineering attacks.

### 3.4 File Upload and Download Activities

**Indicators of File Transfers:**
- Large HTTP POST requests (uploads)
- Sustained data transfer in HTTP responses (downloads)
- FTP commands: STOR (upload), RETR (download)
- SMB/CIFS traffic for file sharing

**File Carving from Network Traffic:**
Using NetworkMiner or Wireshark:
1. Identify file transfer protocols
2. Extract content-type headers
3. Reassemble file fragments
4. Calculate hash values for verification

**Example with Wireshark:**
- File → Export Objects → HTTP
- Select files to extract and save

**Connection to Main Topic:** File transfers are critical events in investigations—they may represent data theft, malware downloads, or evidence of unauthorized access.

### 3.5 Authentication and Login Events

**Identifying Login Attempts:**
- HTTP POST to login endpoints
- Presence of username/password fields
- Authentication cookies (e.g., session tokens)
- Success/failure based on response codes

**Protocols to Monitor:**
- HTTP form-based authentication
- LDAP authentication queries
- Kerberos tickets
- RADIUS authentication
- SSH login attempts

**Brute Force Detection:**
- Multiple failed login attempts from same source
- Rapid succession of authentication requests
- Different username attempts to same service

**Connection to Main Topic:** Authentication events establish user identity and access patterns—fundamental to reconstructing "who did what and when."

---

## Module 4: Application Interaction Analysis

### 4.1 Database Activity Reconstruction

**Database Protocol Analysis:**
- **MySQL:** Port 3306, query commands visible in plaintext
- **PostgreSQL:** Port 5432, protocol inspection shows SQL statements
- **MSSQL:** Port 1433, TDS protocol carries SQL queries
- **Oracle:** Port 1521, TNS protocol for database communication

**What Can Be Reconstructed:**
- Query statements (SELECT, INSERT, UPDATE, DELETE)
- Database user accounts
- Tables and data accessed
- Timing of operations

**Connection to Main Topic:** Database interactions reveal data access patterns, potential data breaches, and insider threat activities.

### 4.2 Remote Access Session Analysis

**RDP (Remote Desktop Protocol) Analysis:**
- Connection establishment on port 3389
- Client and server capabilities negotiation
- Encrypted screen updates (content not visible)
- Metadata: timestamps, duration, bandwidth usage

**SSH Session Analysis:**
- Port 22 traffic
- Encrypted payload prevents command viewing
- Can identify: connection timing, data volume, session duration
- Multiple sessions may indicate lateral movement

**VPN Traffic:**
- Identifying VPN protocols (OpenVPN, IPSec, WireGuard)
- Tunneled traffic analysis (if decryption possible)
- Connection patterns and bandwidth usage

**Connection to Main Topic:** Remote access is a primary vector for both legitimate administration and malicious intrusion. Reconstructing these sessions is critical for incident response.

### 4.3 Cloud Service Interactions

**Common Cloud Service Patterns:**
- **AWS S3:** HTTP/HTTPS to s3.amazonaws.com endpoints
- **Microsoft 365:** Graph API calls, Exchange Online Protocol
- **Google Workspace:** Google API endpoints
- **Dropbox/Box:** File sync protocols

**API Traffic Analysis:**
- REST API calls in HTTP
- JSON payloads reveal actions taken
- Authentication tokens and API keys
- Rate limiting and error responses

**Connection to Main Topic:** Modern enterprises rely on cloud services. Reconstructing cloud interactions reveals data flows, access patterns, and potential misconfigurations.

### 4.4 Instant Messaging and VoIP

**Chat Protocol Analysis:**
- **XMPP:** XML-based messaging (port 5222)
- **IRC:** Plaintext chat protocols
- **Proprietary:** Slack, Teams, Discord (often encrypted)

**VoIP Reconstruction:**
- **SIP (Session Initiation Protocol):** Call setup on port 5060
- **RTP (Real-time Transport Protocol):** Voice data streams
- Can reconstruct: caller/callee, call duration, codec used
- Audio extraction possible if RTP not encrypted

**Connection to Main Topic:** Communication tools are essential workplace applications. Reconstructing these interactions provides context for user behavior and potential policy violations.

---

## Module 5: Advanced Reconstruction Techniques

### 5.1 Timeline Creation and Correlation

**Building Comprehensive Timelines:**

1. **Extract timestamps** from all relevant packets
2. **Normalize time zones** to UTC for consistency
3. **Correlate events** across different protocols
4. **Identify patterns** such as:
   - Login → File access → File transfer → Logout
   - Malware callback patterns
   - Data exfiltration sequences

**Tools for Timeline Analysis:**
- **Timesketch:** Open-source collaborative timeline tool
- **Plaso/log2timeline:** Automated timeline generation
- **Custom scripts:** Python with Scapy for packet parsing

**Example Timeline Entry:**
```
2025-10-09 14:23:15 UTC | TCP | 192.168.1.50:49234 → 10.0.0.5:445 | SMB | File Open: \\FileServer\Confidential\Q3-Results.xlsx
2025-10-09 14:23:47 UTC | TCP | 192.168.1.50:49234 → 10.0.0.5:445 | SMB | File Read: 2.4 MB transferred
2025-10-09 14:24:12 UTC | TCP | 192.168.1.50:51892 → 185.20.10.3:443 | HTTPS | TLS connection to dropbox.com
2025-10-09 14:26:33 UTC | TCP | 192.168.1.50:51892 → 185.20.10.3:443 | HTTPS | POST /upload (2.4 MB)
```

**Connection to Main Topic:** Timelines transform isolated network events into narratives, showing the sequence and relationship of user actions.

### 5.2 Network Flow Analysis

**NetFlow and IPFIX:**
- Summarized network traffic metadata
- Flow records contain: source/dest IPs, ports, protocol, byte counts, timestamps
- Useful for long-term traffic analysis without full packet capture

**Flow Analysis Benefits:**
- Lower storage requirements than full PCAP
- Identify communication patterns and anomalies
- Detect data exfiltration through volume analysis
- Track lateral movement between internal systems

**Tools:**
- **nfdump:** NetFlow analysis tool
- **SiLK (System for Internet-Level Knowledge):** Flow collection and analysis
- **Zeek (formerly Bro):** Network security monitoring with flow logs

**Connection to Main Topic:** Flow data provides the big picture of network activity, allowing reconstruction of communication patterns even without full packet details.

### 5.3 Encryption and Decryption

**SSL/TLS Decryption Methods:**

1. **Private Key Method:**
   - Requires server's private key
   - Works only with RSA key exchange (not Perfect Forward Secrecy)
   - Configure in Wireshark: Edit → Preferences → Protocols → TLS

2. **Session Key Method:**
   - Browser/application logs session keys (SSLKEYLOGFILE environment variable)
   - Works with all cipher suites including PFS
   - More practical for client-side analysis

3. **Man-in-the-Middle Proxy:**
   - Deploy SSL inspection proxy
   - Issues proxy certificates to clients
   - Requires network control and client configuration

**Legal and Ethical Considerations:**
- Decryption may violate privacy expectations
- Requires proper authorization
- Document methodology for court admissibility

**Connection to Main Topic:** Modern traffic is predominantly encrypted. Lawful decryption capabilities are essential for complete event reconstruction.

### 5.4 Protocol Anomaly Detection

**Identifying Suspicious Patterns:**

- **Port Misuse:** HTTP traffic on non-standard ports
- **Protocol Tunneling:** DNS tunneling for data exfiltration
- **Timing Anomalies:** Traffic at unusual hours
- **Volume Anomalies:** Sudden large data transfers
- **Geographical Anomalies:** Connections to unexpected countries

**Indicators of Compromise (IoCs):**
- Beaconing behavior (regular callback intervals)
- Known malicious IP addresses
- Suspicious user-agent strings
- Malformed packets or protocol violations

**Connection to Main Topic:** Not all network activity is benign. Detecting anomalies helps identify malicious actions within reconstructed events.

---

## Module 6: Tools and Automation

### 6.1 Essential Forensic Tools

**Wireshark/tshark:**
- Industry-standard protocol analyzer
- Extensive dissector library for hundreds of protocols
- Export capabilities for objects and data

**NetworkMiner:**
- Passive network forensic tool
- Automatic host, file, and credential extraction
- Operating system fingerprinting

**tcpflow:**
- Captures and reconstructs TCP flows
- Stores each flow in separate files
- Useful for bulk session extraction

**Zeek (Bro):**
- Network security monitoring framework
- Generates structured logs of network activity
- Scriptable for custom detection logic

**Scapy:**
- Python library for packet manipulation
- Programmatic packet creation and analysis
- Ideal for custom forensic scripts

**Connection to Main Topic:** Manual analysis doesn't scale. Tool proficiency enables efficient reconstruction of network events from massive datasets.

### 6.2 Scripting for Automation

**Python with Scapy Example:**
```python
from scapy.all import *

def extract_http_posts(pcap_file):
    packets = rdpcap(pcap_file)
    for packet in packets:
        if packet.haslayer(TCP) and packet.haslayer(Raw):
            if b'POST' in packet[Raw].load:
                print(f"POST request from {packet[IP].src} to {packet[IP].dst}")
                print(packet[Raw].load.decode('utf-8', errors='ignore'))
                print("-" * 50)

extract_http_posts('capture.pcap')
```

**tshark Automation:**
```bash
# Extract all HTTP requests
tshark -r capture.pcap -Y "http.request" -T fields -e frame.time -e ip.src -e http.request.method -e http.request.uri

# Count DNS queries by domain
tshark -r capture.pcap -Y "dns.qry.name" -T fields -e dns.qry.name | sort | uniq -c | sort -rn
```

**Connection to Main Topic:** Automation allows investigators to process large captures quickly, extract relevant events, and identify patterns that manual analysis would miss.

### 6.3 Reporting and Documentation

**Forensic Report Components:**

1. **Executive Summary:** High-level findings
2. **Investigation Scope:** Time period, systems analyzed
3. **Methodology:** Tools used, analysis techniques
4. **Timeline of Events:** Detailed chronological reconstruction
5. **Technical Details:** Packet analysis, artifacts identified
6. **Evidence Appendix:** Packet captures, extracted files
7. **Conclusions:** Summary of findings and recommendations

**Best Practices:**
- Use screenshots with annotations
- Include packet numbers for reference
- Provide hash values for evidence files
- Maintain clear chain of custody documentation
- Write for both technical and non-technical audiences

**Connection to Main Topic:** The ultimate goal of reconstruction is to present findings clearly. Proper documentation ensures your analysis is understood and legally defensible.

---

## Module 7: Case Studies and Practical Applications

### 7.1 Case Study: Data Exfiltration Investigation

**Scenario:**
An employee is suspected of stealing proprietary source code before resignation. Network capture spans the employee's last week.

**Reconstruction Process:**

1. **Identify User's IP Address:**
   - Correlate username with DHCP logs
   - Found IP: 192.168.10.45

2. **Filter User's Traffic:**
   ```
   ip.addr == 192.168.10.45
   ```

3. **Analyze Timeline:**
   - Day 1-4: Normal work patterns (internal file servers, email, development tools)
   - Day 5: Unusual activity detected

4. **Suspicious Events Identified:**
   ```
   15:23 UTC: Access to \\DevServer\SourceCode\Project-Alpha
   15:24-15:47 UTC: 1.2 GB data transfer from \\DevServer (SMB)
   15:48 UTC: TLS connection to cloud.mail.ru (Russian cloud storage)
   15:49-16:15 UTC: HTTPS POST requests, 1.2 GB uploaded
   16:16 UTC: Browser search for "secure file deletion tools"
   ```

5. **Evidence Extracted:**
   - SMB file access logs showing specific files accessed
   - DNS queries revealing cloud storage service
   - HTTPS metadata showing upload volume matching download
   - Browser history reconstructed from HTTP traffic

**Conclusion:** Clear evidence of data exfiltration. Timeline shows deliberate action to transfer and upload company source code to external storage.

**Connection to Main Topic:** This demonstrates end-to-end reconstruction: identifying user, tracking file access, correlating multiple protocols, and building a compelling timeline.

### 7.2 Case Study: Malware Communication Analysis

**Scenario:**
A workstation is suspected of being infected with malware. Analyze network traffic to understand the infection and command-and-control (C2) communication.

**Reconstruction Process:**

1. **Identify Initial Infection Vector:**
   - HTTP download of malicious email attachment
   - File: invoice_483920.pdf.exe (983 KB)

2. **Post-Infection Behavior:**
   - DNS queries to newly registered domains (high entropy names)
   - Beaconing pattern detected: HTTPS connections every 3 minutes
   - Destination: 185.234.19.42 (known malicious IP)

3. **C2 Communication Analysis:**
   - Encrypted payload (TLS 1.2)
   - Regular heartbeat: small packets (~200 bytes) every 180 seconds
   - Larger downloads observed (likely receiving commands)

4. **Lateral Movement Attempts:**
   - SMB connections to other internal hosts
   - Port scanning activity (TCP SYN to ports 139, 445, 3389)
   - Failed RDP login attempts to domain controller

5. **Data Exfiltration:**
   - Large HTTPS POST to compromised C2 server
   - Volume: 450 MB over 2 hours
   - Timing: 2:00 AM - 4:00 AM (off-hours)

**Timeline Reconstruction:**
```
Day 1, 14:32: Malicious email attachment downloaded
Day 1, 14:33: First C2 beacon sent
Day 1, 14:45: Received commands (larger download)
Day 1, 15:00-17:30: Lateral movement scanning
Day 2, 02:00-04:00: Data exfiltration
Day 2-7: Continued beaconing every 3 minutes
```

**Connection to Main Topic:** Malware investigations require reconstructing automated behaviors. Understanding infection chains and C2 patterns is critical for containment and remediation.

---

## Module 8: Challenges and Limitations

### 8.1 Technical Challenges

**Encrypted Traffic:**
- Majority of modern traffic uses TLS/SSL
- Limited visibility without decryption capabilities
- Metadata analysis becomes more important

**Packet Loss:**
- Network congestion or capture device limitations
- Results in incomplete sessions
- May miss critical evidence

**Large-Scale Networks:**
- Enterprise networks generate terabytes daily
- Storage and processing challenges
- Requires strategic capture point selection

**Connection to Main Topic:** Understanding limitations ensures realistic expectations and proper methodology adjustments during reconstruction.

### 8.2 Legal and Privacy Considerations

**Consent and Authorization:**
- Employee monitoring policies must be clear
- Warrant requirements for criminal investigations
- Cross-border data transfer restrictions

**Data Retention:**
- Balance investigation needs with privacy rights
- Comply with data protection regulations (GDPR, CCPA)
- Implement appropriate retention policies

**Admissibility:**
- Chain of custody documentation
- Tool validation and reliability
- Expert witness requirements

**Connection to Main Topic:** Even perfect technical reconstruction is worthless if evidence is inadmissible. Legal compliance is integral to forensic practice.

### 8.3 Emerging Technologies and Future Challenges

**IPv6 Adoption:**
- Larger address space complicates tracking
- Different header structure requires updated tools
- Flow analysis becomes more important

**Increased Encryption:**
- TLS 1.3 with Perfect Forward Secrecy
- QUIC protocol (UDP-based HTTP/3)
- DNS over HTTPS (DoH) and DNS over TLS (DoT)

**Cloud and Virtualization:**
- Evidence scattered across multiple locations
- East-west traffic (within data center) visibility
- Multi-tenant environment challenges

**IoT Devices:**
- Proprietary protocols
- Resource-constrained devices
- Massive scale

**Connection to Main Topic:** Network forensics must evolve with technology. Staying current with emerging protocols and encryption methods is essential for effective reconstruction.

---

## Course Completion and Next Steps

### Congratulations!

You have completed the comprehensive course on Reconstruction of Network Events in Digital Forensics. You should now understand:

✓ The principles and methodology of network forensic analysis  
✓ How to capture and analyze network traffic effectively  
✓ Techniques for reconstructing user actions, file transfers, and application interactions  
✓ The tools and automation strategies for efficient analysis  
✓ Legal and ethical considerations in network forensics  
✓ Real-world application through case studies

### Recommended Practice Activities

1. **Download Practice PCAPs:**
   - Visit Wireshark Sample Captures and analyze various traffic types
   - Work through Malware-Traffic-Analysis.net scenarios
   - Create your own captures of normal activities to understand baseline behavior

2. **Hands-on Labs:**
   - Set up a virtual lab environment with multiple VMs
   - Generate different types of network traffic
   - Practice capturing and reconstructing your own activities

3. **Tool Proficiency:**
   - Complete Wireshark tutorials and challenges
   - Experiment with NetworkMiner, Zeek, and other tools
   - Write Python scripts using Scapy for custom analysis

4. **Stay Current:**
   - Follow security blogs and forums
   - Attend webinars and conferences (SANS, Black Hat, DEF CON)
   - Join professional organizations (HTCIA, IACIS)

### Certification Pathways

Consider pursuing professional certifications to validate your skills:
- GIAC Network Forensic Analyst (GNFA)
- Certified Computer Examiner (CCE)
- EnCase Certified Examiner (EnCE)
- Certified Network Forensics Examiner (CNFE)

### Final Thoughts

Network forensics is both an art and a science. Technical skills must be paired with analytical thinking, attention to detail, and proper methodology. As networks and protocols evolve, continuous learning is essential.

Remember the investigator's mindset:
- **Question everything** - Don't assume normal means benign
- **Verify findings** - Cross-reference across multiple data sources
- **Document thoroughly** - Your analysis must be reproducible
- **Think like the adversary** - Understand attacker techniques
- **Maintain integrity** - Legal and ethical compliance is non-negotiable

Network event reconstruction transforms raw packet data into compelling narratives that can solve crimes, prevent breaches, and protect organizations. Your skills in this domain make you a valuable asset in the cybersecurity ecosystem.

Good luck in your forensic investigations!

