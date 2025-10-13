
### Section A: Multiple Choice Answers

1. **b** - Monitor mode captures management and control frames without association
2. **c** - WEP is fundamentally broken and easily cracked
3. **c** - The client sends SNonce and MIC in Message 2
4. **b** - High volume of deauthentication frames indicates deauth attack
5. **c** - Kismet is designed for wireless detection and IDS
6. **d** - BSSID = Basic Service Set Identifier (MAC address of AP)
7. **b** - Channels 1, 6, and 11 are non-overlapping
8. **b** - A rogue AP is an unauthorized AP on the network
9. **b** - wlan.fc.type_subtype == 0x08 filters beacon frames
10. **c** - WPA3 uses SAE to protect against offline dictionary attacks
11. **b** - EAPOL carries authentication messages for WPA/WPA2
12. **b** - Evil twin attack uses a fake AP with same SSID
13. **b** - OUI = Organizationally Unique Identifier
14. **c** - WPA2 uses CCMP with AES encryption
15. **b** - Probe requests reveal device movement and network history
16. **b** - tcpdump is the command-line packet capture tool
17. **b** - Proper authorization is legally required
18. **b** - Hash values prove integrity and detect tampering
19. **b** - Monitor mode support is essential for forensics
20. **b** - 802.1X provides port-based network access control

### Section B: True/False Answers

21. **True** - Monitor mode captures all frames without association
22. **False** - WPA2-Enterprise uses unique per-user session keys
23. **True** - Deauth frames can be sent unauthenticated (security flaw)
24. **False** - Chain of custody is mandatory for legal admissibility
25. **True** - Rainbow tables pre-compute hashes for common SSIDs
26. **True** - 5 GHz has significantly more non-overlapping channels
27. **False** - Management frames are typically unencrypted
28. **True** - Wireshark can decrypt traffic with the password
29. **False** - Rogue APs can be accidental (shadow IT)
30. **True** - GPS coordinates aid in physical location documentation

### Section C: Short Answer Sample Answers

**31. WPA2-Personal vs WPA2-Enterprise:**
WPA2-Personal uses a pre-shared key (PSK) that is the same for all users, making it possible to decrypt all traffic if the password is recovered. WPA2-Enterprise uses 802.1X authentication with unique per-user credentials and session keys, meaning each user has different encryption keys. From a forensic perspective, cracking WPA2-Personal gives access to all network traffic, while WPA2-Enterprise requires individual user credentials or access to the RADIUS server, making it significantly more challenging to decrypt traffic.

**32. Three indicators of a rogue access point:**
- An SSID matching the organization's network but with an unknown or suspicious BSSID
- MAC address OUI that doesn't match authorized vendor hardware
- Access point broadcasting on an unusual channel or appearing in an unexpected physical location
- (Bonus: Duplicate SSID with weaker security settings, unexpected signal strength patterns)

**33. WPA/WPA2 Four-Way Handshake:**
Message 1: The access point sends the ANonce (authenticator nonce) to the client. Message 2: The client responds with its SNonce (supplicant nonce) and a Message Integrity Check (MIC). Message 3: The AP sends the Group Temporal Key (GTK) to the client. Message 4: The client acknowledges receipt. Capturing this handshake is crucial because it contains the information needed to perform offline password cracking attempts, and if successful, allows decryption of all captured traffic from that session.

**34. Three legal considerations:**
- Obtaining explicit written authorization from the network owner or proper legal authority (warrant/court order)
- Understanding and complying with relevant laws such as the Wiretap Act, ECPA, and CFAA
- Ensuring proper chain of custody documentation to maintain evidence admissibility in legal proceedings
- (Bonus: Protecting privacy of uninvolved parties, defining clear scope limitations)

**35. Management frames value in forensics:**
Management frames (such as beacons, probe requests/responses, and authentication frames) are typically transmitted unencrypted even on WPA2-encrypted networks. These frames reveal valuable information including SSIDs, MAC addresses (BSSIDs and client addresses), supported encryption types, network capabilities, device manufacturers (via OUI), and client movement patterns through probe requests. This information is crucial for network mapping, device identification, and establishing connections between devices and access points without needing to decrypt the network.

### Section D: Practical Scenario Sample Answers

**36. First step before technical analysis:**
The first step is to thoroughly document the authorization to conduct the investigation, including obtaining written permission from appropriate hospital authority, defining the scope of the investigation, and ensuring compliance with healthcare regulations (HIPAA). This is critical because it establishes legal authority to intercept wireless communications, protects the examiner from potential legal liability, ensures evidence admissibility, and defines the boundaries of what can be investigated. Additionally, you should document the chain of custody procedures that will be followed throughout the investigation.

**37. Determining rogue access points:**
To identify rogue APs among the three with matching SSIDs, I would: (1) Compare the BSSIDs against the organization's authorized access point inventory/asset database to identify any unknown MAC addresses; (2) Analyze the MAC address OUI to determine the manufacturer and verify it matches authorized hardware vendors; (3) Perform physical triangulation using signal strength measurements to locate each AP and verify it matches known AP locations; (4) Examine the security configuration and channel assignments to identify any deviations from standard policy; (5) Cross-reference the APs with network management system logs and wired network infrastructure to verify legitimate network connections.

**38. Password recovery tools and methods:**
To attempt password recovery from the captured WPA2 handshake, I would: (1) Use Aircrack-ng with healthcare/medical-themed wordlists and common password patterns; (2) Employ Hashcat with GPU acceleration for faster processing, using dictionary attacks followed by hybrid attacks combining wordlists with rules; (3) Consider creating custom wordlists based on the organization's naming conventions, medical terminology, and publicly available information about the organization. Limitations include: the process is only successful if the password is weak or in the wordlist; strong, random passwords are essentially impossible to crack; the process can be time-consuming even with powerful hardware; and there are legal/ethical considerations about the extent of cracking attempts. Additionally, if the handshake wasn't captured completely or was corrupted, the attack will fail.

**39. Unusual deauthentication patterns:**
Unusual deauthentication patterns affecting multiple clients likely indicate a deauthentication attack, possibly as part of an evil twin attack or attempt to capture WPA handshakes. This could suggest an active wireless attack in progress. Additional evidence to collect would include: (1) Full packet capture of all deauthentication frames, noting source MAC addresses, reason codes, and timing patterns; (2) Complete list of all access points visible, looking for evil twin/rogue APs; (3) Physical security camera footage from the time period to identify potential attackers; (4) Logs from the legitimate access points to correlate events; (5) Analysis of probe requests to identify the attacking device; (6) Any unusual client reconnection patterns or connections to unauthorized APs; (7) Temporal correlation with any reported user issues or security alerts.

**40. Key elements in the forensic report:**
The forensic report should include: (1) Executive Summary with high-level findings in non-technical language for hospital executives, including business impact and risk assessment; (2) Scope and Authorization section documenting the legal authority and investigation parameters; (3) Methodology section detailing tools used (with versions), procedures followed, and analytical techniques employed; (4) Detailed technical findings for IT staff, including evidence of any breaches, rogue APs, attack patterns, and vulnerabilities discovered; (5) Timeline of events correlating wireless activities with any known incidents; (6) Assessment of data exposure and potential HIPAA implications; (7) Recommendations for immediate remediation and long-term security improvements; (8) Chain of custody documentation; (9) Technical appendices with packet captures, tool outputs, and supporting evidence; (10) Conclusion summarizing findings and their significance to the organization's security posture.
