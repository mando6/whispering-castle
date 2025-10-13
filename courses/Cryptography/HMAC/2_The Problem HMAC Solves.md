### Learning Objectives
Students will understand:
- The limitations of simple hash-based authentication
- Why plain concatenation of secrets and messages is insecure
- The specific security requirements HMAC addresses

### Content

#### Authentication vs Encryption
Before diving into HMAC, it's important to distinguish between:
- **Confidentiality** (Encryption) - Keeping data secret
- **Authentication** - Verifying the sender's identity
- **Integrity** - Ensuring data hasn't been tampered with

HMAC provides authentication and integrity, but NOT confidentiality.

#### Why Not Just Hash(Secret + Message)?
A naive approach might be to simply concatenate a secret key with a message and hash the result: `Hash(Secret || Message)`. However, this approach has critical vulnerabilities:

1. **Length Extension Attacks** - For algorithms like MD5 and SHA-1, an attacker who knows the hash can append additional data and compute a valid hash without knowing the secret
2. **Collision Attacks** - If the hash function is vulnerable to collisions, this construction may not provide adequate security

#### Security Requirements
HMAC was designed to provide:
- **Authenticity** - Proof that the message came from someone who knows the secret key
- **Integrity** - Assurance that the message hasn't been modified
- **Non-repudiation** - The sender cannot deny sending the message (in some contexts)

#### Connection to HMAC
These problems led to the development of HMAC, which uses a more sophisticated construction to avoid the pitfalls of naive approaches while maintaining efficiency and security.

### Quiz 2
1. What is the main vulnerability of the Hash(Secret || Message) construction?
   a) It's too slow to compute
   b) It's vulnerable to length extension attacks
   c) It doesn't use enough memory
   d) It produces predictable outputs

2. HMAC provides which of the following? (Select all that apply)
   a) Confidentiality
   b) Authentication
   c) Integrity
   d) Compression