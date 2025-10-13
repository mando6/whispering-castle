
### Learning Goals
- Generate secure GPG key pairs
- Understand key properties and metadata
- Import and export keys
- Manage key revocation and expiration

### Core Content

#### 3.1 Key Generation
**Best Practices:**
- Use strong passphrases
- Choose appropriate key sizes (RSA 4096-bit minimum)
- Set reasonable expiration dates
- Include accurate user ID information

**Command Example:**
```bash
gpg --full-generate-key
```

#### 3.2 Key Properties
**Key Components:**
- **Primary Key**: Master key for identity
- **Subkeys**: Specialized keys for specific functions
- **User ID**: Name and email association
- **Fingerprint**: Unique key identifier
- **Key ID**: Shortened fingerprint

#### 3.3 Key Distribution and Trust
**Web of Trust Model:**
- Decentralized trust system
- Users sign each other's keys
- Trust levels: Unknown, Never, Marginal, Full, Ultimate

**Key Servers:**
- Public repositories for key distribution
- Examples: keys.openpgp.org, keyserver.ubuntu.com
- Upload/download keys for public use

#### 3.4 Key Lifecycle Management
**Expiration:**
- Keys should have expiration dates
- Can be extended before expiration
- Forces regular key review

**Revocation:**
- Generates revocation certificate
- Publishes key compromise or retirement
- Should be prepared during key generation

### Connection to Main Topic
Key management is crucial for GPG security. Poor key practices can undermine all cryptographic protections. This module shows how GPG implements public key infrastructure concepts in practice.

### Practical Exercise 3
**Hands-on Tasks:**
1. Generate a new GPG key pair
2. Export your public key
3. Import a partner's public key
4. Create a revocation certificate
5. Upload your public key to a key server

### Knowledge Check 3
**Quiz Questions:**
1. What is the minimum recommended RSA key size for new GPG keys?
2. What is the difference between a key's fingerprint and key ID?
3. Why should GPG keys have expiration dates?
4. What is a revocation certificate and when should you create one?
5. Explain the Web of Trust model in three sentences.