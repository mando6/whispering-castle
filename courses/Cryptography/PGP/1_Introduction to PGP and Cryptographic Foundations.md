### 1.1 What is PGP?
PGP (Pretty Good Privacy) is a data encryption and decryption computer program that provides cryptographic privacy and authentication for data communication. Created by Phil Zimmermann in 1991, PGP became the de facto standard for email encryption.

**Key Characteristics:**
- Hybrid cryptosystem (combines symmetric and asymmetric encryption)
- Provides confidentiality, integrity, and authentication
- Uses a web of trust model for key validation
- Open standard (OpenPGP RFC 4880)

### 1.2 Historical Context and Importance
PGP emerged during the "Crypto Wars" of the 1990s when the U.S. government attempted to control cryptographic software as munitions. Zimmermann's release of PGP sparked debates about digital privacy rights that continue today.

**Connection to Main Topic**: Understanding PGP's history explains why it was designed with certain principles like decentralization and user control, which directly influence its technical architecture.

### 1.3 Cryptographic Building Blocks
Before diving into PGP's specifics, we need to understand its foundational concepts:

**Symmetric Encryption:**
- Single key for encryption and decryption
- Fast for large data
- Key distribution problem

**Asymmetric Encryption:**
- Key pair: public key (shareable) and private key (secret)
- Slower than symmetric encryption
- Solves key distribution problem

**Hash Functions:**
- One-way mathematical functions
- Create fixed-size "fingerprints" of data
- Used for integrity verification

**Connection to Main Topic**: PGP cleverly combines all three cryptographic primitives to create a system that's both secure and efficient.

### Module 1 Quiz
1. What problem does PGP's hybrid approach solve?
   a) Making encryption faster
   b) Combining the strengths of symmetric and asymmetric encryption
   c) Reducing key sizes
   d) Eliminating the need for hash functions

2. Who created PGP and in what year?
3. Explain why PGP uses both symmetric and asymmetric encryption instead of just one approach.