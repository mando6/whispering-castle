
### Network Capture Commands
```bash
# Capture DNS traffic
tcpdump -i eth0 -w dns_capture.pcap 'port 53'

# Capture ICMP traffic
tcpdump -i eth0 -w icmp_capture.pcap 'icmp'

# Capture HTTP/HTTPS traffic
tcpdump -i eth0 -w web_traffic.pcap 'tcp port 80 or tcp port 443'
```

### Wireshark Display Filters
```
# DNS queries to specific domain
dns.qry.name contains "suspicious-domain.com"

# Large ICMP packets
icmp and ip.len > 100

# HTTP POST requests
http.request.method == "POST"

# Unusual DNS record types
dns.qry.type == 16  # TXT records
```

### Analysis Commands
```bash
# Extract DNS queries from PCAP
tshark -r capture.pcap -Y "dns.flags.response == 0" -T fields -e dns.qry.name

# Calculate file entropy (Python)
python -c "import math; from collections import Counter; 
data = open('file.jpg','rb').read(); 
entropy = -sum(p * math.log2(p) for p in 
[cnt/len(data) for cnt in Counter(data).values()]); 
print(f'Entropy: {entropy}')"

# Check for LSB manipulation indicators
stegdetect -s 1.0 image.jpg
```
