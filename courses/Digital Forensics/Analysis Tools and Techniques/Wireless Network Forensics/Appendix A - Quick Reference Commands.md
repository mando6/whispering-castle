
### Essential Aircrack-ng Commands
```bash
# Enable monitor mode
airmon-ng start wlan0

# Scan for networks
airodump-ng wlan0mon

# Capture specific network
airodump-ng -c 6 --bssid XX:XX:XX:XX:XX:XX -w capture wlan0mon

# Deauthenticate client (with authorization)
aireplay-ng --deauth 10 -a [AP_MAC] -c [CLIENT_MAC] wlan0mon

# Crack WPA/WPA2
aircrack-ng -w wordlist.txt -b [BSSID] capture.cap

# Disable monitor mode
airmon-ng stop wlan0mon
```

### Essential Wireshark Filters
```
# Beacon frames
wlan.fc.type_subtype == 0x08

# Deauth frames
wlan.fc.type_subtype == 0x0c

# EAPOL (handshakes)
eapol

# Probe requests
wlan.fc.type_subtype == 0x04

# Data frames from specific MAC
wlan.sa == XX:XX:XX:XX:XX:XX && wlan.fc.type == 2
```

### Essential Tcpdump Commands
```bash
# Capture to file
tcpdump -i wlan0mon -w capture.pcap

# Capture with filter
tcpdump -i wlan0mon -w capture.pcap 'wlan[0] = 0x80'

# Read from file
tcpdump -r capture.pcap

# Filter and save
tcpdump -r input.pcap -w output.pcap 'wlan type mgt'
```
