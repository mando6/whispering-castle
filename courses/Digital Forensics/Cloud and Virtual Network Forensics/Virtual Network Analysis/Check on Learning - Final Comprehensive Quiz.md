### Section 1: Fundamentals (Questions 1-10)

**Question 1:** What is the primary difference between virtual network forensics and traditional network forensics?

A) Virtual network forensics requires different legal authorization  
B) Virtual networks exist in software and include additional abstraction layers  
C) Traditional network forensics cannot capture encrypted traffic  
D) Virtual networks are always more secure  

**Question 2:** Which hypervisor type runs directly on hardware without a host operating system?

A) Type 0  
B) Type 1  
C) Type 2  
D) Type 3  

**Question 3:** In a NAT network configuration, where would you find evidence of the VM's external communications?

A) Only in the guest VM's logs  
B) In the hypervisor's NAT translation logs  
C) On external network infrastructure only  
D) NAT networks do not allow external communications  

**Question 4:** What does a `.vmx` file contain in a VMware environment?

A) Virtual machine memory contents  
B) Virtual machine disk data  
C) Virtual machine configuration including network settings  
D) Virtual machine snapshot data  

**Question 5:** Which of the following is NOT a common virtual network mode?

A) Bridged  
B) NAT  
C) Host-Only  
D) Distributed  

**Question 6:** What is the forensic significance of VM snapshots?

A) They only save disk state, not network state  
B) They can capture point-in-time configuration and optionally memory  
C) They automatically delete network logs  
D) They prevent forensic analysis  

**Question 7:** Which command would you use in ESXi to list network connections?

A) `netstat -an`  
B) `esxcli network ip connection list`  
C) `show ip connections`  
D) `Get-NetTCPConnection`  

**Question 8:** In Hyper-V, what format are modern VM configuration files stored in?

A) `.xml` (plain text)  
B) `.vmcx` (binary)  
C) `.vmx` (plain text)  
D) `.vhd` (virtual disk)  

**Question 9:** Why is memory forensics particularly valuable in virtual network investigations?

A) It's faster than analyzing disk evidence  
B) It contains ephemeral data like active connections and cached credentials  
C) It's legally admissible while disk evidence is not  
D) Virtual machines don't have persistent storage  

**Question 10:** What is the primary purpose of port mirroring in virtual switch configurations?

A) To increase network performance  
B) To allow one port to receive copies of traffic from other ports for monitoring  
C) To create redundant network connections  
D) To enable VLAN tagging  

### Section 2: VMware Forensics (Questions 11-20)

**Question 11:** Where are ESXi host system logs typically stored?

A) `C:\Windows\System32\Logs`  
B) `/var/log/`  
C) `/etc/vmware/logs/`  
D) `D:\VMware\Logs`  

**Question 12:** What is the recommended first step when collecting evidence from a running VM?

A) Immediately power off the VM  
B) Delete all snapshots  
C) Preserve volatile data like memory and active connections  
D) Export the VM to OVF format  

**Question 13:** Which VMware tool is specifically designed to clone virtual disks?

A) `vmkfstools`  
B) `esxcli`  
C) `vim-cmd`  
D) `vmware-converter`  

**Question 14:** What does enabling "promiscuous mode" on a virtual network adapter potentially indicate?

A) The VM is properly secured  
B) The VM may be monitoring network traffic (possible reconnaissance)  
C) The VM cannot communicate externally  
D) The VM is disconnected from the network  

**Question 15:** In a VMware environment, where is centralized management and event logging typically stored?

A) On each ESXi host individually  
B) In vCenter Server  
C) In the guest VM operating systems  
D) On physical network switches  

**Question 16:** What is the purpose of the `vm-support` command?

A) To start the VMware support service  
B) To collect comprehensive diagnostic and log bundles  
C) To enable technical support access  
D) To upgrade VMware tools  

**Question 17:** Which file extension indicates a VMware virtual disk file?

A) `.vhd`  
B) `.vmdk`  
C) `.vdi`  
D) `.qcow2`  

**Question 18:** When should you use the suspend function instead of shutdown during evidence collection?

A) When you want to delete the VM  
B) When you need to preserve the exact running state including memory  
C) When the VM is already powered off  
D) When you want to reset the VM  

**Question 19:** What information can you gather from vSwitch statistics?

A) Only bandwidth usage  
B) Traffic patterns, port utilization, dropped packets, and security policy violations  
C) VM passwords  
D) User keystrokes  

**Question 20:** Where would you find evidence of VM network adapter changes in VMware?

A) Only in the `.vmx` configuration file  
B) In both the `.vmx` file and system logs  
C) Only in vCenter event database  
D) In the virtual disk contents  

### Section 3: Hyper-V Forensics (Questions 21-30)

**Question 21:** Which PowerShell cmdlet would you use to export a Hyper-V virtual machine?

A) `Save-VM`  
B) `Export-VM`  
C) `Backup-VM`  
D) `Copy-VM`  

**Question 22:** What is the file extension for Hyper-V virtual hard disks (modern format)?

A) `.vmdk`  
B) `.vhd`  
C) `.vhdx`  
D) `.vdi`  

**Question 23:** Which Windows Event Log would contain information about virtual switch operations in Hyper-V?

A) `System`  
B) `Security`  
C) `Microsoft-Windows-Hyper-V-VmSwitch-Operational`  
D) `Application`  

**Question 24:** What does Event ID 3050 indicate in Hyper-V logs?

A) VM network adapter added  
B) VM started  
C) VM crashed  
D) Virtual switch created  

**Question 25:** In Hyper-V, what cmdlet would you use to check if MAC address spoofing is enabled on a VM?

A) `Get-VMNetworkAdapter` with appropriate parameters  
B) `Get-MACAddress`  
C) `Check-VMSecurity`  
D) `Test-VMNetwork`  

**Question 26:** Where are Hyper-V virtual switch configurations primarily stored?

A) In XML files in `C:\ProgramData`  
B) In Windows Management Instrumentation (WMI) and Registry  
C) In SQL Server database  
D) In text files in `C:\Windows\System32`  

**Question 27:** What is the purpose of Integration Services in Hyper-V?

A) To integrate Hyper-V with VMware  
B) To enable enhanced communication and features between host and guest VMs  
C) To connect to external networks  
D) To backup VMs automatically  

**Question 28:** Which of the following is a key advantage of Hyper-V forensics compared to VMware?

A) Hyper-V VMs are always encrypted  
B) Deep integration with Windows Event Logs and PowerShell provides rich audit trails  
C) Hyper-V doesn't require forensic tools  
D) Hyper-V VMs cannot be compromised  

**Question 29:** What file extension indicates a Hyper-V runtime state file?

A) `.vmrs`  
B) `.vmcx`  
C) `.vhdx`  
D) `.avhd`  

**Question 30:** How can you capture the memory state of a running Hyper-V VM?

A) You cannot capture memory from Hyper-V VMs  
B) Use `Save-VM` cmdlet or export with CaptureSavedState option  
C) Only by shutting down the VM  
D) By taking a screenshot  

### Section 4: Network Traffic Analysis (Questions 31-40)

**Question 31:** What is the main advantage of capturing traffic at the virtual switch level versus inside individual VMs?

A) It's faster  
B) It provides visibility into all VM traffic and inter-VM communications  
C) It uses less disk space  
D) It's more secure  

**Question 32:** Which Wireshark display filter would identify all traffic for a specific VM with IP 192.168.1.50?

A) `ip == 192.168.1.50`  
B) `ip.addr == 192.168.1.50`  
C) `host 192.168.1.50`  
D) `address == 192.168.1.50`  

**Question 33:** What is "beaconing" in the context of network forensics?

A) Broadcast traffic  
B) Regular, periodic communication often associated with malware C2 channels  
C) DHCP requests  
D) DNS queries  

**Question 34:** What advantage does NetFlow data provide over full packet capture?

A) NetFlow captures more detail  
B) NetFlow includes packet payloads  
C) NetFlow requires less storage and enables long-term pattern analysis  
D) NetFlow is encrypted  

**Question 35:** In Wireshark, how would you extract files that were transferred over HTTP?

A) File → Save As  
B) File → Export Objects → HTTP  
C) Edit → Extract Files  
D) Tools → File Extraction  

**Question 36:** What is a primary indicator of data exfiltration in network traffic?

A) High volume of inbound traffic  
B) Large outbound transfers to external or unusual destinations  
C) Frequent DNS queries  
D) ICMP ping traffic  

**Question 37:** When analyzing encrypted traffic, what information can still be valuable for forensic analysis?

A) Nothing, encryption prevents all analysis  
B) Metadata including source/destination IPs, ports, timing, and volume  
C) Only the encryption algorithm used  
D) The decryption key  

**Question 38:** What tool is specifically designed for VMware packet capture at the hypervisor level?

A) tcpdump  
B) pktcap-uw  
C) Wireshark  
D) netcat  

**Question 39:** What does DNS tunneling allow an attacker to do?

A) Speed up DNS resolution  
B) Exfiltrate data or establish C2 communications through DNS queries  
C) Block DNS servers  
D) Cache DNS responses longer  

**Question 40:** Why is timeline reconstruction important in network forensics?

A) It makes reports longer  
B) It correlates events across multiple sources to understand the sequence of attack activities  
C) It's required by law  
D) It encrypts the evidence  

### Section 5: Memory Forensics (Questions 41-50)

**Question 41:** What file extension indicates a VMware memory snapshot?

A) `.vmem`  
B) `.mem`  
C) `.dmp`  
D) `.raw`  

**Question 42:** Which Volatility plugin would you use to display network connections from a memory dump?

A) `netstat`  
B) `netscan`  
C) `connections`  
D) Both B and C are correct  

**Question 43:** What is the first step when analyzing memory with Volatility?

A) Run all plugins  
B) Identify the correct OS profile using `imageinfo`  
C) Extract files  
D) Search for passwords  

**Question 44:** What type of network artifact might be found in memory but not in disk analysis?

A) Configuration files  
B) Active connections and encryption keys  
C) Log files  
D) Virtual disk files  

**Question 45:** Why might you choose live memory acquisition over suspending the VM?

A) Live acquisition is always more accurate  
B) To avoid disrupting VM operation while still capturing current state  
C) Live acquisition captures more data  
D) Suspending VMs is not possible  

**Question 46:** What information does the Volatility `pslist` plugin provide that's relevant to network forensics?

A) Only process names  
B) Running processes, which can be correlated with network connections  
C) Physical memory addresses  
D) Deleted files  

**Question 47:** In memory forensics, what might indicate a rootkit or hidden network activity?

A) Processes visible in process list  
B) Network connections without associated processes or hidden processes with connections  
C) High CPU usage  
D) Large memory allocation  

**Question 48:** What is a key limitation of memory forensics?

A) Memory analysis is illegal  
B) Memory is volatile and represents a single point in time  
C) Memory cannot be captured from VMs  
D) Memory dumps are always encrypted  

**Question 49:** Which tool would you use to acquire memory from a live Windows VM?

A) dd  
B) WinPmem or DumpIt  
C) Volatility  
D) FTK Imager for disk only  

**Question 50:** What network-related information can be extracted from the Windows registry in memory?

A) Nothing network-related  
B) Historical network connections, WiFi passwords, and network adapter configurations  
C) Only current IP address  
D) Firewall rules only  

### Section 6: Attack Detection and Analysis (Questions 51-60)

**Question 51:** What is "VM escape"?

A) Exporting a VM to another host  
B) Breaking out of VM isolation to access the hypervisor or host system  
C) A VM losing network connectivity  
D) Shutting down a VM  

**Question 52:** Which of the following is a common indicator of lateral movement between VMs?

A) High CPU usage  
B) Sequential authentication attempts across multiple VMs using similar credentials  
C) Disk fragmentation  
D) Slow network performance  

**Question 53:** What might indicate that a VM is being used for network reconnaissance?

A) Normal web browsing  
B) Port scanning activities and connection attempts to multiple hosts  
C) Email traffic  
D) DNS queries  

**Question 54:** In the context of virtual environments, what is "VM sprawl"?

A) Uncontrolled growth of VMs creating security and management challenges  
B) A type of malware  
C) VM backup process  
D) Network congestion  

**Question 55:** What is a common technique for data staging before exfiltration in virtual environments?

A) Immediate external transfer  
B) Moving data to VMs with external network access before exfiltration  
C) Encrypting all files  
D) Deleting log files  

**Question 56:** Which of the following would be suspicious in virtual network logs?

A) Regular business application traffic  
B) VM accessing hypervisor management interfaces or unusual inter-VM traffic patterns  
C) DHCP requests  
D) Time synchronization traffic  

**Question 57:** What is the forensic significance of finding multiple VMs with identical MAC addresses?

A) It's normal and expected  
B) Could indicate MAC address spoofing or cloning for malicious purposes  
C) Improves network performance  
D) Required for HA configurations  

**Question 58:** What attack technique involves using legitimate administrative tools (like PsExec or WMI)?

A) Zero-day exploits  
B) Living off the land (LOTL) or fileless attacks  
C) Brute force attacks  
D) SQL injection  

**Question 59:** How might an attacker use VM snapshots maliciously?

A) To improve VM performance  
B) To hide malicious activities by reverting or to create hidden copies of data  
C) Snapshots cannot be used maliciously  
D) To update the operating system  

**Question 60:** What is a key indicator that a VM might be part of a botnet?

A) Regular business traffic  
B) Periodic connections to command-and-control servers with similar timing patterns  
C) High memory usage  
D) Multiple network adapters  

### Section 7: Reporting and Best Practices (Questions 61-70)

**Question 61:** What is the primary purpose of maintaining chain of custody?

A) To make reports longer  
B) To document evidence handling and maintain its integrity for legal proceedings  
C) To encrypt evidence  
D) To backup evidence  

**Question 62:** When should you work on original evidence rather than forensic copies?

A) When time is limited  
B) Never - always work on forensic copies to preserve original evidence  
C) When the evidence is encrypted  
D) When requested by management  

**Question 63:** What should be included in the methodology section of a forensic report?

A) Only the final conclusions  
B) Tools used, data sources examined, and any limitations or constraints  
C) Personal opinions  
D) Unverified assumptions  

**Question 64:** What is the purpose of cryptographic hashing in digital forensics?

A) To encrypt evidence  
B) To verify evidence integrity and detect any modifications  
C) To compress files  
D) To delete temporary files  

**Question 65:** Which hash algorithm is currently recommended for forensic evidence verification?

A) MD5 only  
B) SHA-256 or SHA-512  
C) CRC32  
D) Base64  

**Question 66:** What should you do if you discover evidence outside the scope of your original investigation?

A) Ignore it  
B) Delete it  
C) Document it and notify appropriate parties according to organizational policy  
D) Investigate it fully without authorization  

**Question 67:** Why are network topology diagrams important in forensic reports?

A) They make reports look professional  
B) They visually document the environment and help readers understand relationships and attack paths  
C) They are legally required  
D) They replace written descriptions  

**Question 68:** What information should be recorded when acquiring evidence?

A) Only the file size  
B) Date/time, person performing acquisition, tools used, hash values, and storage location  
C) Just the filename  
D) Only the hash value  

**Question 69:** How should conflicting evidence be handled in a forensic report?

A) Report only evidence that supports your conclusion  
B) Present all evidence objectively and explain potential conflicts  
C) Ignore conflicting evidence  
D) Modify evidence to remove conflicts  

**Question 70:** What is the recommended retention period for forensic evidence?

A) 30 days  
B) According to organizational policy, legal requirements, and any litigation holds  
C) Forever  
D) Until the report is complete  

### Section 8: Practical Application (Questions 71-80)

**Question 71:** You discover a VM with an unexpected network adapter configured in bridged mode. What should be your next step?

A) Immediately delete the adapter  
B) Document the configuration, check logs for when it was added, and investigate associated network activity  
C) Ignore it as it's probably legitimate  
D) Restart the VM  

**Question 72:** During analysis, you find gaps in log files. What could this indicate?

A) Normal log rotation  
B) Potential evidence tampering, log deletion, or system issues - requires further investigation  
C) Nothing significant  
D) The logs are encrypted  

**Question 73:** You need to analyze a powered-off VM. What is the correct evidence collection order?

A) Power on, then collect evidence  
B) Hash files, create forensic copy, analyze copy  
C) Delete snapshots first  
D) Export to cloud storage  

**Question 74:** When analyzing packet captures, you find large amounts of encrypted traffic to an unusual IP. What additional analysis should you perform?

A) Nothing, encryption prevents analysis  
B) Analyze traffic patterns, check threat intelligence for the IP, correlate with VM logs and memory  
C) Decrypt the traffic  
D) Block the IP and move on  

**Question 75:** You discover that a VM was exported and deleted. How can you investigate what data it contained?

A) You cannot recover any information  
B) Check snapshots, hypervisor logs, backup systems, and network logs for prior activity  
C) Ask the user what it contained  
D) Recreate it from memory  

**Question 76:** A VM shows connections to multiple other VMs using administrative protocols (SMB, WMI, RDP) within a short timeframe. What does this suggest?

A) Normal administrative activity  
B) Possible lateral movement or attack propagation  
C) Backup operations  
D) Network misconfiguration  

**Question 77:** You need to preserve evidence from a running production VM that cannot be shut down. What approach should you take?

A) Force shutdown immediately  
B) Perform live memory acquisition and network traffic capture while minimizing impact  
C) Wait until the VM can be shut down  
D) Take a screenshot and note what you see  

**Question 78:** When examining vSwitch logs, you notice promiscuous mode was enabled on a port for 2 hours then disabled. What should you investigate?

A) Nothing, this is normal  
B) Check which VM was connected, what traffic occurred during that timeframe, and who made the configuration change  
C) Restart the vSwitch  
D) Enable it again to monitor  

**Question 79:** You find evidence of data exfiltration but the VM's disk doesn't contain the exfiltrated data. Where else should you look?

A) Nowhere, the evidence is lost  
B) Check memory dumps, temp directories, network shares, and other VMs for staging  
C) Recreate the data  
D) Ask the attacker  

**Question 80:** Multiple VMs show signs of compromise with similar indicators. What is your best course of action?

A) Investigate each VM separately over time  
B) Develop a comprehensive investigation plan covering all affected systems, looking for common attack vectors and initial compromise point  
C) Shut down all VMs immediately  
D) Reimage all VMs without investigation  