Part 1: Multiple Choice Answers

1. B - Lack of direct physical access and virtualized infrastructure
2. C - CloudTrail
3. C - KQL (Kusto Query Language)
4. B - Admin Activity Logs
5. C - 90 days
6. B - Exponential backoff and retry
7. B - Within 72 hours
8. B - Detach the instance from ASG and enable termination protection
9. B - Complete documentation of evidence handling
10. C - Too few logs available
11. B - Executive summary, timeline, findings, and recommendations
12. B - CanNotDelete lock
13. B - Indicator of Compromise
14. C - IaaS
15. B - Identify the EBS volume ID
16. B - Log Analytics
17. B - Lien
18. A - Hash at collection and verify throughout
19. B - Timeline analysis
20. A - ISO/IEC 27037

### Part 2: Sample Answers

**Question 21**: Multi-tenancy creates challenges because multiple customers share the same physical infrastructure, making it difficult to isolate evidence specific to one tenant without accessing others' data. Technique: Use CSP-provided isolation mechanisms like AWS Organizations with separate accounts, resource tagging, and IAM policies to ensure evidence collection stays within authorized boundaries.

**Question 22**: Process: (1) Identify target instance and EBS volume, (2) Enable termination protection: `aws ec2 modify-instance-attribute --instance-id i-xxxxx --disable-api-termination`, (3) Create snapshot: `aws ec2 create-snapshot --volume-id vol-xxxxx --description "Forensic evidence"`, (4) Add tags for chain of custody, (5) Verify snapshot completion and hash.

**Question 23**: (1) Activity Logs: Record subscription-level management operations; (2) Sign-in Logs: Track Azure AD authentication events including MFA; (3) NSG Flow Logs: Capture network traffic metadata through Network Security Groups.

**Question 24**: Admin Activity Logs record control-plane operations (create/delete resources), are always enabled, and retained 400 days. Data Access Logs record data reads/writes, must be explicitly enabled, and have configurable retention. Admin logs are free; Data Access logs incur costs.

**Question 25**: Chain of custody is documentation proving evidence handling integrity from collection through presentation. Critical elements: (1) Collection timestamp and collector identity, (2) Hash values for integrity verification, (3) Complete access log showing who handled evidence when and why. Essential for legal admissibility.

**Question 26**: GDPR (EU): Requires breach notification within 72 hours. CCPA (California): Grants consumers right to know what personal data is collected. Both impact what data can be collected and how it must be protected during investigations.

### Part 3: Sample Answers

**Scenario 1:**

a) AWS: CloudTrail logs (API calls), S3 access logs, VPC Flow Logs (network activity), IAM credential reports. Azure: Activity Logs, Storage Analytics logs, Sign-in Logs, NSG Flow Logs.

b) AWS: Create EBS snapshots, enable termination protection, export logs to isolated S3 bucket with versioning and MFA delete. Azure: Create disk snapshots, apply CanNotDelete locks, export logs to immutable storage account. Document all actions with timestamps and hashes.

c) Normalize timestamps to UTC, export all logs to common format (JSON), use correlation fields (username, IP address), create unified CSV or import to SIEM, sort chronologically, identify patterns across platforms.

**Scenario 2:**

a) GCP Cloud Audit Logs (Admin Activity and Data Access), IAM policy history from Cloud Asset Inventory, BigQuery query logs, VPC Flow Logs if applicable, Security Command Center findings.

b) Sample BigQuery SQL:
```sql
SELECT timestamp, protoPayload.authenticationInfo.principalEmail,
       protoPayload.methodName, protoPayload.serviceData.policyDelta
FROM `forensic_logs.cloudaudit_googleapis_com_activity_*`
WHERE protoPayload.methodName = 'SetIamPolicy'
  AND timestamp > TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 11 DAY)
ORDER BY timestamp;
```

c) Legal: Obtain proper authorization, ensure compliance with data privacy regulations (GDPR if EU data involved), document jurisdiction. Ethical: Maintain objectivity, protect employee privacy, collect only necessary data, secure evidence properly, avoid scope creep beyond authorized investigation.
