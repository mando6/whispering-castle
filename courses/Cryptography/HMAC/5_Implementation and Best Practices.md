### Learning Objectives
Students will learn:
- How to implement HMAC correctly
- Common implementation pitfalls and how to avoid them
- Best practices for key management and usage

### Content

#### Implementation Considerations

##### Key Management
1. **Key Generation** - Use cryptographically secure random number generators
2. **Key Length** - Generally, keys should be at least as long as the hash output
3. **Key Storage** - Protect keys with appropriate access controls
4. **Key Rotation** - Regularly update keys in long-term applications

##### Common Implementation Mistakes
1. **Non-constant Time Comparison** - Always use constant-time comparison for HMAC verification
2. **Weak Key Generation** - Never use predictable or user-provided passwords directly as HMAC keys
3. **Key Reuse** - Avoid using the same key for multiple purposes
4. **Insufficient Key Length** - Short keys reduce security significantly

##### Pseudocode Example
```
function HMAC(key, message, hash_function):
    block_size = hash_function.block_size
    
    // Key preparation
    if length(key) > block_size:
        key = hash_function(key)
    if length(key) < block_size:
        key = key || zeros(block_size - length(key))
    
    // Calculate inner hash
    inner_key = key XOR repeat(0x36, block_size)
    inner_hash = hash_function(inner_key || message)
    
    // Calculate outer hash
    outer_key = key XOR repeat(0x5c, block_size)
    return hash_function(outer_key || inner_hash)
```

#### Performance Considerations
- HMAC is approximately 2x slower than a simple hash due to double hashing
- For high-throughput applications, consider hardware acceleration
- Batch processing can improve efficiency for multiple messages

#### Connection to Practical Applications
This module bridges the theoretical understanding from previous modules with real-world implementation challenges. Proper implementation is crucial for maintaining the security guarantees that HMAC provides.

### Quiz 5
1. What is a critical requirement when comparing HMAC values?
   a) Use case-insensitive comparison
   b) Use constant-time comparison
   c) Use string comparison functions
   d) Compare only the first few bytes

2. What should you do if your key is longer than the hash function's block size?
   a) Truncate it
   b) Hash it first
   c) Use it directly
   d) Repeat it to fill the block