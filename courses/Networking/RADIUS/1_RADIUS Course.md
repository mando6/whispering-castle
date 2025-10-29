## Course Overview
### Learning Objectives
By the end of this course, students will be able to:
- Explain what RADIUS is and its primary functions
- Describe the RADIUS authentication, authorization, and accounting (AAA) framework
- Configure basic RADIUS server and client setups
- Troubleshoot common RADIUS implementation issues
- Implement RADIUS in enterprise network environments

---

## Section 1: Introduction to RADIUS

### 1.1 What is RADIUS?

RADIUS (Remote Authentication Dial-In User Service) is a networking protocol that provides centralized authentication, authorization, and accounting (AAA) management for users who connect and use network services. Despite its name referencing "dial-in," RADIUS is widely used for various network access scenarios including wireless networks, VPNs, and network switches.

**Key Characteristics:**
- Client-server protocol
- Uses UDP (User Datagram Protocol)
- Operates on ports 1812 (authentication) and 1813 (accounting)
- Stateless protocol
- Industry standard defined by RFC 2865

### 1.2 Historical Context and Evolution

RADIUS was originally developed by Livingston Enterprises in 1991 for dial-up network access. As networking evolved, RADIUS adapted to support:
- Wireless networks (802.1X)
- VPN connections
- Network device administration
- Web authentication portals

### 1.3 Connection to Core Networking Concepts

RADIUS integrates with fundamental networking concepts:
- **Network Security:** Provides authentication layer
- **Access Control:** Determines user permissions
- **Network Management:** Centralized user administration
- **Scalability:** Supports large distributed networks

---

## Section 2: The AAA Framework

### 2.1 Authentication

**Definition:** The process of verifying user identity

**How it connects to RADIUS:**
- RADIUS receives authentication requests from network access servers (NAS)
- Validates credentials against user database
- Returns Accept, Reject, or Challenge responses

**Authentication Methods:**
- Password Authentication Protocol (PAP)
- Challenge Handshake Authentication Protocol (CHAP)
- Extensible Authentication Protocol (EAP)
- Microsoft CHAP (MS-CHAP)

### 2.2 Authorization

**Definition:** Determining what an authenticated user is allowed to do

**RADIUS Authorization Features:**
- VLAN assignment
- Bandwidth limitations
- Access time restrictions
- Service type definitions
- Filter assignments

### 2.3 Accounting

**Definition:** Tracking and logging user network activity

**RADIUS Accounting Capabilities:**
- Session start/stop times
- Data transfer volumes
- Connection duration
- Resource utilization
- Billing information collection

**Connection to Network Management:** Accounting data feeds into network monitoring, capacity planning, and security analysis systems.

---

## Section 3: RADIUS Protocol Architecture

### 3.1 Client-Server Model

**RADIUS Clients (NAS - Network Access Servers):**
- Wireless access points
- VPN concentrators
- Network switches
- Firewalls
- Remote access servers

**RADIUS Servers:**
- Authenticate users
- Store user profiles
- Maintain accounting records
- Enforce policies

### 3.2 Communication Flow

**Basic Authentication Flow:**
1. User attempts network access
2. NAS sends Access-Request to RADIUS server
3. RADIUS server validates credentials
4. Server responds with Access-Accept, Access-Reject, or Access-Challenge
5. NAS grants or denies access based on response

### 3.3 RADIUS Attributes

**Attribute-Value Pairs (AVPs):**
- User-Name
- User-Password
- NAS-IP-Address
- Service-Type
- Framed-IP-Address
- Session-Timeout

**Connection to Network Configuration:** Attributes allow dynamic network configuration based on user profiles, enabling flexible and scalable network management.

---

## Section 4: RADIUS Message Types and Packet Structure

### 4.1 Message Types

**Authentication Messages:**
- Access-Request (1)
- Access-Accept (2)
- Access-Reject (3)
- Access-Challenge (11)

**Accounting Messages:**
- Accounting-Request (4)
- Accounting-Response (5)

### 4.2 Packet Structure

**RADIUS Packet Format:**
- Code (1 byte): Message type
- Identifier (1 byte): Matches requests/responses
- Length (2 bytes): Packet length
- Authenticator (16 bytes): Security hash
- Attributes (variable): Configuration data

### 4.3 Security Mechanisms

**Shared Secret:**
- Pre-shared key between client and server
- Used for packet authentication
- Encrypts sensitive attributes

**Connection to Network Security:** RADIUS security mechanisms integrate with overall network security architecture, providing authentication layer protection.

---

## Section 5: RADIUS Implementation

### 5.1 Common RADIUS Servers

**Open Source Solutions:**
- FreeRADIUS
- OpenRADIUS

**Commercial Solutions:**
- Microsoft Network Policy Server (NPS)
- Cisco Identity Services Engine (ISE)
- Aruba ClearPass

### 5.2 Integration Scenarios

**Wireless Networks (802.1X):**
- WPA2/WPA3 Enterprise
- Certificate-based authentication
- Dynamic VLAN assignment

**VPN Access:**
- IPSec VPN authentication
- SSL VPN integration
- Multi-factor authentication

**Network Device Management:**
- Switch/router administrative access
- Privilege level assignment
- Command authorization

### 5.3 Configuration Examples

**Basic FreeRADIUS Client Configuration:**
```
client wireless-controller {
    ipaddr = 192.168.1.100
    secret = shared-secret-key
    shortname = wlc-01
}
```

**User Database Entry:**
```
alice   Cleartext-Password := "password123"
        Service-Type = Framed-User,
        Framed-IP-Address = 192.168.10.100
```

---

## Section 6: Advanced RADIUS Topics

### 6.1 RADIUS Proxy and Realms

**Proxy Functionality:**
- Forwards authentication requests
- Enables distributed authentication
- Supports roaming scenarios

**Realm Configuration:**
- User@domain.com format
- Cross-organizational authentication
- Service provider scenarios

### 6.2 High Availability and Load Balancing

**Redundancy Strategies:**
- Multiple RADIUS servers
- Failover mechanisms
- Load distribution

**Connection to Network Reliability:** RADIUS availability directly impacts network access, making redundancy critical for business continuity.

### 6.3 Integration with Directory Services

**LDAP Integration:**
- Active Directory authentication
- Centralized user management
- Group-based policies

**Database Backends:**
- MySQL/PostgreSQL
- SQL Server
- Oracle databases

---

## Section 7: Troubleshooting RADIUS

### 7.1 Common Issues

**Authentication Failures:**
- Incorrect shared secrets
- Network connectivity problems
- User credential mismatches
- Certificate validation errors

**Performance Problems:**
- Server overload
- Network latency
- Database bottlenecks

### 7.2 Diagnostic Tools

**Logging and Monitoring:**
- RADIUS server logs
- Network packet captures
- Authentication event logs
- Performance metrics

**Testing Tools:**
- radtest utility
- NTRadPing
- Wireshark protocol analyzer

### 7.3 Best Practices

**Security:**
- Strong shared secrets
- Regular certificate updates
- Secure transport (RadSec)
- Access control lists

**Performance:**
- Server capacity planning
- Database optimization
- Network path optimization