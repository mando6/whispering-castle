
### Wireshark Display Filters
```
# HTTP traffic
http

# Specific IP address
ip.addr == 192.168.1.100

# TCP port 80
tcp.port == 80

# HTTP POST requests
http.request.method == "POST"

# Large packets (>1000 bytes)
frame.len > 1000

# Failed TCP connections
tcp.flags.reset == 1

# DNS queries for specific domain
dns.qry.name contains "example.com"

# Emails sent via SMTP
smtp.data.fragment
```

### tcpdump Capture Commands
```bash
# Capture all traffic on interface eth0
tcpdump -i eth0 -w capture.pcap

# Capture only HTTP traffic
tcpdump -i eth0 'tcp port 80' -w http.pcap

# Capture traffic from specific host
tcpdump -i eth0 'host 192.168.1.100' -w host.pcap

# Capture with timestamp and don't resolve addresses
tcpdump -i eth0 -tttt -nn -w capture.pcap

# Capture first 100 packets
tcpdump -i eth0 -c 100 -w sample.pcap
```

### tshark Analysis Commands
```bash
# Extract HTTP requests
tshark -r capture.pcap -Y "http.request" -T fields -e http.request.uri

# Count packets by protocol
tshark -r capture.pcap -q -z io,phs

# Extract DNS queries
tshark -r capture.pcap -Y "dns.flags.response == 0" -T fields -e dns.qry.name

# Export HTTP objects
tshark -r capture.pcap --export-objects http,./output_folder

# Statistics on conversations
tshark -r capture.pcap -q -z conv,tcp
```

### Scapy Quick Scripts
```python
# Read PCAP file
from scapy.all import *
packets = rdpcap('capture.pcap')

# Filter HTTP GET requests
http_gets = [p for p in packets if p.haslayer(TCP) and p.haslayer(Raw) and b'GET' in p[Raw].load]

# Extract source IPs
src_ips = [p[IP].src for p in packets if p.haslayer(IP)]

# Find packets to specific port
port_80 = [p for p in packets if p.haslayer(TCP) and p[TCP].dport == 80]
```
