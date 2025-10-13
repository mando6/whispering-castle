### Section A: Multiple Choice Questions

**Question 1:** What is the primary difference between forensic data storage and traditional IT storage requirements?
- A) Forensic storage requires faster performance
- B) Forensic storage must maintain immutable chain of custody and data integrity
- C) Forensic storage is always more expensive
- D) Forensic storage only uses tape media

**Question 2:** In a three-tier storage architecture for forensic data, what is the typical retention period for Tier 1 (hot storage)?
- A) 0-30 days
- B) 0-90 days
- C) 1-2 years
- D) 2-10 years

**Question 3:** Which hash algorithm is most commonly recommended for forensic evidence integrity verification?
- A) MD5 only
- B) SHA-1 only
- C) SHA-256 or stronger
- D) CRC32

**Question 4:** What does the 3-2-1 backup rule specify?
- A) 3 copies, 2 media types, 1 off-site
- B) 3 servers, 2 networks, 1 administrator
- C) 3 years retention, 2 backups, 1 cloud copy
- D) 3 data centers, 2 vendors, 1 backup schedule

**Question 5:** What is the primary purpose of WORM (Write Once, Read Many) storage in forensics?
- A) To improve performance
- B) To reduce costs
- C) To prevent evidence tampering
- D) To enable faster searches

**Question 6:** In continuous monitoring environments, what data reduction technique typically provides the highest compression ratio?
- A) Deduplication
- B) Text log compression
- C) Video compression
- D) Binary compression

**Question 7:** What is the main advantage of using object storage for long-term forensic data retention?
- A) Fastest access speed
- B) Unlimited scalability and cost-effectiveness
- C) Best compression ratios
- D) Simplest implementation

**Question 8:** Which indexing strategy is most appropriate for full-text search of log files?
- A) Hash-based indexing
- B) Inverted index (full-text indexing)
- C) Metadata-only indexing
- D) Binary indexing

**Question 9:** What does RPO (Recovery Point Objective) measure?
- A) How fast data can be accessed
- B) How long recovery takes
- C) How much data can be lost in a disaster
- D) How often backups should occur

**Question 10:** Which cloud storage feature is essential for maintaining forensic evidence integrity?
- A) Auto-scaling
- B) Load balancing
- C) Object Lock/WORM capabilities
- D) Content delivery networks

### Section B: Short Answer Questions

**Question 11:** Explain how tiered storage architecture optimizes both cost and performance in forensic data management. Provide specific examples of what data belongs in each tier.

**Question 12:** Describe three specific challenges unique to storing data from continuous monitoring systems, and propose one solution for each challenge.

**Question 13:** Why is automated lifecycle management critical in forensic data storage? What risks does manual data management introduce?

**Question 14:** Compare synchronous and asynchronous replication for forensic data. When would you choose each approach?

**Question 15:** Explain how retention policies must balance legal requirements, storage costs, and operational needs. What happens if retention policies are incorrectly implemented?

### Section C: Scenario-Based Questions

**Question 16:** You are designing a storage solution for a corporate security operations center that monitors 10,000 endpoints. The endpoints generate 2 TB of log data per day. Legal requirements mandate 7-year retention. 

Calculate:
- Total storage needed over 7 years (include 20% annual growth and 2x redundancy)
- Recommend a tiered storage strategy with specific tier sizes
- Estimate whether on-premises or cloud storage would be more cost-effective

**Question 17:** During an active investigation, investigators report that searches taking over 5 minutes to return results, significantly delaying the investigation. Your forensic storage system holds 500 TB of data across 1,000 cases.

Identify:
- Three potential causes of slow search performance
- Specific diagnostic steps you would take
- Two immediate optimizations and two long-term solutions

**Question 18:** Your organization experienced a ransomware attack that encrypted the forensic storage system. You have backups, but you need to verify their integrity before restoration and estimate recovery time.

Describe:
- The steps you would take to verify backup integrity
- How you would prioritize which data to restore first
- What changes you would make to prevent this in the future
- How this incident highlights the importance of the 3-2-1-1-0 backup strategy