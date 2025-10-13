### 2.1 The Hybrid Encryption Process
PGP's genius lies in combining symmetric and asymmetric encryption in a layered approach:

**Encryption Process:**
1. Generate a random session key (symmetric key)
2. Encrypt the message with the session key using symmetric encryption (e.g., AES)
3. Encrypt the session key with recipient's public key using asymmetric encryption (e.g., RSA)
4. Send both the encrypted message and encrypted session key

**Decryption Process:**
1. Use private key to decrypt the session key
2. Use decrypted session key to decrypt the message

### 2.2 Why This Hybrid Approach?
**Connection to Main Topic**: This architecture solves the fundamental trade-off in cryptography between security and performance:
- Asymmetric encryption provides secure key exchange
- Symmetric encryption provides efficient bulk data encryption
- Together, they offer both security and speed

### 2.3 Algorithm Choices in PGP
**Symmetric Algorithms**: AES, 3DES, Blowfish, CAST5
**Asymmetric Algorithms**: RSA, ElGamal, ECDH, ECDSA
**Hash Algorithms**: SHA-1, SHA-2 family, MD5 (deprecated)

**Connection to Main Topic**: Algorithm agility allows PGP to evolve with cryptographic advances while maintaining backward compatibility.

### Section 2 Practical Exercise
Create a flowchart showing PGP's hybrid encryption process. Include decision points for algorithm selection and key sizes.

### Section 2 Quiz
1. In PGP's hybrid system, what encrypts the actual message content?
2. Why doesn't PGP use only asymmetric encryption for everything?
3. Draw the basic PGP encryption workflow.