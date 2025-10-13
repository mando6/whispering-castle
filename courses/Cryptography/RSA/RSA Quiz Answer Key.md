### Quiz 1: Foundations
1. What is the main advantage of public-key cryptography over symmetric cryptography?
2. Why was the key distribution problem significant in classical cryptography?
3. True/False: In public-key cryptography, the public key must be kept secret.
4. Name two challenges that public-key cryptography aims to solve.

**Answers:**
1. Eliminates the need for secure key distribution
2. Parties needed to share secret keys securely before communicating
3. False - the public key can be freely shared
4. Key distribution and digital signatures/authentication

### Quiz 2: Number Theory
1. Calculate φ(15) where 15 = 3 × 5
2. Compute 7^3 mod 11
3. Why is factoring large numbers considered computationally difficult?
4. What makes a function a "trapdoor" function?
5. If p = 7 and q = 11, what is φ(pq)?

**Answers:**
1. φ(15) = φ(3×5) = (3-1)(5-1) = 2×4 = 8
2. 7^3 mod 11 = 343 mod 11 = 2
3. No known efficient algorithm exists for large numbers
4. Easy to compute forward, hard to reverse without special knowledge
5. φ(77) = (7-1)(11-1) = 6×10 = 60

### Quiz 3: Key Generation
1. In the example above, verify that (e × d) mod φ(n) = 1
2. Why must gcd(e, φ(n)) = 1?
3. What happens if you choose p and q to be the same prime?
4. Why is e = 65537 a popular choice?
5. Generate a key pair with p = 11, q = 13

**Answers:**
1. (5 × 173) mod 288 = 865 mod 288 = 1 ✓
2. To ensure e has a multiplicative inverse modulo φ(n)
3. Security is compromised; n = p² is easier to factor
4. It's prime, has small Hamming weight (efficient), and provides good security
5. n = 143, φ(n) = 120, choose e = 7, then d = 103

### Quiz 4: Encryption/Decryption
1. Using n=323, e=5, encrypt the message M=50
2. If C=200, what is the decrypted message using d=173, n=323?
3. Why must the message M be less than n?
4. What is the purpose of padding schemes in RSA?
5. Explain in your own words why C^d ≡ M (mod n)

**Answers:**
1. C = 50^5 mod 323 = 312,500,000 mod 323 = 267
2. M = 200^173 mod 323 = 10 (requires modular exponentiation)
3. Modular arithmetic only works properly when M < n
4. To prevent certain cryptographic attacks and handle variable message sizes
5. Because ed ≡ 1 (mod φ(n)), raising to both powers returns the original message

### Quiz 5: Digital Signatures
1. Why do we hash messages before signing rather than signing directly?
2. Which key is used for creating signatures and which for verification?
3. What three security properties do digital signatures provide?
4. In RSA, what is the mathematical relationship between signing and encryption?
5. If someone intercepts a signature, can they use it to forge other signatures?

**Answers:**
1. Hashing provides fixed size, efficiency, and security properties
2. Private key for signing, public key for verification
3. Authentication, non-repudiation, and integrity
4. They are mathematical inverses using the same key pair
5. No, each signature is specific to the message hash

### Quiz 6: Security and Implementation
1. What mathematical problem underlies RSA security?
2. Why have recommended key sizes increased over time?
3. Name three types of side-channel attacks against RSA implementations
4. What is a padding oracle attack?
5. How might quantum computing affect RSA's future?

**Answers:**
1. The integer factorization problem
2. Increased computing power makes smaller keys vulnerable to brute force
3. Timing attacks, power analysis, fault injection
4. An attack that exploits improper padding validation to decrypt ciphertexts
5. Shor's algorithm could efficiently break RSA, requiring post-quantum alternatives

### Quiz 7: Applications
1. Name three ways RSA is used in web browsing (HTTPS)
2. Why do most systems use hybrid cryptography instead of pure RSA?
3. What advantage does ECC have over RSA?
4. How does RSA contribute to software security beyond encryption?
5. What is Perfect Forward Secrecy and how does it relate to RSA?

**Answers:**
1. Key exchange, server authentication, certificate signatures
2. RSA is slow for bulk data; hybrid systems use RSA for key exchange and symmetric crypto for data
3. Smaller key sizes for equivalent security levels
4. Digital signatures for code signing and integrity verification
5. Using ephemeral keys so that compromise of long-term RSA keys doesn't affect past sessions

