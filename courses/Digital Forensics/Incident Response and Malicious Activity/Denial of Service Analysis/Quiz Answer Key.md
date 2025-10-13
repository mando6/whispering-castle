### Section A: Multiple Choice
1. B
2. B
3. B
4. B
5. B
6. B
7. C
8. B
9. C
10. B
11. C
12. C
13. B
14. B
15. C
16. B
17. C
18. B
19. B
20. B


### Section B: True/False
21. False (Application layer attacks typically use less bandwidth)
22. False (Single-source DoS attacks exist)
23. True
24. False (Chain of custody is critical for all legal proceedings)
25. True
26. False (Always work on copies to preserve originals)
27. False (New attack methods and tools emerge constantly)
28. True
29. False (IPv6 has its own DDoS vulnerabilities)
30. True

### Section C: Short Answer - Sample Responses

**31.** UTC timestamps ensure consistency across different time zones and avoid confusion during investigations. When correlating evidence from multiple sources in different locations, UTC provides a standard reference point. This is critical for accurately reconstructing attack timelines and for evidence admissibility in legal proceedings.

**32.** Three challenges: (1) IP address spoofing makes it difficult to identify true sources, (2) use of botnets distributes attacks across thousands of compromised systems masking the actual attacker, (3) reflection/amplification techniques bounce traffic through legitimate intermediary servers, obscuring the attack origin.

**33.** Reflection occurs when attackers send requests with spoofed source addresses, causing responses to be sent to the victim. Amplification occurs when the response is larger than the request, multiplying the attack traffic volume. DNS amplification is an example where a small query generates a large response directed at the victim.

**34.** High sophistication: Uses custom tools, sophisticated evasion techniques, multi-vector coordination, and may involve zero-day exploits. Low sophistication: Uses readily available tools, obvious patterns, single attack vector, and minimal attempt at obfuscation.

**35.** A botnet is a network of compromised computers (called "bots" or "zombies") controlled by an attacker through command and control infrastructure. In DDoS attacks, botnets provide the distributed attack sources needed to generate massive traffic volumes from many locations simultaneously.

**36.** Three valuable log types: (1) Firewall logs showing traffic patterns and blocked connections, (2) Web server logs with request details and timing, (3) NetFlow/sFlow data providing network traffic metadata and flow information.

**37.** Technical impact quantifies the attack mechanics (bandwidth, duration, systems affected) for understanding and mitigation. Business impact translates technical metrics into financial terms (revenue loss, customer impact, reputation) needed for executive decision-making, insurance claims, and legal proceedings.

**38.** A forensic timeline provides a chronological reconstruction of events from reconnaissance through recovery. It helps identify attack phases, correlate events across multiple systems, establish causation, identify gaps in detection, and provides a clear narrative for reports and legal proceedings.

**39.** Machine learning can be applied to identify anomalous traffic patterns that deviate from baseline behavior, automatically classify attack types based on traffic characteristics, predict potential attacks based on precursor activities, or reduce false positives in detection systems through improved pattern recognition.

**40.** Defense in depth is a layered security strategy using multiple defensive mechanisms at different levels (network, application, host). For DDoS mitigation, this means combining edge filtering, rate limiting, WAFs, CDNs, and application-level protections so that if one layer is overwhelmed, others continue providing protection.

### Section D: Scenario-Based - Sample Responses

**41.** This is likely an HTTP Flood (application layer DDoS attack), possibly using a botnet given the distributed sources and varying User-Agents.

**Forensic steps:**
1. Capture full packet traces and HTTP logs to analyze request patterns, headers, and timing
2. Perform statistical analysis on source IPs to identify commonalities (ASNs, geographic clustering, behavioral patterns)
3. Analyze User-Agent strings and other HTTP headers for patterns that might indicate automated tools or botnets, despite variation attempts
4. Correlate timing patterns to identify potential command and control synchronization

**42.** This is likely a DNS amplification attack where attackers are spoofing your customer's IP address as the source in DNS queries sent to your server, causing your DNS responses to flood the customer's network.

**Investigation steps:**
1. Examine DNS query logs to verify queries are for unusual record types (ANY, TXT) that generate large responses
2. Verify that source IPs in queries match the affected customer's IP addresses
3. Check if queries originate from expected geographic locations or show signs of being spoofed
4. Contact the customer to confirm they're experiencing abnormal inbound DNS traffic from your servers
5. Implement response rate limiting (RRL) to prevent your server from being used in amplification attacks

**43.** The identical TTL values despite geographic diversity suggest the traffic may not actually originate from those countries—instead, it indicates:
- Possible botnet with standardized configurations
- Traffic routed through a common infrastructure before reaching you
- Potential use of proxy networks or VPN services
- Spoofed source addresses with consistent routing patterns

**Additional analysis:**
1. Perform TCP handshake analysis to see if sources complete connections (spoofed IPs typically cannot)
2. Analyze packet timing and patterns using statistical methods to identify automated generation
3. Check threat intelligence feeds for known malicious infrastructure
4. Examine MAC addresses if captured to identify immediate upstream sources
5. Coordinate with ISPs for upstream traffic analysis and traceback

**44.** Three key executive summary points:

1. **Business Impact:** The 4-hour outage affected 100,000 customers, resulting in an estimated $X in lost revenue, Y customer complaints, and potential regulatory reporting requirements. Service has been fully restored.

2. **Attack Overview:** The organization experienced a distributed denial of service attack using [attack type], originating from [number] of sources across [geographic regions]. This was a [sophistication level] attack likely motivated by [possible motivation if known].

3. **Immediate Actions & Recommendations:** Our team has implemented emergency mitigation measures and preserved all forensic evidence. We recommend investing in [specific solutions] to prevent recurrence, with an estimated implementation cost of $X versus potential future losses of $Y per incident.

**45.** Immediate evidence preservation steps:

1. **Halt further log rotation:** Immediately configure all systems to preserve existing logs and increase retention periods
2. **Capture current state:** Take snapshots of all system configurations, active connections, and current logs before they're overwritten
3. **Image critical systems:** Create forensic images of firewall and server storage to capture any remaining volatile data
4. **Document existing evidence:** Create inventory of all available log sources with timestamps and gaps
5. **Secure evidence:** Move copies to write-once storage with cryptographic hashes and chain of custody documentation

**Gap documentation:**
- Create detailed timeline showing when logs rotated and what data was lost
- Document the firewall reboot timing and what data may have been lost from memory
- Note any systems without logging enabled
- Include timestamps of when preservation efforts began
- Explain impact of gaps on analysis capabilities in written report
- Recommend improvements to logging and retention policies to prevent future evidence loss