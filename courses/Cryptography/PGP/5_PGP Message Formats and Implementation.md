### 5.1 OpenPGP Message Format (RFC 4880)
PGP messages are structured using a packet-based format:
- **Literal Data Packets**: Contain actual message content
- **Compressed Data Packets**: Optional compression
- **Symmetrically Encrypted Data Packets**: Bulk encrypted data
- **Public Key Encrypted Session Key Packets**: Encrypted session keys

### 5.2 ASCII Armor
Human-readable encoding for PGP data:
```
-----BEGIN PGP MESSAGE-----
Version: GnuPG v2

hQIMA... (base64 encoded data)
-----END PGP MESSAGE-----
```

**Connection to Main Topic**: Message format standardization enables interoperability between different PGP implementations while maintaining security.

### 5.3 PGP Implementations
- **GnuPG (GPG)**: Most popular open-source implementation
- **Symantec PGP**: Commercial implementation
- **Bouncy Castle**: Java cryptography library with PGP support
- **OpenPGP.js**: JavaScript implementation for web browsers

### Section 5 Lab Exercise
Examine PGP packet structures using GPG's list-packets command. Compare message sizes before and after encryption/compression.