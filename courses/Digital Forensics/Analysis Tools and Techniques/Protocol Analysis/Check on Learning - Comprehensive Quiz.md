### Section 1: Fundamentals (Questions 1-10)

**Question 1:**
Which layer of the OSI model contains protocols like HTTP, SMTP, and FTP?
- A) Transport Layer
- B) Network Layer
- C) Application Layer
- D) Presentation Layer

**Question 2:**
What is the primary difference between a capture filter and a display filter in Wireshark?
- A) Capture filters are faster
- B) Capture filters are applied during packet capture; display filters are applied to existing captures
- C) Display filters use BPF syntax
- D) There is no difference

**Question 3:**
What does the TCP three-way handshake consist of?
- A) SYN, SYN-ACK, ACK
- B) SYN, ACK, FIN
- C) CONNECT, ACCEPT, CLOSE
- D) REQUEST, RESPONSE, CONFIRM

**Question 4:**
Which file format preserves more metadata and is considered more suitable for forensic purposes?
- A) PCAP
- B) TXT
- C) PCAPNG
- D) CSV

**Question 5:**
What is the primary forensic value of analyzing DHCP traffic?
- A) Identifying malware signatures
- B) Correlating MAC addresses with IP addresses and hostnames
- C) Decrypting encrypted traffic
- D) Monitoring email communications

**Question 6:**
Which port does standard unencrypted HTTP traffic use?
- A) 21
- B) 25
- C) 80
- D) 443

**Question 7:**
What does the "Follow TCP Stream" feature in Wireshark accomplish?
- A) Tracks a single packet through the network
- B) Reconstructs entire bidirectional conversations from packet fragments
- C) Monitors real-time traffic
- D) Filters out TCP traffic

**Question 8:**
Which protocol transmits passwords in cleartext and should be avoided?
- A) SSH
- B) HTTPS
- C) Telnet
- D) SFTP

**Question 9:**
What type of information can you reliably extract from HTTPS traffic WITHOUT decryption keys?
- A) Complete HTTP requests and responses
- B) Passwords and form data
- C) Server Name Indication (SNI), IP addresses, and timing information
- D) Cookie contents

**Question 10:**
What is the primary purpose of the protocol hierarchy statistics in Wireshark?
- A) To display individual packet contents
- B) To show the distribution of protocols in the capture
- C) To decrypt encrypted traffic
- D) To export files from the capture

---

### Section 2: Protocol Analysis (Questions 11-20)

**Question 11:**
In HTTP protocol analysis, what does a POST request typically contain that a GET request does not?
- A) Headers
- B) URL parameters
- C) Request body with form data
- D) Status codes

**Question 12:**
What is the correct sequence of the SMTP email sending process?
- A) CONNECT, SEND, DISCONNECT
- B) HELO/EHLO, MAIL FROM, RCPT TO, DATA, QUIT
- C) LOGIN, COMPOSE, TRANSMIT
- D) AUTHENTICATE, MESSAGE, CLOSE

**Question 13:**
Which email protocol is specifically designed for retrieving email from a server while keeping messages synchronized across multiple devices?
- A) SMTP
- B) POP3
- C) IMAP
- D) FTP

**Question 14:**
What encoding method is commonly used for email attachments?
- A) ASCII
- B) UTF-8
- C) Base64
- D) Hexadecimal

**Question 15:**
In FTP protocol, what are the two channels used?
- A) Input and Output
- B) Control (commands) and Data (file transfers)
- C) Primary and Secondary
- D) Request and Response

**Question 16:**
Which DNS record type is used to resolve a domain name to an IPv4 address?
- A) AAAA
- B) MX
- C) A
- D) CNAME

**Question 17:**
What forensic technique involves searching for file signatures (magic numbers) in packet data to reconstruct files?
- A) File streaming
- B) Data carving
- C) Packet injection
- D) Protocol tunneling

**Question 18:**
Which HTTP status code indicates a successful request?
- A) 404
- B) 500
- C) 200
- D) 302

**Question 19:**
What is DNS tunneling commonly used for in malicious activities?
- A) Speeding up DNS queries
- B) Data exfiltration by encoding data in DNS queries
- C) Legitimate website hosting
- D) Email delivery

**Question 20:**
In Wireshark, which filter would display only HTTP POST requests?
- A) `http.post`
- B) `http.method == POST`
- C) `http.request.method == "POST"`
- D) `post.http`

---

### Section 3: Forensic Applications (Questions 21-30)

**Question 21:**
What is a key indicator of port scanning activity in network traffic?
- A) Large file downloads
- B) Multiple SYN packets to various ports from a single source without established connections
- C) High DNS query volume
- D) Encrypted HTTPS sessions

**Question 22:**
Which of the following is NOT a valid method for decrypting HTTPS traffic in Wireshark?
- A) Using SSL/TLS key log file from browser
- B) Using server's private key (for certain cipher suites)
- C) Using the destination IP address
- D) Deploying a legitimate MITM proxy

**Question 23:**
What is "beaconing" in the context of malware traffic analysis?
- A) Random sporadic connections
- B) Regular, periodic communication patterns typically indicating C&C traffic
- C) Broadcasting to all network hosts
- D) DNS amplification attacks

**Question 24:**
Which Wireshark feature allows you to export files transferred via HTTP?
- A) File → Export → Objects → HTTP
- B) Tools → Extract Files
- C) Edit → Export Data
- D) Analyze → File Recovery

**Question 25:**
What is the primary purpose of establishing a network traffic baseline?
- A) To increase network speed
- B) To identify normal patterns so anomalies can be detected
- C) To block suspicious traffic
- D) To encrypt communications

**Question 26:**
In digital forensics, what is chain of custody?
- A) The network path a packet takes
- B) Documentation tracking evidence handling from collection to presentation
- C) The order of protocols in the OSI model
- D) The sequence of TCP connections

**Question 27:**
Which tool is specifically designed for network forensics and provides automatic protocol parsing and file extraction?
- A) Nmap
- B) Metasploit
- C) NetworkMiner
- D) Burp Suite

**Question 28:**
What should you document when extracting files from packet captures for forensic purposes?
- A) Only the filename
- B) Packet numbers, timestamps, hash values, and extraction methodology
- C) Just the file size
- D) Only the protocol used

**Question 29:**
What type of evidence can be obtained from analyzing email headers?
- A) Only the subject line
- B) Routing path, originating IP, authentication results, and timestamps
- C) Email content only
- D) Attachment names only

**Question 30:**
Why is it important to create forensic copies of packet capture files before analysis?
- A) To save disk space
- B) To preserve original evidence integrity and enable hash verification
- C) To speed up analysis
- D) To compress the files

---

### Section 4: Advanced Topics and Best Practices (Questions 31-40)

**Question 31:**
What legal document typically authorizes law enforcement to intercept network communications in real-time?
- A) Search warrant
- B) Subpoena
- C) Wiretap order (Title III)
- D) Civil summons

**Question 32:**
Which of the following is an indicator of potential data exfiltration?
- A) Normal web browsing
- B) Large outbound transfers to unusual destinations, especially during off-hours
- C) DNS lookups for common websites
- D) Incoming email

**Question 33:**
What does the DORA acronym stand for in DHCP?
- A) Data, Operation, Request, Acknowledgment
- B) Discover, Offer, Request, Acknowledge
- C) Domain, Order, Response, Address
- D) Dynamic, Operational, Reliable, Automatic

**Question 34:**
In VoIP analysis, which protocol carries the actual voice data?
- A) SIP
- B) HTTP
- C) RTP
- D) RTCP

**Question 35:**
What is a significant forensic challenge presented by IPv6?
- A) Smaller address space
- B) Lack of encryption
- C) Much larger address space and privacy extensions complicate tracking
- D) Slower speeds

**Question 36:**
Which Wireshark display filter would show all traffic to or from IP address 192.168.1.100?
- A) `ip == 192.168.1.100`
- B) `ip.addr == 192.168.1.100`
- C) `host 192.168.1.100`
- D) `address = 192.168.1.100`

**Question 37:**
What information can still be analyzed in SSH traffic despite encryption?
- A) Commands executed
- B) Passwords transmitted
- C) Connection timing, duration, data volume, and endpoints
- D) File contents transferred

**Question 38:**
Which of the following best describes promiscuous mode in packet capture?
- A) Capturing only broadcast traffic
- B) Capturing all packets on the network segment, not just those addressed to the capture interface
- C) Capturing encrypted traffic only
- D) Selective packet filtering

**Question 39:**
What is the primary risk of analyzing packet captures that contain unencrypted credentials?
- A) Network slowdown
- B) Exposure of sensitive authentication information requiring secure handling
- C) Increased storage requirements
- D) Compatibility issues

**Question 40:**
Which statistical analysis would best help identify the most active communicating host pairs in a capture?
- A) Protocol Hierarchy
- B) I/O Graphs
- C) Conversations
- D) Expert Info
