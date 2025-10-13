
### Section A: Multiple Choice Questions

**Question 1:** What is the primary difference between steganography and encryption?
- A) Steganography is more secure than encryption
- B) Steganography hides the existence of data, while encryption makes data unreadable
- C) Encryption can only be used for text data
- D) Steganography is a form of encryption

**Question 2:** Which technique is commonly used in image steganography?
- A) MD5 hashing
- B) Least Significant Bit (LSB) substitution
- C) AES encryption
- D) TCP handshake manipulation

**Question 3:** DNS tunneling primarily exploits which aspect of the DNS protocol?
- A) The requirement for DNS servers to forward queries
- B) The ability to encode data in subdomain names and DNS responses
- C) Weak authentication in DNS
- D) The use of UDP instead of TCP

**Question 4:** What is a key indicator of ICMP tunneling?
- A) Large or unusual payload sizes in ICMP packets
- B) Encrypted ICMP headers
- C) ICMP packets using TCP
- D) ICMP traffic on port 80

**Question 5:** Which of the following is NOT a common detection technique for DNS tunneling?
- A) Monitoring subdomain entropy
- B) Analyzing query volume per host
- C) Checking for encryption strength
- D) Detecting unusually long subdomain names

**Question 6:** In the forensic investigation process, what comes after "Identification"?
- A) Analysis
- B) Presentation
- C) Preservation
- D) Examination

**Question 7:** What type of steganography involves hiding data using spaces, tabs, and line breaks?
- A) LSB steganography
- B) Whitespace steganography
- C) Transform domain steganography
- D) Protocol steganography

**Question 8:** Which tool is specifically designed for network protocol analysis and packet inspection?
- A) EnCase
- B) Volatility
- C) Wireshark
- D) Autopsy

**Question 9:** SSH tunneling can be legitimately used for which purpose?
- A) Only for malicious activities
- B) Secure remote access and port forwarding
- C) Replacing firewalls
- D) Disabling network encryption

**Question 10:** What is the primary challenge when investigating HTTPS tunneling?
- A) HTTPS uses uncommon ports
- B) Traffic is encrypted, making content inspection difficult
- C) HTTPS cannot be logged
- D) There are no detection tools for HTTPS

### Section B: Short Answer Questions

**Question 11:** Explain why DNS is an attractive protocol for attackers to use for data exfiltration through tunneling.

**Question 12:** Describe two statistical techniques that can be used to detect steganography in digital images.

**Question 13:** What are three key logs you should collect when investigating suspected HTTP tunneling, and why is each important?

**Question 14:** Explain the concept of "chain of custody" and why it's critical in digital forensics investigations.

**Question 15:** List three behavioral indicators that might suggest a system is involved in covert communication through tunneling.

### Section C: Scenario-Based Questions

**Question 16:** 
You discover that a workstation is making 200+ DNS queries per minute to various subdomains of "data-exfil-2024.com". The subdomain names appear to be random strings of characters.

a) What specific forensic steps would you take to investigate this incident?
b) What tools would you use for analysis?
c) What additional evidence would you seek to correlate with the DNS traffic?

**Question 17:**
During a network capture review, you find ICMP packets with payload sizes of 1,200 bytes traveling between an internal server and an external IP address every 30 seconds. Normal ping packets are typically 32-64 bytes.

a) Why is this suspicious?
b) How would you extract and analyze the ICMP payload?
c) What other network indicators would you investigate?

**Question 18:**
An employee's laptop has multiple image files (JPEGs and PNGs) that were recently accessed. Your initial inspection shows nothing unusual visually. However, file size analysis reveals some images are significantly larger than expected for their dimensions and quality.

a) What steganography detection techniques would you apply?
b) Which tools would be most appropriate for this investigation?
c) If you find hidden data, what steps should you take to preserve it as evidence?

### Section D: True/False Questions

**Question 19:** Encrypted traffic can never contain steganographic data. 
- True / False

**Question 20:** Network tunneling always requires administrative privileges on the compromised system.
- True / False

**Question 21:** Statistical analysis alone can definitively prove the presence of steganographic content in an image.
- True / False

**Question 22:** DNS queries using TXT records are always malicious.
- True / False

**Question 23:** Chain of custody documentation is only necessary for criminal investigations, not internal corporate investigations.
- True / False

**Question 24:** AI and machine learning can completely replace human analysts in detecting steganography and tunneling.
- True / False

**Question 25:** WebSockets can be used to establish persistent HTTP connections that may facilitate covert communications.
- True / False
