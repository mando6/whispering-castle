
### Core Topic: Digital Certificates Structure and Function

**Learning Objectives:**
- Analyze the structure of X.509 digital certificates
- Explain certificate fields and their purposes
- Understand certificate encoding formats

### Lesson Content

#### Digital Certificates Explained
Digital certificates are electronic credentials that bind a public key to an entity's identity. They serve as digital passports, providing trust in digital communications.

**Connection to PKI:** Certificates are the cornerstone of PKI, enabling trust relationships between parties who have never met. Without certificates, there would be no way to verify that a public key belongs to a specific entity.

#### X.509 Certificate Structure
The X.509 standard defines the format for public key certificates:

**Essential Fields:**
- **Version:** X.509 version number
- **Serial Number:** Unique identifier within the CA
- **Signature Algorithm:** Algorithm used by CA to sign the certificate
- **Issuer:** Distinguished Name of the Certificate Authority
- **Validity Period:** Not Before and Not After dates
- **Subject:** Distinguished Name of the certificate holder
- **Subject Public Key Info:** The public key and its algorithm
- **Extensions:** Additional information (Key Usage, Subject Alternative Name, etc.)

#### Certificate Encoding Formats
- **DER (Distinguished Encoding Rules):** Binary format
- **PEM (Privacy-Enhanced Mail):** Base64 encoded DER with headers
- **PKCS#12:** Container format for private keys and certificates

### Supplementary References
- ITU-T X.509 Recommendation
- RFC 3280: Internet X.509 Public Key Infrastructure Certificate and CRL Profile
- "PKI Uncovered" by Andre Kaplan, Chapter 4

### Practical Exercise
Use OpenSSL to examine a certificate:
```bash
openssl x509 -in certificate.pem -text -noout
```

### Knowledge Check Quiz

**Question 1:** What information does the Subject field in an X.509 certificate contain?
a) The CA's identity
b) The certificate holder's identity
c) The public key algorithm
d) The certificate's expiration date

**Question 2:** Which certificate format is human-readable?
a) DER
b) PEM
c) PKCS#12
d) None of the above

**Question 3:** What happens when a certificate's "Not After" date is reached?
a) The certificate is automatically renewed
b) The certificate becomes invalid
c) The private key is compromised
d) The CA is notified