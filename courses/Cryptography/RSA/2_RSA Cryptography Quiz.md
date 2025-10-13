### Foundations
What is the main advantage of public-key cryptography over symmetric cryptography?
2. Why was the key distribution problem significant in classical cryptography?
3. True/False: In public-key cryptography, the public key must be kept secret.
4. Name two challenges that public-key cryptography aims to solve.

### Number Theory
1. Calculate φ(15) where 15 = 3 × 5
2. Compute 7^3 mod 11
3. Why is factoring large numbers considered computationally difficult?
4. What makes a function a "trapdoor" function?
5. If p = 7 and q = 11, what is φ(pq)?

### Key Generation
1. In the example above, verify that (e × d) mod φ(n) = 1
2. Why must gcd(e, φ(n)) = 1?
3. What happens if you choose p and q to be the same prime?
4. Why is e = 65537 a popular choice?
5. Generate a key pair with p = 11, q = 13

### Encryption/Decryption
1. Using n=323, e=5, encrypt the message M=50
2. If C=200, what is the decrypted message using d=173, n=323?
3. Why must the message M be less than n?
4. What is the purpose of padding schemes in RSA?
5. Explain in your own words why C^d ≡ M (mod n)


### Digital Signatures
1. Why do we hash messages before signing rather than signing directly?
2. Which key is used for creating signatures and which for verification?
3. What three security properties do digital signatures provide?
4. In RSA, what is the mathematical relationship between signing and encryption?
5. If someone intercepts a signature, can they use it to forge other signatures?

### Security and Implementation
1. What mathematical problem underlies RSA security?
2. Why have recommended key sizes increased over time?
3. Name three types of side-channel attacks against RSA implementations
4. What is a padding oracle attack?
5. How might quantum computing affect RSA's future?

### Applications
1. Name three ways RSA is used in web browsing (HTTPS)
2. Why do most systems use hybrid cryptography instead of pure RSA?
3. What advantage does ECC have over RSA?
4. How does RSA contribute to software security beyond encryption?
5. What is Perfect Forward Secrecy and how does it relate to RSA?