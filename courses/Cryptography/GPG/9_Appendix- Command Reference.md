
### Key Management
```bash
# Generate new key pair
gpg --full-generate-key

# List public keys
gpg --list-keys

# List private keys
gpg --list-secret-keys

# Export public key
gpg --export --armor user@example.com

# Import key
gpg --import key.asc

# Sign a key
gpg --sign-key user@example.com
```

### Encryption/Decryption
```bash
# Encrypt for recipient
gpg --encrypt --recipient user@example.com file.txt

# Symmetric encryption
gpg --symmetric file.txt

# Decrypt
gpg --decrypt file.txt.gpg
```

### Digital Signatures
```bash
# Create detached signature
gpg --detach-sign file.txt

# Verify signature
gpg --verify file.txt.sig file.txt

# Clear sign text
gpg --clear-sign message.txt
```

### Key Server Operations
```bash
# Upload key to server
gpg --send-keys KEYID

# Download key from server
gpg --recv-keys KEYID

# Refresh keys from server
gpg --refresh-keys
```