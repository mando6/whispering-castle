
### Core Topic: Managing Compromised and Invalid Certificates

**Learning Objectives:**
- Understand reasons for certificate revocation
- Compare CRL and OCSP revocation mechanisms
- Implement revocation checking in applications

### Lesson Content

#### Why Certificates Are Revoked

**Connection to PKI:** Revocation is a critical PKI security mechanism. Without effective revocation, compromised certificates could continue to be trusted, creating significant security risks.

**Common Revocation Reasons:**
- Private key compromise
- CA key compromise
- Change of affiliation
- Certificate superseded
- Cessation of operations
- Certificate hold (temporary suspension)

#### Certificate Revocation Lists (CRL)
- **Structure:** Signed list of revoked certificate serial numbers
- **Distribution:** Published at regular intervals
- **Advantages:** Simple, widely supported
- **Disadvantages:** Scalability issues, delayed updates

#### Online Certificate Status Protocol (OCSP)
- **Function:** Real-time certificate status checking
- **Process:** Query-response protocol
- **Advantages:** Real-time status, reduced bandwidth
- **Disadvantages:** Availability dependency, privacy concerns

#### OCSP Stapling
- **Mechanism:** Server provides OCSP response with certificate
- **Benefits:** Reduces client OCSP queries, improves performance
- **Implementation:** Supported in modern TLS implementations

### Supplementary References
- RFC 3280: Certificate Revocation Lists
- RFC 2560: Online Certificate Status Protocol - OCSP
- RFC 6066: Transport Layer Security Extensions (OCSP Stapling)

### Hands-on Lab
Check certificate revocation status:
```bash
# Check CRL
openssl crl -in crl.pem -text -noout

# OCSP check
openssl ocsp -issuer ca.pem -cert cert.pem -url http://ocsp.example.com
```

### Knowledge Check Quiz

**Question 1:** What is the main advantage of OCSP over CRL?
a) Smaller file sizes
b) Real-time status checking
c) Better security
d) Easier implementation

**Question 2:** What does OCSP Stapling help to reduce?
a) Certificate size
b) Server processing load
c) Client OCSP queries
d) CA workload

**Question 3:** Which revocation reason indicates a temporary suspension?
a) Key compromise
b) Cessation of operations
c) Certificate hold
d) Superseded