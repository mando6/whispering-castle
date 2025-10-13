
### Learning Goals
- Apply GPG knowledge to practical scenarios
- Understand GPG's role in different industries
- Evaluate when GPG is appropriate vs alternatives
- Plan GPG implementation projects

### Core Content

#### 7.1 Use Case: Secure Email Communication
**Scenario**: Journalist communicating with sources
**Requirements**: Confidentiality, authentication, plausible deniability
**Implementation**: GPG with email clients, key distribution via secure channels

#### 7.2 Use Case: Software Distribution
**Scenario**: Open source project distributing software
**Requirements**: Integrity verification, authenticity proof
**Implementation**: Detached signatures for releases, key signing at conferences

#### 7.3 Use Case: Document Archive Encryption
**Scenario**: Law firm archiving client documents
**Requirements**: Long-term confidentiality, key recovery
**Implementation**: Symmetric encryption with GPG, secure key escrow

#### 7.4 Use Case: Git Commit Signing
**Scenario**: Development team ensuring code authenticity
**Requirements**: Developer authentication, integrity verification
**Implementation**: Git GPG integration, key verification workflows

#### 7.5 When NOT to Use GPG
- Real-time communication (use Signal, Wire)
- Large file transfers (use modern tools like Magic Wormhole)
- Group messaging (use encrypted messaging apps)
- Simple password sharing (use password managers)

### Connection to Main Topic
These real-world applications demonstrate how the cryptographic principles and technical skills from previous modules solve actual security problems. Students learn to evaluate trade-offs and choose appropriate tools.

### Case Study Analysis Exercise
**Student Tasks:**
1. Analyze a provided scenario
2. Identify security requirements
3. Design a GPG-based solution
4. Consider potential weaknesses
5. Present recommendations