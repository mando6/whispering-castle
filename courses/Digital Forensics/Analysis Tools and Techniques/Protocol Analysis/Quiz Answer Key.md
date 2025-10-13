### Section 1: Fundamentals
1. **C** - Application Layer contains HTTP, SMTP, FTP, and other user-facing protocols
2. **B** - Capture filters are applied during capture and reduce file size; display filters work on existing captures
3. **A** - SYN, SYN-ACK, ACK is the three-way handshake
4. **C** - PCAPNG preserves metadata better than standard PCAP
5. **B** - DHCP provides MAC-to-IP correlation and hostname information
6. **C** - Port 80 is standard HTTP (443 is HTTPS)
7. **B** - Follow TCP Stream reconstructs complete bidirectional conversations
8. **C** - Telnet transmits credentials in cleartext
9. **C** - Without decryption, you can see SNI, IPs, timing, and metadata
10. **B** - Protocol hierarchy shows distribution of protocols in the capture

### Section 2: Protocol Analysis
11. **C** - POST requests contain a request body with form data
12. **B** - Correct SMTP sequence: HELO/EHLO, MAIL FROM, RCPT TO, DATA, QUIT
13. **C** - IMAP keeps messages synchronized across devices
14. **C** - Base64 encoding is standard for email attachments
15. **B** - FTP uses Control channel (port 21) and Data channel
16. **C** - A records resolve to IPv4 addresses (AAAA for IPv6)
17. **B** - Data carving reconstructs files from packet data using signatures
18. **C** - 200 indicates success (404 = Not Found, 500 = Server Error)
19. **B** - DNS tunneling is used for data exfiltration
20. **C** - `http.request.method == "POST"` is the correct filter

### Section 3: Forensic Applications
21. **B** - Multiple SYN packets to various ports indicates port scanning
22. **C** - IP address alone cannot decrypt HTTPS
23. **B** - Beaconing is regular, periodic C&C communication
24. **A** - File → Export Objects → HTTP extracts files
25. **B** - Baseline establishes normal patterns to detect anomalies
26. **B** - Chain of custody documents evidence handling
27. **C** - NetworkMiner specializes in network forensics
28. **B** - Document packet numbers, timestamps, hashes, and methodology
29. **B** - Email headers reveal routing, IP, authentication, and timing
30. **B** - Forensic copies preserve original evidence integrity

### Section 4: Advanced Topics
31. **C** - Title III wiretap order authorizes real-time interception
32. **B** - Large outbound transfers to unusual destinations suggest exfiltration
33. **B** - DORA: Discover, Offer, Request, Acknowledge
34. **C** - RTP carries actual voice/video data (SIP is for setup)
35. **C** - IPv6's large address space and privacy features complicate tracking
36. **B** - `ip.addr == 192.168.1.100` shows traffic to/from that IP
37. **C** - SSH metadata (timing, endpoints, volume) is visible despite encryption
38. **B** - Promiscuous mode captures all packets on the segment
39. **B** - Unencrypted credentials require secure handling to prevent exposure
40. **C** - Conversations statistic shows communicating host pairs
