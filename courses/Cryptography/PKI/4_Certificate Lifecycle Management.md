
### Core Topic: Managing Certificates Throughout Their Lifetime

**Learning Objectives:**
- Describe the complete certificate lifecycle
- Understand certificate enrollment processes
- Explain certificate renewal and revocation procedures

### Lesson Content

#### Certificate Lifecycle Phases

**Connection to PKI:** Certificate lifecycle management is crucial for PKI operations. Poor lifecycle management leads to security vulnerabilities, service outages, and compliance issues.

**1. Certificate Request/Enrollment**
- Key pair generation
- Certificate Signing Request (CSR) creation
- Identity verification
- Certificate issuance

**2. Certificate Distribution**
- Delivery to certificate holder
- Publication in certificate repository
- Installation in applications/systems

**3. Certificate Usage**
- Authentication processes
- Digital signing
- Encryption/decryption operations

**4. Certificate Renewal**
- Before expiration
- Key rollover considerations
- Automated vs. manual renewal

**5. Certificate Revocation**
- Compromise situations
- Change in status/role
- Revocation mechanisms (CRL, OCSP)

**6. Certificate Archival**
- Historical record keeping
- Legal compliance requirements
- Long-term signature validation

#### Certificate Enrollment Methods
- **Manual Enrollment:** Administrative approval required
- **Auto-enrollment:** Automatic based on policy
- **SCEP (Simple Certificate Enrollment Protocol):** Network device enrollment
- **EST (Enrollment over Secure Transport):** Modern enrollment protocol

### Supplementary References
- RFC 2510: Internet X.509 Public Key Infrastructure Certificate Management Protocols
- RFC 7030: Enrollment over Secure Transport
- "PKI Implementation and Management" by M. Hassell and T. Jenkinson, Chapter 8

### Practical Exercise
Create a Certificate Signing Request using OpenSSL:
```bash
openssl req -new -keyout private.key -out request.csr
```

### Knowledge Check Quiz

**Question 1:** What document is created during the certificate enrollment process?
a) Certificate Revocation List
b) Certificate Signing Request
c) Certificate Authority Certificate
d) Root Certificate

**Question 2:** When should certificate renewal typically occur?
a) After the certificate expires
b) Only when the key is compromised
c) Before the certificate expires
d) Every year regardless of expiration

**Question 3:** What is the primary purpose of certificate archival?
a) To save storage space
b) To maintain historical records for compliance
c) To speed up certificate validation
d) To reduce CA workload
