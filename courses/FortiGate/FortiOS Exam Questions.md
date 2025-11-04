## 1. System and Network Settings

**Question 1.1** (Multiple Choice)  
What is the first step when configuring a FortiGate device from factory default settings?
- A) Configure firewall policies
- B) Set up administrator access and network interfaces
- C) Enable logging
- D) Configure VPN tunnels

**Question 1.2** (Short Answer)  
Explain the difference between using the GUI and CLI for FortiGate administration. When would you prefer one over the other?

**Question 1.3** (Multiple Choice)  
Which of the following methods can be used for FortiGate device registration?
- A) FortiCloud registration
- B) Email verification
- C) SMS authentication
- D) Both A and B

**Question 1.4** (Scenario)  
Your company has just received a new FortiGate device. Describe the initial configuration steps required to establish basic network connectivity, including interface configuration and default gateway settings.

## 2. Logging and Monitoring

**Question 2.1** (Multiple Choice)  
Which device can be used in conjunction with FortiGate to provide centralized log management and analysis?
- A) FortiManager
- B) FortiAnalyzer
- C) FortiClient
- D) FortiSwitch

**Question 2.2** (Short Answer)  
What are three key parameters you can use to filter and search for specific logs in FortiGate?

**Question 2.3** (Scenario)  
A security incident occurred at 2:30 PM yesterday. Walk through the steps you would take to locate relevant logs on FortiAnalyzer to investigate the incident.

**Question 2.4** (True/False)  
FortiGate can only send logs to FortiAnalyzer and cannot store logs locally on its hard drive or flash memory.

## 3. Firewall Policies and NAT

**Question 3.1** (Multiple Choice)  
In IPv4 firewall policies, what is the correct order of evaluation?
- A) Bottom to top
- B) Top to bottom
- C) Based on priority number
- D) Random order

**Question 3.2** (Scenario)  
Your organization needs to allow external users to access an internal web server (IP: 192.168.1.100, port 443) using the public IP 203.0.113.50. Which type of NAT would you configure, and what are the key configuration parameters?

**Question 3.3** (Short Answer)  
Explain the difference between source NAT (SNAT) and destination NAT (DNAT). Provide an example use case for each.

**Question 3.4** (Multiple Choice)  
Port forwarding is a type of:
- A) Source NAT
- B) Destination NAT
- C) Static NAT
- D) Dynamic NAT

**Question 3.5** (Fill in the Blank)  
When multiple internal hosts share a single public IP address to access the internet, this is called __________.

## 4. Routing

**Question 4.1** (Short Answer)  
What command would you use in the CLI to view the complete route table on a FortiGate device?

**Question 4.2** (Multiple Choice)  
Which routing metric is used by default in FortiGate to determine the best path when multiple routes to the same destination exist?
- A) Hop count
- B) Bandwidth
- C) Administrative distance
- D) Cost

**Question 4.3** (Scenario)  
You have two ISP connections on your FortiGate. Configure route redundancy so that if the primary ISP fails, traffic automatically switches to the secondary ISP. What features and settings would you implement?

**Question 4.4** (Short Answer)  
Explain how to implement route-based load balancing across multiple WAN links in FortiGate.

**Question 4.5** (Multiple Choice)  
What is the administrative distance of a static route by default in FortiGate?
- A) 1
- B) 5
- C) 10
- D) 20

## 5. Firewall Authentication

**Question 5.1** (Multiple Choice)  
Which protocol uses UDP port 1812 by default for authentication?
- A) LDAP
- B) RADIUS
- C) TACACS+
- D) Kerberos

**Question 5.2** (Scenario)  
Your company wants to authenticate VPN users against an existing Microsoft Active Directory. Would you configure LDAP or RADIUS, and what are the key configuration steps on FortiGate?

**Question 5.3** (Short Answer)  
Describe three ways to monitor active firewall users from the FortiGate GUI.

**Question 5.4** (True/False)  
LDAP typically uses port 389 for non-encrypted communication and port 636 for LDAPS (LDAP over SSL).

**Question 5.5** (Fill in the Blank)  
The __________ protocol is commonly used for centralized authentication, authorization, and accounting (AAA).

## 6. Fortinet Single Sign-On (FSSO)

**Question 6.1** (Short Answer)  
What is the primary purpose of deploying Fortinet Single Sign-On (FSSO)?

**Question 6.2** (Multiple Choice)  
Which component acts as an intermediary between FortiGate and Microsoft Active Directory in an FSSO deployment?
- A) FSSO Collector Agent
- B) FortiClient
- C) Domain Controller
- D) FortiAuthenticator

**Question 6.3** (Scenario)  
Explain the process of how FSSO identifies and authenticates users when they log into a Windows domain and access network resources through FortiGate.

**Question 6.4** (Multiple Choice)  
FSSO integration with Active Directory allows FortiGate to:
- A) Create firewall policies based on user identity
- B) Bypass all security policies for domain users
- C) Automatically encrypt all traffic
- D) Replace the domain controller

## 7. Certificate Operations

**Question 7.1** (Short Answer)  
Describe the role of digital certificates in encryption and authentication.

**Question 7.2** (Multiple Choice)  
What is the purpose of SSL inspection on FortiGate?
- A) To decrypt and inspect encrypted traffic for threats
- B) To speed up SSL connections
- C) To block all HTTPS traffic
- D) To create SSL certificates

**Question 7.3** (Scenario)  
Your organization needs to implement SSL deep inspection to scan encrypted web traffic for malware. What are the prerequisites and potential challenges you might face?

**Question 7.4** (True/False)  
FortiGate can act as a Certificate Authority (CA) and issue certificates for internal use.

**Question 7.5** (Multiple Choice)  
Which type of SSL inspection requires installing a certificate on client devices?
- A) Certificate Inspection
- B) Deep Inspection
- C) No Inspection
- D) Transparent Inspection

## 8. Antivirus

**Question 8.1** (Multiple Choice)  
Which scanning mode provides the most thorough antivirus protection but may impact performance?
- A) Quick scan
- B) Full scan
- C) Proxy-based inspection
- D) Flow-based inspection

**Question 8.2** (Short Answer)  
Explain the difference between proxy-based and flow-based antivirus scanning in FortiGate.

**Question 8.3** (Scenario)  
A user reports that they cannot download a file from the internet. After investigation, you find it was blocked by the antivirus profile. What steps would you take to verify if this is a false positive and how would you handle it?

**Question 8.4** (Fill in the Blank)  
FortiGate antivirus protection relies on signature updates from __________ to detect known threats.

## 9. Web Filtering

**Question 9.1** (Multiple Choice)  
Which FortiGuard category would you block to prevent users from accessing file-sharing websites like torrent sites?
- A) Malicious Websites
- B) Peer-to-Peer/Freeware
- C) Social Networking
- D) Information Technology

**Question 9.2** (Scenario)  
Your HR department requests that social media websites be accessible only during lunch hours (12:00-13:00). How would you configure web filtering to meet this requirement?

**Question 9.3** (Short Answer)  
What is the difference between FortiGuard Web Filtering and local URL filtering?

**Question 9.4** (Multiple Choice)  
What action can be taken when a web filter matches a blocked category?
- A) Block
- B) Monitor
- C) Warning
- D) All of the above

**Question 9.5** (True/False)  
Web filtering profiles can be applied at the firewall policy level to control which users or groups are subject to specific filtering rules.

## 10. Intrusion Prevention and Application Control

**Question 10.1** (Short Answer)  
How does application control differ from traditional port-based filtering?

**Question 10.2** (Multiple Choice)  
An application is using port 8080 instead of the standard port 80. How can FortiGate still identify and control this application?
- A) It cannot; port-based rules are absolute
- B) Through deep packet inspection and application signatures
- C) By blocking all non-standard ports
- D) Through DNS analysis only

**Question 10.3** (Scenario)  
Your company wants to block all peer-to-peer file sharing applications regardless of which ports they use. Explain how you would configure application control to achieve this.

**Question 10.4** (Multiple Choice)  
Which feature allows FortiGate to detect and block applications that tunnel through common protocols like HTTP?
- A) Port forwarding
- B) Application signatures and behavioral analysis
- C) Static routing
- D) NAT translation

**Question 10.5** (Fill in the Blank)  
IPS (Intrusion Prevention System) protects networks by detecting and blocking __________ and exploits in real-time.

## 11. IPsec VPN

**Question 11.1** (Multiple Choice)  
Which IPsec VPN mode encrypts only the payload of the IP packet?
- A) Tunnel mode
- B) Transport mode
- C) Aggressive mode
- D) Quick mode

**Question 11.2** (Short Answer)  
What is the difference between using the IPsec VPN wizard and the manual configuration process in FortiGate?

**Question 11.3** (Scenario)  
You need to establish a site-to-site IPsec VPN between your headquarters (10.1.0.0/16) and a branch office (10.2.0.0/16). Both sites have FortiGate devices. Outline the key configuration parameters required on both ends.

**Question 11.4** (Multiple Choice)  
What are the two main phases in IPsec VPN negotiation?
- A) Phase 1 and Phase 2
- B) Authentication and Encryption
- C) Handshake and Data Transfer
- D) Setup and Teardown

**Question 11.5** (True/False)  
In a route-based IPsec VPN, a virtual IPsec interface is created, which allows dynamic routing protocols to run over the VPN tunnel.

## 12. SD-WAN Configuration and Monitoring

**Question 12.1** (Short Answer)  
What are the primary benefits of implementing SD-WAN on FortiGate?

**Question 12.2** (Multiple Choice)  
In SD-WAN configuration, what is the purpose of performance SLAs?
- A) To limit bandwidth usage
- B) To measure and ensure link quality based on latency, jitter, and packet loss
- C) To encrypt traffic
- D) To block malicious traffic

**Question 12.3** (Scenario)  
Your organization has three WAN links: two ISP connections and one MPLS link. Configure SD-WAN to route business-critical traffic over MPLS while using ISP links for general internet traffic. What SD-WAN features would you use?

**Question 12.4** (Short Answer)  
How can you verify that traffic is being distributed correctly across SD-WAN members?

**Question 12.5** (Fill in the Blank)  
SD-WAN uses __________ to dynamically select the best path based on application requirements and link performance.

## 13. High Availability

**Question 13.1** (Multiple Choice)  
In an Active-Passive HA cluster, what is the role of the secondary device?
- A) It processes traffic alongside the primary
- B) It remains on standby and takes over if the primary fails
- C) It only handles logging
- D) It acts as a backup configuration store only

**Question 13.2** (Short Answer)  
What is the FortiGate Clustering Protocol (FGCP) and what is its purpose?

**Question 13.3** (Scenario)  
You are configuring HA for two FortiGate devices. Explain the key configuration steps, including priority settings, monitoring interfaces, and heartbeat links.

**Question 13.4** (Multiple Choice)  
Which HA operation mode allows both devices to process traffic simultaneously?
- A) Active-Passive (A-P)
- B) Active-Active (A-A)
- C) Standalone mode
- D) Backup mode

**Question 13.5** (True/False)  
In an HA cluster, configuration changes made on the primary device are automatically synchronized to the secondary device.

## 14. Diagnostics and Troubleshooting

**Question 14.1** (Short Answer)  
What CLI command would you use to perform a packet capture (sniffer) on a FortiGate interface?

**Question 14.2** (Multiple Choice)  
A user cannot access the internet. Which diagnostic tool would you use first to verify basic connectivity from FortiGate?
- A) execute ping
- B) execute traceroute
- C) get system status
- D) diagnose debug flow

**Question 14.3** (Scenario)  
Traffic from internal users to a specific external server is being blocked. Walk through your troubleshooting methodology to identify whether the issue is policy-related, routing-related, or caused by security profiles.

**Question 14.4** (Fill in the Blank)  
The command "diagnose debug flow" is used to __________ in real-time to troubleshoot traffic flow issues.

**Question 14.5** (Multiple Choice)  
Which log type would you check to troubleshoot firewall policy denials?
- A) Event log
- B) Traffic log
- C) System log
- D) Virus log

## 15. FortiGate in the Cloud

**Question 15.1** (Multiple Choice)  
What is FortiGate VM?
- A) A physical FortiGate device
- B) A virtual machine version of FortiGate for cloud and virtualized environments
- C) A management tool for FortiGate
- D) A mobile application

**Question 15.2** (Short Answer)  
What is FortiGate CNF and how does it differ from traditional FortiGate VM deployments?

**Question 15.3** (Scenario)  
Your organization is migrating workloads to AWS. Explain the considerations for deploying FortiGate VM in AWS, including networking, licensing, and integration with AWS services.

**Question 15.4** (True/False)  
FortiGate VM provides the same security features as physical FortiGate appliances.

## 16. FortiSASE

**Question 16.1** (Short Answer)  
What does FortiSASE stand for and what is its primary purpose?

**Question 16.2** (Multiple Choice)  
FortiSASE combines which two network models?
- A) LAN and WAN
- B) SASE (Secure Access Service Edge) and SD-WAN
- C) VPN and Firewall
- D) Cloud and On-Premises

**Question 16.3** (Scenario)  
A company has a distributed workforce with employees working from home, branch offices, and on the road. Describe how FortiSASE could address their security and connectivity challenges.

**Question 16.4** (Multiple Choice)  
Which of the following is a common use case for FortiSASE?
- A) Securing remote worker access to cloud applications
- B) Managing local area networks only
- C) Replacing all physical firewalls
- D) File storage and backup

**Question 16.5** (Fill in the Blank)  
FortiSASE provides secure access to applications and data regardless of user __________ or device type.

---

**Total Questions: 70**

**Question Format Distribution:**
- Multiple Choice: 30 questions
- Short Answer: 19 questions
- Scenario-Based: 13 questions
- True/False: 5 questions
- Fill in the Blank: 5 questions

==*These questions are not from the actual test but generated as study material of possible questions related to FortiOS.*==


