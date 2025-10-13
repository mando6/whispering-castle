
### Common Forensic Artifacts by Platform

**Windows:**
- Event Logs: C:\Windows\System32\winevt\Logs\
- Prefetch: C:\Windows\Prefetch\
- Registry: C:\Windows\System32\config\
- User Profiles: C:\Users\[username]\
- Browser History: C:\Users\[username]\AppData\Local\

**Linux:**
- Auth Logs: /var/log/auth.log or /var/log/secure
- System Logs: /var/log/syslog or /var/log/messages
- Command History: ~/.bash_history
- Cron Jobs: /etc/crontab, /var/spool/cron/

**macOS:**
- Unified Logs: /var/db/diagnostics/
- System Logs: /var/log/
- User Logs: ~/Library/Logs/
- Browser Data: ~/Library/Safari/ or ~/Library/Application Support/

### Essential Forensic Commands

**Windows (PowerShell):**
```powershell
# Get event logs
Get-EventLog -LogName Security -Newest 100

# List running processes
Get-Process

# Check network connections
Get-NetTCPConnection

# View recent file access
Get-ChildItem -Recurse | Select-Object FullName, LastAccessTime
```

**Linux (Bash):**
```bash
# View authentication logs
sudo cat /var/log/auth.log

# Check active connections
netstat -tupan

# List recent commands
history

# Find recently modified files
find /home -type f -mtime -7
```

### Investigation Checklist

- [ ] Secure and preserve original evidence
- [ ] Document chain of custody
- [ ] Create forensic images with write protection
- [ ] Calculate and record hash values
- [ ] Establish investigation timeline
- [ ] Identify all affected systems and accounts
- [ ] Collect logs from all relevant sources
- [ ] Analyze user behavior patterns
- [ ] Correlate evidence across systems
- [ ] Document findings with screenshots
- [ ] Prepare incident report
- [ ] Conduct post-incident review

