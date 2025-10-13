
### Learning Goals
- Understand the difference between symmetric and asymmetric encryption
- Grasp the concept of digital signatures and authentication
- Recognize the importance of key management

### Core Content

#### 1.1 What is Cryptography?
Cryptography is the practice of securing information through mathematical techniques. In the digital age, it protects data confidentiality, integrity, and authenticity.

**Key Concepts:**
- **Confidentiality**: Ensuring only authorized parties can read information
- **Integrity**: Guaranteeing data hasn't been tampered with
- **Authentication**: Verifying the identity of communicating parties
- **Non-repudiation**: Preventing denial of message origin

#### 1.2 Symmetric vs Asymmetric Encryption

**Symmetric Encryption:**
- Same key encrypts and decrypts
- Fast and efficient for large data
- Key distribution problem
- Examples: AES, DES

**Asymmetric Encryption (Public Key Cryptography):**
- Two mathematically related keys: public and private
- Public key encrypts, private key decrypts
- Solves key distribution problem
- Slower than symmetric encryption
- Examples: RSA, ECC

#### 1.3 Digital Signatures
Digital signatures provide:
- Authentication (proves who sent the message)
- Integrity (proves message wasn't altered)
- Non-repudiation (sender can't deny sending it)

**How it works:**
1. Hash the message
2. Encrypt hash with private key (creates signature)
3. Recipient decrypts signature with public key
4. Compare with their own hash of the message

### Connection to GPG
GPG implements these cryptographic principles, serving as a practical tool that combines symmetric and asymmetric encryption, along with digital signatures, in a user-friendly package.

### Knowledge Check 1
**Quiz Questions:**
1. What problem does asymmetric encryption solve that symmetric encryption cannot?
2. List the three main goals of cryptography.
3. True/False: In asymmetric encryption, the private key is used for decryption and the public key for encryption.
4. What does a digital signature prove about a message?