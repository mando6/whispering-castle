### Comprehensive Quiz
1. HMAC primarily provides which security services?
   a) Confidentiality and integrity
   b) Authentication and integrity
   c) Authentication and confidentiality
   d) Integrity and non-repudiation

2. The inner and outer padding constants in HMAC are:
   a) 0x00 and 0xFF
   b) 0x36 and 0x5C
   c) 0xAA and 0x55
   d) 0x01 and 0x80

3. What happens if an HMAC key is longer than the hash function's block size?
   a) The key is truncated
   b) The key is hashed to reduce its size
   c) The excess is ignored
   d) An error occurs

4. Which attack does HMAC's construction specifically prevent?
   a) Brute force attacks
   b) Length extension attacks
   c) Dictionary attacks
   d) Social engineering

5. In constant-time HMAC verification, why is timing important?
   a) To improve performance
   b) To prevent timing side-channel attacks
   c) To ensure compatibility
   d) To reduce memory usage

### Practical Exercise
Implement HMAC-SHA256 verification for a webhook payload:
- Given: Secret key, payload, and received HMAC
- Task: Verify if the HMAC is valid
- Consider: Proper key handling and constant-time comparison