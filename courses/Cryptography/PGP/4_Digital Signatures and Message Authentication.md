### 4.1 Digital Signatures in PGP
Digital signatures provide:
- **Authentication**: Proves who sent the message
- **Integrity**: Ensures message hasn't been tampered with
- **Non-repudiation**: Sender can't deny sending the message

### 4.2 Signature Creation Process
1. Calculate hash of the message
2. Encrypt hash with sender's private key
3. Attach signature to message

### 4.3 Signature Verification Process
1. Decrypt signature with sender's public key to get claimed hash
2. Calculate hash of received message
3. Compare the two hashes

**Connection to Main Topic**: Digital signatures are as important as encryption in PGP's security model, often used even when encryption isn't needed.

### 4.4 Types of PGP Signatures
- **Binary signatures**: Attached to or embedded in documents
- **Detached signatures**: Separate files for verification
- **Clear-text signatures**: Human-readable with signature block

### Section 4 Practical Exercise
Sign and verify messages using different signature types. Analyze what happens when message content is modified after signing.

### Section 4 Quiz
1. What three security properties do digital signatures provide?
2. Why is hashing used in the signature process instead of encrypting the entire message?
3. When might you use a detached signature versus an embedded signature?