## Course Overview

**Learning Objectives:** By the end of this course, students will understand the RSA algorithm, its mathematical foundations, implementation considerations, and real-world applications.

---

## Section 1: Introduction to Cryptography and Public-Key Systems

### Learning Objectives
- Understand the difference between symmetric and asymmetric cryptography
- Explain the key distribution problem
- Identify the core principles of public-key cryptography

### Core Content

**What is Cryptography?**
Cryptography is the practice of securing communication in the presence of adversaries. Traditional cryptography relied on symmetric keys (the same key for encryption and decryption), creating the challenge of securely sharing keys.

**The Key Distribution Problem**
Before RSA, secure communication required parties to share secret keys through secure channels. This created a chicken-and-egg problem: how do you establish a secure channel without already having one?

**Public-Key Cryptography Revolution**
In 1976, Diffie and Hellman introduced the concept of public-key cryptography, where each party has a pair of mathematically related keys: one public (shareable) and one private (secret).

**Connection to RSA:** RSA, developed in 1977, was one of the first practical implementations of public-key cryptography, solving the key distribution problem through mathematical innovation.

### Supplementary References
- [Diffie, W., & Hellman, M. (1976). "New Directions in Cryptography"]([diffie.hellman.pdf](https://www.cs.jhu.edu/~rubin/courses/sp03/papers/diffie.hellman.pdf))
- Schneier, B. "Applied Cryptography" - Chapters 1-2
- [Khan, D. "The Codebreakers" - Historical context](https://avalonlibrary.net/ebooks/David%20Kahn%20-%20The%20Codebreakers.pdf)

---

## Section 2: Mathematical Foundations - Number Theory

### Learning Objectives
- Understand prime numbers and their properties
- Explain modular arithmetic and its operations
- Apply Euler's totient function
- Understand the concept of mathematical trapdoors

### Core Content

**Prime Numbers**
Prime numbers are integers greater than 1 that have no positive divisors other than 1 and themselves. They are the building blocks of RSA's security.

Key properties:
- There are infinitely many primes
- Factoring large numbers into primes is computationally difficult
- Multiplying primes is easy, but factoring the product is hard

**Modular Arithmetic**
Modular arithmetic is arithmetic for integers where numbers "wrap around" after reaching a certain value (the modulus).

Basic operations:
- (a + b) mod n = ((a mod n) + (b mod n)) mod n
- (a × b) mod n = ((a mod n) × (b mod n)) mod n
- (a^b) mod n can be computed efficiently using fast exponentiation

**Euler's Totient Function φ(n)**
φ(n) counts the positive integers up to n that are coprime to n.
- For prime p: φ(p) = p - 1
- For product of primes: φ(pq) = (p-1)(q-1) when p ≠ q

**Mathematical Trapdoors**
A trapdoor function is easy to compute in one direction but hard to reverse without special information (the trapdoor).

**Connection to RSA:** RSA's security relies on the difficulty of factoring large numbers (the product of two primes) without knowing the original primes, which serve as the trapdoor.

### Supplementary References
- [Rosen, K. "Elementary Number Theory" - Chapters 2-4](https://www.scribd.com/document/796866254/Kenneth-H-Rosen-Elementary-Number-Theory-and-Its-Applications-Addison-Wesley-Pub-Co-1984)
- [Cormen, T. "Introduction to Algorithms" - Chapter 31 (Number Theory)](https://www.cs.mcgill.ca/~akroit/math/compsci/Cormen%20Introduction%20to%20Algorithms.pdf)
- [Online: MIT OpenCourseWare Number Theory I](https://ocw.mit.edu/courses/18-785-number-theory-i-fall-2021/)

---

## Section 3: RSA Key Generation

### Learning Objectives
- Generate RSA key pairs step-by-step
- Understand the relationship between public and private keys
- Explain the security requirements for key generation

### Core Content

**RSA Key Generation Algorithm**

**Step 1: Choose Two Large Primes**
- Select two large prime numbers p and q
- For security, p and q should be approximately the same size
- Typical sizes today: 1024-4096 bits each

**Step 2: Compute n = p × q**
- n is the modulus for both public and private keys
- The bit length of n determines the key size (e.g., 2048-bit RSA)

**Step 3: Compute φ(n) = (p-1)(q-1)**
- This is Euler's totient function for n
- φ(n) represents the count of numbers less than n that are coprime to n

**Step 4: Choose Public Exponent e**
- Select e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1
- Common choices: e = 3, 17, 65537 (2^16 + 1)
- e = 65537 is most common due to efficiency and security balance

**Step 5: Compute Private Exponent d**
- Find d such that (e × d) mod φ(n) = 1
- d is the multiplicative inverse of e modulo φ(n)
- Use Extended Euclidean Algorithm to compute d

**Key Pair Result:**
- Public Key: (n, e)
- Private Key: (n, d)
- Keep p, q, and φ(n) secret (often discarded after key generation)

**Connection to RSA:** This key generation process creates the mathematical relationship that enables RSA encryption/decryption and digital signatures.

### Worked Example
Let's generate a small RSA key pair:

1. Choose p = 17, q = 19
2. Compute n = 17 × 19 = 323
3. Compute φ(n) = (17-1)(19-1) = 16 × 18 = 288
4. Choose e = 5 (since gcd(5, 288) = 1)
5. Find d: 5d ≡ 1 (mod 288), so d = 173

Public Key: (323, 5)
Private Key: (323, 173)

### Supplementary References
- [Rivest, R., Shamir, A., Adleman, L. "A Method for Obtaining Digital Signatures and Public-Key Cryptosystems" (Original RSA paper)]([Rsapaper.pdf](https://people.csail.mit.edu/rivest/Rsapaper.pdf))
- [NIST Special Publication 800-56B - Recommendation for Pair-Wise Key Establishment Schemes Using Integer Factorization Cryptography](https://csrc.nist.rip/publications/nistpubs/800-56B/sp800-56B.pdf)
- [RFC 3447 - PKCS #1 RSA Cryptography Specifications]([rfc2437.txt.pdf](https://www.ietf.org/rfc/rfc2437.txt.pdf))

---

## Section 4: RSA Encryption and Decryption

### Learning Objectives
- Perform RSA encryption and decryption operations
- Understand the mathematical relationship between encryption/decryption
- Explain why the algorithm works mathematically

### Core Content

**RSA Encryption Process**
To encrypt a message M using recipient's public key (n, e):
1. Ensure 0 ≤ M < n (message must be smaller than modulus)
2. Compute ciphertext: C = M^e mod n

**RSA Decryption Process**
To decrypt ciphertext C using private key (n, d):
1. Compute plaintext: M = C^d mod n

**Why RSA Works: The Mathematical Proof**
The correctness relies on Euler's theorem and the relationship between e and d:

Since ed ≡ 1 (mod φ(n)), we have ed = kφ(n) + 1 for some integer k.

For decryption:
C^d = (M^e)^d = M^(ed) = M^(kφ(n)+1) = M^(kφ(n)) × M^1

By Euler's theorem, if gcd(M,n) = 1, then M^φ(n) ≡ 1 (mod n)
Therefore: M^(kφ(n)) = (M^φ(n))^k ≡ 1^k ≡ 1 (mod n)

So: C^d ≡ 1 × M ≡ M (mod n)

**Message Encoding**
Real messages need encoding before encryption:
- Text → numeric representation (ASCII, UTF-8)
- Large messages must be split into blocks smaller than n
- Padding schemes prevent certain attacks (PKCS#1, OAEP)

**Connection to RSA:** This encryption/decryption process demonstrates RSA's core functionality and shows how the mathematical relationship between public and private keys enables secure communication.

### Worked Example
Using our previous key pair (n=323, e=5, d=173):

**Encryption:**
Message M = 100
C = 100^5 mod 323 = 10,000,000,000 mod 323 = 242

**Decryption:**
C = 242
M = 242^173 mod 323 = 100 ✓

### Supplementary References
- [Katz, J. & Lindell, Y. "Introduction to Modern Cryptography" - Chapter 11](https://eclass.uniwa.gr/modules/document/file.php/CSCYB105/Reading%20Material/%5BJonathan_Katz%2C_Yehuda_Lindell%5D_Introduction_to_Mo%282nd%29.pdf)
- [RFC 8017 - PKCS #1 v2.2: RSA Cryptography Specifications](https://www.rfc-editor.org/rfc/rfc8017)
- [Washington, L. "Elliptic Curves: Number Theory and Cryptography" - Chapter 2](https://www.math.umd.edu/~lcw/ECTOC.pdf)

---

## Section 5: Digital Signatures with RSA

### Learning Objectives
- Understand the concept of digital signatures
- Implement RSA signature creation and verification
- Explain the relationship between encryption and signing in RSA

### Core Content

**Digital Signatures Overview**
Digital signatures provide:
- **Authentication:** Proves who sent the message
- **Non-repudiation:** Sender cannot deny sending it
- **Integrity:** Detects if message was modified

**RSA Signature Process**

**Signing (using private key):**
1. Compute hash H(M) of message M
2. Apply signature: S = H(M)^d mod n
3. Send (M, S) to recipient

**Verification (using public key):**
1. Compute H' = S^e mod n
2. Compute H(M) of received message
3. If H' = H(M), signature is valid

**Key Insight: RSA Duality**
RSA has a beautiful symmetry:
- Encryption uses public key: C = M^e mod n
- Signing uses private key: S = H(M)^d mod n
- This duality allows the same key pair for both operations

**Hash Functions in Signatures**
Direct message signing is impractical for large messages, so we sign cryptographic hashes:
- SHA-256, SHA-3 are common choices
- Hash provides fixed-size input for RSA
- Any change in message produces different hash

**Connection to RSA:** Digital signatures demonstrate RSA's versatility beyond encryption, using the same mathematical principles in reverse to provide authentication and integrity.

### Security Considerations
- Never sign a message without hashing it first
- Use secure hash functions (avoid MD5, SHA-1)
- Implement proper padding schemes (PSS recommended)

### Worked Example
Using n=323, e=5, d=173:

**Signing:**
Message: "HELLO" → Hash (simplified): 150
Signature: S = 150^173 mod 323 = 165

**Verification:**
Received: ("HELLO", 165)
Compute: 165^5 mod 323 = 150
Hash of "HELLO" = 150
Since 150 = 150, signature is valid ✓

### Supplementary References
- [Goldwasser, S. & Bellare, M. "Lecture Notes on Cryptography"]([gb.pdf](https://cseweb.ucsd.edu/~mihir/papers/gb.pdf))
- [FIPS 186-4 - Digital Signature Standard](https://csrc.nist.rip/external/nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.186-4.pdf)
- [RFC 3447 - PKCS #1 v2.1: RSA signature schemes](https://www.rfc-editor.org/rfc/rfc3447)

---

## Section 6: RSA Security and Real-World Implementation

### Learning Objectives
- Analyze RSA security assumptions and vulnerabilities
- Understand key size recommendations and their evolution
- Identify implementation challenges and solutions

### Core Content

**Security Foundation**
RSA security relies on the **Integer Factorization Problem**:
- Given n = pq, finding p and q is computationally difficult
- Best known algorithms are sub-exponential but still impractical for large n
- Quantum computers threaten this assumption (Shor's algorithm)

**Key Size Evolution**
Recommended minimum key sizes have grown over time:
- 1980s: 512 bits considered secure
- 2000s: 1024 bits standard
- 2010s: 2048 bits recommended
- 2020s: 3072+ bits for long-term security

**Common Vulnerabilities and Attacks**

**Implementation Attacks:**
- **Timing attacks:** Exploit variable execution time
- **Power analysis:** Analyze power consumption patterns
- **Fault injection:** Induce errors to reveal secrets

**Mathematical Attacks:**
- **Common factor attacks:** When multiple keys share a prime
- **Small exponent attacks:** When e is too small and messages are small
- **Chosen ciphertext attacks:** Exploit relationship between related ciphertexts

**Padding Oracle Attacks:**
- Exploit improper padding validation
- Can recover plaintext without private key
- Demonstrates importance of secure implementation

**Real-World Implementation Challenges**

**Random Number Generation:**
- Prime generation requires strong randomness
- Weak RNGs can lead to predictable keys
- Hardware security modules (HSMs) provide secure generation

**Side-Channel Resistance:**
- Constant-time implementations
- Blinding techniques for signatures
- Physical security of key storage

**Standards and Compliance:**
- FIPS 140-2 for cryptographic modules
- Common Criteria evaluations
- Industry-specific requirements (banking, government)

**Connection to RSA:** Understanding these security considerations is crucial for safe RSA implementation and explains why RSA is being supplemented or replaced by newer algorithms in some contexts.

### Modern Context and Future
- **Post-Quantum Cryptography:** NIST standardization of quantum-resistant algorithms
- **Elliptic Curve Cryptography:** More efficient alternative for many applications
- **Hybrid Approaches:** Combining RSA with newer algorithms for transition periods

### Supplementary References
- [Boneh, D. "Twenty Years of Attacks on the RSA Cryptosystem"](https://crypto.stanford.edu/~dabo/pubs/papers/RSA-survey.pdf)
- [NIST SP 800-57 - Key Management Recommendations](https://csrc.nist.gov/pubs/sp/800/57/pt1/r5/final)
- [OWASP Cryptographic Storage Cheat Sheet](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Cryptographic_Storage_Cheat_Sheet.md)
- [Post-Quantum Cryptography: NIST's Plan for the Future](https://www.nist.gov/publications/post-quantum-cryptography-and-quantum-future-cybersecurity)

---

## Section 7: RSA Applications and Practical Uses

### Learning Objectives
- Identify real-world applications of RSA
- Understand RSA's role in modern cryptographic protocols
- Compare RSA with other cryptographic approaches

### Core Content

**Web Security (TLS/SSL)**
RSA plays crucial roles in web security:
- **Key exchange:** Establishing shared symmetric keys
- **Server authentication:** Proving server identity via certificates
- **Certificate authorities:** RSA signatures validate certificate chains

**Email Security**
- **PGP/GPG:** RSA for key exchange and digital signatures
- **S/MIME:** RSA in enterprise email security
- **End-to-end encryption:** Protecting email content

**Code Signing**
RSA signatures verify software integrity:
- Operating system updates
- Application downloads
- Driver signatures
- Mobile app store validation

**Financial Systems**
- **Credit card transactions:** RSA in payment processing protocols
- **Banking APIs:** Securing financial data transmission
- **Cryptocurrency:** RSA in some blockchain implementations

**Government and Enterprise**
- **Document signing:** Legal document authentication
- **VPN systems:** RSA in IPSec and other VPN protocols
- **Smart cards:** RSA in secure identification systems

**Hybrid Cryptosystems**
Real systems rarely use RSA alone:
- **RSA + AES:** RSA encrypts AES keys, AES encrypts bulk data
- **Perfect Forward Secrecy:** Ephemeral keys protect past communications
- **Key derivation:** RSA establishes keys for other algorithms

**Connection to RSA:** These applications demonstrate RSA's foundational role in modern digital security infrastructure, while also showing how it integrates with other cryptographic techniques.

### Performance Considerations
- RSA is slower than symmetric encryption (AES)
- Key generation is computationally expensive
- Signature verification is faster than creation
- Hardware acceleration available (HSMs, crypto accelerators)

### Limitations and Alternatives
**RSA Limitations:**
- Large key sizes compared to elliptic curve alternatives
- Vulnerable to quantum attacks
- Complex implementation requirements

**Modern Alternatives:**
- **Elliptic Curve Cryptography (ECC):** Smaller keys, same security
- **Post-quantum algorithms:** Quantum-resistant approaches
- **EdDSA:** More efficient signature schemes

### Supplementary References
- [Ferguson, N. & Schneier, B. "Practical Cryptography" - Chapter 13](https://cdn.preterhuman.net/texts/cryptography/Practical%20Cryptography.pdf)
- [RFC 5246 - The Transport Layer Security (TLS) Protocol](https://www.rfc-editor.org/rfc/rfc5246)
- [NIST Cybersecurity Framework - Cryptographic standards](https://csrc.nist.gov/Projects/Cryptographic-Standards-and-Guidelines)
- OpenSSL documentation for practical implementation - [Practical Examples](https://allabouttesting.org/practical-examples-of-openssl/#google_vignette), [OpenSSL Cookbook]([openssl-cookbook-3ed.pdf](https://drive.elfile4138.moe/Documents/Science/CS/Cryptography/openssl-cookbook-3ed.pdf))
