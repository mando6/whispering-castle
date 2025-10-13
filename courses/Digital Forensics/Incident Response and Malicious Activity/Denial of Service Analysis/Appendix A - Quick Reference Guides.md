
### Common Attack Signatures

```
SYN Flood Indicators:
- High volume of TCP SYN packets
- No corresponding ACK packets
- Source IPs may be randomized
- Destination port typically same across packets
- Half-open connections in netstat

HTTP Flood Indicators:
- High request rate to same URLs
- Unusual User-Agent patterns
- Requests from suspicious geographic regions
- Same referrer patterns across sources
- Low session duration

DNS Amplification Indicators:
- High volume of DNS responses
- Queries for ANY or TXT records
- Responses larger than queries
- Source IPs of responses are legitimate DNS servers
- Victim is destination of responses

UDP Flood Indicators:
- High volume UDP packets to random ports
- Source IPs typically spoofed
- Responses with ICMP port unreachable
- Bandwidth saturation
- Random or sequential destination ports
```

### Essential Command Reference

```bash
# Network Traffic Capture
tcpdump -i eth0 -w capture.pcap
tcpdump -i eth0 'tcp[tcpflags] & tcp-syn != 0'

# Traffic Analysis
tshark -r capture.pcap -q -z conv,ip
tshark -r capture.pcap -Y "tcp.flags.syn==1 && tcp.flags.ack==0"

# NetFlow Analysis
nfdump -R /path/to/flows -s ip/packets -n 20
nfdump -R /path/to/flows 'proto tcp and flags S and not flags A'

# Log Analysis
grep "GET\|POST" access.log | awk '{print $1}' | sort | uniq -c | sort -rn
awk '{print $1}' access.log | sort | uniq -c | awk '$1 > 1000'

# Evidence Hashing
sha256sum evidence.pcap > evidence.sha256
md5sum evidence.pcap > evidence.md5

# Packet Statistics
capinfos capture.pcap
```

### Forensic Checklist

```
Initial Response:
□ Identify affected systems and services
□ Determine attack is ongoing or historical
□ Notify appropriate stakeholders
□ Begin evidence preservation
□ Activate incident response team

Evidence Collection:
□ Capture network traffic (PCAP)
□ Collect NetFlow/sFlow data
□ Gather firewall logs
□ Obtain IDS/IPS alerts
□ Collect system logs
□ Document configuration states
□ Create forensic hashes
□ Establish chain of custody

Analysis Phase:
□ Create baseline of normal traffic
□ Identify attack patterns and signatures
□ Determine attack type(s)
□ Analyze source attribution
□ Assess target and impact
□ Reconstruct timeline
□ Document vulnerabilities
□ Identify IOCs

Reporting:
□ Create executive summary
□ Document technical findings
□ Include evidence references
□ Provide recommendations
□ Address legal considerations
□ Maintain confidentiality
```

