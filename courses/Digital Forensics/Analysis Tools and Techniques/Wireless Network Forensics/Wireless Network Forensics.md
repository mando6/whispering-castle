## Course Overview

**Course Duration:** 8-10 hours  
**Difficulty Level:** Intermediate to Advanced  
**Prerequisites:** Basic understanding of networking concepts, TCP/IP, and digital forensics fundamentals

### Learning Objectives

By the end of this course, you will be able to:
- Understand the fundamentals of wireless network forensics within the digital forensics framework
- Analyze Wi-Fi traffic to identify security incidents and gather evidence
- Detect and investigate rogue access points in enterprise environments
- Understand wireless encryption protocols and their forensic implications
- Apply proper evidence collection and chain of custody procedures for wireless investigations
- Use industry-standard tools for wireless network analysis

---

## Module 1: Introduction to Wireless Network Forensics

### 1.1 What is Wireless Network Forensics?

Wireless Network Forensics is a specialized branch of digital forensics that focuses on the identification, collection, preservation, analysis, and presentation of evidence from wireless networks. This discipline is critical in modern digital investigations as wireless networks have become ubiquitous in both personal and enterprise environments.

**Connection to Digital Forensics:** Wireless network forensics extends traditional network forensics by addressing the unique challenges posed by wireless communications, including:
- Radio frequency (RF) signal analysis
- Volatile evidence in wireless transmissions
- Mobile device connectivity patterns
- Wireless-specific attack vectors

### 1.2 The Wireless Network Forensics Process

The forensic process follows the standard digital forensics methodology:

1. **Identification:** Recognizing potential wireless evidence sources
2. **Collection:** Capturing wireless traffic and related data
3. **Preservation:** Maintaining integrity of wireless evidence
4. **Analysis:** Examining captured data for relevant information
5. **Presentation:** Reporting findings in a clear, legally admissible format

### 1.3 Legal and Ethical Considerations

Before conducting wireless forensics investigations, practitioners must understand:
- Laws governing wireless interception (e.g., Wiretap Act in the US)
- Authorization requirements for monitoring wireless networks
- Privacy expectations in wireless communications
- Proper documentation and chain of custody procedures

**Key Principle:** Always obtain proper authorization before capturing wireless traffic. Unauthorized interception can violate federal and state laws.

---

## Module 2: Wireless Network Fundamentals

### 2.1 IEEE 802.11 Standards Overview

Understanding the technical foundation of Wi-Fi is essential for effective forensic analysis.

**Evolution of Wi-Fi Standards:**
- **802.11b/g:** 2.4 GHz, legacy standards
- **802.11a:** 5 GHz, higher speed
- **802.11n:** Both 2.4 and 5 GHz, MIMO technology
- **802.11ac (Wi-Fi 5):** 5 GHz, multi-gigabit speeds
- **802.11ax (Wi-Fi 6/6E):** Enhanced efficiency, 6 GHz band support

**Forensic Relevance:** Different standards use varying encryption methods, frame structures, and security features. Identifying the standard in use helps determine what data can be captured and analyzed.

### 2.2 Wireless Frame Structure

802.11 frames consist of three main types:
- **Management Frames:** Network discovery and connection (beacon, probe, authentication)
- **Control Frames:** Medium access and acknowledgments
- **Data Frames:** Actual payload transmission

**Connection to Forensics:** Management frames are often unencrypted even on secured networks, revealing SSIDs, MAC addresses, and network capabilities. These frames are crucial for network mapping and device identification.

### 2.3 Wireless Channels and Frequencies

**2.4 GHz Band:**
- Channels 1-11 (US), 1-13 (Europe), 1-14 (Japan)
- Overlapping channels cause interference
- Channels 1, 6, and 11 are non-overlapping

**5 GHz Band:**
- More channels, less interference
- Multiple non-overlapping channels
- Better for high-density environments

**Forensic Application:** Understanding channel allocation helps in setting up proper monitoring and identifying channel-hopping attacks or hidden networks.

---

## Module 3: Analyzing Wi-Fi Traffic

### 3.1 Traffic Capture Techniques

**Monitor Mode vs. Promiscuous Mode:**
- **Monitor Mode:** Captures all 802.11 frames without association, includes management and control frames
- **Promiscuous Mode:** Captures data frames only after association with a network

**Setting Up Monitor Mode:**

For Linux systems using Airmon-ng:
```bash
# Check wireless interfaces
airmon-ng

# Enable monitor mode on wlan0
airmon-ng start wlan0

# Verify monitor mode (creates wlan0mon)
iwconfig
```

**Connection to Digital Forensics:** Monitor mode is essential for comprehensive wireless forensics as it captures the complete spectrum of wireless activity, not just associated traffic. This is analogous to using a network tap in wired network forensics.

### 3.2 Essential Capture Tools

**Wireshark:**
The industry standard for protocol analysis.
- Comprehensive protocol dissection
- Advanced filtering capabilities
- Export and statistical analysis features

**Tcpdump/Windump:**
Command-line packet analyzer for scripted captures.
```bash
# Capture wireless traffic to file
tcpdump -i wlan0mon -w capture.pcap

# Capture with specific filter
tcpdump -i wlan0mon -w capture.pcap 'wlan type mgt subtype beacon'
```

**Airodump-ng:**
Wireless-specific capture tool from the Aircrack-ng suite.
```bash
# Capture all networks and clients
airodump-ng wlan0mon

# Capture specific network with all handshakes
airodump-ng -c 6 --bssid XX:XX:XX:XX:XX:XX -w capture wlan0mon
```

### 3.3 Traffic Analysis Methodology

**Step-by-Step Analysis Process:**

1. **Initial Reconnaissance:**
   - Identify all access points in range
   - Document SSIDs, BSSIDs, and channels
   - Note encryption types and signal strengths

2. **Client Identification:**
   - Enumerate connected devices (MAC addresses)
   - Track probe requests to identify device movement
   - Correlate devices with specific access points

3. **Temporal Analysis:**
   - Examine connection/disconnection patterns
   - Identify unusual activity times
   - Correlate events with known incidents

4. **Protocol Analysis:**
   - Examine authentication and association frames
   - Analyze EAPOL (Extensible Authentication Protocol over LAN) exchanges
   - Identify protocol anomalies or misconfigurations

**Wireshark Display Filters for Wireless Analysis:**

```
# Show only beacon frames
wlan.fc.type_subtype == 0x08

# Show deauthentication frames
wlan.fc.type_subtype == 0x0c

# Show WPA handshakes
eapol

# Show data frames from specific MAC
wlan.sa == XX:XX:XX:XX:XX:XX && wlan.fc.type == 2

# Show probe requests
wlan.fc.type_subtype == 0x04
```

**Connection to Forensics:** Systematic traffic analysis reveals network behavior patterns, security incidents, and potential evidence. This mirrors the systematic approach used in examining file systems or memory dumps in other forensic disciplines.

### 3.4 Identifying Wireless Attacks in Traffic

**Deauthentication Attack Indicators:**
- High volume of deauthentication frames
- Deauth frames from spoofed MAC addresses
- Unusual reason codes in deauth frames

**Evil Twin Attack Indicators:**
- Duplicate SSIDs with different BSSIDs
- Same SSID on unusual channels
- Legitimate and rogue AP visible simultaneously

**WPS Attack Traces:**
- Repeated WPS probe requests
- WPS M2D (Message 2 Done) messages
- Failed PIN attempts in rapid succession

---

## Module 4: Identifying Rogue Access Points

### 4.1 What Are Rogue Access Points?

A rogue access point (rogue AP) is an unauthorized wireless access point connected to a secure network. Rogue APs pose significant security risks as they can:
- Bypass network security controls
- Provide unauthorized network access
- Enable man-in-the-middle attacks
- Expose sensitive data to interception

**Types of Rogue APs:**
1. **Malicious Rogue APs:** Deliberately installed by attackers
2. **Shadow IT Rogue APs:** Installed by employees without authorization
3. **Misconfigured Personal Devices:** Smartphones or laptops acting as hotspots

**Connection to Digital Forensics:** Identifying rogue APs is crucial in incident response investigations, as they often serve as the initial attack vector. Proper documentation of rogue APs can provide critical evidence in security breach investigations.

### 4.2 Rogue AP Detection Techniques

**Physical Layer Detection:**
- **War Driving/Walking:** Mobile RF scanning to map wireless networks
- **RF Spectrum Analysis:** Using spectrum analyzers to detect unusual signals
- **Signal Strength Triangulation:** Physically locating transmitters

**Logical Detection Methods:**

1. **MAC Address Analysis:**
   - Compare discovered BSSIDs against authorized AP database
   - Identify MAC address OUI (Organizationally Unique Identifier) mismatches
   - Detect MAC address spoofing patterns

2. **SSID Monitoring:**
   - Identify duplicate or suspicious SSIDs
   - Monitor for SSID cloaking attempts
   - Track SSID probes from unknown devices

3. **Network Traffic Correlation:**
   - Cross-reference wireless clients with wired network logs
   - Identify bridged connections indicating rogue APs
   - Monitor for unexpected internal traffic sources

**Automated Detection Tools:**

**Kismet:**
A wireless network detector and IDS.
```bash
# Start Kismet with monitor interface
kismet -c wlan0mon

# Remote capture configuration
kismet_server -c wlan0mon --daemonize
```

**Aircrack-ng Suite:**
```bash
# Scan for networks and identify suspicious APs
airodump-ng wlan0mon

# Focus on specific channel for detailed analysis
airodump-ng -c 6 wlan0mon --write evidence
```

### 4.3 Rogue AP Forensic Investigation Process

**Documentation Requirements:**
1. Date, time, and location of detection
2. SSID, BSSID, and channel information
3. Encryption type and security configuration
4. Signal strength and estimated location
5. Connected clients and their MAC addresses
6. Captured traffic samples

**Evidence Collection:**
```bash
# Comprehensive capture of rogue AP activity
airodump-ng --bssid [ROGUE_BSSID] -c [CHANNEL] -w rogue_evidence wlan0mon
```

**Analysis Steps:**
1. Verify the AP is truly unauthorized against asset inventory
2. Identify device manufacturer from MAC OUI
3. Capture and analyze associated traffic
4. Document connected clients and their activities
5. Assess potential data exposure or breach
6. Prepare incident report with findings

**Connection to Investigation:** Rogue AP investigations often lead to broader security incidents. The forensic evidence collected can support disciplinary actions, legal proceedings, or insurance claims.

---

## Module 5: Wireless Encryption and Decryption

### 5.1 Wireless Encryption Protocols

Understanding encryption is fundamental to wireless forensics, as it determines what evidence can be extracted from captured traffic.

**WEP (Wired Equivalent Privacy):**
- **Status:** Deprecated, fundamentally broken
- **Key Length:** 64-bit or 128-bit (includes 24-bit IV)
- **Vulnerability:** Weak IV implementation, easily cracked
- **Forensic Implication:** Can be broken in minutes with sufficient traffic

**WPA (Wi-Fi Protected Access):**
- **Status:** Deprecated, improved over WEP
- **Protocol:** TKIP (Temporal Key Integrity Protocol)
- **Vulnerability:** Susceptible to various attacks
- **Forensic Implication:** More difficult than WEP but still vulnerable

**WPA2 (802.11i):**
- **Status:** Current standard (though being replaced by WPA3)
- **Protocol:** CCMP using AES encryption
- **Vulnerability:** Secure when using strong passwords; vulnerable to offline brute-force with captured handshake
- **Modes:** 
  - Personal (PSK): Pre-shared key
  - Enterprise: 802.1X authentication with RADIUS

**WPA3:**
- **Status:** Latest standard
- **Improvements:** 
  - SAE (Simultaneous Authentication of Equals) replaces PSK
  - Forward secrecy
  - Protection against offline dictionary attacks
- **Forensic Implication:** Significantly more difficult to break

**Connection to Digital Forensics:** Encryption determines the level of access forensic examiners have to evidence. Understanding these protocols helps determine investigative strategies and legal requirements for accessing encrypted data.

### 5.2 Capturing WPA/WPA2 Handshakes

The four-way handshake contains the information needed to decrypt WPA/WPA2 traffic (given the password).

**Handshake Components:**
1. **Message 1:** AP sends ANonce to client
2. **Message 2:** Client sends SNonce and MIC to AP
3. **Message 3:** AP sends GTK to client
4. **Message 4:** Client confirms receipt

**Passive Capture Method:**
```bash
# Monitor network and wait for client connection
airodump-ng -c [CHANNEL] --bssid [AP_BSSID] -w handshake wlan0mon
```

**Active Capture Method:**
```bash
# Deauthenticate a client to force reconnection (legal only with authorization)
aireplay-ng --deauth 10 -a [AP_BSSID] -c [CLIENT_MAC] wlan0mon
```

**Verifying Handshake Capture:**
```bash
# Check if handshake is complete
aircrack-ng -w /dev/null handshake-01.cap
# Look for "1 handshake" message
```

**Legal Warning:** Forcing client disconnections may be illegal without proper authorization. Always ensure you have explicit permission before performing active wireless testing.

### 5.3 Decryption Techniques and Tools

**Dictionary/Wordlist Attacks:**

Using Aircrack-ng:
```bash
# Attempt to crack WPA/WPA2 with wordlist
aircrack-ng -w /path/to/wordlist.txt -b [BSSID] capture.cap

# Using specific ESSID
aircrack-ng -w wordlist.txt -e "NetworkName" capture.cap
```

Using Hashcat (GPU-accelerated):
```bash
# Convert capture to hashcat format
hcxpcaptool -z hash.hc22000 capture.cap

# Crack using hashcat
hashcat -m 22000 -a 0 hash.hc22000 wordlist.txt
```

**Brute-Force Attacks:**
```bash
# Generate custom wordlist based on known patterns
crunch 8 12 -t password%%% > custom_wordlist.txt

# Use with aircrack-ng
aircrack-ng -w custom_wordlist.txt capture.cap
```

**Rainbow Table Attacks:**
Pre-computed hashes for common SSIDs can speed up cracking.
- CoWPAtty with rainbow tables
- Church of WiFi rainbow tables for common SSIDs

**Decrypting Traffic in Wireshark:**

Once password is obtained:
1. Open capture file in Wireshark
2. Edit → Preferences → Protocols → IEEE 802.11
3. Enable decryption
4. Add decryption key: wpa-pwd:password:SSID
5. Apply and observe decrypted traffic

**Enterprise Network Challenges:**

WPA2-Enterprise uses 802.1X authentication with unique session keys per user:
- Cannot decrypt without access to RADIUS server
- Per-user credentials required
- Each session has unique encryption keys
- Requires cooperation from network administrators or legal authority

**Connection to Forensics:** Successful decryption allows examiners to access application-layer evidence (HTTP, email, file transfers, etc.) that would otherwise be inaccessible. This mirrors password recovery in encrypted file system forensics.

### 5.4 Legal and Ethical Considerations in Breaking Encryption

**Authorization Requirements:**
- Explicit permission from network owner
- Legal warrant or court order when applicable
- Clear scope of investigation documented
- Proper chain of custody for any recovered passwords

**Ethical Guidelines:**
- Only access networks you are authorized to test
- Minimize disruption to legitimate users
- Protect privacy of uninvolved parties
- Report findings through proper channels

**Documentation:**
- Authorization documents
- Methodology used for decryption
- Tools and versions employed
- Time and date of successful decryption
- Evidence handling procedures

---

## Module 6: Forensic Tools and Frameworks

### 6.1 Comprehensive Tool Overview

**Wireshark/Tshark:**
- **Purpose:** Protocol analysis and packet inspection
- **Strengths:** Extensive protocol support, powerful filtering, cross-platform
- **Use Case:** Detailed analysis of captured traffic
- **Reference:** https://www.wireshark.org/docs/

**Aircrack-ng Suite:**
- **Components:** Airmon-ng, Airodump-ng, Aireplay-ng, Aircrack-ng
- **Purpose:** Wireless security testing and password recovery
- **Use Case:** Handshake capture, WEP/WPA cracking
- **Reference:** https://www.aircrack-ng.org/documentation.html

**Kismet:**
- **Purpose:** Wireless network detector and IDS
- **Strengths:** Passive detection, works with multiple capture sources
- **Use Case:** Network discovery, rogue AP detection
- **Reference:** https://www.kismetwireless.net/docs/

**Ettercap:**
- **Purpose:** Man-in-the-middle attack framework
- **Use Case:** ARP poisoning, traffic interception
- **Note:** For authorized testing only

**Bettercap:**
- **Purpose:** Modern network attack and monitoring framework
- **Strengths:** Modular, powerful scripting, multiple attack vectors
- **Use Case:** Network reconnaissance, MITM attacks (authorized only)

**Hashcat:**
- **Purpose:** GPU-accelerated password recovery
- **Strengths:** Extremely fast, supports numerous hash types
- **Use Case:** WPA/WPA2 handshake cracking

### 6.2 Creating a Forensic Wireless Lab

**Hardware Requirements:**
- Compatible wireless adapter supporting monitor mode (e.g., Alfa AWUS036ACH)
- Multiple adapters for simultaneous monitoring on different channels
- Portable computer for field investigations
- GPS device for location tracking (optional)
- External antennas for extended range (optional)

**Software Stack:**
- Kali Linux or similar security-focused distribution
- Wireshark with appropriate plugins
- Aircrack-ng suite (latest version)
- Kismet
- Python with Scapy for custom analysis

**Testing Environment:**
Create isolated test networks:
- Dedicated router with various security configurations
- Test clients (virtual machines or physical devices)
- No connection to production networks
- Proper RF shielding if necessary

---

## Module 7: Case Study Analysis

### Case Study 1: Rogue Access Point Investigation

**Scenario:**
A financial institution detects unusual outbound traffic patterns. Network security suspects an internal breach.

**Investigation Steps:**

1. **Initial Detection:**
   - SIEM alerts show unexpected internal traffic
   - Network scan reveals unauthorized wireless network with corporate SSID

2. **Evidence Collection:**
   - Deploy mobile monitoring station near suspected area
   - Capture wireless traffic from rogue AP
   - Document all connected clients and their activities

3. **Analysis:**
   - MAC address OUI reveals consumer-grade hardware
   - Traffic analysis shows data exfiltration to external IP
   - Correlate client MAC addresses with employee device registry

4. **Physical Location:**
   - Use directional antenna and signal strength triangulation
   - Locate rogue AP in employee break room
   - Device identified as personal router

5. **Findings:**
   - Employee installed personal router for better Wi-Fi coverage
   - Unintentionally created bridge to internal network
   - No malicious intent but significant security exposure

**Lessons Learned:**
- Importance of regular wireless audits
- Need for employee security awareness training
- Value of automated rogue AP detection systems

### Case Study 2: Wireless Network Attack Investigation

**Scenario:**
E-commerce company reports suspected data breach. Forensic team investigates possible wireless attack vector.

**Investigation Process:**

1. **Initial Assessment:**
   - Review incident timeline
   - Interview staff about suspicious activities
   - Check physical security logs

2. **Wireless Traffic Analysis:**
   - Examine archived wireless logs
   - Identify deauthentication attack patterns
   - Discover evil twin access point during incident timeframe

3. **Evidence Recovery:**
   - Analyze captured handshakes
   - Identify attacker's device through probe requests
   - Correlate with physical security camera footage

4. **Attribution:**
   - Device MAC address matches visitor log
   - Video evidence shows individual with laptop near entrance
   - Timing correlates with packet captures

5. **Outcome:**
   - Attacker successfully captured credentials from employees
   - Incident led to enhanced wireless security measures
   - Evidence supported law enforcement prosecution

---

## Module 8: Best Practices and Legal Compliance

### 8.1 Chain of Custody

Proper documentation is critical for legal admissibility:

**Required Documentation:**
- Date, time, and location of evidence collection
- Identity of person collecting evidence
- Description of evidence collected
- Storage and handling procedures
- Any transfers of custody
- Analysis performed and by whom

**Evidence Storage:**
- Use write-protected media when possible
- Calculate and document hash values (MD5, SHA-256)
- Store in secure, access-controlled environment
- Maintain backup copies

### 8.2 Report Writing

**Essential Report Components:**
1. Executive Summary
2. Investigation scope and authorization
3. Methodology and tools used
4. Findings with supporting evidence
5. Timeline of events
6. Conclusions and recommendations
7. Appendices with technical details

**Report Quality Characteristics:**
- Clear, concise language
- Technically accurate
- Supported by evidence
- Objective and unbiased
- Properly cited sources

### 8.3 Legal Considerations

**Key Legal Frameworks:**
- Electronic Communications Privacy Act (ECPA)
- Computer Fraud and Abuse Act (CFAA)
- State-specific wiretapping laws
- International laws (GDPR for EU, etc.)

**Authorization Requirements:**
- Written permission from network owner
- Court orders for criminal investigations
- Scope limitations clearly defined
- Privacy protections for uninvolved parties

---

## Course Completion

Upon achieving a passing score of 70% or higher on the Check on Learning Quiz, you will have demonstrated competency in:

✓ Wireless network forensics fundamentals  
✓ Wi-Fi traffic analysis techniques  
✓ Rogue access point identification and investigation  
✓ Wireless encryption protocols and decryption methods  
✓ Legal and ethical considerations in wireless forensics  
✓ Tool proficiency for wireless investigations  
✓ Evidence collection and chain of custody procedures  
✓ Forensic report writing and presentation  

**Recommended Next Steps:**
1. Set up a personal wireless forensics lab for practice
2. Participate in Capture The Flag (CTF) competitions with wireless challenges
3. Pursue relevant professional certifications (GCFA, GNFA, CWNP)
4. Join professional organizations (HTCIA, IACIS, InfraGard)
5. Continue education with advanced courses in digital forensics
6. Practice ethical disclosure and stay current with emerging wireless technologies

