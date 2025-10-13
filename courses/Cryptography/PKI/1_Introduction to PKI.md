### Core Topic: Foundations of Public Key Infrastructure

**Learning Objectives:**
- Define PKI and its purpose in modern cybersecurity
- Distinguish between symmetric and asymmetric cryptography
- Identify the core components of a PKI system

### Lesson Content

#### What is PKI?
Public Key Infrastructure (PKI) is a framework that manages digital keys and certificates to enable secure communication, authentication, and data integrity in digital environments. PKI provides the foundation for many security services including:
- Secure email communication
- Web browsing security (HTTPS)
- Code signing
- Document signing
- VPN authentication

#### Connection to Cryptography
PKI is built upon **asymmetric cryptography** (public-key cryptography), which uses mathematically related key pairs:
- **Public Key:** Freely distributed and used for encryption or signature verification
- **Private Key:** Kept secret and used for decryption or digital signing

This differs from symmetric cryptography, which uses a single shared key for both encryption and decryption.

#### Core PKI Components
1. **Certificate Authority (CA):** Issues and manages digital certificates
2. **Digital Certificates:** Electronic documents that bind public keys to identities
3. **Certificate Repository:** Storage for certificates and Certificate Revocation Lists
4. **Key Management:** Systems for generating, distributing, and managing keys

### Supplementary References
- RFC 5280: Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile
- "Applied Cryptography" by Bruce Schneier, Chapters 2-3
- NIST SP 800-57: Recommendations for Key Management

### Knowledge Check Quiz

**Question 1:** What is the primary advantage of asymmetric cryptography over symmetric cryptography in large-scale networks?
a) Faster encryption/decryption
b) Eliminates the key distribution problem
c) Uses shorter keys
d) Requires less computational power

**Question 2:** Which PKI component is responsible for issuing digital certificates?
a) Certificate Repository
b) Certificate Authority (CA)
c) Key Management System
d) Registration Authority

**Question 3:** True/False: In PKI, the private key should be freely distributed to enable secure communication.
