### C.1 Signature-Based Investigation Checklist

**When Signature Match Detected:**

- [ ] Verify signature match accuracy (check for false positive)
- [ ] Document signature that triggered alert (rule ID, signature name)
- [ ] Identify affected systems/assets
- [ ] Determine signature type (hash, pattern, behavior, network)
- [ ] Check signature age and last update date
- [ ] Correlate with other security events
- [ ] Review threat intelligence for IOCs
- [ ] Assess criticality and potential impact
- [ ] Preserve evidence (logs, files, memory, network traffic)
- [ ] Escalate according to incident response plan
- [ ] Update signature database if new variant discovered

### C.2 Anomaly-Based Investigation Checklist

**When Anomaly Detected:**

- [ ] Document specific anomaly indicators
- [ ] Verify baseline accuracy for comparison period
- [ ] Quantify deviation magnitude (how far from normal)
- [ ] Determine anomaly type (point, contextual, collective)
- [ ] Check for legitimate business justification
- [ ] Review recent changes (patches, updates, configuration)
- [ ] Examine user/system context
- [ ] Correlate with other anomalies or signatures
- [ ] Interview relevant users if appropriate
- [ ] Assess false positive likelihood
- [ ] Document baseline update if legitimate business change
- [ ] Tune thresholds if excessive false positives
- [ ] Escalate confirmed anomalies per IR procedures

### C.3 Combined Investigation Workflow

**Integrated Detection Investigation:**

```
1. Initial Detection
   ├─ Signature Match? → Quick validation path
   └─ Anomaly Only? → Detailed context analysis

2. Evidence Collection
   ├─ Network: PCAPs, flow records, DNS logs
   ├─ Endpoint: disk images, memory dumps, registry
   ├─ Logs: authentication, application, system
   └─ External: threat intelligence, OSINT

3. Analysis Phase
   ├─ Timeline construction
   ├─ IOC correlation (signature data)
   ├─ Behavioral analysis (anomaly data)
   └─ Attack vector identification

4. Validation
   ├─ Confirm true positive
   ├─ Assess scope and impact
   └─ Identify root cause

5. Response
   ├─ Contain threat
   ├─ Eradicate malicious artifacts
   ├─ Recover systems
   └─ Document lessons learned

6. Improvement
   ├─ Update signatures
   ├─ Refine baselines
   └─ Tune detection rules
```

