### Section 1: Fundamentals

**1. B** - Virtual networks exist in software with additional abstraction layers (hypervisor, virtual switches, etc.) that don't exist in traditional physical networks.

**2. B** - Type 1 hypervisors (bare metal) run directly on hardware; Type 2 run on top of a host OS.

**3. B** - In NAT mode, the hypervisor performs address translation, so its NAT logs contain records of internal-to-external communications.

**4. C** - The `.vmx` file is a text configuration file containing VM settings including network adapter configurations.

**5. D** - Bridged, NAT, and Host-Only are standard network modes; "Distributed" refers to distributed switches, not a network mode.

**6. B** - Snapshots can capture the complete VM state at a point in time, including configuration and optionally memory, making them valuable for forensic preservation.

**7. B** - `esxcli network ip connection list` is the correct ESXi command to list network connections.

**8. B** - Modern Hyper-V VMs (Server 2016+) use `.vmcx` binary format for configuration; older versions used `.xml`.

**9. B** - Memory contains ephemeral data like active network connections, cached credentials, and encryption keys not stored on disk.

**10. B** - Port mirroring (SPAN) copies traffic from one or more ports to a monitoring port for analysis.

### Section 2: VMware Forensics

**11. B** - ESXi logs are stored in `/var/log/` directory.

**12. C** - Always preserve volatile data (memory, active connections) first before they are lost.

**13. A** - `vmkfstools` is the VMware utility specifically designed for virtual disk operations including cloning.

**14. B** - Promiscuous mode allows a network adapter to receive all traffic on the network segment, often used for reconnaissance or sniffing.

**15. B** - vCenter Server provides centralized management and stores consolidated event logs from all managed hosts.

**16. B** - `vm-support` collects comprehensive diagnostic and log bundles for troubleshooting and forensic analysis.

**17. B** - `.vmdk` is the VMware virtual disk file extension.

**18. B** - Suspending preserves the exact running state including memory, active connections, and volatile data.

**19. B** - vSwitch statistics provide comprehensive information about traffic patterns, utilization, errors, and security events.

**20. B** - Network adapter changes are recorded in both the VM configuration file and system/vCenter logs.

### Section 3: Hyper-V Forensics

**21. B** - `Export-VM` is the PowerShell cmdlet to export Hyper-V VMs.

**22. C** - `.vhdx` is the modern Hyper-V virtual hard disk format (`.vhd` is the legacy format).

**23. C** - `Microsoft-Windows-Hyper-V-VmSwitch-Operational` log contains virtual switch operations.

**24. B** - Event ID 3050 indicates a VM has started.

**25. A** - `Get-VMNetworkAdapter` with appropriate filtering can show MAC address spoofing settings.

**26. B** - Hyper-V configurations are stored in WMI and the Windows Registry.

**27. B** - Integration Services provide enhanced communication capabilities between Hyper-V host and guest VMs.

**28. B** - Hyper-V's deep integration with Windows provides extensive audit trails through Event Logs and PowerShell.

**29. A** - `.vmrs` files contain Hyper-V runtime state information.

**30. B** - `Save-VM` cmdlet or `Export-VM` with CaptureSavedState option captures VM memory state.

### Section 4: Network Traffic Analysis

**31. B** - Virtual switch-level capture provides complete visibility into all VM traffic including inter-VM communications.

**32. B** - `ip.addr == 192.168.1.50` is the correct Wireshark filter for all traffic to/from an IP address.

**33. B** - Beaconing refers to regular, periodic communications typical of malware command-and-control channels.

**34. C** - NetFlow provides traffic metadata (who, what, when, how much) with much lower storage requirements than full packet capture.

**35. B** - Wireshark's File → Export Objects → HTTP feature extracts files transferred via HTTP.

**36. B** - Large outbound transfers to external or unusual destinations are primary indicators of data exfiltration.

**37. B** - Even with encryption, metadata (IPs, ports, timing, volume) provides valuable forensic information.

**38. B** - `pktcap-uw` is VMware's hypervisor-level packet capture utility.

**39. B** - DNS tunneling encodes data within DNS queries/responses to exfiltrate data or establish covert channels.

**40. B** - Timeline reconstruction correlates events across multiple sources to understand the complete sequence of activities.

### Section 5: Memory Forensics

**41. A** - `.vmem` is the VMware memory snapshot file extension.

**42. D** - Both `netscan` and `connections`/`connscan` plugins can display network connections (depends on OS version).

**43. B** - First identify the correct OS profile using `imageinfo` or `kdbgscan`.

**44. B** - Active connections, encryption keys, cached credentials, and running process network activity exist in memory but not on disk.

**45. B** - Live acquisition allows evidence collection without disrupting operations.

**46. B** - Process lists can be correlated with network connections to identify which processes made network connections.

**47. B** - Network connections without associated visible processes or hidden processes may indicate rootkits.

**48. B** - Memory is volatile and represents only the state at acquisition time.

**49. B** - WinPmem and DumpIt are designed for live Windows memory acquisition.

**50. B** - Windows registry in memory contains network history, WiFi passwords, adapter configurations, and network locations.

### Section 6: Attack Detection

**51. B** - VM escape means breaking out of VM isolation to access the underlying hypervisor or host system.

**52. B** - Sequential authentication across multiple VMs with similar credentials indicates lateral movement.

**53. B** - Port scanning and systematic connection attempts to multiple hosts indicate reconnaissance activity.

**54. A** - VM sprawl is uncontrolled growth of VMs creating security and management challenges.

**55. B** - Attackers often move data to VMs with external access before exfiltration.

**56. B** - VMs accessing hypervisor management interfaces or unusual inter-VM traffic patterns are suspicious.

**57. B** - Duplicate MAC addresses could indicate spoofing or malicious VM cloning.

**58. B** - Using legitimate tools for malicious purposes is called "living off the land" (LOTL).

**59. B** - Snapshots can hide activities by reverting or create hidden data copies.

**60. B** - Regular, periodic connections to C2 servers with similar timing patterns indicate botnet activity.

### Section 7: Reporting and Best Practices

**61. B** - Chain of custody documents evidence handling to maintain integrity for legal proceedings.

**62. B** - Never work on original evidence; always use forensic copies to preserve the original.

**63. B** - Methodology should document tools, data sources, procedures, and any limitations.

**64. B** - Cryptographic hashes verify evidence integrity and detect modifications.

**65. B** - SHA-256 or SHA-512 are currently recommended (MD5 is considered cryptographically broken).

**66. C** - Document out-of-scope evidence and notify appropriate parties per organizational policy.

**67. B** - Network diagrams visually document the environment and help explain complex relationships.

**68. B** - Document comprehensive acquisition details including date/time, person, tools, hashes, and storage.

**69. B** - Present all evidence objectively and explain any conflicts without bias.

**70. B** - Retention follows organizational policy, legal requirements, and litigation holds.

### Section 8: Practical Application

**71. B** - Document the configuration, investigate when it was added, and analyze associated activity.

**72. B** - Log gaps require investigation as they may indicate tampering, deletion, or system issues.

**73. B** - Proper order: hash original files, create forensic copy, work on copy.

**74. B** - Analyze patterns, check threat intelligence, correlate with other evidence sources.

**75. B** - Check snapshots, logs, backups, and network logs for information about the deleted VM.

**76. B** - Multiple administrative connections in short timeframe suggests lateral movement or attack propagation.

**77. B** - Perform live acquisition and monitoring with minimal impact to preserve evidence while maintaining operations.

**78. B** - Investigate which VM was connected, what happened during that time, and who made the change.

**79. B** - Check memory, temp directories, network shares, and other VMs for staging locations.

**80. B** - Develop comprehensive investigation plan for all affected systems to identify common attack vectors and initial compromise.
