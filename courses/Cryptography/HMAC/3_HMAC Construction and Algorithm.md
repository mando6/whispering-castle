### Learning Objectives
Students will:
- Understand the detailed HMAC construction
- Explain why the specific construction provides security
- Trace through an HMAC calculation step by step

### Content

#### HMAC Construction
HMAC uses a nested hash construction with two constants:

**HMAC(K, m) = H((K ⊕ opad) || H((K ⊕ ipad) || m))**

Where:
- **K** = Secret key
- **m** = Message to authenticate
- **H** = Chosen hash function (e.g., SHA-256)
- **opad** = Outer padding (0x5c repeated)
- **ipad** = Inner padding (0x36 repeated)
- **⊕** = XOR operation
- **||** = Concatenation

#### Step-by-Step Process

1. **Key Preparation**
   - If key is longer than block size, hash it first
   - If key is shorter than block size, pad with zeros to block size

2. **Inner Hash**
   - XOR the prepared key with ipad (0x36...)
   - Concatenate with the message
   - Hash the result: `H((K ⊕ ipad) || m)`

3. **Outer Hash**
   - XOR the prepared key with opad (0x5c...)
   - Concatenate with the inner hash result
   - Hash the result: `H((K ⊕ opad) || inner_hash)`

#### Why This Construction Works
The nested structure with different padding constants ensures that:
- Both inner and outer hash computations use different effective keys
- Length extension attacks are prevented by the outer hash
- The construction remains secure even if the underlying hash function has some weaknesses

#### Connection to Previous Modules
This construction directly addresses the vulnerabilities identified in Module 2 by using a proven secure method that has been extensively analyzed by cryptographers. The use of two different padding constants and nested hashing prevents the attacks that plague simpler constructions.

### Practical Example
Let's trace through HMAC-SHA256 with a simple example:
- Key: "secret"
- Message: "Hello, World!"
- Block size: 64 bytes (for SHA-256)

(Full calculation would be shown with actual hex values in a real implementation)

### Quiz 3
1. What are the two padding constants used in HMAC?
   a) 0x36 and 0x5c
   b) 0x00 and 0xff
   c) 0xaa and 0x55
   d) 0x01 and 0x80

2. Why does HMAC use a nested hash construction?
   a) To make it faster
   b) To prevent length extension attacks
   c) To use less memory
   d) To make it compatible with more hash functions