
### A.1 File-Based Signatures

**YARA Rule Example - Detecting Suspicious PowerShell:**
```yara
rule Suspicious_PowerShell_DownloadString
{
    meta:
        description = "Detects PowerShell download cradle"
        author = "Security Team"
        date = "2024-01-15"
        
    strings:
        $s1 = "Net.WebClient" nocase
        $s2 = "DownloadString" nocase
        $s3 = "IEX" nocase
        $s4 = "Invoke-Expression" nocase
        
    condition:
        $s1 and $s2 and ($s3 or $s4)
}
```

### A.2 Network Signatures

**Suricata Rule - Detecting SQL Injection Attempt:**
```
alert http any any -> $HOME_NET any (msg:"SQL Injection Attempt"; 
flow:established,to_server; content:"GET"; http_method; 
pcre:"/(\%27)|(\')|(\-\-)|(\%23)|(#)/i"; 
classtype:web-application-attack; sid:1000001; rev:1;)
```

**Snort Rule - Detecting Suspicious DNS Tunneling:**
```
alert udp $HOME_NET any -> any 53 (msg:"Possible DNS Tunneling - Long Query"; 
dsize:>100; content:"|01 00 00 01|"; offset:2; depth:4; 
threshold:type both, track by_src, count 5, seconds 60; 
sid:1000002; rev:1;)
```
