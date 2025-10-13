### Section A: Multiple Choice

**1.** What is the primary purpose of using promiscuous mode on a network interface?
- A) To encrypt all captured packets
- B) To capture only packets destined for that interface
- C) To capture all packets on the network segment, not just those destined for the interface
- D) To prevent packet loss during capture

**2.** Which tool is best suited for automated, command-line packet capture on a remote Linux server?
- A) Wireshark
- B) NetworkMiner
- C) tcpdump
- D) Windows Network Monitor

**3.** What is the main disadvantage of using SPAN ports compared to network TAPs?
- A) SPAN ports are more expensive
- B) SPAN ports can drop packets under heavy load
- C) SPAN ports cannot capture bidirectional traffic
- D) SPAN ports are detectable but TAPs are not

**4.** Which Wireshark filter would identify all HTTP POST requests?
- A) `tcp.port == 80 && http.request`
- B) `http.request.method == "POST"`
- C) `http.post == true`
- D) `tcp.http.method == POST`

**5.** What does the "Follow TCP Stream" feature in Wireshark do?
- A) Captures only TCP traffic going forward
- B) Reconstructs and displays the complete conversation between two endpoints
- C) Follows a single packet through the network
- D) Tracks the TCP handshake process

**6.** In digital forensics, why is maintaining chain of custody for packet captures critical?
- A) To ensure faster analysis
- B) To reduce file size
- C) To ensure evidence remains admissible in legal proceedings
- D) To enable real-time monitoring

**7.** What is DNS tunneling commonly used for by attackers?
- A) Improving DNS resolution speed
- B) Exfiltrating data or establishing command and control channels
- C) Blocking DNS queries
- D) Enhancing DNS security

**8.** Which tcpdump option writes captured packets to a file?
- A) `-r`
- B) `-f`
- C) `-w`
- D) `-o`

**9.** What information remains visible even when analyzing encrypted HTTPS traffic?
- A) The content of web pages
- B) Form data and passwords
- C) Source/destination IP addresses, ports, and packet timing
- D) Decrypted HTTP headers

**10.** Which type of attack is characterized by multiple SYN packets without completing the three-way handshake?
- A) Man-in-the-middle attack
- B) DNS poisoning
- C) SYN flood attack
- D) Session hijacking

**11.** What does the BPF acronym stand for in the context of packet filtering?
- A) Binary Packet Format
- B) Berkeley Packet Filter
- C) Basic Protocol Framework
- D) Bidirectional Packet Flow

**12.** When should capture filters be applied?
- A) After the capture is complete
- B) During packet capture to reduce file size
- C) Only when analyzing encrypted traffic
- D) When creating forensic reports

**13.** Which layer of the TCP/IP model does packet capture primarily operate at?
- A) Application Layer
- B) Transport Layer
- C) Internet Layer
- D) Network Access Layer

**14.** What is a key advantage of hardware network TAPs over software-based capture?
- A) Lower cost
- B) Easier to configure
- C) No packet loss and undetectable operation
- D) Can decrypt encrypted traffic

**15.** In a forensic investigation, what should you do before analyzing a packet capture file?
- A) Delete unnecessary packets
- B) Generate and record hash values of the file
- C) Convert it to a different format
- D) Remove all encrypted traffic

**16.** Which protocol is used for VoIP call setup and signaling?
- A) RTP
- B) RTCP
- C) SIP
- D) HTTP

**17.** What does the `-nn` option do in tcpdump?
- A) Enables name resolution for hosts and ports
- B) Disables name resolution for both hosts and ports
- C) Captures only named packets
- D) Creates numbered output files

**18.** Which Wireshark menu provides flow graphs and conversation analysis?
- A) File
- B) Edit
- C) Statistics
- D) Analyze

**19.** What is the primary legal requirement before capturing network traffic in a corporate environment?
- A) Employee notification via email
- B) Proper authorization and compliance with privacy laws
- C) Installing antivirus software
- D) Creating backup copies

**20.** Which file format is the standard output for Wireshark captures?
- A) .txt
- B) .log
- C) .pcap or .pcapng
- D) .cap

---

### Section B: True/False

**21.** Display filters in Wireshark can be changed dynamically while viewing a capture file.
- True
- False

**22.** tcpdump can only capture traffic on Linux systems.
- True
- False

**23.** Network TAPs introduce latency and can slow down network performance.
- True
- False

**24.** Packet capture can reveal the actual content of encrypted HTTPS communications without private keys.
- True
- False

**25.** Following TCP streams in Wireshark can help reconstruct file transfers and conversations.
- True
- False

**26.** Capture filters use the same syntax as display filters in Wireshark.
- True
- False

**27.** In promiscuous mode, a network interface captures all packets on the network segment it can see.
- True
- False

**28.** SPAN port configurations are invisible and cannot be detected by network administrators.
- True
- False

**29.** Malware often uses regular beaconing patterns to communicate with command and control servers.
- True
- False

**30.** Hash values (MD5, SHA-256) of capture files are important for maintaining evidence integrity.
- True
- False

---

### Section C: Short Answer

**31.** Explain the difference between capture filters and display filters in Wireshark. When would you use each, and what are the trade-offs?

**32.** Describe three specific indicators you would look for in packet captures that might suggest a data exfiltration attempt. Include the types of protocols and traffic patterns you would analyze.

**33.** You are investigating a suspected malware infection. Walk through the steps you would take to analyze the packet capture, from identifying the initial compromise to documenting command and control communications.

**34.** Explain why proper documentation and chain of custody are critical when capturing network traffic for forensic investigations. What specific information should be documented? 

**35.** Compare and contrast network TAPs and SPAN ports for forensic packet capture. In what scenarios would you choose one over the other? 
