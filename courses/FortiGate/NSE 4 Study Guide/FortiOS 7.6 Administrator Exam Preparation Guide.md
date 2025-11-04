## Table of Contents
1. [Exam Questions by Topic](#exam-questions-by-topic)
2. [Answer Key](#answer-key)
3. [Comprehensive Objective Summaries](#comprehensive-objective-summaries)

---

## Exam Questions by Topic

### Section 1: Deployment and System Configuration

#### Initial Configuration

**Question 1** (Multiple Choice)  
Which interface mode allows you to use both physical and VLAN interfaces on the same physical port?
- A) Transparent mode
- B) NAT mode
- C) Interface mode
- D) VLAN mode

**Question 2** (True/False)  
During initial configuration, the default admin account has no password set by default on FortiGate devices.

**Question 3** (Scenario)  
You need to configure a FortiGate with the management IP 192.168.1.99/24 on port1. Which CLI commands would you use? (Write the command sequence)

**Question 4** (Multiple Choice)  
What is the default operation mode for a FortiGate upon initial deployment?
- A) Transparent mode
- B) NAT/Route mode
- C) Virtual Wire Pair mode
- D) Switch mode

#### Log Settings and Diagnostics

**Question 5** (Multiple Choice)  
Which log type should you enable to troubleshoot VPN tunnel establishment issues?
- A) Traffic logs
- B) Event logs
- C) Security logs
- D) System logs

**Question 6** (Fill in the Blank)  
The command `execute log filter ________` is used to filter log output based on specific criteria in the CLI.

**Question 7** (Multiple Choice)  
What is the recommended minimum disk quota percentage for logging to avoid log loss?
- A) 10%
- B) 20%
- C) 30%
- D) 50%

**Question 8** (True/False)  
FortiGate can send logs to multiple FortiAnalyzer devices simultaneously for redundancy.

#### FGCP HA Configuration

**Question 9** (Multiple Choice)  
In FGCP HA, which mode provides the highest level of session synchronization?
- A) Active-Passive (A-P)
- B) Active-Active (A-A)
- C) Load Balance mode
- D) Virtual Cluster mode

**Question 10** (Scenario)  
You have configured an FGCP cluster with two FortiGates. FGT-1 has priority 200 and FGT-2 has priority 150. Both units are functioning normally. Which unit will be the primary?
- A) FGT-1
- B) FGT-2
- C) Both will share the role
- D) Neither, manual intervention required

**Question 11** (Fill in the Blank)  
In FGCP HA, the ________ interface is used for heartbeat communication between cluster members.

**Question 12** (Multiple Choice)  
What happens to active sessions when an HA failover occurs in Active-Passive mode with session pickup enabled?
- A) All sessions are dropped
- B) TCP sessions continue, UDP sessions are dropped
- C) Sessions are maintained without interruption
- D) Only administrative sessions are dropped

#### Resource and Connectivity Diagnostics

**Question 13** (Multiple Choice)  
Which command is used to verify the current CPU and memory utilization on a FortiGate?
- A) get system status
- B) get system performance status
- C) diagnose sys top
- D) show system resources

**Question 14** (True/False)  
The command `diagnose debug flow` can be used to trace packets through the FortiGate for troubleshooting purposes.

**Question 15** (Scenario)  
A user reports they cannot access the internet through the FortiGate. Which diagnostic command would you use first to verify if the FortiGate can reach the default gateway?
- A) execute ping
- B) diagnose sniffer packet
- C) get router info routing-table all
- D) diagnose debug flow

**Question 16** (Multiple Choice)  
What does the conserve mode threshold indicate on a FortiGate?
- A) CPU utilization limit
- B) Memory utilization limit before entering conserve mode
- C) Disk space threshold
- D) Session table capacity

#### FortiGate CNF and VM in Public Cloud

**Question 17** (Multiple Choice)  
What is the primary deployment model for FortiGate CNF (Cloud-Native Firewall)?
- A) Container-based deployment in Kubernetes
- B) Virtual machine in hypervisor
- C) Physical appliance
- D) Software-defined networking controller

**Question 18** (True/False)  
FortiGate VM in AWS supports both PAYG (Pay-As-You-Go) and BYOL (Bring Your Own License) licensing models.

**Question 19** (Multiple Choice)  
In Azure, which feature allows FortiGate VM to provide high availability across availability zones?
- A) Load Balancer with HA ports
- B) Active-Passive with Azure SDN connector
- C) Virtual Wire Pairs
- D) FGCP clustering

**Question 20** (Fill in the Blank)  
FortiGate CNF is designed to run natively in ________ environments, providing cloud-native security services.

#### FortiSASE Administration

**Question 21** (Multiple Choice)  
What is the primary use case for FortiSASE?
- A) On-premises firewall management
- B) Secure Access Service Edge with unified SASE capabilities
- C) Database security
- D) Email security gateway

**Question 22** (True/False)  
FortiSASE integrates SD-WAN, ZTNA, SWG, and CASB functionalities into a single cloud-delivered service.

**Question 23** (Multiple Choice)  
Which user onboarding method in FortiSASE allows automatic agent deployment through existing endpoint management tools?
- A) Manual installation
- B) Zero-touch provisioning
- C) Email invitation with download link
- D) All of the above

---

### Section 2: Firewall Policies and Authentication

#### Firewall Policy Configuration

**Question 24** (Multiple Choice)  
In a firewall policy, what is the default action if no explicit deny or accept rule matches the traffic?
- A) Accept
- B) Deny (implicit deny)
- C) Log only
- D) Forward to next device

**Question 25** (Scenario)  
You have three firewall policies with IDs 1, 2, and 3. Policy 1 allows HTTP traffic, Policy 2 denies all traffic from source 10.0.0.5, and Policy 3 allows all traffic. In what order should these policies be arranged for Policy 2 to be effective?
- A) 1, 2, 3
- B) 2, 1, 3
- C) 3, 2, 1
- D) Order doesn't matter

**Question 26** (True/False)  
Firewall policies are processed in a top-down manner, and processing stops at the first matching policy.

**Question 27** (Multiple Choice)  
Which security profile can be applied to a firewall policy to scan for malicious files?
- A) Web Filter
- B) Application Control
- C) AntiVirus
- D) IPS

**Question 28** (Fill in the Blank)  
To allow traffic from VLAN 10 to VLAN 20, you must create a firewall policy from the ________ interface to the ________ interface.

#### SNAT and DNAT Configuration

**Question 29** (Multiple Choice)  
What is the primary purpose of SNAT (Source NAT)?
- A) Translate destination IP addresses
- B) Translate source IP addresses for outbound traffic
- C) Create virtual IPs
- D) Load balance traffic

**Question 30** (Scenario)  
You need to publish an internal web server (10.1.1.50:80) to the internet using public IP 203.0.113.10:80. Which NAT type should you configure?
- A) SNAT
- B) DNAT (Destination NAT/Virtual IP)
- C) PAT
- D) Full NAT

**Question 31** (True/False)  
Central SNAT allows you to configure source NAT independently from firewall policies in a centralized table.

**Question 32** (Multiple Choice)  
When configuring a Virtual IP (VIP) for DNAT, which of the following is mapped?
- A) Internal IP to external IP for outbound traffic
- B) External IP to internal IP for inbound traffic
- C) MAC address to IP address
- D) Port number only

**Question 33** (Fill in the Blank)  
In IP Pool configuration, when "Port Block Allocation" is enabled, each user is assigned a ________ of ports rather than individual ports.

#### Firewall Authentication Methods

**Question 34** (Multiple Choice)  
Which authentication method requires users to enter credentials before accessing network resources through the firewall?
- A) Passive authentication
- B) Active authentication
- C) Transparent authentication
- D) Certificate-based authentication only

**Question 35** (Multiple Choice)  
What is the primary advantage of using FSSO (Fortinet Single Sign-On) over active authentication?
- A) Better encryption
- B) No user interaction required for authentication
- C) Faster network performance
- D) Lower licensing cost

**Question 36** (True/False)  
RADIUS and LDAP are both supported as external authentication servers for FortiGate firewall policies.

**Question 37** (Scenario)  
You want to authenticate users transparently using their Windows domain credentials without a captive portal. Which authentication method should you implement?
- A) Active authentication with captive portal
- B) FSSO (Fortinet Single Sign-On)
- C) Local user database
- D) RADIUS with challenge-response

#### FSSO Deployment and Configuration

**Question 38** (Multiple Choice)  
Which component is required on the Windows domain to enable FSSO?
- A) FortiGate VM
- B) FortiAuthenticator
- C) DC Agent or Collector Agent
- D) FortiAnalyzer

**Question 39** (Fill in the Blank)  
FSSO uses ________ events from Windows Domain Controllers to identify user login information.

**Question 40** (True/False)  
FSSO can integrate with both on-premises Active Directory and cloud-based identity providers like Azure AD.

**Question 41** (Multiple Choice)  
In FSSO, what information is primarily mapped to create user identity?
- A) MAC address to hostname
- B) IP address to username
- C) Port number to application
- D) VLAN ID to department

---

### Section 3: Content Inspection

#### Encrypted Traffic Inspection

**Question 42** (Multiple Choice)  
What is required on a FortiGate to inspect HTTPS traffic?
- A) A valid SSL certificate installed on FortiGate
- B) SSL deep inspection enabled with appropriate certificates
- C) Port forwarding rules
- D) IPsec VPN tunnel

**Question 43** (True/False)  
Certificate inspection mode allows FortiGate to inspect the certificate metadata without decrypting the actual content.

**Question 44** (Scenario)  
Your organization requires inspection of all encrypted traffic except for banking websites. Which SSL inspection mode and configuration approach should you use?
- A) Deep inspection with exemption list for banking sites
- B) Certificate inspection for all sites
- C) No inspection mode
- D) Flow-based inspection only

**Question 45** (Multiple Choice)  
Which SSL/TLS inspection mode provides the highest level of security visibility?
- A) Certificate Inspection
- B) Deep Inspection
- C) No Inspection
- D) Passive Inspection

**Question 46** (Fill in the Blank)  
To enable SSL deep inspection, you must import or generate a ________ certificate authority (CA) certificate on FortiGate.

#### Inspection Modes and Web Filtering

**Question 47** (Multiple Choice)  
Which inspection mode processes packets at the session level and is faster but has limited protocol support?
- A) Proxy-based inspection
- B) Flow-based inspection
- C) Deep inspection
- D) Inline inspection

**Question 48** (Multiple Choice)  
In web filtering, what does the FortiGuard category rating "High Risk" indicate?
- A) Websites with high bandwidth usage
- B) Websites known for hosting malware or illegal content
- C) Websites requiring high security clearance
- D) Websites with high user traffic

**Question 49** (True/False)  
Web filtering can be configured to allow access during specific time periods using schedule objects.

**Question 50** (Scenario)  
You need to block social media websites for all users except the marketing department. How would you configure this in web filtering?
- A) Create two web filter profiles with different category settings
- B) Use a single profile with exemption based on source address
- C) Create firewall policies with different web filter profiles for different user groups
- D) Both A and C are valid approaches

**Question 51** (Fill in the Blank)  
FortiGuard Web Filtering uses ________ to categorize websites into different content categories.

#### Application Control

**Question 52** (Multiple Choice)  
What is the primary purpose of Application Control on FortiGate?
- A) Control application installation on endpoints
- B) Identify and control network applications regardless of port or protocol
- C) Manage application licenses
- D) Optimize application performance

**Question 53** (True/False)  
Application Control can identify applications that use encryption or non-standard ports to evade traditional firewall rules.

**Question 54** (Multiple Choice)  
Which action can be applied to an application signature in an Application Control profile?
- A) Allow
- B) Block
- C) Monitor
- D) All of the above

**Question 55** (Scenario)  
Users are accessing Facebook through HTTPS, which is allowed by your firewall policy. However, you want to block Facebook Chat while allowing other Facebook features. How can you achieve this?
- A) Block all HTTPS traffic
- B) Use Application Control to block Facebook.Chat signature
- C) Use web filtering to block chat.facebook.com
- D) Create a separate firewall policy for port 443

#### AntiVirus Scanning

**Question 56** (Multiple Choice)  
Which antivirus scanning mode provides the fastest performance but may miss some sophisticated threats?
- A) Flow-based
- B) Proxy-based
- C) Full scan
- D) Deep scan

**Question 57** (Fill in the Blank)  
FortiGate AntiVirus uses ________ from FortiGuard Labs to detect and block malware threats.

**Question 58** (True/False)  
FortiGate can be configured to scan archives (ZIP, RAR) for malware, but this increases CPU utilization.

**Question 59** (Multiple Choice)  
What happens to a file detected as malware when the antivirus action is set to "Block"?
- A) File is quarantined for review
- B) File transfer is blocked and logged
- C) File is cleaned and delivered
- D) Warning is displayed but file is allowed

#### IPS Configuration

**Question 60** (Multiple Choice)  
What is the main difference between IPS (Intrusion Prevention System) and Antivirus?
- A) IPS blocks network-based attacks, Antivirus blocks file-based malware
- B) IPS is faster than Antivirus
- C) IPS requires more CPU resources
- D) There is no difference

**Question 61** (True/False)  
IPS signatures are organized by severity levels (critical, high, medium, low, info) to help prioritize threats.

**Question 62** (Scenario)  
You want to protect your network from zero-day attacks. Which IPS feature should you enable?
- A) Signature-based detection only
- B) Anomaly-based detection (protocol decoders)
- C) Rate-based signatures
- D) All of the above for comprehensive protection

**Question 63** (Multiple Choice)  
In IPS configuration, what does the "packet-logging" option do?
- A) Logs all packets passing through FortiGate
- B) Logs packets that match IPS signatures
- C) Enables full packet capture for forensics
- D) Disables logging to improve performance

---

### Section 4: Routing

#### Static Routes

**Question 64** (Multiple Choice)  
What is the default administrative distance for a static route on FortiGate?
- A) 1
- B) 5
- C) 10
- D) 20

**Question 65** (Fill in the Blank)  
The command `get router info routing-table all` displays the ________ table, showing all active routes.

**Question 66** (True/False)  
A static route with a lower administrative distance is preferred over a route with a higher administrative distance.

**Question 67** (Scenario)  
You have two internet connections: ISP1 (203.0.113.1) and ISP2 (198.51.100.1). You want ISP1 to be the primary route and ISP2 to be the backup. How should you configure the administrative distance?
- A) Both with distance 10
- B) ISP1 with distance 10, ISP2 with distance 20
- C) ISP1 with distance 20, ISP2 with distance 10
- D) Use priority instead of distance

**Question 68** (Multiple Choice)  
Which type of static route is used when the next-hop is reachable through an unnumbered interface?
- A) Gateway route
- B) Interface route
- C) Recursive route
- D) Default route

#### SD-WAN Configuration

**Question 69** (Multiple Choice)  
What is the primary benefit of implementing SD-WAN on FortiGate?
- A) Increased security
- B) Intelligent traffic load balancing across multiple WAN links
- C) Reduced hardware costs
- D) Simplified firewall rules

**Question 70** (True/False)  
SD-WAN health checks actively monitor the quality and availability of WAN links using probes.

**Question 71** (Multiple Choice)  
Which SD-WAN strategy prioritizes links based on the best performance metrics (latency, jitter, packet loss)?
- A) Volume-based
- B) Session-based
- C) Best Quality (SLA)
- D) Source-based

**Question 72** (Scenario)  
You have configured SD-WAN with three members: ISP1 (fiber, high speed), ISP2 (cable, medium speed), and ISP3 (LTE, backup). You want business-critical applications to use ISP1 primarily. Which load balancing algorithm should you configure?
- A) Weighted round-robin with highest weight on ISP1
- B) Priority with ISP1 as first priority
- C) Source IP hash
- D) Least connections

**Question 73** (Fill in the Blank)  
In SD-WAN configuration, ________ rules determine which traffic uses which WAN links based on various criteria.

---

### Section 5: VPN

#### IPsec VPN Configuration

**Question 74** (Multiple Choice)  
Which Phase 1 authentication method is most commonly used for site-to-site IPsec VPNs?
- A) Username/password
- B) Pre-shared key (PSK)
- C) Certificate
- D) Token-based

**Question 75** (True/False)  
In a meshed IPsec VPN topology, each site has a direct tunnel to every other site.

**Question 76** (Multiple Choice)  
What is the purpose of Phase 2 in IPsec VPN negotiation?
- A) Authenticate VPN peers
- B) Establish encryption keys for data encryption
- C) Create tunnel interface
- D) Configure routing protocols

**Question 77** (Scenario)  
You need to create a VPN between FortiGate-HQ (public IP: 203.0.113.10, LAN: 10.10.0.0/16) and FortiGate-Branch (public IP: 198.51.100.20, LAN: 10.20.0.0/16). What should be configured in the Phase 2 selectors?
- A) HQ: 203.0.113.10, Branch: 198.51.100.20
- B) HQ: 10.10.0.0/16, Branch: 10.20.0.0/16
- C) Both: 0.0.0.0/0
- D) Interface names

**Question 78** (Fill in the Blank)  
IPsec VPN uses port ________ (UDP) for NAT traversal (NAT-T) when VPN peers are behind NAT devices.

**Question 79** (Multiple Choice)  
What does "Dead Peer Detection" (DPD) do in IPsec VPN?
- A) Encrypts traffic to dead hosts
- B) Detects and recovers from tunnel failures
- C) Prevents unauthorized access
- D) Monitors bandwidth usage

**Question 80** (True/False)  
A hub-and-spoke VPN topology requires fewer tunnels than a full mesh topology for connecting multiple sites.

**Question 81** (Multiple Choice)  
Which feature allows partial redundancy in IPsec VPN by enabling automatic failover to backup tunnels?
- A) VPN monitoring with route failover
- B) Load balancing
- C) Split tunneling
- D) Tunnel encryption

**Question 82** (Scenario)  
Your company has four branch offices that need to communicate with headquarters and occasionally with each other. Which VPN topology is most efficient?
- A) Full mesh
- B) Hub-and-spoke
- C) Point-to-point
- D) Partial mesh (hub-and-spoke with selected branch-to-branch tunnels)

---

## Answer Key

### Section 1: Deployment and System Configuration

1. **C** - Interface mode (allows mixed physical and VLAN interfaces)
2. **False** - Default admin account requires a password to be set during initial setup or first login
3. **Answer:**
   ```
   config system interface
       edit "port1"
           set ip 192.168.1.99 255.255.255.0
           set allowaccess ping https ssh
       next
   end
   ```
4. **B** - NAT/Route mode
5. **B** - Event logs (contain VPN-related events and tunnel status)
6. **device** (or category, field, etc. - accepts various filter types)
7. **B** - 20%
8. **True**
9. **A** - Active-Passive with session pickup enabled
10. **A** - FGT-1 (higher priority value becomes primary)
11. **heartbeat** or **HA**
12. **C** - Sessions are maintained without interruption (with session pickup)
13. **B** - get system performance status
14. **True**
15. **A** - execute ping (verify basic connectivity first)
16. **B** - Memory utilization limit before entering conserve mode
17. **A** - Container-based deployment in Kubernetes
18. **True**
19. **B** - Active-Passive with Azure SDN connector
20. **Kubernetes** or **container**
21. **B** - Secure Access Service Edge with unified SASE capabilities
22. **True**
23. **D** - All of the above

### Section 2: Firewall Policies and Authentication

24. **B** - Deny (implicit deny)
25. **B** - 2, 1, 3 (specific deny before allows)
26. **True**
27. **C** - AntiVirus
28. **VLAN10** (or source), **VLAN20** (or destination)
29. **B** - Translate source IP addresses for outbound traffic
30. **B** - DNAT (Destination NAT/Virtual IP)
31. **True**
32. **B** - External IP to internal IP for inbound traffic
33. **block** or **range**
34. **B** - Active authentication
35. **B** - No user interaction required for authentication
36. **True**
37. **B** - FSSO (Fortinet Single Sign-On)
38. **C** - DC Agent or Collector Agent
39. **security** or **logon**
40. **True**
41. **B** - IP address to username

### Section 3: Content Inspection

42. **B** - SSL deep inspection enabled with appropriate certificates
43. **True**
44. **A** - Deep inspection with exemption list for banking sites
45. **B** - Deep Inspection
46. **root** or **CA**
47. **B** - Flow-based inspection
48. **B** - Websites known for hosting malware or illegal content
49. **True**
50. **D** - Both A and C are valid approaches
51. **FortiGuard** or **URL database**
52. **B** - Identify and control network applications regardless of port or protocol
53. **True**
54. **D** - All of the above
55. **B** - Use Application Control to block Facebook.Chat signature
56. **A** - Flow-based
57. **signatures** or **definitions**
58. **True**
59. **B** - File transfer is blocked and logged
60. **A** - IPS blocks network-based attacks, Antivirus blocks file-based malware
61. **True**
62. **D** - All of the above for comprehensive protection
63. **B** - Logs packets that match IPS signatures

### Section 4: Routing

64. **C** - 10
65. **routing**
66. **True**
67. **B** - ISP1 with distance 10, ISP2 with distance 20
68. **B** - Interface route
69. **B** - Intelligent traffic load balancing across multiple WAN links
70. **True**
71. **C** - Best Quality (SLA)
72. **B** - Priority with ISP1 as first priority
73. **performance** or **SD-WAN**

### Section 5: VPN

74. **B** - Pre-shared key (PSK)
75. **True**
76. **B** - Establish encryption keys for data encryption
77. **B** - HQ: 10.10.0.0/16, Branch: 10.20.0.0/16
78. **4500**
79. **B** - Detects and recovers from tunnel failures
80. **True**
81. **A** - VPN monitoring with route failover
82. **D** - Partial mesh (hub-and-spoke with selected branch-to-branch tunnels)

---

## Comprehensive Objective Summaries

### Topic 1: Deployment and System Configuration

#### 1.1 Initial Configuration

**Objective:** Perform initial configuration of FortiGate devices

**Key Concepts:**
- **Default Operation Modes**: FortiGate supports NAT/Route mode (default), Transparent mode, and Virtual Wire Pair mode
- **Initial Access**: Default access via HTTPS to management interface; initial admin password must be set on first login
- **Interface Configuration**: Configure IP addresses, administrative access protocols (HTTPS, SSH, ping, SNMP), and interface roles
- **System Settings**: Configure hostname, time zone, NTP servers, and DNS settings for proper system operation
- **Administrative Access**: Define allowed administrative protocols and restrict access by trusted hosts
- **Backup and Restore**: Regular configuration backups are critical; FortiGate supports full system backups and specific configuration exports

**Best Practices:**
- Always change default credentials immediately
- Configure management interface on a separate, secured network
- Enable only necessary administrative access protocols
- Document all initial configuration changes
- Test connectivity before deploying in production

#### 1.2 Log Settings and Diagnostics

**Objective:** Configure log settings and diagnose problems using logs

**Key Concepts:**
- **Log Types**: Traffic logs (allowed/denied traffic), Event logs (system and VPN events), Security logs (threat detections), System logs (administrative actions)
- **Log Destinations**: Local disk, FortiAnalyzer, Syslog server, FortiCloud
- **Disk Quota Management**: Configure minimum disk quota (recommended 20%) to prevent log loss; implement log rotation policies
- **Log Filtering**: Use filters to view specific log types, severity levels, or source/destination criteria
- **FortiAnalyzer Integration**: Centralized logging, reporting, and analysis platform; supports real-time and historical log queries
- **Log Retention**: Balance retention period with storage capacity and compliance requirements

**Diagnostic Commands:**
- `execute log filter` - Filter log display by various criteria
- `execute log display` - View filtered logs
- `diagnose debug application` - Enable application-level debugging
- `diagnose debug flow` - Trace packet flow through FortiGate

**Best Practices:**
- Enable logging for all critical security events
- Configure multiple log destinations for redundancy
- Monitor disk space regularly to prevent log loss
- Use log filters effectively to reduce noise
- Integrate with FortiAnalyzer for long-term retention and analysis

#### 1.3 FGCP HA Configuration

**Objective:** Configure FortiGate Clustering Protocol (FGCP) High Availability cluster

**Key Concepts:**
- **HA Modes**: Active-Passive (A-P) for failover redundancy, Active-Active (A-A) for load balancing with session distribution
- **Cluster Synchronization**: Configuration, routing tables, IPsec SA, user authentication data, and sessions (with session pickup)
- **Heartbeat Interfaces**: Dedicated interfaces for cluster health monitoring; multiple heartbeat links recommended for redundancy
- **Priority and Override**: Device priority (0-255) determines primary role; override mode forces higher priority device to reclaim primary role
- **Session Pickup**: Synchronizes active sessions between cluster members; requires enable in A-P mode for seamless failover
- **Virtual MAC**: Cluster uses virtual MAC addresses for gratuitous ARP during failover
- **Monitoring**: Interface monitoring, gateway monitoring, and remote link health checks ensure failover triggers appropriately

**Configuration Elements:**
- Device priority (higher = preferred primary)
- Group ID (0-255, must match on all members)
- Cluster password for authentication
- Heartbeat interface selection
- Session pickup enable/disable
- Override enable/disable

**Best Practices:**
- Use dedicated heartbeat interfaces (minimum two for redundancy)
- Configure appropriate priorities to control primary selection
- Enable session pickup for critical services requiring connection persistence
- Test failover scenarios before production deployment
- Monitor cluster status regularly
- Document cluster configuration and failover procedures

#### 1.4 Resource and Connectivity Diagnostics

**Objective:** Diagnose resource utilization and connectivity problems

**Key Concepts:**
- **Resource Monitoring**: CPU, memory, disk, and session table utilization; conserve mode triggers when memory reaches threshold
- **Connectivity Testing**: Ping, traceroute, and packet sniffing tools for network troubleshooting
- **Packet Flow Analysis**: Debug flow traces packets from ingress to egress, showing policy matching and NAT translations
- **Session Table**: Displays active sessions with source/destination, policy ID, and timeout information
- **Routing Table Verification**: Examine active routes, administrative distances, and route preferences

**Essential Diagnostic Commands:**
- `get system performance status` - CPU, memory, session count, and throughput
- `diagnose sys top` - Real-time process CPU and memory utilization
- `execute ping` / `execute traceroute` - Basic connectivity testing
- `diagnose sniffer packet <interface> <filter>` - Capture packets on specific interfaces
- `diagnose debug flow` - Trace packet processing through firewall
- `get router info routing-table all` - Display full routing table
- `diagnose sys session list` - Show active sessions
- `get system status` - System information, uptime, version

**Debug Flow Procedure:**
```
diagnose debug reset
diagnose debug flow filter addr <ip-address>
diagnose debug flow show console enable
diagnose debug flow trace start 10
diagnose debug enable
```

**Best Practices:**
- Establish baseline performance metrics
- Monitor conserve mode entries (indicates memory pressure)
- Use debug flow with filters to reduce output volume
- Document diagnostic procedures for common issues
- Review logs in conjunction with diagnostic commands
- Clean up debug settings after troubleshooting

#### 1.5 FortiGate CNF and VM in Public Cloud

**Objective:** Describe FortiGate Cloud-Native Firewall and VM deployments in public cloud

**Key Concepts:**
- **FortiGate CNF**: Container-based security platform designed for Kubernetes environments; runs as pods with cloud-native orchestration
- **FortiGate VM**: Virtual machine instances deployed in AWS, Azure, GCP, and other cloud platforms
- **Licensing Models**: PAYG (Pay-As-You-Go) for flexible consumption, BYOL (Bring Your Own License) for existing license portability
- **HA in Cloud**: Active-Passive configurations using cloud SDN connectors for automatic failover and route updates
- **AWS Deployments**: Single VPC, multi-VPC with Transit Gateway, and Gateway Load Balancer (GWLB) architectures
- **Azure Deployments**: Hub-and-spoke topologies, Azure Load Balancer for HA, integration with Azure Virtual WAN
- **Cloud SDN Connectors**: Dynamic object updates from cloud platforms (instances, networks) for policy automation
- **Auto-scaling**: Some cloud deployments support horizontal scaling based on traffic load

**AWS-Specific Features:**
- Integration with AWS Transit Gateway for multi-VPC connectivity
- Support for Gateway Load Balancer for transparent inspection
- CloudFormation templates for automated deployment
- Integration with AWS Security Hub

**Azure-Specific Features:**
- Azure SDN connector for automated IP failover
- Integration with Azure Firewall Manager
- ARM templates for deployment automation
- Support for Azure availability zones

**CNF Advantages:**
- Cloud-native architecture with Kubernetes orchestration
- Rapid scaling and deployment
- Microservices-friendly security
- Integration with DevOps pipelines

**Best Practices:**
- Choose appropriate instance size based on throughput requirements
- Implement HA configurations for production workloads
- Use cloud SDN connectors for dynamic policy updates
- Monitor cloud-specific metrics (API calls, SDN updates)
- Follow cloud provider's security best practices
- Regular testing of failover mechanisms in cloud HA setups

#### 1.6 FortiSASE Administration

**Objective:** Explain FortiSASE administration and user onboarding methods

**Key Concepts:**
- **SASE Architecture**: Secure Access Service Edge combines network security functions with WAN capabilities in a cloud-delivered service
- **FortiSASE Components**: SD-WAN, Zero Trust Network Access (ZTNA), Secure Web Gateway (SWG), Cloud Access Security Broker (CASB), Firewall-as-a-Service (FWaaS)
- **Unified Management**: Single pane of glass for managing all SASE services through cloud portal
- **User Onboarding Methods**: 
  - Zero-touch provisioning with automated agent deployment
  - Email invitations with agent download links
  - Integration with endpoint management tools (SCCM, Intune)
  - Manual installation packages
- **Identity Integration**: Connects with Active Directory, Azure AD, Okta, and other IdPs for user authentication
- **Edge Points of Presence (PoPs)**: Global network of security inspection points close to users and resources

**Onboarding Workflows:**
1. **Zero-Touch**: Agent auto-installs via provisioning profiles
2. **Email Invitation**: Users receive link, download agent, automatic configuration
3. **MDM Integration**: Push agent through existing mobile device management
4. **Manual**: IT downloads and distributes installation packages

**FortiSASE Advantages:**
- Simplified deployment without on-premises hardware
- Automatic scaling based on user count and traffic
- Consistent security for remote and office workers
- Reduced complexity vs. multiple point solutions
- Built-in SD-WAN for optimized cloud access

**Best Practices:**
- Plan onboarding strategy based on user distribution
- Integrate with existing identity provider for SSO
- Configure appropriate security policies before wide deployment
- Monitor edge PoP performance and user experience
- Provide user training on agent functionality
- Establish helpdesk procedures for onboarding issues

---

### Topic 2: Firewall Policies and Authentication

#### 2.1 Firewall Policy Configuration

**Objective:** Configure and manage firewall policies effectively

**Key Concepts:**
- **Policy Components**: Source (interface, addresses, users), Destination (interface, addresses), Service/Application, Action (Accept/Deny), Security Profiles
- **Implicit Deny**: Traffic not matching any policy is automatically denied
- **Policy Order**: Processed top-to-bottom; first match wins, processing stops
- **Policy Actions**: Accept, Deny, IPsec (VPN traffic), SSL Inspect
- **Security Profiles**: AntiVirus, Web Filter, Application Control, IPS, DLP, Email Filter
- **Logging**: Traffic logs (accepted and/or denied traffic), Security logs (threat detections)
- **NAT Settings**: Source NAT (outbound translation), Destination NAT (via Virtual IP)
- **Schedule Objects**: Time-based policy enforcement
- **Policy Comments**: Documentation for policy purpose and maintenance

**Policy Best Practices:**
- Place more specific policies before general policies
- Group related policies for easier management
- Use address and service objects instead of inline definitions
- Enable logging for security events and policy troubleshooting
- Document policy purpose in comments
- Regular policy review to remove obsolete rules
- Use policy consolidation to reduce rule count
- Test policy changes in non-production before deployment

**Common Policy Patterns:**
- Internet access: Internal → WAN with security profiles
- Inter-VLAN routing: VLAN_A → VLAN_B with appropriate restrictions
- Server publishing: WAN → DMZ with DNAT and strict security
- Deny policies: Explicit denies before catch-all rules

#### 2.2 SNAT and DNAT Configuration

**Objective:** Configure Source NAT and Destination NAT in firewall policies

**Key Concepts:**
- **Source NAT (SNAT)**: Translates private source IPs to public IPs for outbound internet access
  - **Outgoing Interface Address**: Uses interface IP (most common)
  - **Dynamic IP Pool**: Rotates through pool of public IPs
  - **Fixed Port Range**: Assigns specific port range per internal IP
- **Destination NAT (DNAT)**: Publishes internal servers using public IPs via Virtual IPs (VIPs)
  - **Static NAT**: One-to-one IP mapping
  - **Port Forwarding**: External IP:Port → Internal IP:Port
  - **Load Balancing VIP**: Distributes to multiple internal servers
- **Central SNAT**: Centralized source NAT table independent of firewall policies
- **Port Block Allocation**: Assigns port blocks to users for better tracking and NAT scalability
- **NAT64/NAT46**: Translation between IPv4 and IPv6 networks

**SNAT Configuration Scenarios:**
- Default: Enable NAT, use outgoing interface address
- Multiple public IPs: Create IP pool, assign to policy
- Per-user tracking: Enable port block allocation
- Central SNAT: Configure in central SNAT table for shared translation rules

**DNAT/Virtual IP Scenarios:**
- Web server publishing: VIP maps external:80 → internal_server:80
- Port redirection: VIP maps external:8080 → internal_server:80
- Load balancing: VIP distributes to multiple backend servers
- Static NAT: VIP maps entire IP range

**Virtual IP Types:**
- Static NAT: Complete IP mapping
- Port Forwarding: Specific port translation
- Server Load Balance: Distribution across servers

**Best Practices:**
- Use IP pools when multiple public IPs available
- Document VIP to internal server mappings
- Enable port forwarding only for required services
- Consider security implications of published services
- Use Central SNAT for consistent outbound translation
- Monitor NAT table utilization
- Implement port block allocation for large user bases

#### 2.3 Firewall Authentication Methods

**Objective:** Configure different methods of firewall authentication

**Key Concepts:**
- **Authentication Methods**:
  - **Active Authentication**: Users explicitly authenticate (captive portal, explicit proxy)
  - **Passive Authentication**: Transparent authentication using FSSO, RSSO (no user interaction)
  - **Certificate-Based**: Using digital certificates for user identification
- **Identity Sources**: Local user database, LDAP, RADIUS, TACACS+, SAML, PKI
- **Captive Portal**: Web-based authentication page for guest or user access
- **Explicit Proxy**: Browser configured to use FortiGate as proxy; authentication before internet access
- **Authentication Timeouts**: Idle timeout and hard timeout configurations
- **SSO Integration**: FSSO for Windows domains, RSSO for RADIUS-based SSO
- **Multi-Factor Authentication (MFA)**: FortiToken, email, SMS for additional security layer

**Authentication Flows:**
1. **Active (Captive Portal)**: User connects → Redirect to portal → Enter credentials → Authentication → Access granted
2. **Passive (FSSO)**: User logs into Windows → DC Agent detects → IP-username mapping → FortiGate applies policies
3. **Certificate**: User presents certificate → FortiGate validates against CA → Access granted

**Authentication in Policies:**
- Add user/group objects to firewall policy source
- Policy enforces authentication requirement automatically
- Authenticated users matched against group membership

**Best Practices:**
- Use FSSO for transparent authentication in corporate networks
- Implement MFA for administrative access and sensitive resources
- Configure appropriate authentication timeouts
- Use explicit proxy for granular control in corporate environments
- Deploy captive portal for guest networks
- Regular auditing of authenticated sessions
- Integrate with central identity provider (AD, LDAP)

#### 2.4 FSSO Deployment and Configuration

**Objective:** Deploy and configure Fortinet Single Sign-On

**Key Concepts:**
- **FSSO Purpose**: Transparent authentication using Windows domain credentials without captive portals
- **Components**:
  - **DC Agent**: Installed on domain controller; monitors security event logs for logon/logoff
  - **Collector Agent**: Optional; aggregates logon info from multiple DCs
  - **FortiGate**: Receives IP-username mappings from agents
- **Logon Detection**: Monitors Windows Security Event IDs (4624 for logon, 4634/4647 for logoff)
- **IP-Username Mapping**: Associates user's IP address with domain username
- **Group Queries**: FortiGate queries AD for user group membership
- **Workstation Check**: Optional; enforces that IP matches user's designated workstation
- **Multi-Domain Support**: Single collector can aggregate from multiple domains
- **Cloud Integration**: FSSO can integrate with Azure AD and cloud identity providers

**Deployment Architectures:**
- **DC Agent Mode**: Agent installed directly on each domain controller
- **Collector Agent Mode**: Central collector polls multiple DCs via WMI
- **Polling vs. Push**: DC Agent pushes events; Collector polls at intervals

**Configuration Steps:**
1. Install DC Agent or Collector Agent on Windows server
2. Configure agent to monitor domain controllers
3. Add FortiGate as authorized device in agent
4. Configure FSSO on FortiGate (agent IP, credentials)
5. Enable FSSO in firewall policies
6. Test with domain user authentication

**Advanced Features:**
- **NTLM Authentication Fallback**: If FSSO fails, prompt for credentials
- **API-based FSSO**: REST API for custom integrations
- **Guest Group Matching**: Handles unauthenticated users

**Best Practices:**
- Install DC Agent on read-only domain controller when possible
- Use Collector Agent for scalability with multiple DCs
- Configure agent redundancy for high availability
- Enable workstation check for enhanced security
- Monitor FSSO status and synchronization
- Regular testing of logon/logoff detection
- Document FSSO architecture and dependencies
- Plan for cloud identity integration for hybrid environments

---

### Topic 3: Content Inspection

#### 3.1 Encrypted Traffic Inspection

**Objective:** Inspect encrypted traffic using SSL/TLS inspection

**Key Concepts:**
- **SSL Inspection Modes**:
  - **Certificate Inspection**: Examines certificate metadata without decrypting content; low resource usage
  - **Deep Inspection**: Full man-in-the-middle decryption and inspection; highest security
  - **No Inspection**: Traffic passes without examination
- **Certificate Requirements**: FortiGate must have root CA certificate to re-sign server certificates for deep inspection
- **Certificate Distribution**: Client devices must trust FortiGate's CA certificate
- **Inspection Exemptions**: Whitelist sensitive sites (banking, healthcare) to bypass inspection
- **Protocol Support**: HTTPS, SMTPS, POP3S, IMAPS, FTPS
- **Certificate Validation**: Block invalid, expired, or untrusted certificates

**Deep Inspection Process:**
1. Client initiates HTTPS connection to server
2. FortiGate intercepts and establishes two SSL sessions
3. FortiGate inspects decrypted content
4. FortiGate re-encrypts and forwards to destination

**Certificate Inspection Use Cases:**
- Validate certificate authenticity
- Block connections to sites with invalid certificates
- Lower overhead when full inspection not required

**Configuration Components:**
- SSL/SSH Inspection profile
- Certificate (CA certificate for deep inspection)
- Exemption list for sensitive domains
- Apply profile to firewall policy

**Best Practices:**
- Generate or import dedicated CA certificate for SSL inspection
- Deploy CA certificate to all client devices via GPO or MDM
- Create exemption list for banking, healthcare, and privacy-sensitive sites
- Monitor SSL inspection performance impact
- Use certificate inspection for performance-sensitive environments
- Deep inspection for high-security zones
- Regular updates to exemption list
- Consider privacy and legal implications

#### 3.2 Inspection Modes and Web Filtering

**Objective:** Understand inspection modes and configure web filtering

**Key Concepts:**
- **Inspection Modes**:
  - **Flow-Based**: Fast, session-level inspection; limited protocol support; ideal for high-throughput
  - **Proxy-Based**: Full protocol decoding; all security features; higher latency and resource usage
- **Web Filter Methods**:
  - **FortiGuard Category**: Cloud-based URL categorization database
  - **Static URL Filter**: Manually defined allow/block lists
  - **Content Filter**: Keywords and patterns in web content
  - **Advanced Filters**: Search engine filters, script filters
- **FortiGuard Categories**: 80+ categories (social media, gambling, malware, adult content, etc.)
- **Category Actions**: Allow, Block, Monitor, Warning, Authenticate
- **Safe Search Enforcement**: Forces safe search on search engines
- **Web Content Filter**: Blocks pages containing specific keywords
- **Override Options**: Allow users to override blocks with password or after time delay

**Web Filter Profile Components:**
- FortiGuard category filters with actions
- Static URL filter (blacklist/whitelist)
- Web content filter (banned words)
- Category override settings
- Search engine and YouTube filtering

**Quota Management:**
- Time-based quotas per category
- User or group-based quota allocation
- Reset schedules (daily, weekly)

**Best Practices:**
- Use FortiGuard categories as foundation
- Supplement with static URL filters for organization-specific requirements
- Enable logging for policy tuning
- Schedule-based filtering for time-of-day restrictions
- Category-based quotas for reasonable use policies
- Regular review of blocked and monitored categories
- User education on acceptable use
- Test filter policies before full deployment
- Balance security with productivity

#### 3.3 Application Control

**Objective:** Monitor and control network applications

**Key Concepts:**
- **Application Signatures**: Database of 6000+ application patterns independent of port/protocol
- **Deep Packet Inspection (DPI)**: Examines packet payloads to identify applications
- **Application Categories**: Collaboration, P2P, Gaming, Proxy, VoIP, etc.
- **Signature Actions**: Allow, Monitor, Block, Quarantine
- **Application Filters**: Category-based and individual application control
- **Technology Detection**: Identifies application components (e.g., Facebook.Chat, Facebook.Posting)
- **Risk Ratings**: Applications rated 1-5 for security risk
- **Protocol Detection**: Identifies protocols even on non-standard ports

**Application Control Profile Structure:**
- Category filters (block all P2P)
- Application overrides (allow specific apps within blocked category)
- Unknown application action
- Filter overrides based on popularity or risk

**Common Use Cases:**
- Block P2P file sharing applications
- Monitor cloud storage usage
- Control social media components
- Block proxy and anonymizer tools
- Limit gaming and streaming
- Manage VoIP applications

**Granular Control Examples:**
- Allow Facebook but block Facebook.Chat
- Allow Microsoft Office 365 but block OneDrive
- Monitor YouTube without blocking

**Best Practices:**
- Start with monitoring mode to establish baseline
- Use category filters for broad control
- Application overrides for exceptions
- Block high-risk applications
- Monitor unknown applications
- Regular review of application usage reports
- User awareness of application policies
- Test policies to avoid blocking business-critical apps
- Combine with web filtering for comprehensive control

#### 3.4 AntiVirus Scanning

**Objective:** Configure antivirus scanning to neutralize malware

**Key Concepts:**
- **Scanning Modes**:
  - **Flow-Based**: Fast, inline scanning; may miss some threats
  - **Proxy-Based**: Full file reconstruction and scanning; more thorough
- **Detection Methods**: Signature-based, heuristic analysis, AI-based detection
- **FortiGuard AV Service**: Cloud-based virus definition updates
- **Protocols**: HTTP, FTP, SMTP, POP3, IMAP, MAPI
- **Actions**: Block, Monitor, Quarantine
- **File Type Blocking**: Block specific file extensions regardless of content
- **Archive Scanning**: Inspect compressed files (ZIP, RAR, 7z); resource-intensive
- **Grayware**: Potentially unwanted applications (PUA) detection
- **Mobile Malware**: Android and iOS malware detection

**AntiVirus Profile Components:**
- Protocol scanning options (HTTP, FTP, Email)
- Scan mode (flow or proxy)
- Action on virus detection
- Archive handling (scan, block, or allow)
- Mobile malware detection
- Outbreak prevention settings

**Outbreak Prevention:**
- Temporarily blocks files during active malware outbreaks
- Automatic updates from FortiGuard Outbreak database
- Reduces risk during zero-day attacks

**Performance Considerations:**
- Proxy-based scanning increases latency
- Archive scanning is CPU-intensive
- Large file scanning impacts throughput
- Balance security with performance requirements

**Best Practices:**
- Enable AV on all internet-facing policies
- Use proxy-based mode for high-security environments
- Configure archive scanning based on risk tolerance
- Enable outbreak prevention
- Block high-risk file types
- Monitor CPU impact of AV scanning
- Regular update of FortiGuard definitions
- Quarantine malware for analysis
- User notification on blocked content

#### 3.5 IPS Configuration

**Objective:** Configure Intrusion Prevention System to protect against network attacks

**Key Concepts:**
- **IPS vs. Antivirus**: IPS detects network-based attacks; AV detects file-based malware
- **Detection Methods**:
  - **Signature-Based**: Matches known attack patterns
  - **Anomaly-Based**: Protocol decoders detect protocol violations
  - **Rate-Based**: Detects abnormal traffic rates (DDoS indicators)
- **Signature Database**: 10,000+ signatures covering exploits, vulnerabilities, and attacks
- **Severity Levels**: Critical, High, Medium, Low, Info
- **Actions**: Block, Monitor, Reset (RST), Quarantine
- **Protocol Decoders**: Deep protocol analysis for HTTP, DNS, SMB, etc.
- **Packet Logging**: Capture packets matching signatures for forensics
- **Rate-Based Signatures**: Detect flood attacks and scanning

**IPS Profile Configuration:**
- Signature filters (by severity, target, OS)
- Enabled signatures or signature groups
- Action overrides for specific signatures
- Protocol decoder settings
- Packet logging options
- Rate-based signature thresholds

**Signature Targeting:**
- Client protection (signatures targeting clients)
- Server protection (signatures targeting servers)
- OS-specific signatures (Windows, Linux, etc.)
- Application-specific (Apache, IIS, SQL)

**False Positive Management:**
- Tune sensitivity based on environment
- Disable irrelevant signatures
- Monitor mode for new signatures
- Regular review of IPS logs
- Whitelist legitimate traffic patterns

**Best Practices:**
- Enable all critical and high severity signatures
- Use default profiles as starting point
- Custom profiles for specific server protection
- Enable protocol decoders for protocol validation
- Packet logging for forensic investigation
- Regular signature updates from FortiGuard
- Balance detection sensitivity with false positives
- Combine with other security profiles for defense-in-depth
- Monitor IPS performance impact
- Document signature customizations

---

### Topic 4: Routing

#### 4.1 Static Routes

**Objective:** Configure and route packets using static routes

**Key Concepts:**
- **Static Route Components**: Destination network, subnet mask, gateway (next-hop), interface, administrative distance
- **Administrative Distance (AD)**: Priority of route (lower = preferred); static route default = 10
- **Route Types**:
  - **Gateway Route**: Next-hop is IP address
  - **Interface Route**: Next-hop is interface name (for point-to-point links)
  - **Default Route**: 0.0.0.0/0 destination
  - **Black Hole Route**: Discard route (null interface)
- **Route Priority**: Multiple routes to same destination; lowest AD wins
- **Routing Table**: Shows active routes; use `get router info routing-table all`
- **ECMP (Equal Cost Multi-Path)**: Load balance across routes with same destination and AD

**Static Route Configuration:**
```
config router static
    edit 1
        set dst 10.20.0.0 255.255.255.0
        set gateway 192.168.1.1
        set device "port2"
        set distance 10
    next
end
```

**Common Static Route Scenarios:**
- Default route to internet: 0.0.0.0/0 → ISP gateway
- Branch office routing: Remote_Network → VPN tunnel interface
- Backup routes: Primary route AD 10, backup route AD 20
- Null routes: Discard traffic to specific destinations

**Route Monitoring:**
- Use `get router info routing-table all` to view active routes
- Link monitoring can disable routes when gateway unreachable
- SD-WAN can provide intelligent routing vs. static routes

**Best Practices:**
- Use meaningful route IDs and comments
- Configure backup routes with higher AD
- Implement route monitoring for automatic failover
- Document routing design and decisions
- Prefer dynamic routing (OSPF, BGP) for complex topologies
- Use static routes for simple topologies and default routes
- Regular auditing of routing table
- Test failover behavior with link monitoring

#### 4.2 SD-WAN Configuration

**Objective:** Configure SD-WAN for effective load balancing across multiple WAN links

**Key Concepts:**
- **SD-WAN Benefits**: Intelligent traffic steering, automatic failover, application-based routing, WAN optimization
- **SD-WAN Members**: WAN interfaces participating in SD-WAN zone
- **Health Checks**: Active monitoring using ping, HTTP, or DNS probes to measure link quality
  - **SLA Targets**: Latency, jitter, packet loss thresholds
- **Performance SLA**: Define acceptable performance parameters for each health check
- **Load Balancing Strategies**:
  - **Volume-Based**: Balance by data volume across links
  - **Session-Based**: Distribute sessions evenly
  - **Spillover**: Use primary until threshold, then secondary
  - **Source-Based**: Consistent link per source IP
  - **Best Quality (SLA)**: Route based on lowest latency/jitter/loss
  - **Priority**: Manual priority order
- **SD-WAN Rules**: Match traffic by application, destination, or source; steer to specific members
- **Application Steering**: Route specific applications (Office 365, VoIP) to best-performing link

**SD-WAN Configuration Components:**
1. **SD-WAN Interface Members**: Define WAN interfaces and costs
2. **Health Check Servers**: Targets for SLA monitoring (internet: 8.8.8.8, internal: server IPs)
3. **Performance SLA**: Define acceptable latency, jitter, packet loss
4. **SD-WAN Rules**: Traffic matching and steering policies
5. **Load Balance Algorithm**: Strategy per rule

**Health Check Configuration:**
- Protocol: Ping, HTTP, DNS
- Target: Server or destination to monitor
- Interval: Frequency of probes
- SLA thresholds: Latency, jitter, packet loss limits
- Failover: Link marked down when SLA violated

**SD-WAN Rule Matching:**
- Source/destination addresses
- Applications (via Application Control)
- Internet service (SaaS: Office365, Salesforce)
- URL categories
- User/group

**Typical SD-WAN Scenarios:**
- **Dual ISP Failover**: Primary ISP with automatic failover to backup
- **Application-Based Routing**: VoIP uses low-latency link, bulk traffic uses high-bandwidth link
- **Load Balancing**: Equal distribution of sessions across multiple links
- **Quality-Based**: Critical apps use best-performing link based on SLA

**Best Practices:**
- Deploy at least two WAN links for SD-WAN benefit
- Configure health checks to multiple targets for redundancy
- Set realistic SLA targets based on application requirements
- Use application-based rules for critical services
- Monitor SD-WAN dashboard for link quality trends
- Priority rules for mission-critical applications
- Document SD-WAN design and rule logic
- Regular testing of failover scenarios
- Combine with local-out traffic for FortiGate-originated traffic steering

---

### Topic 5: VPN

#### 5.1 Meshed and Redundant IPsec VPN

**Objective:** Implement meshed or partially redundant IPsec VPN topologies

**Key Concepts:**
- **VPN Topologies**:
  - **Point-to-Point**: Single tunnel between two sites
  - **Hub-and-Spoke**: Central hub with tunnels to multiple spokes; spokes route through hub to reach each other
  - **Full Mesh**: Every site has direct tunnel to every other site; n sites require n(n-1)/2 tunnels
  - **Partial Mesh**: Hub-and-spoke with selective direct spoke-to-spoke tunnels
- **IPsec Phases**:
  - **Phase 1**: Authentication and key exchange; establishes IKE SA (Security Association)
  - **Phase 2**: Negotiates encryption parameters for actual data; establishes IPsec SA
- **Authentication Methods**: Pre-shared key (PSK), certificate-based (PKI), both
- **Tunnel Interface vs. Policy-Based**: Route-based (virtual tunnel interface) preferred for dynamic routing and management
- **Phase 2 Selectors**: Define traffic to encrypt (quick mode selectors); typically local and remote subnets
- **NAT Traversal (NAT-T)**: Encapsulates IPsec in UDP port 4500 for NAT compatibility
- **Dead Peer Detection (DPD)**: Detects tunnel failures and triggers reconnection
- **Redundancy Methods**:
  - **Backup Tunnel**: Primary tunnel with higher priority/lower route distance
  - **ECMP VPN**: Multiple tunnels with equal priority for load balancing
  - **SD-WAN VPN**: Intelligent selection across multiple VPN tunnels

**IPsec Phase 1 Configuration:**
- IKE version (IKEv1 or IKEv2)
- Authentication method (PSK or certificate)
- Encryption and authentication algorithms (AES-256, SHA-256)
- DH group for key exchange
- NAT traversal enable
- DPD settings

**IPsec Phase 2 Configuration:**
- Encryption and authentication algorithms
- Local and remote subnets (quick mode selectors)
- PFS (Perfect Forward Secrecy) enable/disable
- Key lifetime
- Autokey keep-alive

**VPN Routing:**
- Static routes pointing to tunnel interface
- Dynamic routing (OSPF, BGP) over tunnel
- Route-based VPN allows flexible routing
- Policy-based VPN uses selectors for routing

**Hub-and-Spoke Design:**
- Hub has tunnels to all spokes
- Spokes reach each other via hub
- Fewer tunnels than full mesh (2n-2 for n sites)
- Hub requires routing between spoke networks

**Full Mesh Design:**
- Direct tunnels between all sites
- Optimal latency for site-to-site communication
- High management overhead
- Best for small number of sites (<5-6)

**Partial Mesh Design:**
- Hub-and-spoke baseline
- Direct tunnels for frequently communicating spokes
- Balance between mesh and hub-and-spoke
- Flexible and scalable

**VPN Redundancy Scenarios:**
1. **Dual Tunnels Different ISPs**: Primary tunnel on ISP1, backup on ISP2; route distance determines active tunnel
2. **SD-WAN VPN Overlay**: Multiple VPN tunnels as SD-WAN members; intelligent steering based on SLA
3. **Redundant Hubs**: Spoke tunnels to two hub sites; automatic failover on hub failure

**Monitoring and Troubleshooting:**
- `get vpn ipsec tunnel summary` - View tunnel status
- `diagnose vpn ike gateway list` - Phase 1 status and negotiation details
- `diagnose vpn tunnel list` - Phase 2 status and encryption counters
- `diagnose debug application ike -1` - Detailed IKE negotiation debug
- Event logs for tunnel up/down events

**Best Practices:**
- Use IKEv2 for better performance and reliability
- Certificate-based authentication for scalability and security
- Enable NAT-T for NAT compatibility
- Configure DPD for fast failure detection
- Use route-based VPN with tunnel interfaces
- Document tunnel endpoints and selectors
- Implement redundancy for critical site connectivity
- Regular testing of VPN failover
- Monitor VPN bandwidth utilization
- Use dynamic routing over VPN for flexibility
- Hub-and-spoke for many sites, partial mesh for specific needs
- SD-WAN integration for optimal VPN performance

---

## Study Tips and Recommendations

### Exam Preparation Strategy

1. **Hands-On Practice**: Set up FortiGate VM lab environment to practice configurations
2. **Documentation Review**: Study official Fortinet documentation linked in exam blueprint
3. **Topic Prioritization**: Focus on deployment, firewall policies, and content inspection (heavier topics)
4. **CLI Familiarity**: Learn common diagnostic and configuration commands
5. **Scenario Practice**: Work through real-world scenarios to understand application
6. **Review Logs**: Practice interpreting FortiGate logs for troubleshooting

### Key Commands Reference

**System and Diagnostics:**
- `get system status` - System information
- `get system performance status` - Resource utilization
- `diagnose sys top` - Real-time process monitoring
- `diagnose debug flow` - Packet flow tracing
- `diagnose sniffer packet <int> '<filter>'` - Packet capture

**Routing and VPN:**
- `get router info routing-table all` - Routing table
- `get vpn ipsec tunnel summary` - VPN tunnel status
- `diagnose vpn tunnel list` - Detailed tunnel information

**Configuration:**
- `show` - Display configuration
- `execute backup config` - Backup configuration
- `execute restore config` - Restore configuration

### Common Pitfalls to Avoid

1. Forgetting implicit deny in firewall policies
2. Incorrect policy ordering (specific before general)
3. Misconfiguring Phase 2 selectors in VPN
4. Not enabling session pickup in HA configurations
5. Overlooking administrative distance in static routes
6. Forgetting to apply security profiles to policies
7. Not distributing CA certificate for SSL deep inspection
8. Improper NAT configuration causing connectivity issues

---

*End of FortiOS 7.6 Administrator Exam Preparation Guide*