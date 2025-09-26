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
