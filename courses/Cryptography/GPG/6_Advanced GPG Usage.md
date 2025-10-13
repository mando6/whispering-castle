
### Learning Goals
- Configure GPG for optimal security
- Use GPG with automation and scripts
- Implement GPG in team environments
- Handle edge cases and troubleshooting

### Core Content

#### 6.1 Configuration and Security Hardening
**GPG Configuration File (~/.gnupg/gpg.conf):**
```
# Stronger algorithms
personal-digest-preferences SHA512
cert-digest-algo SHA512
default-preference-list SHA512 SHA384 SHA256 AES256 AES192 AES ZLIB BZIP2 ZIP Uncompressed

# Key server configuration
keyserver hkps://keys.openpgp.org
keyserver-options no-honor-keyserver-url
keyserver-options include-revoked

# Security settings
no-emit-version
no-comments
with-fingerprint
require-cross-certification
```

#### 6.2 Automation and Scripting
**Non-interactive usage:**
```bash
# Use --batch --yes for scripts
gpg --batch --yes --encrypt --recipient user@example.com file.txt

# Use --passphrase-fd for automated passphrase input
echo "passphrase" | gpg --batch --yes --passphrase-fd 0 --decrypt file.gpg
```

**GPG Agent:**
- Caches passphrases
- Provides secure passphrase prompts
- Integrates with system keyring

#### 6.3 Team and Enterprise Usage
**Key Management Strategies:**
- Centralized key distribution
- Key signing policies
- Backup and recovery procedures
- Regular key rotation schedules

**Integration Points:**
- Version control systems (Git signing)
- Continuous integration pipelines
- Email servers and clients
- File sharing systems

#### 6.4 Troubleshooting Common Issues
**Permission Problems:**
```bash
# Fix GPG directory permissions
chmod 700 ~/.gnupg
chmod 600 ~/.gnupg/*
```

**Trust Database Issues:**
```bash
# Rebuild trust database
gpg --import-ownertrust < trustdb.txt
```

**Key Server Problems:**
- Use multiple key servers
- Verify key fingerprints
- Consider key server alternatives

### Connection to Main Topic
This advanced module shows how GPG scales from individual use to enterprise deployments. It demonstrates the practical considerations needed to maintain the security principles from earlier modules in complex, real-world environments.

### Practical Exercise 6
**Hands-on Tasks:**
1. Configure GPG with security-hardened settings
2. Write a script to encrypt multiple files
3. Set up GPG agent for passphrase caching
4. Practice key server synchronization
5. Troubleshoot a broken GPG setup

### Knowledge Check 6
**Quiz Questions:**
1. What are the benefits of using stronger digest algorithms in GPG configuration?
2. Why is GPG agent useful for automation scenarios?
3. What permissions should the ~/.gnupg directory have?
4. Name three ways GPG can be integrated into development workflows.
5. How would you troubleshoot a "No secret key" error?