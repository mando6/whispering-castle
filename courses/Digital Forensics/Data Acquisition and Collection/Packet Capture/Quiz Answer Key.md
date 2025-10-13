### Section A: Multiple Choice

1. **C** - Promiscuous mode captures all packets on the network segment, not just those destined for the interface
2. **C** - tcpdump is ideal for command-line, remote packet capture
3. **B** - SPAN ports can drop packets under heavy load, while TAPs provide complete capture
4. **B** - `http.request.method == "POST"` is the correct Wireshark display filter
5. **B** - Follow TCP Stream reconstructs the complete conversation between endpoints
6. **C** - Chain of custody ensures evidence admissibility in legal proceedings
7. **B** - DNS tunneling is used for data exfiltration and C2 channels
8. **C** - The `-w` option writes packets to a file
9. **C** - Metadata (IPs, ports, timing) remains visible in encrypted traffic
10. **C** - SYN flood attacks send multiple SYN packets without completing handshakes
11. **B** - BPF stands for Berkeley Packet Filter
12. **B** - Capture filters are applied during capture to reduce file size
13. **D** - Packet capture operates primarily at the Network Access Layer
14. **C** - TAPs provide no packet loss and undetectable operation
15. **B** - Hash values should be generated before analysis to ensure integrity
16. **C** - SIP (Session Initiation Protocol) handles VoIP call setup
17. **B** - `-nn` disables name resolution for both hosts and ports
18. **C** - The Statistics menu provides flow graphs and conversation analysis
19. **B** - Proper authorization and legal compliance are required
20. **C** - .pcap and .pcapng are standard Wireshark capture formats

### Section B: True/False

21. **True** - Display filters can be changed dynamically during analysis
22. **False** - tcpdump is available on Unix-like systems including BSD and macOS
23. **False** - Passive TAPs introduce no latency (they're passive devices)
24. **False** - Encrypted content requires private keys or session keys to decrypt
25. **True** - Following TCP streams reconstructs complete data exchanges
26. **False** - Capture filters use BPF syntax; display filters use different syntax
27. **True** - Promiscuous mode captures all visible packets on the segment
28. **False** - SPAN configurations are visible in switch configurations
29. **True** - Regular beaconing is a common C2 communication pattern
30. **True** - Hash values are critical for evidence integrity verification

### Section C: Short Answer - Sample Answers

**31. Capture Filters vs. Display Filters**

*Key points for full credit:*
- Capture filters: Applied during capture using BPF syntax, reduce file size, cannot be changed after capture, permanently exclude data
- Display filters: Applied to captured data, can be changed dynamically, more powerful/flexible syntax, no permanent data loss
- Use capture filters when: Storage is limited, capturing on high-traffic networks, need to focus on specific traffic
- Use display filters when: Need flexibility in analysis, want to preserve all data, performing detailed forensic investigation
- Trade-offs: Capture filters risk excluding relevant evidence but save space; display filters preserve everything but create larger files

**32. Data Exfiltration Indicators**

*Key points for full credit:*
- Large outbound data transfers: HTTP/HTTPS POST requests with large payload sizes, FTP PUT operations, unusual upload volumes
- Connections to personal cloud storage: Dropbox, Google Drive, OneDrive IPs or domains from corporate workstations
- Unusual protocols or ports: Data tunneling through DNS, ICMP, or non-standard ports
- Time-based patterns: Large transfers during off-hours, unusual access times
- Compressed or encrypted files: Large .zip, .rar, or encrypted containers being transmitted
- Filter examples: `frame.len > 1400 && ip.src == [internal_IP]`, `http.request.method == "POST"`, DNS queries with unusually long names

**33. Malware Infection Analysis Steps**

*Key points for full credit:*
- Step 1: Identify initial compromise - Look for suspicious downloads, email attachments, exploit kit traffic, malicious URLs
- Step 2: Extract IOCs - Document malicious IPs, domains, file hashes, URLs from initial infection
- Step 3: Track C2 communications - Filter for external connections, identify beaconing patterns, unusual protocols
- Step 4: Analyze lateral movement - Look for SMB traffic to other hosts, remote execution attempts, credential harvesting
- Step 5: Document data access/exfiltration - Identify accessed resources, data transferred outbound
- Step 6: Create timeline - Establish chronological sequence of events from infection to current state
- Step 7: Extract artifacts - Save malware samples, C2 communications, affected file lists

**34. Documentation and Chain of Custody**

*Key points for full credit:*
- Ensures evidence admissibility in legal proceedings
- Proves evidence integrity and hasn't been tampered with
- Establishes who collected, handled, and analyzed evidence
- Required information: Date/time of capture, capturing personnel, capture location/device, network topology, tool versions, capture parameters/filters, file hash values (MD5/SHA-256)
- Continuous documentation of evidence custody transfers
- Proper storage on forensic write-protected media
- Legal authorization documentation
- Analysis methodology documentation

**35. TAPs vs. SPAN Ports**

*Key points for full credit:*
- Network TAPs: Hardware devices, passive operation, no packet loss, undetectable, fail-safe, higher cost, requires physical installation
- SPAN Ports: Software configuration, potential packet loss under load, visible in switch config, lower cost, performance overhead on switch, easier to deploy
- Choose TAPs when: Complete packet capture is mandatory, detection must be prevented, high-traffic environments, legal/compliance requirements demand complete evidence
- Choose SPAN when: Budget is limited, temporary monitoring is needed, acceptable risk of packet loss, quick deployment required
- Hybrid approach: Use both for redundancy in critical investigations