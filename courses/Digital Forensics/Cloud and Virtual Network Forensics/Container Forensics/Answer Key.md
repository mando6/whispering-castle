**Question 1:** B) Containers are ephemeral and share the host kernel

Explanation: Container forensics differs due to the ephemeral nature of containers (they're designed to be short-lived), the shared kernel architecture, layered file systems, and dynamic orchestration—all of which create unique forensic challenges compared to traditional systems.

-----

**Question 2:** 
B) `/var/lib/docker/containers/[CONTAINER_ID]/[CONTAINER_ID]-json.log`

Explanation: Docker stores container logs in JSON format within the container's directory under `/var/lib/docker/containers/`. Each container has its own subdirectory identified by the container ID.

----

**Question 3:** C) `docker commit`

Explanation: `docker commit` creates a new image from a container's changes, preserving the current state. `docker save` exports an image to tar, `docker export` flattens a container's filesystem, and `docker snapshot` doesn't exist.

---

**Question 4:** B) Record all API server requests and user actions

Explanation: Kubernetes audit logs record all requests made to the API server, including user actions, system component activities, authentication attempts, and RBAC policy evaluations, making them crucial for forensic investigations.

---

**Question 5:** **C) Network namespaces**

Explanation: Network namespaces provide each container with its own isolated network stack, including interfaces, routing tables, and firewall rules. cgroups control resources, SELinux provides MAC, and iptables manages packet filtering.

---

**Question 6:** **C) Use nsenter to enter the container's network namespace and run tcpdump**

Explanation: Using `nsenter` to enter the container's specific network namespace provides the most accurate capture of that container's traffic without interference from other containers or host traffic.

----

**Question 7:** **B) Changes to a container's filesystem compared to its image**

Explanation: `docker diff` displays files and directories that have been added (A), deleted (D), or changed (C) in a container's filesystem relative to its base image, which is valuable for identifying malicious modifications.

----

**Question 8:** **B) `kubectl logs [POD_NAME] --all-containers=true`**

Explanation: The `--all-containers=true` flag ensures logs are collected from all containers in a multi-container pod, which is essential for complete evidence collection.

---

**Question 9:** **C) Container filesystem layers**

Explanation: The overlay2 directory contains the layered filesystem used by Docker containers, including both image layers and container modifications. This is a critical evidence source for file-based forensics.

----

**Question 10:** **B) It documents configuration, environment variables, volumes, and network settings**

Explanation: `docker inspect` provides comprehensive metadata including creation time, image hash, environment variables (which may contain credentials), mounted volumes, network configuration, and security settings—all critical for understanding the container's context during an incident.

----

**Question 11:** **C) jq**

Explanation: jq is specifically designed for parsing and manipulating JSON data, making it ideal for Docker's JSON-formatted logs. While grep, awk, and sed can work with text, jq provides structured JSON querying capabilities.

----

**Question 12:** **B) Command line arguments, environment variables, and file descriptors**

Explanation: The `/proc/[PID]/` directory contains valuable forensic data including cmdline (command arguments), environ (environment variables), fd/ (file descriptors), and other process-specific information useful for reconstructing attacker actions.

----

**Question 13:** **B) In the upper (read-write) layer**

Explanation: Docker uses union filesystem (OverlayFS/AUFS) where base image layers are read-only and all container modifications are written to the upper read-write layer, making this layer crucial for identifying changes made during an incident.

-----

**Question 14:** D) `dns and (dns.qry.name.len > 50 or dns.resp.len > 512)`****

Explanation: DNS tunneling often uses unusually long query names or large response packets to exfiltrate data. Filtering for DNS queries/responses exceeding normal sizes helps identify this technique.

----

**Question 15:** **B) Retrieve cluster state, configurations, and secrets**

Explanation: etcd is Kubernetes' distributed key-value store containing all cluster state information, including pod specifications, secrets, config maps, and service definitions—essential for understanding the cluster's configuration during an incident.

----

**Question 16:** **B) Monitoring CPU/GPU usage and checking for unexpected processes**

Explanation: Cryptominers typically consume high CPU or GPU resources. Combining resource monitoring (docker stats) with process analysis (docker top, ps) helps identify mining processes, especially those with suspicious names or high resource consumption.

----

**Question 17:** **B) A user requesting `escalate` or `impersonate` verbs on RBAC resources**

Explanation: API audit logs showing requests for RBAC escalate or impersonate permissions indicate potential privilege escalation attempts, as these verbs allow users to gain higher privileges or act as other users/service accounts.

----

**Question 18:** **B) It provides image signature verification for supply chain security**

Explanation: Docker Content Trust uses digital signatures to verify image authenticity and integrity, helping forensic investigators determine if images were tampered with or if unauthorized images were used during an incident.

-----

**Question 19:** **B) A fileless malware attack or in-memory exploitation occurred**

Explanation: Fileless attacks operate entirely in memory without writing to disk, making memory forensics critical. This technique is common in advanced attacks to evade file-based detection and forensics.

------

**Question 20:** **B) Disabling all container logging to improve performance**

Explanation: Disabling logging destroys evidence and prevents effective forensic investigation. While logging has performance impacts, it's essential for security and forensics. Proper log management (rotation, aggregation) addresses performance concerns without sacrificing visibility.

----

**Question 21:** **C) Capture volatile data (memory, running processes, network connections)**

Explanation: Following the Order of Volatility principle, you must capture volatile data first before it's lost. Stopping or deleting the container destroys volatile evidence. Live acquisition of memory, processes, and network state takes priority.

------

**Question 22:** **B) Node-level container runtime artifacts, centralized logs, and API audit logs**

Explanation: Even after pod termination, evidence persists in node-level directories (/var/lib/docker, /var/log/pods), centralized logging systems (if configured), Kubernetes audit logs, and potentially in persistent volumes. Memory and running state are lost, but many artifacts remain.

----

**Question 23:** **B) Analyze connection frequency, data volumes, DNS queries, and check threat intelligence**

Explanation: While payload inspection isn't possible with encrypted traffic, metadata analysis reveals patterns: C2 beaconing (regular intervals), data exfiltration (large uploads), and threat intelligence can identify known malicious IPs. DNS queries may reveal the domain before encryption.

----

**Question 24:** **B) The container has extensive host access and could be used for container escape**

Explanation: Privileged mode disables security protections and grants host capabilities, while hostPath mounts provide direct host filesystem access. Combined, these allow container escape and host compromise—major red flags in forensic investigations.

-----

**Question 25:** **B) Docker daemon logs, host system logs, network traffic captures, and parent image**

Explanation: Docker daemon logs record container lifecycle events, host system logs may capture process activity, network captures show external communications, and the parent image reveals what tools were available. Multiple evidence sources enable reconstruction despite container deletion.


