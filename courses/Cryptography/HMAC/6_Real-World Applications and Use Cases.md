### Learning Objectives
Students will understand:
- Common protocols and systems that use HMAC
- How HMAC fits into larger security architectures
- Practical use cases and their requirements

### Content

#### Protocol Applications

##### Web Security
- **JWT (JSON Web Tokens)** - Uses HMAC for token integrity
- **OAuth 2.0** - HMAC for request signing
- **Webhook Security** - Verifying webhook authenticity

##### Network Protocols
- **TLS/SSL** - HMAC in various cipher suites
- **IPSec** - Authentication headers use HMAC
- **SSH** - Message authentication in secure shell

##### Database and Storage
- **Password Storage** - PBKDF2 uses HMAC internally
- **API Authentication** - AWS Signature Version 4 uses HMAC
- **Message Queues** - Ensuring message integrity

#### Specific Use Case: API Authentication
Many APIs use HMAC for request authentication:
1. Client and server share a secret key
2. Client creates a signature using HMAC over the request data
3. Server verifies the signature to authenticate the request
4. Prevents tampering and ensures authenticity

#### Integration Patterns
- **Encrypt-then-MAC** - Encrypt data, then HMAC the ciphertext
- **MAC-then-Encrypt** - HMAC plaintext, then encrypt everything
- **Encrypt-and-MAC** - Separate encryption and authentication

#### Connection to Course Content
This module demonstrates how all the theoretical concepts and implementation details from previous modules come together in real-world systems. Understanding these applications helps solidify the importance and practical value of mastering HMAC.

### Quiz 6
1. In which of the following is HMAC commonly used?
   a) JWT tokens
   b) Password hashing
   c) File compression
   d) Random number generation

2. What is the recommended approach for combining encryption and authentication?
   a) MAC-then-Encrypt
   b) Encrypt-then-MAC
   c) Encrypt-and-MAC
   d) It doesn't matter