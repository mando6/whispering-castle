
### Section A: Multiple Choice

**1. What is the primary advantage of using monitor mode over promiscuous mode in wireless forensics?**
   - a) It consumes less power
   - b) It captures management and control frames without association
   - c) It provides faster packet processing
   - d) It automatically decrypts encrypted traffic

**2. Which encryption protocol is considered fundamentally broken and can be cracked in minutes?**
   - a) WPA2
   - b) WPA3
   - c) WEP
   - d) AES

**3. In the WPA/WPA2 four-way handshake, what does the client send in Message 2?**
   - a) ANonce only
   - b) GTK only
   - c) SNonce and MIC
   - d) PTK only

**4. What is the primary indicator of a deauthentication attack?**
   - a) Increased beacon frame rate
   - b) High volume of deauthentication frames
   - c) Duplicate IP addresses
   - d) Weak signal strength

**5. Which tool is specifically designed for wireless network detection and intrusion detection?**
   - a) Nmap
   - b) Wireshark
   - c) Kismet
   - d) Metasploit

**6. What does BSSID stand for?**
   - a) Basic Service Set Identity
   - b) Basic Service Security Identifier
   - c) Broadcast System Set Identifier
   - d) Basic Service Set Identifier

**7. Which channels in the 2.4 GHz band are non-overlapping in the US?**
   - a) 1, 2, 3
   - b) 1, 6, 11
   - c) 1, 5, 9
   - d) 2, 7, 12

**8. What is a rogue access point?**
   - a) An AP with weak encryption
   - b) An unauthorized AP connected to a network
   - c) A malfunctioning AP
   - d) An AP with low signal strength

**9. Which Wireshark filter shows only beacon frames?**
   - a) wlan.type == beacon
   - b) wlan.fc.type_subtype == 0x08
   - c) frame.type == 0x08
   - d) beacon.filter

**10. What is the main improvement of WPA3 over WPA2?**
   - a) Faster speeds
   - b) Better range
   - c) Protection against offline dictionary attacks using SAE
   - d) Support for more devices

**11. What is the purpose of the EAPOL frame?**
   - a) To broadcast the SSID
   - b) To carry authentication messages for WPA/WPA2
   - c) To deauthenticate clients
   - d) To scan for available networks

**12. Which attack involves creating a fake access point with the same SSID as a legitimate one?**
   - a) Deauthentication attack
   - b) Evil twin attack
   - c) WPS attack
   - d) Fragmentation attack

**13. What does OUI stand for in MAC address analysis?**
   - a) Operational User Interface
   - b) Organizationally Unique Identifier
   - c) Optional User Information
   - d) Operational Unique Identity

**14. Which protocol does WPA2 use for encryption?**
   - a) TKIP
   - b) RC4
   - c) CCMP with AES
   - d) DES

**15. What is the primary purpose of capturing probe requests in wireless forensics?**
   - a) To measure signal strength
   - b) To identify device movement and previously connected networks
   - c) To decrypt traffic
   - d) To authenticate devices

**16. Which command-line tool is used for packet capture in Linux?**
   - a) netstat
   - b) tcpdump
   - c) ifconfig
   - d) traceroute

**17. What is the legal requirement before conducting wireless network forensics?**
   - a) No requirement necessary
   - b) Proper authorization from the network owner
   - c) A computer science degree
   - d) Registration with the FCC

**18. What is the purpose of documenting hash values of evidence?**
   - a) To encrypt the evidence
   - b) To prove integrity and detect tampering
   - c) To compress the files
   - d) To speed up analysis

**19. Which wireless adapter feature is essential for wireless forensics?**
   - a) Bluetooth support
   - b) Monitor mode support
   - c) USB 3.0 interface
   - d) LED indicators

**20. What does the 802.1X protocol provide?**
   - a) Network bandwidth management
   - b) Port-based network access control and authentication
   - c) Wireless channel allocation
   - d) IP address assignment

---

### Section B: True/False

**21. Monitor mode allows capturing packets from all wireless networks in range without association.**
   - True / False

**22. WPA2-Enterprise uses the same encryption key for all users.**
   - True / False

**23. Deauthentication frames can be sent by anyone without authentication.**
   - True / False

**24. Chain of custody documentation is optional in forensic investigations.**
   - True / False

**25. Rainbow tables can speed up WPA/WPA2 password cracking for common SSIDs.**
   - True / False

**26. The 5 GHz band has more non-overlapping channels than the 2.4 GHz band.**
   - True / False

**27. Management frames are always encrypted, even on open networks.**
   - False / True

**28. Wireshark can decrypt WPA2 traffic if you know the password.**
   - True / False

**29. A rogue access point always indicates malicious activity.**
   - True / False

**30. GPS coordinates should be documented when conducting field wireless forensics.**
   - True / False

---

### Section C: Short Answer

**31. Explain the difference between WPA2-Personal and WPA2-Enterprise from a forensic perspective. (3-4 sentences)**

**32. List three indicators that might suggest the presence of a rogue access point in an enterprise environment.**

**33. Describe the four messages in the WPA/WPA2 four-way handshake and explain why capturing this handshake is important for forensic analysis.**

**34. What are three legal considerations that must be addressed before conducting wireless network forensics?**

**35. Explain why management frames are valuable in wireless forensics even when the network uses WPA2 encryption.**

---

### Section D: Practical Scenario

**Read the following scenario and answer the questions:**

You are a digital forensics examiner hired by a healthcare organization to investigate a suspected data breach. Initial analysis suggests the breach may have occurred through the wireless network. You have been granted full authorization to conduct a wireless forensic investigation.

**36. What is the first step you should take before beginning technical analysis, and why is it important?**

**37. You discover three access points broadcasting the organization's SSID. How would you determine which, if any, is a rogue access point?**

**38. While monitoring the wireless network, you capture a complete WPA2 four-way handshake. What tools and methods would you use to attempt to recover the network password, and what are the limitations of this approach?**

**39. You identify unusual deauthentication patterns affecting multiple clients. Describe what this might indicate and what additional evidence you would collect.**

**40. After completing your investigation, you must present findings to both technical staff and hospital executives. What are the key elements that should be included in your forensic report?**
