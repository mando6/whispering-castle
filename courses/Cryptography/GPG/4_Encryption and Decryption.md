
### Learning Goals
- Encrypt files and messages using GPG
- Decrypt received encrypted content
- Understand hybrid encryption in GPG
- Use symmetric encryption when appropriate

### Core Content

#### 4.1 How GPG Encryption Works
**Hybrid Encryption Process:**
1. Generate random symmetric key (session key)
2. Encrypt message with session key (fast symmetric encryption)
3. Encrypt session key with recipient's public key
4. Combine encrypted message and encrypted session key

This provides the speed of symmetric encryption with the convenience of asymmetric encryption.

#### 4.2 Encrypting Data
**For specific recipients:**
```bash
gpg --encrypt --recipient user@example.com file.txt
```

**With symmetric encryption (password-based):**
```bash
gpg --symmetric file.txt
```

**Best Practices:**
- Always encrypt for yourself too (add your own key as recipient)
- Use armor format for text transmission
- Verify recipient keys before encryption

#### 4.3 Decrypting Data
```bash
gpg --decrypt file.txt.gpg
```

**Process:**
1. GPG identifies which private key is needed
2. Prompts for passphrase
3. Decrypts session key with private key
4. Decrypts message with session key

#### 4.4 Integration Examples
**Email Integration:**
- Thunderbird with Enigmail
- Outlook with Gpg4win
- Command line with mutt

**File Manager Integration:**
- Right-click context menus
- Automated backup encryption
- Cloud storage encryption

### Connection to Main Topic
This module demonstrates the practical application of Module 1's encryption concepts. Students see how GPG seamlessly combines symmetric and asymmetric encryption to create an efficient, secure system.

### Practical Exercise 4
**Hands-on Tasks:**
1. Encrypt a file for a specific recipient
2. Encrypt a file with symmetric encryption
3. Decrypt files you've received
4. Practice with ASCII armor format
5. Encrypt a message for multiple recipients

### Knowledge Check 4
**Quiz Questions:**
1. Why does GPG use hybrid encryption instead of pure asymmetric encryption?
2. What happens if you don't include yourself as a recipient when encrypting?
3. What is ASCII armor format and when is it useful?
4. Can you decrypt a symmetrically encrypted file with a GPG key pair? Why or why not?