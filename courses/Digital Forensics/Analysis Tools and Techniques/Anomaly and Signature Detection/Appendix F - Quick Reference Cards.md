
### Signature Detection Quick Reference

| Type | Best For | Limitations |
|------|----------|-------------|
| File Hash | Known malware variants | Easily evaded by modification |
| YARA Rules | Pattern matching in files | Requires regular updates |
| Network Signatures | Known attack patterns | Cannot detect unknown attacks |
| Behavioral Signatures | Action sequences | Complex to create and maintain |

**When to Use**: Known threats, compliance requirements, high-confidence detection

### Anomaly Detection Quick Reference

| Type | Best For | Limitations |
|------|----------|-------------|
| Statistical | Quantifiable metrics | Requires clean baseline |
| ML-Based | Complex patterns | Black box, requires training |
| Behavioral | User/system actions | High false positive risk |
| Time Series | Temporal patterns | Sensitive to seasonality |

**When to Use**: Zero-day threats, insider threats, unknown attack patterns

### Investigation Priority Matrix

| Signature Match | Anomaly Detected | Priority | Action |
|----------------|------------------|----------|---------|
| Yes | Yes | Critical | Immediate investigation |
| Yes | No | High | Investigate promptly |
| No | Yes (High deviation) | Medium-High | Investigate with context |
| No | Yes (Low deviation) | Low-Medium | Monitor, log for correlation |
| No | No | Informational | Normal activity |
