### Section A: Multiple Choice (4 points each)

1. **B** - Chain of custody and data integrity are fundamental forensic requirements
2. **B** - 0-90 days is typical for hot storage in forensic architectures
3. **C** - SHA-256 or stronger is current best practice; MD5/SHA-1 have known vulnerabilities
4. **A** - 3 copies on 2 different media with 1 off-site
5. **C** - WORM prevents tampering, ensuring evidence integrity
6. **B** - Text logs achieve 5:1 to 10:1 compression ratios
7. **B** - Unlimited scalability and cost-effectiveness for long-term retention
8. **B** - Inverted indexes enable efficient full-text search
9. **C** - RPO measures acceptable data loss (time between backups)
10. **C** - Object Lock/WORM maintains immutability for evidence

### Section B: Short Answer (6 points each)

**Question 11 - Rubric:**
- Explains cost optimization through tiered pricing
- Explains performance optimization through appropriate tier placement
- Provides specific examples for each tier (hot: active cases 0-90 days; warm: recent closed cases 90 days-2 years; cold: long-term retention 2+ years)

**Question 12 - Rubric:**
- Three challenges with solutions:
  - Volume: Implement data reduction techniques (compression, deduplication, filtering)
  - Sustained write throughput: Use message queues and buffering
  - Real-time indexing: Implement distributed search clusters or hybrid real-time/batch indexing

**Question 13 - Rubric:**
- Explains automation ensures consistency, eliminates human error, scales effectively
- Identifies risks: Premature deletion violating legal holds, over-retention increasing costs, inconsistent application of policies, lack of auditability

**Question 14 - Rubric:**
- Synchronous: Zero data loss, limited distance, higher cost; use for critical evidence and regulatory requirements
- Asynchronous: Minimal loss, unlimited distance, lower cost; use for large volumes where minutes of potential loss acceptable

**Question 15 - Rubric:**
- Legal requirements set minimum retention periods
- Storage costs increase with longer retention
- Incorrect policies risk: Legal sanctions for premature deletion, unnecessary costs for over-retention, inability to defend in court

### Section C: Scenario-Based (10 points each)

**Question 16 - Rubric:**
- Calculation: 2 TB/day × 365 days × 7 years = 5,110 TB base; with 20% annual growth ≈ 7,500 TB; with 2x redundancy = 15,000 TB (15 PB)
- Tiered strategy: Hot 500 TB (active 90 days), Warm 2,500 TB (cases 90 days-2 years), Cold 12,000 TB (2-7 years)
- Cost comparison with reasoning: Likely hybrid approach optimal (on-premises hot/warm, cloud cold storage)

**Question 17 - Rubric:**
- Causes: Insufficient indexing, inadequate storage performance, overloaded search cluster, poor query optimization
- Diagnostics: Check index health and coverage, monitor storage IOPS/latency, analyze slow query logs, verify resource utilization
- Solutions - Immediate: Add caching, optimize frequent queries, add search nodes; Long-term: Rebuild indexes, partition data, upgrade storage tier, implement query optimization

**Question 18 - Rubric:**
- Verification: Restore to isolated environment, verify hashes against original, test data integrity, check for encryption
- Prioritization: Active investigations first, then recent cases, then historical based on legal requirements
- Prevention: Implement air-gapped backups, enhance access controls, add immutable snapshots, improve monitoring
- Explains 3-2-1-1-0 importance: Offline copy (the "1") would have been unaffected by ransomware
