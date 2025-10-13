### Part 1: Multiple Choice Questions

**Question 1**: What is the primary difference between traditional forensics and CSP forensics?
- A) Cost of tools
- B) Lack of direct physical access and virtualized infrastructure
- C) Amount of training required
- D) Speed of investigation

**Question 2**: Which AWS service provides API-level audit logging?
- A) VPC Flow Logs
- B) CloudWatch
- C) CloudTrail
- D) GuardDuty

**Question 3**: In Azure, what query language is used for Log Analytics?
- A) SQL
- B) Python
- C) KQL (Kusto Query Language)
- D) JavaScript

**Question 4**: Which GCP log type is always enabled with 400-day retention?
- A) Data Access Logs
- B) Admin Activity Logs
- C) VPC Flow Logs
- D) Application Logs

**Question 5: What is the recommended minimum log retention period for forensic readiness?
- A) 7 days
- B) 30 days
- C) 90 days
- D) 1 year

**Question 6**: Which technique helps handle CSP API rate limiting?
- A) Using multiple accounts simultaneously
- B) Exponential backoff and retry
- C) Ignoring rate limits
- D) Switching to different CSPs

**Question 7**: What does GDPR require for data breach notification?
- A) Within 24 hours
- B) Within 72 hours
- C) Within 7 days
- D) No specific timeframe

**Question 8**: How should you preserve an AWS EC2 instance that's part of an Auto Scaling group?
- A) Stop the entire Auto Scaling group
- B) Detach the instance from ASG and enable termination protection
- C) Delete the Auto Scaling group
- D) Change the instance type

**Question 9**: What is chain of custody?
- A) A type of encryption
- B) Complete documentation of evidence handling
- C) A cloud storage service
- D) A network protocol

**Question 10**: Which is NOT a core challenge in cloud forensics?
- A) Data location uncertainty
- B) Multi-tenancy
- C) Too few logs available
- D) Limited physical access

**Question 11**: What should be included in every forensic report?
- A) Only technical details
- B) Executive summary, timeline, findings, and recommendations
- C) Just log files
- D) Only conclusions

**Question 12**: In Azure, what prevents accidental resource deletion during investigation?
- A) ReadOnly lock
- B) CanNotDelete lock
- C) Immutable lock
- D) Protected lock

**Question 13**: What does IOC stand for?
- A) Internet Operations Center
- B) Indicator of Compromise
- C) International Operations Code
- D) Internal Operations Control

**Question 14**: Which cloud service model gives investigators the highest level of access?
- A) SaaS
- B) PaaS
- C) IaaS
- D) All are equal

**Question 15**: What is the first step in creating an AWS EC2 snapshot?
- A) Stop the instance
- B) Identify the EBS volume ID
- C) Delete the instance
- D) Change security groups

**Question 16**: Which Azure service provides centralized logging with KQL queries?
- A) Activity Log only
- B) Log Analytics
- C) Storage Analytics
- D) Network Watcher only

**Question 17**: What GCP feature prevents accidental project deletion?
- A) Resource lock
- B) Lien
- C) Freeze
- D) Hold

**Question 18**: Which is a best practice for evidence integrity?
- A) Hash at collection and verify throughout
- B) Only hash at the end
- C) Hashing is not necessary
- D) Hash only if asked by court

**Question 19**: What type of analysis reconstructs the sequence of events?
- A) Behavioral analysis
- B) Timeline analysis
- C) Impact analysis
- D) Cost analysis

**Question 20**: Which standard provides guidelines for digital evidence collection?
- A) ISO/IEC 27037
- B) ISO 9001
- C) IEEE 802.11
- D) RFC 1918

### Part 2: Short Answer Questions

**Question 21**: Explain why multi-tenancy in cloud environments creates forensic challenges and describe one technique to address this challenge.

**Question 22**: Describe the process for creating and preserving a forensic snapshot of an AWS EC2 instance, including at least three specific commands or actions.

**Question 23**: List and briefly explain three different types of logs available in Azure for forensic investigation.

**Question 24**: What are the key differences between Admin Activity Logs and Data Access Logs in GCP? Include retention periods.

**Question 25**: Explain the concept of chain of custody and why it's critical in cloud forensics. Provide at least three elements that should be documented.

**Question 26**: Describe two privacy regulations that impact cloud forensic investigations and explain one specific requirement from each.

### Part 3: Scenario-Based Questions

**Scenario 1**: 
You are investigating a suspected data breach in a multi-cloud environment (AWS and Azure). The security team reports that a user account has been accessing large amounts of data from S3 buckets and Azure Blob Storage over the past 48 hours.

**Tasks:**
a) (5 points) List the specific logs you would collect from AWS and Azure for this investigation.
b) (5 points) Describe your evidence preservation strategy, including specific commands or procedures.
c) (5 points) Explain how you would correlate events across both platforms to create a unified timeline.

**Scenario 2**:
A GCP-hosted application has been compromised. The attacker created a new service account, assigned it elevated privileges, and then used it to access BigQuery datasets. The compromise was discovered 10 days after the initial breach.

**Tasks:**
a) Identify the specific GCP logs and services you would use to investigate this incident.
b) Write a sample query (in the appropriate query language) that would help identify the privilege escalation.
c) Describe the legal and ethical considerations you must address before beginning this investigation.
