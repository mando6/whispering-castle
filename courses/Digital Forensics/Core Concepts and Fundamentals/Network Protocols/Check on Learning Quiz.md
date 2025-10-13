### Section A: Protocol Fundamentals (10 questions)

**Question 1:** What are the three steps of the TCP three-way handshake in order?
- A) ACK, SYN, SYN-ACK
- B) SYN, SYN-ACK, ACK
- C) SYN, ACK, FIN
- D) HELLO, ACK, FIN

**Question 2:** Which of the following is NOT a characteristic of UDP?
- A) Connectionless
- B) No delivery guarantee
- C) Three-way handshake
- D) Low overhead

**Question 3:** What TCP/IP layer do HTTP, DNS, and SMTP operate at?
- A) Transport Layer
- B) Network Layer
- C) Application Layer
- D) Link Layer

**Question 4:** What is the primary purpose of the TTL (Time to Live) field in an IP header?
- A) To encrypt the packet
- B) To prevent infinite routing loops
- C) To authenticate the sender
- D) To compress the data

**Question 5:** Which DNS record type is used to specify mail servers for a domain?
- A) A record
- B) CNAME record
- C) MX record
- D) TXT record

**Question 6:** In SMTP, which header is most reliable for tracing the origin of an email?
- A) From header
- B) To header
- C) Received headers chain
- D) Subject header

**Question 7:** What HTTP method is typically used to submit form data to a web server?
- A) GET
- B) POST
- C) HEAD
- D) DELETE

**Question 8:** What does a SYN flood attack exploit?
- A) DNS caching
- B) TCP three-way handshake
- C) HTTP cookies
- D) SMTP relay

**Question 9:** Which protocol is connectionless and does not guarantee delivery?
- A) TCP
- B) HTTP
- C) UDP
- D) SMTP

**Question 10:** What is the typical forensic indicator of a DNS tunneling attack?
- A) Short domain names
- B) Long subdomain names and high query volume
- C) No DNS queries
- D) Only IPv6 queries

---

### Section B: Forensic Analysis (10 questions)

**Question 11:** An investigator notices numerous half-open TCP connections. What type of attack is this indicative of?
- A) SQL injection
- B) SYN flood
- C) DNS poisoning
- D) Email spoofing

**Question 12:** When analyzing HTTP traffic for SQL injection attempts, what should an investigator look for?
- A) Large file uploads
- B) SQL keywords and syntax in URL parameters or POST data
- C) Multiple DNS queries
- D) Encrypted traffic only

**Question 13:** What forensic artifact would best help identify the operating system of a remote host?
- A) DNS query type
- B) IP TTL value and TCP window size
- C) HTTP cookie value
- D) Email subject line

**Question 14:** Which of the following is the most reliable way to verify email sender authenticity?
- A) Checking the From header
- B) Validating SPF, DKIM, and analyzing Received headers
- C) Reading the subject line
- D) Checking the recipient list

**Question 15:** An investigator finds NXDOMAIN responses to randomly-generated-looking domains. What is the likely cause?
- A) Normal user browsing
- B) Domain Generation Algorithm (DGA) malware
- C) DNS server misconfiguration
- D) Email spam

**Question 16:** What does the presence of overlapping IP fragments typically indicate?
- A) Normal network congestion
- B) Evasion technique to bypass IDS/IPS
- C) High-quality video streaming
- D) Email transmission

**Question 17:** In HTTP analysis, what does a large number of 404 response codes from a single source suggest?
- A) Normal user behavior
- B) Web scanning or directory enumeration
- C) Successful data download
- D) DNS failure

**Question 18:** What is the primary forensic challenge when analyzing HTTPS traffic?
- A) It uses TCP instead of UDP
- B) Content is encrypted and requires decryption for deep inspection
- C) It doesn't leave log files
- D) It operates on non-standard ports

**Question 19:** What forensic technique helps detect DNS cache poisoning?
- A) Monitoring HTTP cookies
- B) Comparing resolved IPs with authoritative nameserver records
- C) Analyzing email headers
- D) Checking TCP sequence numbers

**Question 20:** Which tool is best suited for deep packet inspection and protocol analysis?
- A) ping
- B) netstat
- C) Wireshark
- D) traceroute

---

### Section C: Attack Patterns and Abuse (10 questions)

**Question 21:** An attacker uses DNS queries with large TXT record responses directed at a victim's IP address. What attack is this?
- A) DNS tunneling
- B) DNS amplification
- C) DNS hijacking
- D) Phishing

**Question 22:** What is a common forensic signature of web shell access?
- A) High volume of DNS queries
- B) Unusual POST requests to PHP, ASP, or JSP files
- C) SYN flood patterns
- D) SMTP relay attempts

**Question 23:** In a Business Email Compromise (BEC) attack, what should investigators examine?
- A) Only the email body
- B) Sender domain for look-alikes, urgency language, and wire transfer requests
- C) Only the recipient address
- D) The email file size

**Question 24:** What indicates potential data exfiltration via HTTP?
- A) Many 404 errors
- B) Large POST bodies or encoded GET parameters with unusual data
- C) Short connection times
- D) Low bandwidth usage

**Question 25:** How does IP spoofing typically manifest in forensic analysis?
- A) Encrypted traffic
- B) Responses to IP addresses that shouldn't be communicating
- C) High TTL values
- D) Long domain names

**Question 26:** What is a key indicator of UDP port scanning?
- A) TCP three-way handshakes
- B) ICMP "port unreachable" messages to sequential ports
- C) DNS queries
- D) HTTP POST requests

**Question 27:** Cross-Site Scripting (XSS) attacks in HTTP traffic are identified by:
- A) SQL keywords
- B) JavaScript or HTML tags in request parameters
- C) DNS queries
- D) Large file downloads

**Question 28:** What distinguishes Fast-Flux DNS from normal DNS behavior?
- A) Long TTL values
- B) Rapid IP address changes for a domain
- C) No DNS queries
- D) Single, static IP resolution

**Question 29:** In SMTP forensics, what indicates email spoofing?
- A) Large attachments
- B) SPF failures and inconsistent header information
- C) Multiple recipients
- D) HTML email format

**Question 30:** What forensic evidence would indicate TCP session hijacking?
- A) Normal three-way handshake
- B) Duplicate or out-of-sequence packets with anomalous sequence numbers
- C) High TTL values
- D) DNS queries
