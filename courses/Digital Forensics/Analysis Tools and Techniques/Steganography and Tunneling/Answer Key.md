### Section A - Multiple Choice
1. **B** - Steganography hides the existence of data, while encryption makes data unreadable
2. **B** - Least Significant Bit (LSB) substitution
3. **B** - The ability to encode data in subdomain names and DNS responses
4. **A** - Large or unusual payload sizes in ICMP packets
5. **C** - Checking for encryption strength (DNS tunneling detection focuses on behavioral patterns)
6. **C** - Preservation
7. **B** - Whitespace steganography
8. **C** - Wireshark
9. **B** - Secure remote access and port forwarding
10. **B** - Traffic is encrypted, making content inspection difficult

### Section B - Short Answer (Sample Answers)

**Question 11:**
DNS is attractive for data exfiltration because: (1) DNS traffic is essential for network operations and is rarely blocked by firewalls, (2) DNS queries and responses can carry arbitrary data in subdomain names and various record types, (3) many organizations don't monitor DNS traffic as closely as other protocols, and (4) DNS typically uses UDP which doesn't require connection establishment, making it lightweight and fast.

**Question 12:**
Two statistical techniques for detecting image steganography:
- **Chi-square test:** Analyzes the distribution of pixel values to detect anomalies introduced by LSB modification. The test compares expected vs. observed frequency distributions.
- **RS (Regular-Singular) analysis:** Examines how pixels in groups change when LSBs are flipped. Steganographic content creates asymmetry in these groups that can be statistically measured.

**Question 13:**
Three key logs for HTTP tunneling investigation:
- **Proxy logs:** Show complete URL requests, user agents, and response sizes - critical for identifying suspicious domains and unusual request patterns
- **Firewall logs:** Reveal connection attempts, blocked/allowed traffic, and external IP addresses - helps establish network-level context
- **Web server logs:** If internal server is involved, shows incoming connections and can reveal compromised systems acting as relay points

**Question 14:**
Chain of custody is the chronological documentation of evidence handling from collection through presentation. It records who collected, transferred, analyzed, and stored evidence, along with dates and times. It's critical because it establishes evidence integrity and admissibility in legal proceedings by proving the evidence wasn't tampered with or altered.

**Question 15:**
Three behavioral indicators of covert communication:
- **Regular beaconing patterns:** Consistent, periodic network connections at fixed intervals (e.g., every 5 minutes)
- **Unusual outbound connections:** Systems connecting to unusual external IPs, newly registered domains, or known malicious infrastructure
- **Abnormal protocol usage:** Non-server systems generating high volumes of DNS queries, or workstations using protocols like SSH to external destinations

### Section C - Scenario-Based (Sample Answers)

**Question 16:**
a) **Forensic steps:**
   - Immediately capture live DNS traffic using tcpdump/Wireshark
   - Isolate the workstation from network (contain potential data loss)
   - Acquire system memory dump and hard drive image
   - Extract DNS query logs from local DNS cache and network devices
   - Document all actions with timestamps

b) **Tools:**
   - Wireshark for packet capture and analysis
   - Python with Scapy for automated subdomain decoding
   - Volatility for memory analysis
   - Process monitoring tools to identify the responsible application
   - WHOIS/DNS reconnaissance tools for domain information

c) **Additional evidence:**
   - System event logs (process execution, login events)
   - Network connection logs from host-based firewall
   - Email logs (potential phishing vector)
   - Recent file modifications
   - Browser history and downloads
   - Correlation with IDS/IPS alerts for same timeframe

**Question 17:**
a) **Why suspicious:**
   - Normal ICMP echo requests have small payloads (32-64 bytes)
   - 1,200-byte payloads suggest data is being embedded
   - Regular 30-second intervals indicate automated beaconing
   - Server-to-external communication via ICMP is highly unusual

b) **Payload extraction and analysis:**
   - Use Wireshark to filter ICMP traffic: `icmp`
   - Export packet bytes and extract payload section (after ICMP header)
   - Analyze payload for patterns: base64 encoding, compression, encryption
   - Use hex editors and scripting to decode/decompress data
   - Look for file headers, ASCII strings, or structured data
   - Compare multiple packets to identify transmission patterns

c) **Other indicators to investigate:**
   - Check firewall logs for the external IP address
   - Investigate the internal server for compromise indicators
   - Search for process with high network activity
   - Review authentication logs on the server
   - Check for scheduled tasks or cron jobs
   - Examine recent software installations or modifications

**Question 18:**
a) **Detection techniques:**
   - Calculate expected file sizes based on dimensions and quality
   - Perform LSB analysis on pixel data
   - Run chi-square statistical tests
   - Conduct histogram analysis for distribution anomalies
   - Check EXIF metadata for unusual entries
   - Compare file entropy (randomness) against known clean images

b) **Appropriate tools:**
   - StegDetect or StegExpose for automated detection
   - OpenStego for extraction attempts
   - ExifTool for metadata analysis
   - Python PIL/Pillow for custom LSB analysis
   - Hex editors (HxD, 010 Editor) for manual inspection
   - StegSpy or Steganalysis tools

c) **Evidence preservation steps:**
   - Calculate and document cryptographic hashes (SHA-256) immediately
   - Create forensic copies using write-blocking devices
   - Store original files in secure, tamper-evident containers
   - Document chain of custody
   - Extract hidden data to separate evidence files
   - Photograph/screenshot extraction process
   - Maintain both original and extracted data with clear labels
   - Store in multiple locations with access controls

### Section D - True/False

**Question 19:** **False** - Encrypted traffic can still contain steganographic data. The steganography could be applied before encryption, or data could be hidden in protocol metadata that isn't encrypted.

**Question 20:** **False** - While some tunneling techniques benefit from elevated privileges, many can be executed with standard user permissions, especially application-layer tunneling like DNS or HTTP.

**Question 21:** **False** - Statistical analysis provides strong indicators but cannot definitively prove steganography without actually extracting and identifying hidden content. False positives are possible.

**Question 22:** **False** - TXT records have legitimate uses (SPF records, domain verification, etc.). However, excessive TXT queries or queries with unusual patterns may indicate DNS tunneling.

**Question 23:** **False** - Chain of custody is important for all investigations where evidence may be used in any proceeding, including internal disciplinary actions, civil litigation, or regulatory compliance.

**Question 24:** **False** - AI and ML are powerful tools that augment human analysis but cannot completely replace human judgment, contextual understanding, and ethical decision-making.

**Question 25:** **True** - WebSockets establish persistent, bidirectional connections over HTTP/HTTPS that can be used for real-time covert communications, making them more difficult to detect than traditional request-response patterns.
