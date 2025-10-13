### Learning Objectives
By the end of this module, students will be able to:
- Define what a cryptographic hash function is
- Identify the key properties of secure hash functions
- Explain common hash algorithms (MD5, SHA-1, SHA-256)

### Content

#### What is a Hash Function?
A cryptographic hash function is a mathematical algorithm that takes an input of arbitrary size and produces a fixed-size string of bytes, typically represented in hexadecimal. Think of it as a digital fingerprint for data.

**Key Properties:**
1. **Deterministic** - Same input always produces same output
2. **Fixed Output Size** - Regardless of input size, output is always the same length
3. **Avalanche Effect** - Small input changes cause dramatic output changes
4. **One-way Function** - Computationally infeasible to reverse
5. **Collision Resistant** - Very difficult to find two inputs with same output

#### Common Hash Algorithms
- **MD5** - 128-bit output (now considered insecure)
- **SHA-1** - 160-bit output (deprecated for security applications)
- **SHA-256** - 256-bit output (current standard)
- **SHA-3** - Variable output sizes (newest standard)

#### Connection to HMAC
Hash functions are the building blocks of HMAC. Understanding their properties is crucial because HMAC inherits and extends these characteristics to provide message authentication capabilities. Without secure hash functions, HMAC cannot provide security guarantees.

### Quiz 1
1. What happens to the SHA-256 hash if you change one bit in the input?
   a) The hash changes by one bit
   b) The hash changes completely (avalanche effect)
   c) The hash remains the same
   d) Only the first byte changes

2. Why is MD5 no longer recommended for security applications?
   a) It's too slow
   b) Collision attacks have been demonstrated
   c) It produces outputs that are too short
   d) It's not deterministic