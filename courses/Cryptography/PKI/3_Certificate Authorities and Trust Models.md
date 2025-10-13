
### Core Topic: Trust Establishment in PKI

**Learning Objectives:**
- Compare different CA trust models
- Understand the CA hierarchy structure
- Evaluate trust anchors and root certificates

### Lesson Content

#### Certificate Authority Role
Certificate Authorities are trusted third parties that issue, manage, and revoke digital certificates. They act as the "notary public" of the digital world.

**Connection to PKI:** CAs are central to PKI trust. Without trusted CAs, there would be no way to establish trust in digital certificates. The entire PKI ecosystem relies on trust in Certificate Authorities.

#### Trust Models

**1. Single CA Model**
- One CA issues all certificates
- Simple but creates single point of failure
- Suitable for small, closed environments

**2. Hierarchical CA Model**
- Root CA at the top, subordinate CAs below
- Distributes trust and management load
- Most common in enterprise environments

**3. Web of Trust Model**
- Decentralized trust (used in PGP)
- Users validate each other's keys
- No central authority required

**4. Cross-Certification Model**
- Multiple CA hierarchies trust each other
- Enables inter-organizational communication
- Complex trust relationships

#### Root Certificates and Trust Anchors
- **Root Certificate:** Self-signed certificate of the Root CA
- **Trust Anchor:** Pre-installed root certificates in browsers/systems
- **Certificate Chain:** Path from end-entity certificate to trusted root

### Supplementary References
- RFC 4158: Internet X.509 Public Key Infrastructure: Certification Path Building
- "Understanding PKI" by Carlisle Adams and Steve Lloyd, Chapter 6
- NIST SP 800-15: Minimum Interoperability Specification for PKI Components

### Case Study
Analyze the trust chain for a major website (e.g., Google.com):
1. End-entity certificate
2. Intermediate CA certificate(s)
3. Root CA certificate

### Knowledge Check Quiz

**Question 1:** In a hierarchical CA model, what validates the intermediate CA's certificate?
a) The end-entity certificate
b) The Root CA
c) Another intermediate CA
d) The certificate holder

**Question 2:** What is a trust anchor?
a) A certificate that needs validation
b) A pre-installed root certificate
c) An intermediate CA certificate
d) A revoked certificate

**Question 3:** Which trust model is most suitable for a large enterprise with multiple departments?
a) Single CA
b) Web of Trust
c) Hierarchical CA
d) Cross-Certification