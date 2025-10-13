Section 1: Fundamentals (Questions 1-5)

**Question 1:** What makes container forensics different from traditional digital forensics?
- A) Containers use different operating systems
- B) Containers are ephemeral and share the host kernel
- C) Containers don't generate logs
- D) Containers can't be analyzed remotely

**Question 2:** Where are Docker container logs typically stored by default?
- A) `/var/log/docker/`
- B) `/var/lib/docker/containers/[CONTAINER_ID]/[CONTAINER_ID]-json.log`
- C) `/etc/docker/logs/`
- D) Inside the container at `/var/log/`

**Question 3:** Which Docker command would you use to capture the current state of a running container as a new image?
- A) `docker save`
- B) `docker export`
- C) `docker commit`
- D) `docker snapshot`

**Question 4:** What is the primary purpose of Kubernetes audit logs?
- A) Monitor container resource usage
- B) Record all API server requests and user actions
- C) Store application error logs
- D) Track network traffic between pods

**Question 5:** Which Linux feature allows containers to have isolated network stacks?
- A) cgroups
- B) SELinux
- C) Network namespaces
- D) iptables

### Section 2: Evidence Collection (Questions 6-10)

**Question 6:** You need to capture network traffic from a specific running Docker container. What is the most direct method?
- A) Use tcpdump on the host's main interface
- B) Use tcpdump on the docker0 bridge
- C) Use nsenter to enter the container's network namespace and run tcpdump
- D) Install tcpdump inside the container first

**Question 7:** What does the `docker diff` command show?
- A) Differences between two containers
- B) Changes to a container's filesystem compared to its image
- C) Differences between image layers
- D) Network traffic differences

**Question 8:** When collecting evidence from a Kubernetes pod, which command extracts logs from all containers within the pod?
- A) `kubectl logs [POD_NAME]`
- B) `kubectl logs [POD_NAME] --all-containers=true`
- C) `kubectl get logs [POD_NAME]`
- D) `kubectl describe pod [POD_NAME]`

**Question 9:** What type of data is stored in Docker's `/var/lib/docker/overlay2/` directory?
- A) Container logs only
- B) Docker daemon configuration
- C) Container filesystem layers
- D) Network configuration files

**Question 10:** In a forensic investigation, why is it important to capture container metadata using `docker inspect`?
- A) It provides the container's IP address only
- B) It documents configuration, environment variables, volumes, and network settings
- C) It only shows the container's running status
- D) It replaces the need for log collection

### Section 3: Analysis Techniques (Questions 11-15)

**Question 11:** When analyzing Docker container logs in JSON format, which tool is most effective for parsing and filtering?
- A) grep
- B) awk
- C) jq
- D) sed

**Question 12:** What forensic evidence can be found in a container's `/proc/[PID]/` directory?
- A) Only the process ID
- B) Command line arguments, environment variables, and file descriptors
- C) Container logs
- D) Network packets

**Question 13:** In a layered Docker filesystem, where are container-specific modifications stored?
- A) In the base image layers
- B) In the upper (read-write) layer
- C) In Docker volumes only
- D) In the Docker daemon memory

**Question 14:** What Wireshark filter would help identify potential data exfiltration through DNS tunneling?
- A) `http.request`
- B) `dns and dns.qry.name contains "unusual"`
- C) `tcp.port == 53`
- D) `dns and (dns.qry.name.len > 50 or dns.resp.len > 512)`

**Question 15:** What is the primary purpose of analyzing etcd in Kubernetes forensics?
- A) Monitor pod network traffic
- B) Retrieve cluster state, configurations, and secrets
- C) Analyze container logs
- D) Track node resource usage

### Section 4: Advanced Topics (Questions 16-20)

**Question 17:** In Kubernetes API audit logs, which event would indicate a potential privilege escalation attempt?
- A) A user creating a new pod
- B) A user requesting `escalate` or `impersonate` verbs on RBAC resources
- C) A pod being deleted
- D) A service being exposed

**Question 18:** What is the forensic significance of Docker Content Trust?
- A) It encrypts container data
- B) It provides image signature verification for supply chain security
- C) It manages container secrets
- D) It controls network access

**Question 19:** When investigating a container breach, you find evidence in memory but not on disk. What is the most likely explanation?
- A) The container logs were corrupted
- B) A fileless malware attack or in-memory exploitation occurred
- C) The container was never compromised
- D) Docker deleted the evidence automatically

**Question 20:** Which of the following is NOT a recommended practice for forensic preparedness in containerized environments?
- A) Implementing centralized log aggregation
- B) Disabling all container logging to improve performance
- C) Creating forensic tool containers for rapid deployment
- D) Enabling Kubernetes API audit logging

### Section 5: Scenario-Based Questions (Questions 21-25)

**Question 21:** Scenario: You're investigating a suspected container breach. The container is still running. What should be your FIRST action?
- A) Immediately stop the container
- B) Delete the container to prevent further damage
- C) Capture volatile data (memory, running processes, network connections)
- D) Review container logs only

**Question 22:** Scenario: A Kubernetes pod was used in an attack but has since been terminated. Where might you still find evidence?
- A) Nowhere—all evidence is lost
- B) Node-level container runtime artifacts, centralized logs, and API audit logs
- C) Only in other running pods
- D) In the pod's memory

**Question 23:** Scenario: You observe encrypted network traffic from a container to an unknown external IP. What analysis steps should you take?
- A) Ignore it—encrypted traffic can't be analyzed
- B) Analyze connection frequency, data volumes, DNS queries, and check threat intelligence
- C) Immediately block all container network access
- D) Only review container logs

**Question 24:** Scenario: You find a container running with `--privileged` flag and `hostPath` volume mounts to sensitive directories. What security implication does this have?
- A) This is normal container configuration
- B) The container has extensive host access and could be used for container escape
- C) This only affects container performance
- D) The container is more secure

**Question 25:** Scenario: During timeline analysis, you find that a container was created, a suspicious process ran for 2 minutes, then the container was deleted. What additional evidence sources should you examine?
- A) Only the deleted container's logs
- B) Docker daemon logs, host system logs, network traffic captures, and parent image
- C) Nothing—evidence is completely gone
- D) Only the container's IP address