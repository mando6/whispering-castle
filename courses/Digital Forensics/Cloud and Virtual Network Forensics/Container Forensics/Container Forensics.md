## Course Overview

**Duration:** 8-10 hours  
**Level:** Intermediate to Advanced  
**Prerequisites:** Basic understanding of Linux, networking, and digital forensics principles

### Learning Objectives

By the end of this course, you will be able to:
- Understand container architecture and its implications for forensic investigations
- Identify and preserve container evidence effectively
- Analyze Docker and Kubernetes environments for security incidents
- Extract and interpret network traffic from containerized applications
- Investigate container state, logs, and runtime artifacts
- Apply forensic methodologies specific to ephemeral container environments

---

## Module 1: Introduction to Container Forensics

### 1.1 What is Container Forensics?

Container forensics is a specialized branch of digital forensics focused on investigating security incidents, breaches, and malicious activities within containerized environments. Unlike traditional forensics, container forensics deals with ephemeral, lightweight, and highly dynamic systems that present unique challenges.

**Connection to Digital Forensics:** Container forensics extends traditional digital forensics principles (preservation, acquisition, analysis, and reporting) to cloud-native and containerized infrastructures. The fundamental goal remains the same: to identify, preserve, and analyze digital evidence in a forensically sound manner.

### 1.2 Container Technology Overview

**Docker Architecture:**
- **Images:** Read-only templates containing application code, libraries, and dependencies
- **Containers:** Runtime instances of images with an isolated user space
- **Layers:** Union file system layers that compose images
- **Volumes:** Persistent data storage mechanisms
- **Networks:** Virtual networks connecting containers

**Kubernetes Architecture:**
- **Pods:** Smallest deployable units containing one or more containers
- **Nodes:** Worker machines running containerized applications
- **Services:** Abstractions defining logical sets of pods
- **Deployments:** Declarative updates for pods and replica sets
- **Control Plane:** Master components managing cluster state

**Why Container Forensics is Different:**
- **Ephemeral Nature:** Containers are designed to be short-lived and disposable
- **Layered File Systems:** Multiple overlay layers complicate file analysis
- **Shared Kernel:** Multiple containers share the host OS kernel
- **Orchestration Complexity:** Kubernetes adds layers of abstraction
- **Dynamic Networking:** Software-defined networks create complex traffic patterns

---

## Module 2: Container Evidence Sources

### 2.1 Docker Evidence Sources

**Container Layer Artifacts:**
- **Location:** `/var/lib/docker/overlay2/` or `/var/lib/docker/aufs/`
- **Contains:** Container file system layers, both running and stopped
- **Forensic Value:** Application files, configuration, temporary data

**Container Metadata:**
- **Location:** `/var/lib/docker/containers/[CONTAINER_ID]/`
- **Files:** `config.v2.json`, `hostconfig.json`
- **Contains:** Container configuration, environment variables, command history

**Docker Logs:**
- **Location:** `/var/lib/docker/containers/[CONTAINER_ID]/[CONTAINER_ID]-json.log`
- **Contains:** stdout/stderr output from containerized applications
- **Format:** JSON lines with timestamps

**Image Layers:**
- **Location:** `/var/lib/docker/image/overlay2/`
- **Contains:** Image metadata, layer chain information
- **Forensic Value:** Baseline for detecting modifications

**Docker Daemon Logs:**
- **Location:** `/var/log/docker.log` or systemd journal
- **Contains:** Docker engine operations, API calls, errors

### 2.2 Kubernetes Evidence Sources

**Pod Specifications and Logs:**
- Retrieved via `kubectl` commands or API
- Contains pod definitions, resource allocations, environment variables
- Log aggregation through centralized logging systems

**etcd Data Store:**
- Kubernetes' distributed key-value store
- Contains cluster state, configurations, secrets
- **Location:** Typically `/var/lib/etcd/`

**Node-Level Artifacts:**
- **Kubelet Logs:** `/var/log/pods/` and systemd journal
- **Container Runtime Logs:** Similar to Docker artifacts
- **Network Configuration:** CNI plugin configurations

**API Server Audit Logs:**
- Records all requests to Kubernetes API
- Critical for understanding cluster-level activities
- **Location:** Configured in API server (often `/var/log/kube-apiserver-audit.log`)

### 2.3 Network Evidence

**Container Network Namespaces:**
- Each container has isolated network stack
- **Investigation Tools:** `nsenter`, `ip netns`

**Virtual Network Interfaces:**
- `veth` pairs connecting containers to bridges
- Examine with `ip link` and `tcpdump`

**Overlay Networks:**
- Docker networks: bridge, host, overlay, macvlan
- Kubernetes CNI plugins: Calico, Flannel, Weave

---

## Module 3: Evidence Acquisition and Preservation

### 3.1 Live Container Acquisition

**Principles:**
1. Minimize impact on running containers
2. Prioritize volatile data collection
3. Document all actions taken

**Docker Live Acquisition Commands:**

```bash
# Capture container metadata
docker inspect [CONTAINER_ID] > container_metadata.json

# Export container filesystem
docker export [CONTAINER_ID] -o container_export.tar

# Commit running container to image
docker commit [CONTAINER_ID] evidence-image:tag

# Copy specific files
docker cp [CONTAINER_ID]:/path/to/file ./evidence/

# Capture container logs
docker logs [CONTAINER_ID] > container_logs.txt

# View running processes
docker top [CONTAINER_ID]

# Monitor resource usage
docker stats [CONTAINER_ID] --no-stream
```

**Kubernetes Live Acquisition Commands:**

```bash
# Get pod details
kubectl get pod [POD_NAME] -n [NAMESPACE] -o yaml > pod_spec.yaml

# Extract pod logs
kubectl logs [POD_NAME] -n [NAMESPACE] --all-containers=true > pod_logs.txt

# Copy files from pod
kubectl cp [NAMESPACE]/[POD_NAME]:/path/to/file ./evidence/

# Execute commands in pod for volatile data
kubectl exec [POD_NAME] -n [NAMESPACE] -- ps aux > processes.txt
kubectl exec [POD_NAME] -n [NAMESPACE] -- netstat -tulpn > network_connections.txt

# Get events
kubectl get events -n [NAMESPACE] --sort-by='.lastTimestamp' > events.log
```

### 3.2 Host-Level Acquisition

**Docker Host Acquisition:**

```bash
# Create forensic image of Docker directory
tar -czf docker_lib_backup.tar.gz /var/lib/docker/

# Copy specific container data
cp -r /var/lib/docker/containers/[CONTAINER_ID] ./evidence/

# Capture Docker daemon information
systemctl status docker > docker_service_status.txt
journalctl -u docker > docker_daemon_logs.txt
```

**Memory Acquisition:**
- Use tools like `LiME` (Linux Memory Extractor) for host memory
- Container memory can be analyzed through host memory dumps
- Process memory within containers accessible via `/proc/[PID]/`

### 3.3 Network Traffic Capture

**Capturing Container Network Traffic:**

```bash
# Identify container's network namespace
docker inspect -f '{{.State.Pid}}' [CONTAINER_ID]

# Enter network namespace and capture traffic
nsenter -t [PID] -n tcpdump -i eth0 -w container_traffic.pcap

# Alternative: Capture on host bridge
tcpdump -i docker0 -w docker_bridge_traffic.pcap

# Kubernetes pod traffic capture
kubectl exec [POD_NAME] -n [NAMESPACE] -- tcpdump -i any -w - > pod_traffic.pcap
```

**Connection to Main Topic:** Proper evidence acquisition is fundamental to container forensics. The ephemeral nature of containers means evidence can disappear when containers restart or terminate. Understanding both live and post-mortem acquisition techniques ensures forensic investigators can capture critical evidence before it's lost.

---

## Module 4: Analyzing Container State and Runtime

### 4.1 Container Process Analysis

**Understanding Container Processes:**

Containers use Linux namespaces (PID, NET, MNT, UTS, IPC, USER) to isolate processes. From the host perspective, container processes are visible but appear isolated within the container.

**Analysis Techniques:**

```bash
# View processes from host
ps auxf | grep [CONTAINER_ID]

# View process tree within container
docker exec [CONTAINER_ID] ps auxf

# Examine process details
docker exec [CONTAINER_ID] cat /proc/[PID]/cmdline
docker exec [CONTAINER_ID] cat /proc/[PID]/environ

# Check for suspicious processes
docker exec [CONTAINER_ID] lsof -p [PID]
```

**Key Indicators:**
- Unexpected processes running
- Processes running as root when they shouldn't
- Unusual parent-child process relationships
- High resource consumption

### 4.2 File System Analysis

**Docker Layered File System:**

Container file systems use union mounts (OverlayFS, AUFS) where:
- Lower layers are read-only (from image)
- Upper layer is read-write (container modifications)
- Merged view presented to container

**Analysis Commands:**

```bash
# Examine container file system layers
docker inspect -f '{{.GraphDriver.Data}}' [CONTAINER_ID]

# Access merged filesystem
ls -la /var/lib/docker/overlay2/[LAYER_ID]/merged/

# Check container modifications (diff)
docker diff [CONTAINER_ID]

# Export and analyze filesystem
docker export [CONTAINER_ID] | tar -C ./analysis/ -xvf -
```

**Timeline Analysis:**

```bash
# Find recently modified files
find /var/lib/docker/overlay2/[LAYER_ID]/diff -type f -mtime -1

# Generate timeline with mactime (Sleuth Kit)
fls -r -m / /var/lib/docker/overlay2/[LAYER_ID]/merged > bodyfile
mactime -b bodyfile -d > timeline.csv
```

### 4.3 Container Configuration Analysis

**Docker Configuration Files:**

`config.v2.json` contains:
- Container creation timestamp
- Image SHA256 hash
- Environment variables (may contain secrets!)
- Mounted volumes
- Network settings
- Command and entrypoint

**Analysis Checklist:**
- [ ] Review environment variables for hardcoded credentials
- [ ] Check volume mounts for sensitive data exposure
- [ ] Examine network mode (host mode is less isolated)
- [ ] Verify user context (running as root?)
- [ ] Review security options (privileged mode, capabilities)

**Example Analysis:**

```bash
# Parse config with jq
cat config.v2.json | jq '.Config.Env'
cat config.v2.json | jq '.HostConfig.Privileged'
cat config.v2.json | jq '.NetworkSettings'
```

### 4.4 Container Log Analysis

**Log Locations and Formats:**

Docker logs are JSON-formatted by default:
```json
{"log":"Application started\n","stream":"stdout","time":"2025-10-09T10:30:00.123456789Z"}
```

**Analysis Techniques:**

```bash
# Parse logs with jq
cat [CONTAINER_ID]-json.log | jq -r '.log'

# Filter by time range
cat [CONTAINER_ID]-json.log | jq -r 'select(.time >= "2025-10-09T10:00:00")'

# Search for suspicious patterns
grep -E "(error|exception|failed|unauthorized)" [CONTAINER_ID]-json.log

# Analyze HTTP access logs
cat [CONTAINER_ID]-json.log | grep "HTTP" | awk '{print $9}' | sort | uniq -c
```

**Kubernetes Logging:**

Kubernetes aggregates logs from multiple sources:
- Use centralized logging solutions (ELK, Splunk, Loki)
- Query aggregated logs for correlation across pods
- Check for log gaps indicating tampering or deletion

**Connection to Main Topic:** Container state analysis reveals what happened during a security incident. By examining processes, file systems, configurations, and logs, forensic investigators can reconstruct attacker activities, identify compromised containers, and understand the scope of an incident.

---

## Module 5: Network Traffic Analysis in Containerized Environments

### 5.1 Container Network Architecture

**Docker Network Types:**

1. **Bridge Network (Default):**
   - Containers connected to virtual bridge (`docker0`)
   - NAT for external communication
   - Internal IP range (typically 172.17.0.0/16)

2. **Host Network:**
   - Container shares host's network namespace
   - No network isolation
   - Direct access to host interfaces

3. **Overlay Network:**
   - Multi-host networking for Docker Swarm
   - VXLAN encapsulation
   - Distributed routing

4. **Macvlan:**
   - Container gets own MAC address
   - Appears as physical device on network

**Kubernetes Networking:**

- **Pod-to-Pod:** All pods can communicate without NAT
- **CNI Plugins:** Implement network policies (Calico, Flannel, Weave, Cilium)
- **Services:** Provide stable endpoints with load balancing
- **Ingress:** Manages external HTTP/HTTPS access

### 5.2 Traffic Capture Strategies

**Strategy 1: Host-Level Capture**

```bash
# Capture all Docker bridge traffic
tcpdump -i docker0 -w all_containers.pcap

# Capture specific container IP
tcpdump -i docker0 host 172.17.0.5 -w container_traffic.pcap

# Kubernetes node capture
tcpdump -i [NODE_INTERFACE] -w node_traffic.pcap
```

**Strategy 2: Namespace-Level Capture**

```bash
# Find container PID
CPID=$(docker inspect -f '{{.State.Pid}}' [CONTAINER_ID])

# Enter network namespace and capture
nsenter -t $CPID -n tcpdump -i eth0 -w container_internal.pcap
```

**Strategy 3: Service Mesh Inspection**

Service meshes (Istio, Linkerd) provide:
- Automatic traffic encryption (mTLS)
- Detailed telemetry
- Traffic logs and traces

Access via:
- Prometheus metrics
- Jaeger traces
- Envoy access logs

### 5.3 Traffic Analysis Techniques

**Wireshark Analysis:**

1. **Identify Container Traffic:**
   - Filter by container IP ranges
   - Look for specific ports (80, 443, 3306, 5432, etc.)

2. **Protocol Analysis:**
   - Analyze HTTP/HTTPS requests
   - Examine database queries
   - Check for unencrypted credentials

3. **Anomaly Detection:**
   - Unusual outbound connections
   - Data exfiltration patterns
   - Port scanning activities
   - C2 communication beacons

**Common Wireshark Filters:**

```
# Filter by container IP
ip.addr == 172.17.0.5

# HTTP traffic
http

# DNS queries (potential data exfiltration)
dns

# Large data transfers
tcp.len > 1000

# Failed connections
tcp.flags.reset == 1

# Unusual ports
tcp.port > 10000
```

**Traffic Pattern Analysis:**

```bash
# Extract HTTP hosts
tshark -r container_traffic.pcap -Y http.request -T fields -e http.host | sort | uniq -c

# DNS queries
tshark -r container_traffic.pcap -Y dns.qry.name -T fields -e dns.qry.name | sort | uniq

# Connection frequency (potential C2 beacons)
tshark -r container_traffic.pcap -T fields -e frame.time -e ip.dst | awk '{print $2}' | sort | uniq -c | sort -rn
```

### 5.4 Kubernetes Network Policy Analysis

**Network Policy Forensics:**

```bash
# Get all network policies
kubectl get networkpolicies --all-namespaces -o yaml > network_policies.yaml

# Check policy applied to pod
kubectl describe pod [POD_NAME] -n [NAMESPACE] | grep -A 10 "Network Policy"

# Audit policy violations in CNI logs
# (Varies by CNI plugin - example for Calico)
kubectl logs -n kube-system -l k8s-app=calico-node
```

**Analyzing Network Flows:**

Tools like Hubble (Cilium) or Calico's flow logs provide:
- Source and destination pods
- Allowed/denied connections
- Protocol and port information
- Network policy verdicts

**Connection to Main Topic:** Network traffic analysis in containerized environments is essential for understanding lateral movement, data exfiltration, and command-and-control communications during security incidents. The virtualized and encapsulated nature of container networks requires specialized capture and analysis techniques.

---

## Module 6: Advanced Container Forensics

### 6.1 Image Forensics and Supply Chain Analysis

**Image Layer Analysis:**

```bash
# Inspect image layers
docker history [IMAGE_NAME]

# Export image for analysis
docker save [IMAGE_NAME] -o image.tar
tar -xvf image.tar

# Analyze each layer
for layer in */layer.tar; do
    echo "Analyzing $layer"
    tar -tvf "$layer" | grep -E "(sh|bash|python|perl)"
done
```

**Vulnerability and Malware Scanning:**

```bash
# Using Trivy
trivy image [IMAGE_NAME]

# Using Clair
clair-scanner [IMAGE_NAME]

# Using Grype
grype [IMAGE_NAME]
```

**Supply Chain Verification:**

- Check image signatures (Docker Content Trust, Notary)
- Verify base image provenance
- Review Dockerfile for suspicious commands
- Analyze build history for unauthorized changes

### 6.2 Memory Forensics for Containers

**Container Memory Analysis:**

```bash
# Dump container memory via host
CPID=$(docker inspect -f '{{.State.Pid}}' [CONTAINER_ID])
gcore -o container_memory $CPID

# Analyze with Volatility
volatility -f container_memory.[PID] linux_pslist
volatility -f container_memory.[PID] linux_netstat
volatility -f container_memory.[PID] linux_bash
```

**Memory-Resident Artifacts:**
- Injected code or libraries
- Decrypted credentials
- Command history
- Network connections
- Running threads and handles

### 6.3 Kubernetes Forensics

**API Server Audit Log Analysis:**

Audit logs record:
- User actions (kubectl commands)
- System component activities
- Failed authentication attempts
- RBAC policy evaluations

**Example Analysis:**

```bash
# Find privilege escalation attempts
grep "escalate" kube-apiserver-audit.log

# Identify failed auth attempts
grep "Forbidden" kube-apiserver-audit.log | grep "401"

# Track secret access
grep "secrets" kube-apiserver-audit.log | jq '.requestURI'

# Find suspicious pod creation
grep "pods" kube-apiserver-audit.log | grep "create" | jq '.user.username'
```

**etcd Forensics:**

```bash
# Backup etcd (requires etcdctl)
ETCDCTL_API=3 etcdctl snapshot save etcd_backup.db

# Query specific keys
ETCDCTL_API=3 etcdctl get /registry/secrets/default/[SECRET_NAME]

# List all pods
ETCDCTL_API=3 etcdctl get /registry/pods --prefix --keys-only
```

### 6.4 Incident Reconstruction

**Timeline Development:**

1. **Gather timestamps from all sources:**
   - Container creation/start/stop times
   - Log entries
   - File modification times
   - Network connection times
   - Kubernetes events

2. **Correlate across layers:**
   - Host OS events
   - Container runtime events
   - Application logs
   - Network traffic

3. **Build narrative:**
   - Initial access vector
   - Lateral movement
   - Privilege escalation
   - Data exfiltration
   - Persistence mechanisms

**Example Timeline Construction:**

```bash
# Combine multiple sources
cat docker_events.log | awk '{print $1,$2,$3,$4}' > timeline.txt
cat container_logs.txt | jq -r '.time + " " + .log' >> timeline.txt
cat kube_events.log | jq -r '.lastTimestamp + " " + .message' >> timeline.txt

# Sort chronologically
sort -k1,2 timeline.txt > sorted_timeline.txt
```

---

## Module 7: Container Security Best Practices and Forensic Preparedness

### 7.1 Logging and Monitoring Configuration

**Essential Logging:**

1. **Container Runtime Logs:**
   - Enable Docker daemon debug logging
   - Configure log rotation to prevent loss
   - Use centralized log aggregation

2. **Application Logs:**
   - Implement structured logging (JSON)
   - Include correlation IDs
   - Log security-relevant events

3. **Kubernetes Audit Logging:**
   - Enable API server audit logging
   - Configure appropriate audit policy
   - Send to secure, immutable storage

**Example Audit Policy:**

```yaml
apiVersion: audit.k8s.io/v1
kind: Policy
rules:
  - level: RequestResponse
    verbs: ["create", "update", "patch", "delete"]
  - level: Metadata
    resources:
      - group: ""
        resources: ["secrets", "configmaps"]
  - level: Request
    verbs: ["get", "list", "watch"]
```

### 7.2 Evidence Preservation Strategies

**Immutable Infrastructure:**
- Treat containers as immutable
- Preserve images used in incidents
- Store in secure image registry

**Persistent Volume Management:**
- Use persistent volumes for critical data
- Regular backups of persistent storage
- Implement volume snapshots

**Log Retention:**
- Define retention policies (90+ days recommended)
- Store logs externally from containers
- Ensure tamper-evident storage (WORM)

### 7.3 Incident Response Preparation

**Pre-Incident Preparation:**

1. **Baseline Normal Behavior:**
   - Document normal network flows
   - Catalog authorized images
   - Map service dependencies

2. **Forensic Tool Preparation:**
   - Pre-stage forensic containers/pods
   - Prepare jump boxes with tools installed
   - Test acquisition procedures

3. **Runbook Development:**
   - Document container acquisition procedures
   - Define escalation paths
   - Establish communication protocols

**Forensic Container Example:**

```dockerfile
FROM ubuntu:22.04
RUN apt-get update && apt-get install -y \
    tcpdump \
    net-tools \
    iproute2 \
    strace \
    lsof \
    volatility \
    sleuthkit \
    && rm -rf /var/lib/apt/lists/*
ENTRYPOINT ["/bin/bash"]
```

**Connection to Main Topic:** Forensic preparedness ensures that when incidents occur, investigators have the necessary logs, tools, and procedures to effectively conduct container forensics. Proper logging and monitoring configuration creates the evidence base needed for successful investigations.

---

## Module 8: Tools and Resources

### 8.1 Essential Forensic Tools

**Container-Specific Tools:**

1. **Docker Forensics Tools:**
   - `docker-forensics-toolkit`: Automated evidence collection
   - `container-diff`: Compare container images
   - `dive`: Explore Docker image layers

2. **Kubernetes Tools:**
   - `kubectl`: Primary CLI tool
   - `stern`: Multi-pod log tailing
   - `k9s`: Terminal UI for Kubernetes
   - `Popeye`: Cluster sanitizer

3. **Network Analysis:**
   - `Wireshark/tshark`: Packet analysis
   - `Zeek (Bro)`: Network security monitor
   - `Suricata`: IDS/IPS for containers

4. **Memory Forensics:**
   - `Volatility`: Memory analysis framework
   - `LiME`: Linux Memory Extractor
   - `gcore`: GNU core dumper

5. **File System Analysis:**
   - `Sleuth Kit`: File system forensics
   - `Autopsy`: Digital forensics platform
   - `binwalk`: Firmware analysis

### 8.2 Commercial Platforms

- **Sysdig**: Container security and forensics
- **Aqua Security**: Container security platform
- **Falco**: Runtime security with forensic capabilities
- **Prisma Cloud (Palo Alto)**: Cloud-native security

### 8.3 Open Source Projects

- **CRI-O**: Container runtime with built-in logging
- **Cilium**: Network observability for Kubernetes
- **Prometheus + Grafana**: Metrics and monitoring
- **ELK Stack**: Elasticsearch, Logstash, Kibana for log analysis


---

## Course Completion

You have gained comprehensive knowledge in:
- Container architecture and forensic challenges
- Evidence identification and acquisition in Docker and Kubernetes
- Network traffic analysis in containerized environments
- Advanced forensic techniques including memory analysis and timeline reconstruction
- Security best practices and forensic preparedness

**Next Steps:**
1. Practice hands-on with Docker and Kubernetes environments
2. Set up a forensic lab with vulnerable containers
3. Explore specialized tools like Sysdig and Falco
4. Pursue relevant certifications (CKS, SANS SEC541)
5. Stay updated with container security research and techniques

**Additional Resources:**
- Join container security communities (CNCF, Docker forums)
- Participate in CTF challenges focused on container security
- Follow container security researchers on social media and blogs
- Contribute to open-source forensic tools