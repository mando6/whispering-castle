### Learning Objectives
Students will understand:
- The formal security guarantees HMAC provides
- The relationship between HMAC security and underlying hash function security
- Common attack vectors and their mitigation

### Content

#### Security Guarantees
HMAC provides security under the assumption that:
1. The underlying hash function is secure (collision-resistant, preimage-resistant)
2. The secret key remains confidential
3. The key is chosen uniformly at random

#### Proven Security Properties
- **Unforgeable** - Without the key, it's computationally infeasible to create a valid HMAC for any message
- **Collision Resistant** - If the underlying hash is collision-resistant, finding two messages with the same HMAC (under the same key) is computationally infeasible
- **Pseudorandom** - HMAC outputs are indistinguishable from random to attackers without the key

#### Relationship to Hash Function Security
HMAC's security is closely tied to the underlying hash function:
- If SHA-256 is secure, then HMAC-SHA256 is secure
- Even if the hash function has some weaknesses, HMAC may still provide security due to its construction
- HMAC-MD5 is still considered secure for authentication despite MD5's collision vulnerabilities

#### Common Attack Scenarios
1. **Brute Force Key Search** - Try all possible keys (prevented by using sufficiently long random keys)
2. **Timing Attacks** - Exploit timing differences in HMAC verification (prevented by constant-time comparison)
3. **Side-Channel Attacks** - Exploit physical characteristics of implementation

#### Connection to Real-World Usage
Understanding these security properties is crucial for implementing HMAC correctly in applications. Many security vulnerabilities arise not from HMAC itself, but from incorrect implementation or usage patterns.

### Quiz 4
1. HMAC's security primarily depends on:
   a) The speed of the hash function
   b) The security of the underlying hash function
   c) The length of the message
   d) The number of rounds in the hash algorithm

2. Which of the following is NOT a security property of HMAC?
   a) Unforgeability
   b) Collision resistance
   c) Confidentiality
   d) Pseudorandomness