### B.1 Statistical Baseline for Network Traffic

**Example: Calculating Anomaly Threshold for Outbound Connections**

```
Dataset: Daily outbound connections per workstation (30-day sample)
[245, 267, 251, 298, 242, 256, 271, 263, 254, 249, 
 289, 267, 245, 251, 276, 268, 254, 291, 263, 247,
 256, 271, 268, 254, 259, 276, 248, 267, 254, 271]

Calculations:
Mean (μ) = 262.7 connections
Standard Deviation (σ) = 15.8 connections

Anomaly Thresholds:
- Lower bound: μ - 2σ = 262.7 - 31.6 = 231.1
- Upper bound: μ + 2σ = 262.7 + 31.6 = 294.3

Alert Trigger: Connections < 231 or > 294
Critical Alert: Connections < 215 or > 310 (3σ)
```

### B.2 Time-Based Behavioral Baseline

**Example: User Activity Pattern**

```
Normal Login Hours Profile (90-day analysis):
- Monday-Friday: 08:00-18:00 (95% of logins)
- Weekend: <5% of total logins
- After 22:00: <1% of logins

Data Access Pattern:
- Files accessed per session: 15-45 (median: 28)
- Sensitive data access: 2-3 times per week
- Departments accessed: Engineering (95%), HR (5%)

Anomaly Triggers:
- Login outside 07:00-19:00 on weekdays
- Any weekend login
- >60 files in single session
- Access to Finance/Legal departments
- >5 sensitive data accesses per day
```
