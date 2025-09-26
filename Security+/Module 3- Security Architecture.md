# Module 3 – Security Architecture  

## 3.1 Cloud Computing  

**NIST SP 800-145 Definition**  
> “Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.”  

---

## 🌩️ Cloud Drivers (Why Cloud Computing?)  
- Scalability  
- Mobility  
- Elasticity  
- Cost-saving  
- Risk transference / reduction  
- Reduced infrastructure  
- Less overhead  
- Pay-as-you-go  
- Shifting capital expenditure → operational expenditure  

---

## 🛠️ Cloud Service Models (What service the provider delivers)  

### 1. Software as a Service (SaaS)  
- Consumer uses the provider’s applications running on cloud infrastructure.  
- Accessible via web browser or app interface.  
- **You manage**: only your data/input & usage.  
- **Provider manages**: everything else.  
- **Examples**: Google Workspace, Salesforce, Dropbox.  

---

### 2. Platform as a Service (PaaS)  
- Consumer deploys applications on cloud infrastructure using provider-supported programming languages, libraries, services, and tools.  
- **You manage**: your applications & data.  
- **Provider manages**: OS, runtime, servers, networking, storage.  
- **Examples**: Google App Engine, Microsoft Azure App Service, Heroku.  

---

### 3. Infrastructure as a Service (IaaS)  
- Provides raw infrastructure: servers, storage, networking.  
- **You manage**: OS, apps, configurations, storage.  
- **Provider manages**: hardware, virtualization, networking.  
- **Examples**: AWS EC2, Azure VM, Google Compute Engine.  

---

## ☁️ Cloud Deployment Models (How & where the cloud is deployed)  

### 1. Public Cloud  
- **Users**: Multi-tenant (shared by many organizations).  
- **Pros**:  
  - Cost-effective (pay-as-you-go)  
  - High scalability & elasticity  
  - No hardware maintenance  
- **Cons**:  
  - Less control over infrastructure  
  - Security & compliance concerns  
- **Examples**: AWS, Azure, GCP  

---

### 2. Private Cloud  
- **Users**: Single-tenant (exclusive use).  
- **Pros**:  
  - More control & customization  
  - Better for compliance & sensitive workloads  
- **Cons**:  
  - Higher cost (must build/manage resources)  
  - Less scalability compared to public cloud  
- **Examples**: VMware Private Cloud, OpenStack  

---

### 3. Hybrid Cloud  
- Combines **public + private** with orchestration between them.  
- **Pros**:  
  - Balance of cost & security  
  - Disaster recovery / backup flexibility  
  - Sensitive data stays private, while scaling apps in public cloud  
- **Cons**:  
  - Complex integration & management  
- **Examples**: AWS Outposts, Azure Stack, Google Anthos  

---

### 4. Community Cloud  
- Infrastructure shared by organizations with common interests (e.g., compliance, mission, security).  
- **Users**: Multiple organizations, usually within the same sector.  
- **Pros**:  
  - Shared cost among community  
  - Tailored for industry needs (healthcare, government, research)  
- **Cons**:  
  - Limited scalability compared to public cloud  
  - Shared resources may raise security concerns  

---

## 🔑 Quick Comparison  

| Aspect              | Service Models (IaaS / PaaS / SaaS) | Deployment Models (Public / Private / Hybrid / Community) |
|---------------------|--------------------------------------|-----------------------------------------------------------|
| **Focus**           | What service is delivered            | Where and how cloud is deployed                           |
| **Defines**         | Level of control & responsibility    | Ownership, accessibility, location                        |
| **Examples**        | SaaS = Gmail, PaaS = Heroku, IaaS = AWS EC2 | Public = AWS, Private = VMware, Hybrid = Azure Stack, Community = Gov Cloud |
| **Question**        | *What am I consuming?*               | *Where is it running, and who shares it?*                 |


## 3.2 Data Security in the Cloud  

### Protecting Data Moving to and Within the Cloud  
- **Encryption protocols**: SSL / TLS / IPSec  

---

### 🔐 CASB (Cloud Access Security Broker)  
A security tool/service that sits between cloud service users and cloud applications to enforce security, compliance, and governance policies.  

**Functions:**  
1. **Visibility**  
   - Shows who is using which cloud apps (approved & shadow IT).  
   - Detects risky or unauthorized usage.  

2. **Compliance**  
   - Ensures compliance with regulations (GDPR, HIPAA, PCI-DSS).  
   - Monitors & reports data handling for audits.  

3. **Data Security**  
   - Protects sensitive data with encryption, tokenization, or DLP (Data Loss Prevention).  
   - Prevents data leaks (e.g., uploading sensitive files to Dropbox).  

4. **Threat Protection**  
   - Detects suspicious activity (account hijacking, malware in cloud apps).  
   - Uses anomaly detection & threat intelligence.  

---

### 🛡️ Protecting Data in the Cloud  
- **Encryption**: Protects confidentiality of data.  
- **DLP (Data Loss Prevention)**: Detects and prevents unauthorized data movement to cloud.  
- **Data Dispersion**: Data is replicated across multiple physical locations → higher availability.  
- **Data Fragmentation**: Splits a dataset into smaller fragments/shards and distributes across many machines.  
- **Cryptoshredding**: Renders encrypted data inaccessible by deleting encryption keys (data remnants are unusable).  

## 3.3 Additional Architectures  

### ⚙️ Infrastructure as Code (IaC)  
Define your infrastructure with code → automated, versioned, repeatable.  

**Key Points:**  
- **Automation**: Faster, consistent deployment.  
- **Consistency**: Same config file = same environment.  
- **Version Control**: Store IaC files in Git.  
- **Scalability**: Easy to replicate infra for dev, test, prod.  
- **Compliance**: Policies embedded in code for auditing.  

**Tools:** Terraform, AWS CloudFormation, Ansible, Puppet, Chef  

---

### ⚡ Serverless Architecture  
Focus only on **functions / code**, provider handles the infrastructure.  

**Key Characteristics:**  
- No server management (abstracted away).  
- Event-driven (triggers: HTTP request, DB update, file upload).  
- Automatic scaling.  
- Pay-per-use (execution time & resources, not idle servers).  
- Short-lived, stateless functions.  

**Relation to Cloud Models:**  
- Often considered an extension of **PaaS**, sometimes called **FaaS**.  
- Difference: In PaaS, you still manage runtime; in Serverless, only code/events.  

**Examples:** AWS Lambda, Azure Functions, Google Cloud Functions  

---

### 🧩 Microservices Architecture  
Instead of one monolithic app, break into many **loosely coupled services**, each responsible for a function.  

**Key Characteristics:**  
- Independent services (develop, deploy, scale separately).  
- Decentralized data (each service may have its own DB).  
- Communicate via APIs (REST, gRPC, message queues).  

**Benefits:** Scalability, flexibility, faster releases, resilience.  
**Challenges:** Complexity, inter-service networking, data consistency, DevOps overhead.  

---

### 🌐 Virtual Local Area Networks (VLANs)  
Logical segmentation of a physical network into **smaller, isolated networks**.  

**Why VLANs?**  
- **Segmentation**: Separate groups (HR, Finance, Students, Guests).  
- **Security**: Prevents unauthorized communication between groups.  
- **Efficiency**: Smaller broadcast domains → less traffic.  
- **Flexibility**: Devices don’t need physical proximity; grouped logically.  

**Key Concepts:** VLAN ID, Access Port, Trunk Port (802.1Q tagging), Inter-VLAN routing.  

---

### 🖧 Software-Defined Networking (SDN)  
Network architecture that separates the **control plane** from the **data plane**.  

**Key Characteristics:**  
1. **Separation of Planes**  
   - Control Plane = decides where traffic goes (brains).  
   - Data Plane = forwards traffic (muscles).  
   - Centralized in a controller, not per-device.  

2. **Centralized Management**  
   - Single SDN controller manages the entire network.  
   - Global view → easier automation, policy enforcement.  

3. **Programmability**  
   - Network defined by software APIs.  
   - Dynamic changes: scale bandwidth, reroute traffic, enforce security.  

4. **Open Standards**  
   - Uses protocols like **OpenFlow** to link controller & devices.  

**Benefits:** Agility, automation, centralized security, cost-effective.  
**Challenges:** Controller as single point of failure, complexity, security risks.  

**Examples:** Cisco ACI, VMware NSX, OpenDaylight, Google B4 WAN  

## On-Premises Architectures  

### 🏢 On-Premises (本地部署)  
Infrastructure hosted in the organization’s own data center, fully owned and managed by the organization (hardware, servers, storage, networking, security).  

---

### 🔑 Key Concepts  

#### 1. Centralization vs Decentralization  
- **Centralization**:  
  - Resources and infrastructure are consolidated in a single data center.  
  - Easier to manage and secure, but creates a single point of failure.  
- **Decentralization**:  
  - Resources are distributed across multiple sites.  
  - Increases redundancy and resilience but adds management complexity.  

---

#### 2. Logical Isolation  
- Separation of resources within the same physical infrastructure.  
- Achieved via **VLANs, firewalls, access controls, or hypervisor-level separation**.  
- Prevents one system from directly accessing another without proper authorization.  

---

#### 3. Virtualization vs Containerization  
- **Virtualization**: Runs multiple **VMs** on a single physical machine, each with its own OS.  
  - Example: VMware, Hyper-V, KVM.  
  - Good for isolation but heavier (requires more resources).  
- **Containerization**: Runs multiple **containers** on the same OS kernel.  
  - Example: Docker, Kubernetes.  
  - Lightweight, faster startup, easier scaling, but shares OS kernel (less isolation than VMs).  

---

#### 4. Physical Security  
- Protecting infrastructure with **restricted access, surveillance, biometrics, and guards**.  
- Physical measures ensure servers are not tampered with.  

**Air Gaps**:  
- A security practice where a system/network is **physically isolated** from unsecured networks (like the internet).  
- Often used in **military, nuclear, and high-security environments**.  

---

### ✅ Summary  
On-Premises = full control and ownership of infrastructure. Organizations must handle **management, security, and scalability** themselves. Concepts like **centralization, isolation, virtualization, and physical air-gapping** play a major role in designing secure on-prem deployments.  

## 3.4 Architecture Considerations

- **Availability** – Ensure the system is accessible when needed.  
- **Resilience** – Ability to withstand failures and continue operating.  
- **Cost** – Financial considerations for design and operation.  
- **Responsiveness** – How quickly the system reacts to requests.  
- **Scalability** – Ability to grow and handle increased demand.  
- **Ease of deployment** – How easily new systems/services can be deployed.  
- **Risk transference** – Shifting risks to third parties (e.g., insurance, cloud).  
- **Ease of recovery** – Speed and simplicity of restoring operations after disruption.  
- **Patch availability** – Vendor-provided updates and fixes.  
- **Ability to patch** – How easily patches can be applied to the system.  
- **Power** – Energy requirements and availability.  
- **Compute** – Processing capacity to meet workload demands.

## 3.5 IDS and IPS

### Intrusion Detection System (IDS)
- **Types**:
  - **HIDS (Host-based IDS)** – Monitors activity on individual systems.
  - **NIDS (Network-based IDS)** – Monitors network traffic across the network.  
- **Function**:
  - Monitors for signs of an attack.
  - Only reports if it finds anything (no prevention).
- **Analysis Techniques**:
  - **Signature-based** – Detects patterns of known attacks.
  - **Anomaly-based** – Detects deviations from normal behavior.
  - **Behavior-based** – Monitors actions/behaviors that resemble attacks.

---

### Intrusion Prevention System (IPS)
- **Types**:
  - **NIPS (Network Intrusion Prevention System)** – Positioned in-line to inspect and block network traffic.
  - **Wireless IPS** – Can block unknown/unauthorized wireless devices.
- **Function**:
  - A step beyond IDS — reacts to events it detects.
  - Can reset connections or block malicious traffic.
  - Must be placed **in-line** to actively prevent threats.

## 3.6 Firewalls

### Security Zones
A fundamental requirement in network security is to **isolate trusted resources from untrusted entities**.  
Networks are segmented into zones based on trust:

- **LAN (Trusted)** – Internal network, highest trust.
- **DMZ (Screened Subnet / Semi-Trusted)**  
  - Buffer zone between an unprotected network (internet) and a protected network.  
  - Internet-accessible servers (bastion hosts) are placed in the DMZ.  
- **Internet (Untrusted)** – Lowest trust, public access.

---

### Firewall Basics
- A firewall uses **rule-based access control** to evaluate traffic and allow or deny based on predefined criteria.  
- **Types**:
  - **Web Application Firewalls (WAF)** – Protect web apps from SQL injection, XSS, etc.  
  - **Forward Proxy** – Inspects traffic going from the internal network out to the internet.  
  - **Reverse Proxy** – Inspects traffic coming from the external network into the internal network.  

---

### Configuring Firewall Rules

**Task**: Configure four rules on the firewall.

1. **Allow Accounting → Admin Server 1 via HTTPS**  
   - Source: `10.18.255.10/24` (Accounting subnet)  
   - Destination: `10.18.255.101` (Admin Server 1)  
   - Port: `443 TCP` (HTTPS)  
   - Action: **Allow**

2. **Allow HR → Server 2 via SCP (SSH)**  
   - Source: `10.18.255.10/23` (HR subnet)  
   - Destination: `10.18.255.2` (Server 2)  
   - Port: `22 TCP` (SCP uses SSH)  
   - Action: **Allow**

3. **Allow IT → Admin Server 1**  
   - Source: `10.18.255.10/25` (IT subnet)  
   - Destination: `10.18.255.101` (Admin Server 1)  
   - Port: *Any*  
   - Action: **Allow**

4. **Allow IT → Admin Server 2**  
   - Source: `10.18.255.10/25` (IT subnet)  
   - Destination: `10.18.255.102` (Admin Server 2)  
   - Port: *Any*  
   - Action: **Allow**

---

### Example Firewall Rule Table

| Source IP/Subnet   | Destination IP   | Port Number | Protocol | Action |
|--------------------|------------------|-------------|----------|--------|
| 10.18.255.10/24    | 10.18.255.101    | 443         | TCP      | Allow  |
| 10.18.255.10/23    | 10.18.255.2      | 22          | TCP      | Allow  |
| 10.18.255.10/25    | 10.18.255.101    | Any         | TCP/UDP  | Allow  |
| 10.18.255.10/25    | 10.18.255.102    | Any         | TCP/UDP  | Allow  |

## 3.7 Zero Trust

- **Definition**: A newer trend in network security that assumes **no inherent trust** — every entity must authenticate before access is allowed.  
- **Principle**: *“Never trust, always verify.”*  
- **Why it’s necessary**:
  - Rogue processes and malware can impersonate trusted users or systems.
  - Insider threats or compromised devices can bypass perimeter defenses.
- **Implementation strategies**:
  - Require authentication and authorization for every request (users, devices, applications).  
  - Enforce least privilege access.  
  - Break down the network into smaller, easier-to-manage **segments (planes)**.  
  - Use continuous monitoring and identity validation.  

## 3.8 Jump Server

- **Definition**: A special-purpose server used as a **gateway** to access and manage devices in a separate security zone (e.g., internal servers in a data center).  
- **Purpose**:
  - Adds an **extra layer of security** by forcing admins to authenticate on the jump server before reaching sensitive systems.  
  - Helps isolate **administrative access** from regular user access.  
- **Use Cases**:
  - Remote administrators connecting to internal servers from outside the network.  
  - Segregating access to critical servers (databases, financial systems) behind a controlled point.  
- **Security Benefits**:
  - Centralizes access control and monitoring of administrative activities.  
  - Reduces attack surface — only the jump server is exposed to external access, not every internal server.  
  - Supports logging and auditing of admin commands.  
- **Example**:
  - Admin connects via SSH/RDP → Jump Server → Internal Servers.  

## 3.9 Additional Security Devices

- **Honeypots**  
  - Decoy systems designed to attract attackers.  
  - Used to detect, deflect, or study intrusion attempts.  

- **Security Information and Event Managers (SIEMs)**  
  - Collect, aggregate, and analyze security event logs.  
  - Provide real-time monitoring, alerts, and correlation of events.  
  - Examples: Splunk, IBM QRadar, ArcSight.  

- **Unified Threat Management (UTM) Systems**  
  - All-in-one security appliances combining firewall, IDS/IPS, antivirus, VPN, and more.  
  - Simplifies management but may create a single point of failure.  

- **Network Load Balancers and Traffic Shapers**  
  - **Load Balancing**: Distributes workload across multiple servers to ensure availability and performance.  
  - **Traffic Shaping**: Controls the flow of network traffic by prioritizing certain types of packets.  
    - Example: MPLS networks use labels to indicate priority for Quality of Service (QoS).  
  - Both are designed to **improve performance** and **optimize resource usage**.  

## 3.10 VPNs

### Tunneling
- A function of VPNs: encapsulates one protocol within another, creating a **virtual network**.
- Provides **encapsulation** and can also provide security services such as **encryption** and **authentication**.
- Allows routing of non-routable protocols and private IP addresses.
- Common tunneling protocols:
  - PPTP (Point-to-Point Tunneling Protocol)
  - L2TP (Layer 2 Tunneling Protocol)
  - IPSec
  - GRE (Generic Routing Encapsulation)
  - SSL/TLS

---

### IPSec (Internet Protocol Security)
- **Framework** that provides:
  - Encryption
  - Authentication
  - Integrity
- Works at the **network layer** of the OSI model.

#### Modes
- **Tunnel Mode**: Entire IP packet is encapsulated (used in site-to-site VPNs).  
- **Transport Mode**: Only the payload is encapsulated (used in end-to-end VPNs).
![IPSec Tunnel vs Transport](images/ipsec-tunnel-vs-transport.jpg)



---

### IPSec Sub-protocols
- **Authentication Header (AH)**  
  - Provides **integrity, authenticity, and non-repudiation** (Integrity Check Value).  
  - Protects the entire packet (header, data, trailer) except dynamic fields (e.g., TTL).  
  - ⚠️ **No confidentiality (no encryption).**

- **Encapsulating Security Payload (ESP)**  
  - Provides **encryption**, authenticity, and integrity (via MAC).  
  - Protects the payload only.  
  - Ensures confidentiality + authenticity.

- **Internet Key Exchange (IKE)**  
  - Manages secure connections and key exchange (⚠️ no direct security services itself).  
  - Based on Diffie-Hellman for key agreement.  
  - Uses ISAKMP to manage:
    - Security Associations (SAs)  
    - Keys  
    - Security Parameters Index (SPI)  

---

### Key Points
- IPSec provides **encapsulation**, but encryption depends on the protocol (AH = no encryption, ESP = encryption).  
- What is encapsulated can be protected using AH/ESP inside IPSec.  
- VPNs rely heavily on IPSec for secure tunneling across untrusted networks like the Internet.  

3.11 Protecitng Data
