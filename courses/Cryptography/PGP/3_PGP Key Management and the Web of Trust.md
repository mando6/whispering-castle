### 3.1 Key Generation and Structure
PGP keys contain multiple components:
- **Master Key**: Primary signing key
- **Subkeys**: Separate keys for encryption, additional signing
- **User IDs**: Email addresses and names
- **Signatures**: Certifications of key ownership

### 3.2 The Web of Trust Model
Unlike hierarchical PKI systems, PGP uses a decentralized web of trust:
- Users sign each other's keys to vouch for identity
- Trust is transitive but diminishes with distance
- No central authority required

**Connection to Main Topic**: The web of trust reflects PGP's philosophy of user empowerment and decentralization, directly addressing the key authentication problem in public-key cryptography.

### 3.3 Trust Levels and Key Validation
**Trust Levels:**
- Unknown: No trust information
- None: Explicitly not trusted
- Marginal: Some trust in key owner
- Full: Complete trust in key owner
- Ultimate: Your own keys

**Validity Calculation:**
- One fully trusted signature = valid key
- Two marginally trusted signatures = valid key
- Configurable thresholds

### 3.4 Key Servers and Distribution
- Public key servers (e.g., keys.openpgp.org)
- Fingerprint verification
- Key server synchronization challenges

**Connection to Main Topic**: Key distribution and verification are critical to PGP's security model - without proper key management, the cryptographic strength becomes meaningless.

### Section 3 Lab Exercise
1. Generate a PGP key pair using GPG
2. Create multiple User IDs
3. Practice key signing with classmates
4. Upload keys to a public key server

### Section 3 Quiz
1. What is the difference between trust and validity in PGP?
2. How many marginally trusted signatures equal one fully trusted signature?
3. Explain why key fingerprint verification is crucial.
4. What problems does the web of trust solve compared to hierarchical PKI?