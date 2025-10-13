**Course Level:** Intermediate  
**Estimated Time:** 4-6 hours  
**Prerequisites:** Basic understanding of computer networks and digital forensics fundamentals

---
## Course Overview

This course provides digital forensics professionals with comprehensive knowledge of network topologies and devices essential for conducting network-based investigations. Understanding network architecture and device functionality is critical for identifying evidence sources, reconstructing network traffic, and analyzing security incidents.

**Learning Objectives:**
- Understand common network topologies and their forensic implications
- Identify the role and forensic value of network devices
- Recognize how network devices store and process evidence
- Apply topology knowledge to forensic investigation planning

---

## Module 1: Network Topologies

### Introduction

Network topology refers to the arrangement of nodes and connections in a network. From a forensics perspective, understanding topology is essential because it determines:
- Where evidence may be located
- How traffic flows through the network
- Which devices witnessed specific communications
- Potential points of compromise or data exfiltration

### 1.1 Physical vs. Logical Topology

**Physical Topology** describes the actual physical layout of cables, devices, and connections. This is crucial for forensic investigators when:
- Conducting on-site evidence collection
- Identifying physical access points
- Determining cable tapping possibilities
- Mapping physical security controls

**Logical Topology** describes how data flows through the network regardless of physical layout. This matters for:
- Traffic analysis and reconstruction
- Understanding data paths during incidents
- Identifying monitoring points
- Analyzing access control implementations

**Forensic Connection:** During investigations, you must map both topologies. Physical topology reveals where devices are located and how they're connected, while logical topology shows how data actually travels and where it can be intercepted or logged.

### 1.2 Common Network Topologies

#### Bus Topology
In a bus topology, all devices connect to a single central cable (the bus). While largely obsolete in modern networks, you may encounter it in:
- Legacy industrial control systems
- Older building management systems
- Historical network reconstructions

**Forensic Considerations:**
- Limited logging capabilities
- Single point of failure affects evidence availability
- Difficult to isolate specific device communications
- Promiscuous mode capture can see all traffic

#### Star Topology
The most common modern topology, where all devices connect to a central hub or switch. This is the standard for most corporate LANs.

**Forensic Considerations:**
- Central device (switch) is critical evidence source
- Easy to isolate individual devices for analysis
- Switch port mirroring enables traffic capture
- Central logging point for network activity
- Simplified evidence collection planning

**Connection to Forensics:** Star topologies centralize evidence at the switch level, making it your primary target for network traffic analysis and connection logs.

#### Ring Topology
Devices connect in a circular fashion, with each device having exactly two neighbors. Common in Token Ring networks and some Fiber Distributed Data Interface (FDDI) implementations.

**Forensic Considerations:**
- Traffic passes through multiple devices
- Each device can potentially log or capture traffic
- Break in ring affects evidence availability
- Useful for redundancy analysis in incident response

#### Mesh Topology
Every device connects to multiple other devices, providing redundancy. Common in:
- Wireless mesh networks
- Enterprise core networks
- Internet backbone infrastructure
- Software-defined networks (SDN)

**Forensic Considerations:**
- Multiple data paths complicate traffic reconstruction
- High redundancy means multiple evidence sources
- Complex routing requires detailed path analysis
- Useful for identifying data exfiltration routes

#### Hybrid Topologies
Real-world networks combine multiple topologies. For example, a corporate network might use:
- Star topology for access layer (end-user connections)
- Mesh topology for distribution/core layer (redundancy)
- Point-to-point for WAN connections

**Forensic Connection:** Understanding the hybrid nature helps you identify all potential evidence sources and traffic paths relevant to your investigation.

---

## Module 2: Network Devices and Forensic Artifacts

### Introduction

Network devices are critical evidence sources in digital forensics. Each device type processes, stores, and logs information differently. Understanding device functionality helps forensic examiners identify what evidence exists, where it's stored, and how to extract it properly.

### 2.1 Hubs (Layer 1 Devices)

#### Functionality
Hubs operate at the Physical Layer (OSI Layer 1) and simply repeat all incoming signals to all ports. They are essentially multi-port repeaters with no intelligence.

**Key Characteristics:**
- No packet inspection or filtering
- Creates single collision domain
- Half-duplex communication
- No MAC address awareness

#### Forensic Value and Limitations

**Limited Forensic Value:**
- No logging capabilities
- No configuration storage
- No traffic analysis features
- Cannot isolate specific connections

**Forensic Applications:**
- Can be inserted for passive traffic capture (span all traffic)
- Useful in controlled forensic environments for monitoring
- Historical network reconstructions

**Connection to Digital Forensics:** While hubs provide minimal forensic artifacts themselves, their broadcast nature means any device on the network can capture all traffic in promiscuous mode, which is valuable for live traffic analysis but raises questions about unauthorized monitoring in investigations.

### 2.2 Switches (Layer 2 Devices)

#### Functionality
Switches operate at the Data Link Layer (OSI Layer 2) and make forwarding decisions based on MAC addresses. Modern switches are the backbone of LAN infrastructure.

**Key Operations:**
- MAC address learning and table building
- Frame forwarding based on destination MAC
- VLAN segmentation
- Port security features
- Spanning Tree Protocol (STP) operation

#### Forensic Artifacts

Switches are goldmines for forensic investigators. They maintain numerous artifacts:

**MAC Address Tables:**
- Show which MAC addresses are connected to which ports
- Timestamp information (on capable switches)
- VLAN associations
- Help identify device locations and movements

**VLAN Configuration:**
- Logical network segmentation
- Access control boundaries
- Inter-VLAN routing rules
- Security policy implementation

**Port Configuration:**
- Speed/duplex settings
- Port security settings (MAC filtering)
- Port mirroring (SPAN) configurations
- Disabled/unused ports

**Logs and SNMP Data:**
- Port up/down events
- Security violations
- DHCP snooping information
- Authentication attempts (802.1X)

**ARP Tables:**
- IP-to-MAC address mappings
- Cache timing information
- ARP spoofing evidence

#### Forensic Techniques

**Port Mirroring (SPAN):**
Configure switches to copy traffic from one or more ports to a monitoring port for live capture and analysis.

**MAC Address Analysis:**
Track device movements across the network by correlating MAC addresses with switch port histories.

**VLAN Investigation:**
Identify unauthorized VLAN hopping or misconfigured trunk ports that could indicate security breaches.

**Connection to Digital Forensics:** Switches provide context about network connectivity, device location, and communication patterns. Their logs can establish timelines, identify unauthorized devices, and reveal network-based attacks like MAC flooding or VLAN hopping.

### 2.3 Routers (Layer 3 Devices)

#### Functionality
Routers operate at the Network Layer (OSI Layer 3) and forward packets between different networks based on IP addresses. They're the gatekeepers between network segments and to the Internet.

**Key Operations:**
- IP packet forwarding based on routing tables
- Network Address Translation (NAT)
- Access Control Lists (ACLs)
- Quality of Service (QoS) implementation
- Routing protocol operations (BGP, OSPF, EIGRP)

#### Forensic Artifacts

Routers maintain critical evidence for tracking inter-network communications:

**Routing Tables:**
- Show network paths and next-hop information
- Help reconstruct traffic flows
- Identify routing anomalies or hijacking

**NAT/PAT Tables:**
- Critical for mapping private IPs to public IPs
- Include port mappings for connection tracking
- Time-stamped session information
- Essential for correlating internal hosts with external communications

**Access Control Lists (ACLs):**
- Filter rules showing allowed/denied traffic
- Security policy implementation
- Can include logged denied connections
- Show security posture and policy violations

**NetFlow/IPFIX Data:**
- Summarized connection records (5-tuple: src IP, dst IP, src port, dst port, protocol)
- Bandwidth usage statistics
- Communication patterns and baselines
- Long-term traffic history (if exported to collector)

**System Logs:**
- Configuration changes
- Authentication attempts
- Routing protocol updates
- Interface status changes
- Security events

**DHCP Server Logs:**
- IP address assignments to MAC addresses
- Lease times and renewal history
- Hostname information
- Critical for IP-to-device correlation

#### Forensic Significance

**Connection Correlation:**
NAT tables are essential for attributing external communications to specific internal hosts. Without this data, you cannot definitively link internal devices to external connections.

**Traffic Pattern Analysis:**
NetFlow data provides historical visibility into network communications, enabling investigators to identify anomalous connections, data exfiltration, and command-and-control traffic patterns.

**Policy Enforcement Evidence:**
ACL logs demonstrate what was technically possible on the network and can prove or disprove access claims.

**Connection to Digital Forensics:** Routers are critical chokepoints where inter-network traffic must pass. Their logs and state tables are essential for attributing network activity, understanding traffic flows during incidents, and reconstructing attack timelines.

### 2.4 Firewalls (Layer 3-7 Devices)

#### Functionality
Firewalls enforce security policies by filtering traffic based on various criteria. Modern firewalls operate across multiple OSI layers and provide deep packet inspection capabilities.

**Types of Firewalls:**
- **Packet Filtering (Layer 3-4):** Basic IP/port-based filtering
- **Stateful Inspection:** Tracks connection states and contexts
- **Application Layer (Layer 7):** Deep inspection of application protocols
- **Next-Generation Firewalls (NGFW):** Integrated IPS, application awareness, user identity

#### Forensic Artifacts

Firewalls are among the most valuable forensic evidence sources:

**Connection Logs:**
- Source and destination IPs/ports
- Timestamps (start, end, duration)
- Bytes transferred
- Action taken (allow/deny)
- User identity (if integrated with directory services)

**Security Event Logs:**
- Blocked connection attempts
- Policy violations
- Malware detection (if NGFW)
- Intrusion attempts
- Application usage

**Rule Base Configuration:**
- Current security policies
- Change history and audit trails
- Administrator actions
- Policy exceptions

**VPN Logs:**
- Remote access connections
- User authentication records
- Session duration and data transfer
- Endpoint security compliance checks

**URL Filtering Logs:**
- Web browsing history
- Category-based blocking
- User attribution

**Advanced Threat Protection Logs:**
- Sandboxing results
- File transfer records
- Malware detection and blocking
- Command-and-control communications

#### Forensic Applications

**Incident Timeline Reconstruction:**
Firewall logs provide precise timestamps for network connections, enabling investigators to build detailed timelines of attacker actions or insider threats.

**Attribution:**
User identity integration allows direct attribution of network activity to specific individuals, crucial for insider threat investigations.

**Data Exfiltration Analysis:**
Large data transfers, unusual destinations, or policy violations in logs can indicate data theft or exfiltration.

**Connection to Digital Forensics:** Firewalls serve as security enforcement points and comprehensive logging platforms. Their logs are often the most detailed and retained longest, making them primary evidence sources for establishing what happened on the network, who was involved, and when events occurred.

### 2.5 Intrusion Detection/Prevention Systems (IDS/IPS)

#### Functionality

**Intrusion Detection Systems (IDS):**
- Monitor network traffic for suspicious patterns
- Alert on potential security incidents
- Passive observation (doesn't block traffic)
- Network-based (NIDS) or Host-based (HIDS)

**Intrusion Prevention Systems (IPS):**
- Active monitoring with blocking capabilities
- Can terminate malicious connections
- Inline deployment (traffic passes through)
- May modify or drop packets

#### Detection Methods

**Signature-Based Detection:**
- Matches traffic against known attack patterns
- High accuracy for known threats
- Requires regular signature updates
- Low false positive rate

**Anomaly-Based Detection:**
- Establishes baseline of normal behavior
- Detects deviations from baseline
- Can identify zero-day attacks
- Higher false positive rate

**Behavioral Analysis:**
- Monitors for suspicious behaviors
- Protocol anomalies
- Unusual traffic patterns
- Advanced persistent threat (APT) indicators

#### Forensic Artifacts

IDS/IPS systems provide detailed attack intelligence:

**Alert Logs:**
- Attack signatures detected
- Severity ratings
- Source/destination information
- Attack classification (reconnaissance, exploitation, C2)

**Packet Captures (PCAPs):**
- Full or partial packet captures around alerts
- Enable deep dive analysis
- Can be replayed for investigation
- Contain complete attack evidence

**Attack Timeline Data:**
- Chronological sequence of events
- Multi-stage attack reconstruction
- Lateral movement tracking

**Threat Intelligence Correlation:**
- Known malicious IPs and domains
- Threat actor attribution
- Campaign identification
- IOC (Indicators of Compromise) matching

**False Positive Analysis:**
- Helps refine understanding of normal network behavior
- Identifies misconfigurations
- Improves future detection

#### Forensic Significance

**Attack Reconstruction:**
IDS/IPS alerts and packet captures enable investigators to understand exactly how an attack unfolded, what vulnerabilities were exploited, and what data was accessed or exfiltrated.

**Early Warning Indicators:**
Alert logs can reveal attempted attacks that were blocked, showing attack patterns and helping identify if defenses were effective.

**Evidence Preservation:**
Packet captures provide immutable evidence of network communications, including malicious payloads, command-and-control traffic, and exfiltration attempts.

**Connection to Digital Forensics:** IDS/IPS systems act as network security sensors, providing detailed visibility into attack methods and malicious activity. Their alerts guide investigation focus, while packet captures provide irrefutable evidence of network-based attacks. For forensic examiners, IDS/IPS logs often contain the smoking gun evidence of compromise.

---

## Module 3: Integration and Forensic Investigation Planning

### Connecting Topology to Device Placement

Understanding how devices are positioned within network topologies is essential for comprehensive investigations:

**Edge Devices (Network Perimeter):**
- Firewalls at Internet connection points
- Primary evidence for external threats
- VPN concentrators for remote access
- First/last point of contact logging

**Distribution Layer:**
- Core routers and switches
- Aggregate traffic from multiple access switches
- Strategic IDS/IPS placement
- Inter-VLAN routing evidence

**Access Layer:**
- End-user switches
- Directly connected to endpoints
- Detailed port-level evidence
- Physical access and port security logs

**DMZ (Demilitarized Zone):**
- Public-facing servers
- Additional firewalls
- Enhanced monitoring and logging
- Critical for external attack investigations

### Evidence Collection Strategy

**Priority Evidence Sources (in typical order):**
1. Firewall logs (connection records, user attribution)
2. IDS/IPS alerts and packet captures (attack evidence)
3. Router NAT tables and NetFlow data (connection correlation)
4. Switch MAC tables and port logs (device location)
5. DHCP server logs (IP-to-device mapping)
6. DNS server logs (domain resolution)

**Temporal Considerations:**
- Volatile data first (active connections, ARP/NAT tables)
- Time-sensitive logs before rotation
- Configuration snapshots
- Archived logs and flow data

**Chain of Evidence:**
- Document network topology
- Photograph rack layouts and connections
- Hash configuration files
- Preserve timestamps (consider NTP accuracy)
- Document collection methodology

### Common Forensic Scenarios

**Scenario 1: Data Exfiltration Investigation**
- Firewall logs identify large outbound transfers
- Router NetFlow confirms sustained connection
- IDS/IPS may have alerted on data staging
- Switch logs show source device port
- DHCP logs correlate IP to MAC and hostname

**Scenario 2: Lateral Movement After Compromise**
- IDS/IPS alerts on exploitation attempt
- Switch logs show unusual port-to-port traffic patterns
- Firewall shows authorized user making unusual connections
- Router ACLs reveal cross-segment access
- Timeline reconstruction from correlated device logs

**Scenario 3: Insider Threat**
- Firewall VPN logs show remote access
- User attribution from authentication systems
- Switch port security violations
- Unusual VLAN access attempts
- Correlation with physical access logs

---

## Course Conclusion

### Key Takeaways

Network topologies and devices form the foundation of digital forensics investigations involving network activity. Understanding these components enables forensic examiners to:

1. **Identify evidence sources** based on network architecture
2. **Extract relevant artifacts** from switches, routers, firewalls, and IDS/IPS
3. **Correlate evidence** across multiple devices for comprehensive analysis
4. **Reconstruct incidents** using complementary data from various network layers
5. **Plan investigations** efficiently by targeting high-value evidence sources

### Professional Application

The concepts covered in this course directly apply to:
- Incident response and breach investigations
- Insider threat investigations
- Data exfiltration analysis
- Attack timeline reconstruction
- Expert testimony preparation
- Security architecture assessment

### Continuing Education

Network forensics is an evolving field. Stay current by:
- Following vendor security bulletins and documentation updates
- Participating in professional organizations (HTCIA, IACIS, ISFCE)
- Attending conferences (SANS DFIR Summit, DFRWS, Black Hat)
- Practicing with lab environments and capture-the-flag exercises
- Obtaining relevant certifications (GCFA, GNFA, EnCE, CCE)

### Final Notes

This course provides intermediate-level knowledge. Real-world investigations require hands-on practice, familiarity with specific vendor implementations, and understanding of legal and procedural requirements. Always follow your organization's policies and applicable laws when conducting forensic examinations.

For questions or further discussion about this course material, consult the supplementary resources provided or reach out to professional forensics communities and training organizations.