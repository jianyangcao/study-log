# Networking Fundamentals

## 1.What is a Network?
- A network is simply **things connected**.  
- Example: your friendship circle, connected through shared interests, hobbies, or skills.  

### Examples of Networks in Daily Life
- A city’s public transportation system  
- National power grid for electricity  
- Meeting and greeting neighbors  
- Postal systems for letters and parcels  

### Networks in Computing
- Same principle, but applied to **technological devices**.  
- Example: your phone connects to access services.  
- Networks can range from **2 devices to billions** (e.g., laptops, phones, cameras, traffic lights, IoT devices).  
- Integrated into daily life: weather data, electricity delivery, traffic management, etc.  

---

## Networking Example
- **Alice, Bob, and Jim** form a simple network (connected to exchange data).  
- Networks come in all shapes and sizes.  

---

## The Internet
- The Internet is one giant network made up of many smaller networks.  
- Example: Alice introduces new friends (Zayn, Toby) to Bob and Jim.  
  - Alice acts as a **messenger** since she “speaks the same language.”  

### History
- First iteration: **ARPANET (1960s)**, funded by the US Defense Department.  
- Modern Internet began in **1989**, created by **Tim Berners-Lee** with the invention of the **World Wide Web (WWW)**.  

### Structure
- Many **private networks** connected together.  
- When private networks connect → form **public networks** (the Internet).
## Private Network vs Public Network vs Internet

| Feature              | Private Network                 | Public Network                  | Internet (Global Network) |
|-----------------------|---------------------------------|---------------------------------|----------------------------|
| **Access**           | Restricted (home, company)      | Open to anyone nearby           | Open to all (global)      |
| **Security**         | More secure, controlled access  | Less secure, potential risks    | Varies (depends on endpoint security) |
| **IP Addresses**     | Private IP ranges (RFC 1918)    | Public IPs assigned by ISP      | Public IPs (globally unique) |
| **Examples**         | Home Wi-Fi, LAN, intranet       | Coffee shop Wi-Fi, hotel Wi-Fi  | Websites, cloud, global apps |


---

## Identifying Devices on a Network
Similar to humans having **names** and **fingerprints**, devices also have two identifiers:
1. **IP Address** – can change, but identifies devices within a network.  
2. **MAC Address** – fixed (like a fingerprint/serial number).  

---

## IP Addresses
- IP = Internet Protocol address.  
- Used to identify a device on a network.  
- Format: **four octets (0–255)** separated by dots.  
  - Example: `192.168.1.1`  

### Characteristics
- IP addresses can change.  
- Each device must have a **unique IP** within the same network.  
- Governed by **protocols** (rules of communication).  

### Types of IP Addresses
- **Private IP**: used within a local/private network.  
- **Public IP**: used to identify a device on the Internet (assigned by ISP).  

#### Example
| Device Name       | IP Address    | Type    |
|-------------------|--------------|---------|
| DESKTOP-KJE57FD   | 192.168.1.77 | Private |
| DESKTOP-KJE57FD   | 86.157.52.21 | Public  |
| CMNatic-PC        | 192.168.1.74 | Private |
| CMNatic-PC        | 86.157.52.21 | Public  |

- Private IPs allow internal communication.  
- Public IP (from ISP) is shared when accessing the Internet.  

---

## IPv4 vs IPv6
- **IPv4**:  
  - 2^32 = ~4.29 billion addresses.  
  - Running out due to billions of devices.  

- **IPv6**:  
  - 2^128 = ~340 trillion-plus addresses.  
  - Solves IPv4 exhaustion.  
  - More efficient addressing methodologies.  

---

## MAC Addresses
- **MAC (Media Access Control)** = permanent unique identifier for a network interface.  
- Format: **12-character hexadecimal**, split into pairs, separated by colons.  
  - Example: `a4:c3:f0:85:ac:2d`  

### Structure
- First 6 hex digits = **vendor/manufacturer**.  
- Last 6 hex digits = **unique identifier** for the device.  

---

## MAC Spoofing
- MAC addresses can be **faked/spoofed**.  
- Spoofing = device pretends to use another device’s MAC address.  
- Can bypass weak security systems (e.g., firewalls configured to trust certain MACs).  

### Real-world Use
- Public places (cafes, hotels, coffee shops) often use **MAC-based access control** for guest Wi-Fi.  
- Example: pay-per-device Wi-Fi → can be bypassed with spoofing.
---

## What is Ping?
- **Ping** is a fundamental network tool.  
- Uses **ICMP (Internet Control Message Protocol)** packets.  
- Purpose:  
  - Check if a device/host is reachable.  
  - Measure performance (latency, reliability).  

---

### How Ping Works
1. Ping sends an **ICMP Echo Request** to the target.  
2. The target replies with an **ICMP Echo Reply**.  
3. The time between request and reply is measured.  

---

### Ping Syntax
`ping [IP address or website URL]`

- Example:  
  `ping 192.168.1.254`
  
---

## 2

## LAN Topologies
A **topology** is the design or structure of how devices are connected in a network.  

### Star Topology
- Devices connect to a **central device** (switch/hub).  
- **Advantages**:  
  - Reliable, scalable (easy to add devices).  
  - Centralized management.  
- **Disadvantages**:  
  - Higher cost (more cabling + equipment).  
  - Central device is a **single point of failure**.  

---

### Bus Topology
- All devices share a **single backbone cable**.  
- **Advantages**:  
  - Simple and cost-effective.  
- **Disadvantages**:  
  - Bottlenecks due to shared medium.  
  - Troubleshooting is difficult.  
  - **Single point of failure** = if cable breaks, entire network fails.  

---

### Ring Topology
- Devices form a **loop**, each forwarding data to the next until it reaches destination.  
- **Advantages**:  
  - Less prone to bottlenecks than bus.  
  - Easy fault isolation.  
- **Disadvantages**:  
  - Inefficient (data may pass through many devices).  
  - Failure of one cable/device can break the entire ring.  

---

## Switches
- A **switch** connects multiple devices in a network (computers, printers, etc.) via **ports**.  
- More efficient than **hubs/repeaters**:  
  - Sends data only to the **intended target** (not all devices).  
  - Reduces network traffic.  
- Found in larger networks (businesses, schools).  
- Support many ports (4, 8, 16, 24, 32, 64).  

---

## Routers
- A **router** connects **different networks** together (e.g., LAN → Internet).  
- Uses **routing tables** to determine best path for data delivery.  
- Enables communication between networks.  
- Provides **path redundancy** (multiple routes possible).  

---

## Quick Comparison Table

| Topology  | Main Feature                  | Advantage                  | Disadvantage                   |
|-----------|-------------------------------|----------------------------|--------------------------------|
| Star      | Central device (switch/hub)  | Reliable, scalable         | Central device failure = outage |
| Bus       | Single backbone cable        | Simple, cheap              | Bottlenecks, single point of failure |
| Ring      | Devices in loop              | Less bottleneck than bus   | One failure breaks whole ring  |
| Switch    | Connects devices via ports   | Efficient, reduces traffic | Costlier than hub              |
| Router    | Connects networks            | Path redundancy, Internet access | More complex, configuration needed |

---


  
