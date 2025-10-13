### Section 1: Network Topologies

1. **Answer: C** - Star topologies centralize connections at switches, making them primary evidence sources with port-level granularity for traffic capture and device isolation.

2. **Answer: B** - Bus topologies have minimal intelligence, no centralized logging, and broadcast all traffic, making it difficult to isolate specific communications.

3. **Answer: C** - Physical topology reveals the actual hardware layout and physical access points, while logical topology shows data flow paths and monitoring opportunities.

4. **Answer: B** - Mesh topologies have multiple redundant paths, requiring investigators to analyze multiple devices to fully reconstruct traffic flows.

5. **Answer: C** - Dual firewall DMZ configurations provide layered security enforcement and logging at critical boundaries, enhancing evidence availability.

### Section 2: Network Devices

6. **Answer: B** - MAC address tables map devices to switch ports and VLANs, showing device location and movement within the network.

7. **Answer: C** - NAT/PAT tables are essential for correlating private internal IP addresses with public external communications through port mappings.

8. **Answer: B** - Connection logs provide detailed session information including destinations, protocols, data volumes, and duration of the VPN session.

9. **Answer: C** - In APT investigations, prioritize high-severity alerts and look for patterns indicating multi-stage attacks or lateral movement rather than reviewing alerts sequentially.

10. **Answer: C** - Port mirroring (SPAN) copies traffic to a monitoring port, but may drop packets under heavy load, potentially missing evidence.

11. **Answer: B** - NetFlow provides connection metadata (5-tuple) and statistics but does not capture actual packet payloads, limiting deep content analysis.

12. **Answer: B** - VLAN configuration, trunk port settings, and security violation logs are most relevant for investigating VLAN hopping attacks.

13. **Answer: B** - NGFWs provide comprehensive evidence including classification, packet captures, and threat intelligence correlation for deep analysis.

14. **Answer: B** - User identity integration directly attributes network activity to specific individuals, strengthening the evidentiary chain.

15. **Answer: B** - IPS systems operating inline can definitively show whether traffic was blocked or allowed to pass, providing evidence of protective action.

### Section 3: Integration and Investigation Planning

16. **Answer: C** - Volatile data (active connections, NAT tables) should be collected first, followed by time-sensitive logs before rotation, then configurations, then archives.

17. **Answer: A** - Combining router flow data, switch port information, and DHCP logs allows complete correlation from IP address to physical device.

18. **Answer: B** - Lateral movement requires correlating IDS/IPS exploitation alerts, switch traffic patterns, and router segment traversal logs.

19. **Answer: B** - Proper evidence handling requires cryptographic hashing, comprehensive documentation, timestamp preservation, and physical layout recording.

### Section 4: Applied Scenarios

**Question 20 - Scoring Rubric (10 points total):**
- Identifies at least 3 appropriate device types (3 points)
- Describes specific artifacts from each device (3 points)
- Explains how artifacts contribute to timeline reconstruction (2 points)
- Demonstrates understanding of evidence correlation (2 points)

**Sample Strong Answer:**
"I would collect evidence from: (1) **Firewall** - connection logs showing outbound transfers to external IPs with timestamps, user attribution if available, and bytes transferred to quantify exfiltration; (2) **IDS/IPS** - alerts showing initial phishing payload delivery or exploitation, subsequent lateral movement attempts, and packet captures of suspicious traffic for analysis; (3) **File Server's Switch** - MAC address tables and port logs showing which devices accessed the file server during the attack window, correlating with firewall logs. The firewall provides the exfiltration timeline and destination, IDS/IPS shows attack methodology and progression, and switch logs identify the source device and establish physical presence on the network."

**Question 21 - Scoring Rubric (10 points total):**
- Identifies appropriate devices for investigation (2 points)
- Lists specific relevant artifacts (3 points)
- Describes correlation methodology (3 points)
- Demonstrates logical investigation flow (2 points)

**Sample Strong Answer:**
"Investigation plan: (a) **Target devices**: NGFW (user activity), router (NetFlow for external connections), switches (device location/access), IPS (anomaly detection), DHCP server (IP correlation); (b) **Specific artifacts**: From NGFW - VPN logs, connection logs with user identity showing access to file server and cloud storage domains during non-business hours, data transfer volumes; From router - NetFlow records to external cloud IPs, NAT tables for session correlation; From switches - MAC address tables showing connections to file server ports, port logs with timestamps; From IPS - any alerts on unusual file access patterns or large transfers; From DHCP - IP-to-MAC-to-hostname mappings; (c) **Correlation strategy**: Start with NGFW user identity logs to identify suspect's authenticated sessions. Cross-reference session timestamps with router NetFlow to confirm external cloud connections. Use switch port logs to verify physical/logical connection to file server during alleged timeframe. Correlate all IP addresses through DHCP logs to confirm device identity. Compare access patterns against baseline behavior and file server access logs. This multi-source correlation establishes: authentication (who), authorization (access rights), action (file access and transfer), and attribution (linking user to device to activity)."
