## Table of Contents
1. [Deployment and Configuration](#deployment-and-configuration)
2. [Encryption, Authentication, and Compliance](#encryption-authentication-and-compliance)
3. [Web Application Security](#web-application-security)
4. [Machine Learning (ML)](#machine-learning-ml)

---

## Deployment and Configuration

### Objective Summary

**Deployment Requirements and System Settings**
FortiWeb deployment requires careful consideration of network topology, traffic flow patterns, and security requirements. Administrators must identify whether to deploy in reverse proxy, transparent inspection, offline protection, or WCCP modes. System settings include network interfaces, routing configuration, administrative access controls, DNS settings, time synchronization, and system resource monitoring. Proper initial configuration ensures optimal performance and security posture.

**Server Pools, Policies, and Protected Hostnames**
Server pools define backend application servers that FortiWeb protects. Administrators configure server load balancing methods (round-robin, weighted, least-connections, etc.), health monitoring, and persistence settings. Policies bind protection profiles to specific protected hostnames and virtual servers. Protected hostnames define the web applications and domains that FortiWeb secures, including URL patterns and allowed HTTP methods.

**High Availability (HA) Configuration**
FortiWeb HA provides redundancy and failover capabilities using active-passive or active-active modes. Configuration includes heartbeat interfaces, priority settings, session synchronization, and configuration synchronization. HA monitoring ensures automatic failover when the primary unit fails, maintaining continuous protection without service disruption.

**Troubleshooting Deployment Issues**
Common deployment issues include connectivity problems, routing misconfigurations, policy conflicts, and performance bottlenecks. Troubleshooting requires analyzing system logs, monitoring resource utilization, verifying network paths, and testing traffic flow. Administrators use diagnostic commands, packet captures, and debug logging to identify and resolve issues.

---

### Exam Questions: Deployment and Configuration

**Multiple Choice Questions**

1. Which FortiWeb deployment mode allows the appliance to inspect traffic without being inline?
   - A) Reverse Proxy Mode
   - B) Transparent Inspection Mode
   - C) Offline Protection Mode
   - D) True Transparent Proxy Mode
   - **Answer: C**

2. What is the primary purpose of a server pool in FortiWeb?
   - A) To define protected hostnames
   - B) To group backend application servers for load balancing
   - C) To configure SSL certificates
   - D) To establish HA relationships
   - **Answer: B**

3. Which load balancing method distributes traffic based on current server connections?
   - A) Round Robin
   - B) Weighted Round Robin
   - C) Least Connections
   - D) IP Hash
   - **Answer: C**

4. In FortiWeb HA configuration, what is the purpose of the heartbeat interface?
   - A) To route client traffic
   - B) To synchronize configurations between HA members
   - C) To monitor the health status of the HA pair
   - D) To connect to backend servers
   - **Answer: C**

5. Which component directly associates protection profiles with specific web applications?
   - A) Server Pool
   - B) Virtual Server
   - C) Server Policy
   - D) Protected Hostname
   - **Answer: C**

6. What happens when FortiWeb is deployed in True Transparent Proxy mode?
   - A) It acts as the default gateway
   - B) It modifies source IP addresses
   - C) It preserves both source and destination IP addresses
   - D) It requires DNS redirection
   - **Answer: C**

7. Which HA mode provides load sharing capabilities across both units?
   - A) Active-Passive
   - B) Active-Active
   - C) Standalone
   - D) Clustered
   - **Answer: B**

8. What is the recommended first step when troubleshooting a FortiWeb deployment issue?
   - A) Reboot the system
   - B) Review system logs and event messages
   - C) Disable all security features
   - D) Reset to factory defaults
   - **Answer: B**

9. Which setting determines session persistence in a server pool?
   - A) Health Check
   - B) Server Balance
   - C) Persistence
   - D) Connection Limit
   - **Answer: C**

10. What does a protected hostname define in FortiWeb?
    - A) The IP address of backend servers
    - B) The domain name or host header of the protected web application
    - C) The SSL certificate common name
    - D) The admin access hostname
    - **Answer: B**

**True/False Questions**

11. FortiWeb can operate in multiple deployment modes simultaneously on different interfaces.
    - **Answer: True**

12. Server health checks are optional in FortiWeb server pool configurations.
    - **Answer: False** (Health checks are critical for proper load balancing)

13. HA configuration synchronization automatically replicates all system settings to the secondary unit.
    - **Answer: True**

14. Protected hostnames must exactly match the Host header in HTTP requests.
    - **Answer: False** (Can use wildcards and patterns)

15. FortiWeb requires a dedicated management interface separate from data interfaces.
    - **Answer: False** (Management can share interfaces)

**Scenario-Based Questions**

16. Your organization needs to protect multiple web applications with different security requirements. Which FortiWeb feature allows you to apply different protection profiles to each application?
    - A) Server Pools
    - B) Server Policies with different protected hostnames
    - C) Virtual IPs
    - D) Single Policy with multiple rules
    - **Answer: B**

17. You notice traffic is not being distributed evenly across backend servers. The first server receives most connections. What is the most likely cause?
    - A) Incorrect load balancing method (using First Alive instead of Round Robin)
    - B) Network connectivity issue
    - C) Insufficient server resources
    - D) SSL offloading misconfiguration
    - **Answer: A**

18. During a planned maintenance window for the primary HA unit, what should you configure to prevent automatic failback?
    - A) Disable HA monitoring
    - B) Set override to disabled
    - C) Increase failback delay timer
    - D) Configure maintenance mode on the primary unit
    - **Answer: B**

**Fill-in-the-Blank Questions**

19. The three primary FortiWeb deployment modes are Reverse Proxy, Transparent Inspection, and __________ Protection.
    - **Answer: Offline**

20. In server pool configuration, __________ defines how long a client session remains bound to the same backend server.
    - **Answer: Persistence (or Session Persistence)**

21. The __________ configuration in FortiWeb defines the backend application servers' IP addresses and ports.
    - **Answer: Server Pool (or Physical Server)**

---

## Encryption, Authentication, and Compliance

### Objective Summary

**Web Application Vulnerabilities Mitigation**
FortiWeb protects against common web application vulnerabilities including OWASP Top 10 threats such as SQL injection, cross-site scripting (XSS), command injection, path traversal, and remote file inclusion. Protection mechanisms include signature-based detection, behavioral analysis, input validation, and output encoding. Administrators configure exception rules for legitimate traffic that might trigger false positives.

**Access Control and Tracking Methods**
FortiWeb implements multiple access control mechanisms including IP reputation filtering, geolocation blocking, URL access policies, HTTP protocol constraints, and custom access rules. Tracking methods monitor user sessions, enforce rate limiting, and prevent credential stuffing attacks. Black/white lists provide explicit allow/deny controls for known trusted or malicious sources.

**Authentication Attack Mitigation**
Protection against authentication attacks includes brute force prevention, credential stuffing detection, session hijacking prevention, and multi-factor authentication enforcement. FortiWeb monitors login attempts, enforces account lockout policies, and detects abnormal authentication patterns. Cookie security features prevent session fixation and theft.

**SSL Inspection and Offloading**
SSL/TLS inspection enables FortiWeb to decrypt, inspect, and re-encrypt HTTPS traffic to detect threats in encrypted communications. SSL offloading terminates SSL connections at FortiWeb, reducing computational load on backend servers. Configuration includes certificate management, cipher suite selection, protocol version enforcement, and certificate validation. FortiWeb supports Server Name Indication (SNI) for hosting multiple SSL sites.

**Troubleshooting Encryption and Authentication**
Common issues include certificate validation errors, cipher suite mismatches, authentication failures, and false positive detections. Troubleshooting involves validating certificate chains, reviewing authentication logs, analyzing blocked requests, and adjusting security thresholds. Administrators use debug logging and packet captures to diagnose SSL/TLS handshake failures.

---

### Exam Questions: Encryption, Authentication, and Compliance

**Multiple Choice Questions**

22. Which OWASP Top 10 vulnerability allows attackers to execute arbitrary SQL commands on the database?
    - A) Cross-Site Scripting (XSS)
    - B) SQL Injection
    - C) Cross-Site Request Forgery (CSRF)
    - D) Broken Authentication
    - **Answer: B**

23. What is the primary benefit of SSL offloading on FortiWeb?
    - A) Improved security
    - B) Reduced processing load on backend servers
    - C) Enhanced encryption strength
    - D) Automatic certificate renewal
    - **Answer: B**

24. Which access control method blocks traffic based on the geographical location of the source IP?
    - A) IP Reputation
    - B) URL Access Policy
    - C) Geolocation Blocking
    - D) Custom Access Rule
    - **Answer: C**

25. What does SNI (Server Name Indication) enable in SSL/TLS configurations?
    - A) Stronger encryption algorithms
    - B) Multiple SSL certificates on a single IP address
    - C) Automatic certificate validation
    - D) Client certificate authentication
    - **Answer: B**

26. Which attack involves flooding login pages with username/password combinations obtained from other breaches?
    - A) Brute Force Attack
    - B) Session Hijacking
    - C) Credential Stuffing
    - D) Password Spraying
    - **Answer: C**

27. What is the purpose of HTTP protocol constraints in FortiWeb?
    - A) To improve performance
    - B) To enforce RFC compliance and prevent protocol violations
    - C) To compress HTTP traffic
    - D) To cache static content
    - **Answer: B**

28. Which FortiWeb feature prevents automated tools from repeatedly attempting to log in?
    - A) URL Access Policy
    - B) Rate Limiting / Brute Force Prevention
    - C) Cookie Security
    - D) IP Reputation
    - **Answer: B**

29. When FortiWeb performs SSL inspection, what happens to the encrypted traffic?
    - A) It is blocked
    - B) It bypasses inspection
    - C) It is decrypted, inspected, and re-encrypted
    - D) It is logged only
    - **Answer: C**

30. What is the purpose of an exception rule in vulnerability protection?
    - A) To block additional threats
    - B) To allow legitimate traffic that triggers false positives
    - C) To encrypt specific traffic
    - D) To redirect traffic to another server
    - **Answer: B**

31. Which authentication attack exploits predictable session identifiers?
    - A) Brute Force
    - B) Credential Stuffing
    - C) Session Fixation
    - D) Password Spraying
    - **Answer: C**

**True/False Questions**

32. FortiWeb can decrypt and inspect SSL/TLS 1.3 traffic.
    - **Answer: True**

33. IP reputation filtering relies solely on internal threat intelligence.
    - **Answer: False** (Uses both internal and external threat feeds)

34. Cross-Site Scripting (XSS) attacks can be mitigated by input validation and output encoding.
    - **Answer: True**

35. SSL offloading and SSL inspection are the same feature.
    - **Answer: False** (Offloading terminates SSL; inspection decrypts and re-encrypts)

36. Rate limiting can help prevent both brute force attacks and denial-of-service attacks.
    - **Answer: True**

**Scenario-Based Questions**

37. Your web application legitimately uses SQL keywords in URL parameters for a search function. How should you configure FortiWeb to prevent false positives while maintaining SQL injection protection?
    - A) Disable SQL injection protection entirely
    - B) Create an exception rule for the specific URL path and parameter
    - C) Increase the attack severity threshold globally
    - D) Whitelist all URLs containing SQL keywords
    - **Answer: B**

38. Users report SSL certificate warnings when accessing your protected web application. What is the most likely cause?
    - A) The backend server certificate is expired
    - B) FortiWeb is using a self-signed certificate or certificate not trusted by clients
    - C) SSL offloading is disabled
    - D) The cipher suite is too weak
    - **Answer: B**

39. You need to block traffic from specific countries known for malicious activity while allowing your legitimate global user base. Which feature combination should you use?
    - A) IP Reputation only
    - B) Geolocation blocking with whitelist exceptions for legitimate users
    - C) URL Access Policy
    - D) Rate Limiting
    - **Answer: B**

40. An attacker is slowly attempting to guess passwords using different usernames (password spraying). Which FortiWeb feature is most effective against this attack?
    - A) SQL Injection Protection
    - B) Session Management
    - C) Brute Force Prevention with account lockout
    - D) XSS Protection
    - **Answer: C**

**Fill-in-the-Blank Questions**

41. The protection mechanism that prevents attackers from injecting malicious scripts into web pages viewed by other users is called __________ protection.
    - **Answer: Cross-Site Scripting (XSS)**

42. When FortiWeb terminates SSL connections and forwards unencrypted traffic to backend servers, this is called SSL __________.
    - **Answer: Offloading**

43. A __________ attack attempts to traverse the directory structure to access files outside the web root directory.
    - **Answer: Path Traversal (or Directory Traversal)**

44. The security feature that validates and enforces proper HTTP methods, headers, and structure is called __________ constraints.
    - **Answer: HTTP Protocol (or Protocol Constraints)**

---

## Web Application Security

### Objective Summary

**Threat Mitigation Features**
FortiWeb provides comprehensive threat mitigation including input validation, attack signature detection, protocol anomaly detection, data leak prevention, and malicious file upload blocking. Features include parameter validation, cookie security, hidden field protection, CSRF token validation, and JSON/XML schema enforcement. Advanced capabilities include zero-day threat protection through behavioral analysis and anomaly detection.

**Blocking Known Attacks**
FortiWeb maintains continuously updated attack signature databases to identify and block known attack patterns. Signature categories include injection attacks, protocol violations, malicious bots, scanning tools, and exploit attempts. Administrators configure signature sensitivity levels, create custom signatures, and schedule automatic signature updates. FortiWeb correlates multiple indicators to improve detection accuracy and reduce false positives.

**Troubleshooting Threat Detection**
Effective troubleshooting requires analyzing attack logs, reviewing blocked requests, validating security policies, and tuning detection thresholds. Administrators use traffic monitoring tools, analyze HTTP headers and payloads, and review threat intelligence feeds. Common issues include legitimate traffic being blocked, attacks going undetected due to insufficient protection levels, and performance impacts from overly aggressive inspection.

**API Protection**
Modern applications rely on APIs that require specialized protection. FortiWeb provides REST API security including schema validation, rate limiting per API endpoint, authentication enforcement, parameter validation, and API key management. Protection extends to GraphQL, SOAP, and other API protocols. API discovery features identify and profile API endpoints automatically.

---

### Exam Questions: Web Application Security

**Multiple Choice Questions**

45. What is the primary purpose of attack signatures in FortiWeb?
    - A) To encrypt traffic
    - B) To identify and block known attack patterns
    - C) To balance server load
    - D) To cache web content
    - **Answer: B**

46. Which FortiWeb feature prevents attackers from uploading malicious files to web applications?
    - A) Data Leak Prevention
    - B) File Upload Restriction
    - C) Parameter Validation
    - D) Cookie Security
    - **Answer: B**

47. What does CSRF (Cross-Site Request Forgery) protection validate?
    - A) SQL query syntax
    - B) Anti-CSRF tokens in form submissions
    - C) SSL certificate validity
    - D) Session timeout values
    - **Answer: B**

48. Which type of attack attempts to extract sensitive data from web applications?
    - A) Data Injection
    - B) Session Hijacking
    - C) Data Leak / Information Disclosure
    - D) Brute Force
    - **Answer: C**

49. What is the benefit of automatic signature updates in FortiWeb?
    - A) Improved server performance
    - B) Protection against newly discovered threats
    - C) Reduced memory usage
    - D) Faster SSL processing
    - **Answer: B**

50. Which FortiWeb feature validates that API requests conform to expected schemas?
    - A) Input Validation
    - B) API Schema Validation
    - C) Protocol Constraints
    - D) URL Access Policy
    - **Answer: B**

51. What does "hidden field protection" prevent in web applications?
    - A) SQL injection
    - B) Unauthorized modification of hidden form fields
    - C) XSS attacks
    - D) Brute force attacks
    - **Answer: B**

52. Which attack detection method identifies threats based on deviation from normal behavior?
    - A) Signature-Based Detection
    - B) Rule-Based Detection
    - C) Anomaly-Based Detection
    - D) Heuristic Detection
    - **Answer: C**

53. What is the purpose of parameter validation in FortiWeb?
    - A) To verify SSL certificates
    - B) To ensure input data meets expected formats and constraints
    - C) To authenticate users
    - D) To compress HTTP traffic
    - **Answer: B**

54. Which threat mitigation feature prevents sensitive information from being exposed in HTTP responses?
    - A) Input Validation
    - B) Output Filtering
    - C) Data Leak Prevention
    - D) Cookie Security
    - **Answer: C**

**True/False Questions**

55. FortiWeb can create custom attack signatures based on specific application needs.
    - **Answer: True**

56. Cookie security features can prevent cookie theft and manipulation.
    - **Answer: True**

57. API rate limiting applies the same limits to all endpoints uniformly.
    - **Answer: False** (Can be configured per endpoint)

58. Zero-day attacks can only be detected using signature-based methods.
    - **Answer: False** (Anomaly and behavior-based detection help with zero-days)

59. FortiWeb can automatically discover and profile API endpoints.
    - **Answer: True**

**Scenario-Based Questions**

60. Your REST API is experiencing abuse from automated clients making thousands of requests per minute. Which FortiWeb feature should you prioritize?
    - A) SQL Injection Protection
    - B) API Rate Limiting per endpoint
    - C) SSL Offloading
    - D) Server Pool Configuration
    - **Answer: B**

61. Legitimate users report their shopping cart items are being cleared unexpectedly. Investigation reveals attackers are exploiting CSRF vulnerabilities. What should you enable?
    - A) Session Timeout
    - B) CSRF Token Validation
    - C) Cookie Encryption
    - D) IP Reputation
    - **Answer: B**

62. Security audits reveal sensitive database error messages are being displayed to users. Which feature addresses this?
    - A) Input Validation
    - B) Attack Signatures
    - C) Data Leak Prevention / Error Message Filtering
    - D) Protocol Constraints
    - **Answer: C**

63. A new zero-day vulnerability has been announced but no signature is available yet. Which FortiWeb capability provides interim protection?
    - A) Signature Updates Only
    - B) Machine Learning and Anomaly Detection
    - C) SSL Inspection
    - D) Server Load Balancing
    - **Answer: B**

**Fill-in-the-Blank Questions**

64. The protection mechanism that validates anti-CSRF tokens is called __________ protection.
    - **Answer: Cross-Site Request Forgery (CSRF)**

65. When FortiWeb validates that input parameters match expected data types and patterns, this is called __________ validation.
    - **Answer: Parameter (or Input)**

66. Attack __________ are patterns or rules that identify known malicious traffic based on threat intelligence.
    - **Answer: Signatures**

67. The process of identifying what APIs exist in your application environment is called API __________.
    - **Answer: Discovery**

---

## Machine Learning (ML)

### Objective Summary

**Machine Learning for Anomalies**
FortiWeb's ML-based anomaly detection establishes baselines of normal application behavior through learning periods. The system analyzes traffic patterns, request frequencies, parameter values, URL access patterns, and user behaviors to create behavioral models. During enforcement, deviations from established baselines trigger alerts or blocks. ML adapts to application changes over time through continuous learning modes. This approach effectively detects zero-day attacks and novel exploit techniques that signature-based systems miss.

**Machine Learning for Bots**
Bot detection using ML distinguishes between legitimate human users, good bots (search engines), and malicious bots (scrapers, credential stuffers, vulnerability scanners). The system analyzes behavioral patterns including mouse movements, keystroke dynamics, session characteristics, request timing, and browser fingerprints. ML-based bot detection adapts to evolving bot techniques and reduces reliance on static indicators like user agents or IP addresses.

**Machine Learning for APIs**
API-specific ML protection learns normal API usage patterns including request frequencies, parameter values, response sizes, endpoint sequences, and client behaviors. The system establishes baselines for each API endpoint and client relationship. Anomalous API usage triggers graduated responses from monitoring to blocking. This protects against API abuse, data exfiltration, and novel API-specific attacks. ML adapts to legitimate API evolution while maintaining security.

---

### Exam Questions: Machine Learning (ML)

**Multiple Choice Questions**

68. What is the primary purpose of the ML learning period in FortiWeb?
    - A) To update attack signatures
    - B) To establish a baseline of normal application behavior
    - C) To configure server pools
    - D) To optimize SSL performance
    - **Answer: B**

69. Which type of attack is ML-based anomaly detection most effective against?
    - A) Known signature-based attacks
    - B) Zero-day and novel attacks
    - C) DDoS attacks
    - D) Physical security breaches
    - **Answer: B**

70. What characteristics does ML-based bot detection analyze?
    - A) Only IP addresses
    - B) Only user agent strings
    - C) Behavioral patterns including mouse movements and keystroke dynamics
    - D) Only request headers
    - **Answer: C**

71. During the ML learning period, how should FortiWeb be configured?
    - A) In blocking mode to capture attacks
    - B) In monitoring mode to observe legitimate traffic without blocking
    - C) With all features disabled
    - D) In offline mode
    - **Answer: B**

72. What does continuous learning mode allow in ML configuration?
    - A) Automatic signature updates
    - B) The model to adapt to application changes over time
    - C) Faster processing speeds
    - D) Reduced memory usage
    - **Answer: B**

73. Which ML feature helps detect API data exfiltration attempts?
    - A) Server pool learning
    - B) ML for APIs analyzing request patterns and response sizes
    - C) SSL offloading
    - D) HA synchronization
    - **Answer: B**

74. What distinguishes "good bots" from "bad bots" in ML bot detection?
    - A) IP address only
    - B) Behavioral analysis and reputation
    - C) Connection speed
    - D) SSL certificate
    - **Answer: B**

75. How does ML-based API protection handle legitimate API evolution?
    - A) It blocks all changes
    - B) It requires manual reconfiguration
    - C) It adapts through continuous learning while maintaining security
    - D) It disables protection temporarily
    - **Answer: C**

76. What should you do if ML anomaly detection generates too many false positives?
    - A) Disable ML entirely
    - B) Extend the learning period or adjust sensitivity thresholds
    - C) Reset to factory defaults
    - D) Increase signature severity
    - **Answer: B**

77. Which behavioral pattern is NOT typically analyzed by ML bot detection?
    - A) Mouse movements
    - B) Keystroke dynamics
    - C) Backend server CPU usage
    - D) Browser fingerprints
    - **Answer: C**

**True/False Questions**

78. ML-based anomaly detection requires pre-configured attack signatures.
    - **Answer: False** (It learns normal behavior patterns)

79. During the learning period, FortiWeb ML should be exposed to representative legitimate traffic.
    - **Answer: True**

80. ML bot detection can identify credential stuffing attacks by analyzing behavioral patterns.
    - **Answer: True**

81. Once ML training is complete, the model never needs updating.
    - **Answer: False** (Continuous learning adapts to changes)

82. ML for APIs can establish different baselines for different API clients.
    - **Answer: True**

**Scenario-Based Questions**

83. You've deployed a new web application and want to enable ML-based protection. What is the correct sequence of steps?
    - A) Enable blocking mode immediately
    - B) Configure ML in monitoring mode, allow learning period with legitimate traffic, review results, then enable blocking
    - C) Enable all signatures first, then ML
    - D) Skip learning period for faster deployment
    - **Answer: B**

84. Your API experiences sudden legitimate traffic spikes during business hours. How should ML for APIs be configured to avoid false positives?
    - A) Disable ML during business hours
    - B) Use continuous learning mode and appropriate sensitivity settings
    - C) Block all traffic spikes
    - D) Rely only on signature-based detection
    - **Answer: B**

85. You notice ML bot detection is blocking legitimate search engine crawlers. What should you check first?
    - A) Server pool configuration
    - B) Bot reputation settings and whitelists for known good bots
    - C) SSL certificates
    - D) HA synchronization
    - **Answer: B**

86. After deploying new application features, ML anomaly detection begins alerting frequently. What is the most appropriate action?
    - A) Disable anomaly detection
    - B) Initiate a new learning period or adjust to allow the model to adapt
    - C) Ignore the alerts
    - D) Block all new traffic patterns
    - **Answer: B**

**Fill-in-the-Blank Questions**

87. The initial phase where ML observes traffic to establish normal patterns is called the __________ period.
    - **Answer: Learning (or Training)**

88. ML-based protection that adapts to application changes over time uses __________ learning mode.
    - **Answer: Continuous**

89. The ML feature that distinguishes between human users and automated scripts is called __________ detection.
    - **Answer: Bot**

90. When ML identifies traffic that deviates significantly from learned patterns, it detects an __________.
    - **Answer: Anomaly**

---

## Answer Key Summary

### Deployment and Configuration (Questions 1-21)
1. C | 2. B | 3. C | 4. C | 5. C | 6. C | 7. B | 8. B | 9. C | 10. B
11. T | 12. F | 13. T | 14. F | 15. F | 16. B | 17. A | 18. B
19. Offline | 20. Persistence | 21. Server Pool

### Encryption, Authentication, and Compliance (Questions 22-44)
22. B | 23. B | 24. C | 25. B | 26. C | 27. B | 28. B | 29. C | 30. B | 31. C
32. T | 33. F | 34. T | 35. F | 36. T | 37. B | 38. B | 39. B | 40. C
41. XSS | 42. Offloading | 43. Path Traversal | 44. HTTP Protocol

### Web Application Security (Questions 45-67)
45. B | 46. B | 47. B | 48. C | 49. B | 50. B | 51. B | 52. C | 53. B | 54. C
55. T | 56. T | 57. F | 58. F | 59. T | 60. B | 61. B | 62. C | 63. B
64. CSRF | 65. Parameter | 66. Signatures | 67. Discovery

### Machine Learning (Questions 68-90)
68. B | 69. B | 70. C | 71. B | 72. B | 73. B | 74. B | 75. C | 76. B | 77. C
78. F | 79. T | 80. T | 81. F | 82. T | 83. B | 84. B | 85. B | 86. B
87. Learning | 88. Continuous | 89. Bot | 90. Anomaly

---

## Study Recommendations

### Key Focus Areas for Exam Preparation

1. **Deployment Concepts**: Understand the differences between deployment modes and when to use each
2. **HA Configuration**: Know how to configure and troubleshoot high availability setups
3. **OWASP Top 10**: Be familiar with common web vulnerabilities and how FortiWeb mitigates them
4. **SSL/TLS**: Understand the difference between SSL inspection and offloading
5. **Attack Signatures**: Know how signature-based detection works and how to manage false positives
6. **ML Concepts**: Understand learning periods, continuous learning, and when ML is most effective
7. **API Security**: Be familiar with API-specific threats and protection mechanisms
8. **Troubleshooting**: Practice systematic troubleshooting approaches for common issues

### Reference Documentation
- FortiWeb 7.4.0 Administration Guide: https://docs.fortinet.com/document/fortiweb/7.4.0/administration-guide/60895/introduction

---

**Total Questions: 90** (60+ as requested)
- Multiple Choice: 57 questions
- True/False: 18 questions  
- Scenario-Based: 10 questions
- Fill-in-the-Blank: 15 questions

**Difficulty Level**: Intermediate (suitable for administrator-level certification)

*Note: This study guide is based on FortiWeb 7.4 documentation and covers intermediate-level topics appropriate for administrator certification exams.*
