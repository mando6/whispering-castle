
### Learning Goals
- Create digital signatures with GPG
- Verify signatures on received content
- Understand signature types and their uses
- Implement signature verification in workflows

### Core Content

#### 5.1 Digital Signatures with GPG
**Types of Signatures:**
- **Detached Signatures**: Separate signature file
- **Embedded Signatures**: Signature included with data
- **Clear Text Signatures**: Human-readable signed text

#### 5.2 Creating Signatures
**Detached signature:**
```bash
gpg --detach-sign file.txt
```

**Embedded signature:**
```bash
gpg --sign file.txt
```

**Clear text signature:**
```bash
gpg --clear-sign message.txt
```

#### 5.3 Verifying Signatures
**Verify detached signature:**
```bash
gpg --verify file.txt.sig file.txt
```

**Verify and extract signed content:**
```bash
gpg --decrypt signed_file.txt.gpg
```

#### 5.4 Signature Trust and Validation
**What signature verification tells you:**
- Message integrity (not tampered with)
- Authenticity (from claimed sender)
- When it was signed
- Trust level of the signing key

**Warning signs:**
- Unknown signature key
- Expired signing key
- Revoked signing key
- Signature doesn't match content

### Connection to Main Topic
Digital signatures demonstrate the authentication and integrity aspects of cryptography from Module 1. This shows how GPG provides non-repudiation and proves message authenticity in practical scenarios.

### Practical Exercise 5
**Hands-on Tasks:**
1. Sign a document with a detached signature
2. Create a clear-text signed message
3. Verify signatures from others
4. Practice with expired/invalid signatures
5. Sign and encrypt a file simultaneously

### Knowledge Check 5
**Quiz Questions:**
1. What's the difference between detached and embedded signatures?
2. What information does signature verification provide?
3. Can you verify a signature without trusting the signing key?
4. When would you use clear-text signatures vs. detached signatures?
5. What should you do if GPG warns about an expired signature?