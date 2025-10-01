# 4.1 Common Security Techniques

## Baseline Configuration and Deployment

### Definition
- **Baseline Configuration**:  
  A **reference point** or **approved secure setup** for systems and devices. It ensures that all systems start from a **known, hardened state** and helps maintain consistency, compliance, and security across an organization.  

- **Deployment**:  
  The **process of rolling out** systems, software, or devices into production. It applies the baseline configuration and makes systems operational for users while ensuring security measures are in place.  

---

### Key Steps
- **Uninstall or disable unnecessary** devices, services, or protocols  
- **Install patches and updates** to keep systems secure  
- **Configure shared resources, ACLs, and user privileges**  
- **Rename default accounts** (e.g., “admin”)  
- **Change default settings** to reduce vulnerabilities  
- **Install and configure security software**, including:  
  - Anti-malware  
  - Host firewall / Intrusion Detection System (IDS)  

---

### Quick Summary
- **Baseline configuration** = “what the secure system should look like.”  
- **Deployment** = “how we roll it out and enforce the baseline.”  

---

# 4.2 Securing Mobile Devices

## Mobile Device Deployment Models

### 1. Bring Your Own Device (BYOD)
- Employees use **their personal devices** (phones, laptops, tablets) for work.  
- **Pros**: Lower cost for the company, employee convenience.  
- **Cons**: Security risks, lack of full control over the device, potential privacy concerns.  

---

### 2. Corporate Owned, Business Only (COBO)
- Company **purchases and owns** the device.  
- Device is used **exclusively for business purposes**.  
- **Pros**: Maximum control and security, standardized configuration.  
- **Cons**: Less flexibility for employees, higher company cost.  

---

### 3. Corporate Owned, Personally Enabled (COPE)
- Company owns the device but allows **limited personal use**.  
- Balanced approach between **control** and **user flexibility**.  
- **Pros**: Strong security, while still allowing personal convenience.  
- **Cons**: Company still pays for devices, potential mix of personal/work data.  

---

### 4. Choose Your Own Device (CYOD)
- Employees choose from a **pre-approved list of devices**.  
- Company ensures security standards are met.  
- **Pros**: Employee choice + IT control.  
- **Cons**: Company still funds devices, but with limited model flexibility.  

---

### 5. Virtual Desktop Infrastructure (VDI)
- Employees connect to a **virtual environment** hosted by the company.  
- Device itself only acts as an **access terminal**.  
- **Pros**: No sensitive data stored on personal devices, high security.  
- **Cons**: Requires strong network connection, high infrastructure cost.  

---

## Quick Comparison

| Model | Who Owns Device | Usage | Control | Security |
|-------|-----------------|-------|---------|----------|
| **BYOD** | Employee | Work + Personal | Low | Lowest |
| **COBO** | Company  | Business Only   | High | Highest |
| **COPE** | Company  | Business + Some Personal | High | High |
| **CYOD** | Company (employee picks model) | Work + Personal | Medium | Medium |
| **VDI**  | Either (focus on virtual access) | Virtual work only | Very High | Very High |

---

## Mobile Device Management (MDM)
- Software that applies **security policies** to mobile devices used in an enterprise.  
- Can be specific to **iOS/Android** or multi-vendor.  
- Often part of **Enterprise Mobility Management (EMM)** platforms.  
- Functions:  
  - Enroll devices into the corporate network.  
  - Control or restrict device functions (camera, Bluetooth, etc.).  
  - Push/install corporate apps and updates.  
  - Monitor device compliance.  

---

## iOS in the Enterprise
- Managed using **Apple MDM framework**.  
- Supports features like:  
  - Enforcing passcodes, screen locks.  
  - Controlling app installations.  
  - Secure container for separating **corporate vs personal data**.  

---

## Android in the Enterprise
- Managed using **Android Enterprise** or vendor-specific solutions (Samsung Knox, etc.).  
- Supports:  
  - Work profiles (separating work and personal apps).  
  - Control of app installations.  
  - Remote wipe and encryption.  

---

## Cellular and Wi-Fi Connection Methods
- **Cellular Risks**:  
  - Attacks on authentication and confidentiality (e.g., fake base stations).  
- **Wi-Fi Risks**:  
  - Open access points are insecure.  
  - Rogue access points can impersonate trusted networks and steal credentials.  

---

## Personal Area Network (PAN) Technologies
- **Bluetooth**: Used for headphones, car connections, IoT devices. Vulnerable to attacks like Bluejacking, Bluesnarfing.  
- **ANT/ANT+**: Low-power wireless protocols used in health monitors, fitness trackers.  
- **Z-Wave**: Used in smart home devices like personal assistants and IoT sensors.  
- **Wi-Fi Direct**: Device-to-device Wi-Fi connection (no router).  
- **Tethering**: Sharing a phone’s Internet with other devices. Risk: could expose corporate data over insecure connections.  
- **Infrared (IR)**: Short-range, line-of-sight communication (remote controls, sensors).  

---

## NFC and Mobile Payment Services
- **Near Field Communication (NFC)** enables close-range communication (few centimeters).  
- Common use: **mobile wallet apps**.  
  - Apple Pay, Google Pay, Samsung Pay.  
- **Authentication methods**: biometrics (fingerprint, FaceID), PIN.  
- **Potential NFC Exploits**:  
  - **Eavesdropping/skimming**: capturing payment data.  
  - **DoS**: preventing NFC services from functioning.  

---

## Mobile Access Control Systems
- **Screen lock**: first defense (time-based auto-lock).  
- **Password/PIN**: numeric or alphanumeric entry.  
- **Swipe pattern**: common in Android (weaker than PIN).  
- **Biometric**: fingerprint, facial recognition, iris scan.  
- **Lockout**: device blocks access after failed attempts.  
- **Context-based authentication**: adaptive security (e.g., require stronger auth if logging in from new location or untrusted Wi-Fi).  

---

## Remote Wipe
- Also called **“kill switch”**.  
- Restores device to factory defaults or clears storage (entirely or partially).  
- Initiated from enterprise management software (MDM/EMM).  
- Risk: if device is offline or blocked, wipe may not execute.  

---

## Full Device Encryption and External Media
- **iOS Device Encryption**: built-in, includes data protection and secure erase.  
- **Android Device Encryption**: newer versions enable full-disk encryption by default.  
- **External Media**: USB drives, SD cards must also be encrypted to protect sensitive data.  

---

## Guidelines for Implementing Mobile Device Security
- Be aware of **connection methods** (cellular, Wi-Fi, Bluetooth, NFC).  
- Understand the **level of control** for each connection method.  
- Use an **MDM/EMM platform** to enforce policies.  
- Apply **security controls** on all corporate devices.  
- Monitor and restrict **third-party app installations**.  
- Prevent **rooting, jailbreaking, carrier unlocking** (weakens device security).  
- Enforce policies to disable risky features (e.g., USB debugging).  
- Plan secure **deployment models** (BYOD, COBO, COPE, CYOD, VDI).  
- Recognize inherent risks with **BYOD** and mitigate with security policies.  
- Apply multiple security controls to **balance usability and protection**.  

---

## Quick Summary Table

| Feature / Method          | Purpose | Security Risks | Mitigation |
|----------------------------|---------|----------------|------------|
| **MDM/EMM**               | Centralized management of devices | Bypass by user, limited support on old devices | Use enforced enrollment, strong policies |
| **Cellular/Wi-Fi**        | Connectivity | Rogue APs, fake base stations | VPN, WPA3, disable auto-connect |
| **PAN (Bluetooth, etc.)** | Short-range communication | Bluejacking, Bluesnarfing | Disable when not needed, patch devices |
| **NFC / Mobile Payments** | Mobile transactions | Skimming, DoS | Tokenization, biometric auth |
| **Access Control**        | Device authentication | Weak PINs, stolen device | Strong PIN, biometrics, lockout |
| **Remote Wipe**           | Erase lost/stolen devices | Device offline | Auto-wipe after failed logins |
| **Full Encryption**       | Protect stored data | None if disabled | Enable by default, encrypt SD cards |

---

# 4.3 Embedded Systems

## Embedded Systems
- **Definition**: A computer system with a **dedicated function** (unlike general-purpose computers).  
- Characteristics:  
  - Static environments (rarely updated).  
  - Can be small (smart sensor) or complex (vehicle systems).  
  - Depend on **vendor support** for security patches and updates.  
  - Often run firmware on **programmable logic controllers (PLCs)**.  

⚠️ **Security concern**: Many embedded systems are not patched regularly → vulnerable to attacks.

---

## SCADA and HVAC Control
- **SCADA (Supervisory Control and Data Acquisition)**  
  - Used to monitor/manage **industrial, infrastructure, and facility-based processes**.  
  - Runs on PCs but controls **plant devices and field devices**.  
  - Security issues can impact critical infrastructure.  

- **ICS (Industrial Control Systems)**  
  - Broader category that includes SCADA.  
  - Controls industrial processes like power plants, manufacturing, pipelines.  

- **HVAC (Heating, Ventilation, Air Conditioning)**  
  - Integrated into building automation.  
  - Can be exploited as an entry point for malware.  
  - Example: **Stuxnet** targeted ICS/SCADA systems.  

---

## Medical Devices
- Found in hospitals, clinics, and home environments.  
- Often run on **unsecure protocols and control systems**.  
- Risks:  
  - Attackers can pivot into networks storing **Protected Health Information (PHI)**.  
  - Ransomware: attackers disrupt services until ransom is paid.  
  - Safety risks: tampering with **dosage levels or device settings** can cause injury/death.  

⚠️ Security+ takeaway: Medical devices are **life-critical** → confidentiality + safety risks.

---

## In-Vehicle Computing Systems and Drones

### In-Vehicle Computing
- Includes computer-assisted systems:  
  - Engine, steering, brakes.  
  - Entertainment and navigation systems.  
  - Event data recorders (“black box”).  
- Risks: Remote exploitation could endanger safety.  

### UAVs (Unmanned Aerial Vehicles)
- Examples: fixed-wing aircraft, multi-rotor drones.  
- Risks:  
  - **Insecure communication channels**.  
  - Can be used for **surveillance or malicious attacks**.  

---

## Smart Devices and IoT (Internet of Things)
- **Smart Devices**: appliances with processing, storage, and networking (e.g., smart TVs, thermostats).  
- **Home Automation**:  
  - Central hubs controlling lighting, locks, alarms, cameras.  
  - Require secure patch policies.  
- **Wearable Technology**: smart watches, fitness trackers → collect sensitive personal data.  
- **Smart Camera Systems**: often exposed to the Internet with weak passwords.  

⚠️ Security+ takeaway: IoT = high risk because of **default passwords, weak updates, always-on connectivity**.  

---

## Security for Embedded Systems
### Key Controls:
1. **Network Segmentation**  
   - Place embedded/IoT devices in **isolated VLANs** to limit lateral movement.  

2. **Application Firewalls**  
   - Protect applications communicating with embedded systems.  

3. **Wrappers (Host-based Firewalls)**  
   - Provide additional filtering/protection for devices lacking native defenses.  

4. **Firmware Version Control & Updates**  
   - Keep firmware patched and up to date.  
   - Apply vendor security updates promptly.  

---

## Exam Tips (Security+ Focus)
- **Embedded systems** = specialized devices with limited update capability → often vulnerable.  
- **SCADA/ICS** = high-value targets; attacks can disrupt **critical infrastructure**.  
- **Medical devices** = safety + data confidentiality (PHI).  
- **In-vehicle systems/drones** = safety-critical; insecure communication is a major risk.  
- **IoT/Smart devices** = often default credentials, poor vendor patching → require **network segmentation + strong authentication**.  
- **Mitigation** = segmentation, firewalls, firmware updates, vendor management.  

---
# 4.4 Wireless Security

## 🔹 Installation Considerations
When setting up wireless networks, proper planning improves performance and reduces security risks.

- **Site Surveys**  
  Assess the physical environment to determine the best placement for wireless access points (WAPs). Helps avoid dead zones and interference.

- **Heat Maps (Coverage Maps)**  
  Visual maps showing wireless signal strength across an area. Useful for spotting weak coverage areas.

- **WiFi Analyzers**  
  Tools that measure signal strength, interference, and channel usage. Help optimize performance and security.

- **Channel Overlaps**  
  Occur when nearby wireless networks use the same or overlapping frequencies (e.g., 2.4 GHz channels). Can cause interference and degraded performance.

- **Wireless Access Point (WAP) Placement**  
  Proper placement ensures good coverage while minimizing signal leakage outside secure areas (reducing risk of external attacks).

---

## 🔹 Wireless Security Problems

- **Unauthorized Access**  
  Attackers connect to a wireless network without permission, often exploiting weak or default passwords.

- **Sniffing**  
  Capturing and analyzing wireless traffic. If unencrypted, attackers can steal credentials or sensitive data.

- **War Driving**  
  Driving around with a laptop/antenna to discover and map unsecured or poorly secured wireless networks.

- **Unauthorized Access Points & Evil Twins (Man-in-the-Middle)**  
  - **Unauthorized Access Point (Rogue AP):** An attacker sets up a wireless AP on the network without authorization.  
  - **Evil Twin:** A fake AP that mimics a legitimate one. Users unknowingly connect, allowing attackers to intercept traffic (MITM attack).

- **Wi-Fi Protected Setup (WPS) Vulnerability**  
  - WPS is a feature meant to simplify connecting devices with a PIN or button.  
  - Vulnerable to brute-force attacks against the WPS PIN.  
  - Best practice: disable WPS.

---

✅ **Summary:**  
Wireless networks require careful planning (site surveys, heat maps, analyzer tools) and strong protections. Security threats like sniffing, war driving, and evil twin attacks make **encryption (WPA3), strong authentication, and disabling insecure features (like WPS)** essential.

---

# 4.5 Wireless Configuration

## 🔹 Antenna Types
- **Omnidirectional Antenna**  
  - Radiation power distributed equally in all directions (horizontal plane).  
  - Example: Wi-Fi access point antennas.  
  - Pros: Covers a wide area.  
  - Cons: Easier for attackers to detect signals outside secure areas.

- **Directional Antenna (e.g., Yagi Antenna)**  
  - Radiation power concentrated in one specific direction.  
  - Pros: Stronger signal in target direction, longer range.  
  - Cons: Limited coverage angle.

---

## 🔹 Wireless Security: Encryption

### WEP (Wired Equivalent Privacy)
- Uses **RC4 stream cipher** (weak).  
- Issues:  
  - Easily crackable.  
  - Only option for old **802.11b** networks.  
  - **Static keys** (don’t change).  
- Encryption strength:  
  - Low: 64-bit key.  
  - High: 128-bit key.  
- Uses an **Initialization Vector (IV)**, but it’s too short and predictable.  
- ⚠️ Considered insecure and deprecated.

---

### WPA (Wi-Fi Protected Access)
- Introduced **TKIP (Temporal Key Integrity Protocol)** with **dynamic keys**.  
- Still relied on **RC4**.  
- Used longer initialization vector than WEP.  
- Transitional step—no longer secure today.

---

### WPA2
- Replaced RC4 with **AES (block cipher)**.  
- Uses **CCMP (Counter Mode with Cipher Block Chaining Message Authentication Protocol)**.  
- Provides strong encryption + integrity.  
- **Not backwards compatible** with WEP/WPA (different ciphers).  
- Still widely in use, but vulnerable to some brute-force/side-channel attacks.

---

### WPA3
- Uses **Dragonfly handshake (SAE – Simultaneous Authentication of Equals)**.  
- Protects against offline password cracking.  
- Uses **Galois Counter Mode (GCM)** for integrity checking.  
- Stronger security, mandatory in modern devices.

---

## 🔹 Authentication

### Decentralized Authentication
- Client authenticates **directly** with AP/VPN/RAS.  
- Each access device manages its own credentials.  
- Simple, but not scalable.  
- Example: **WPA2-Personal (PSK)** at home Wi-Fi.
![decentralized](images/centralizd.png)

### Centralized Authentication (Enterprise)
- Based on **802.1X** standard.  
- Roles:  
  - **Supplicant** → client device (Wi-Fi laptop, VPN client).  
  - **Authenticator** → AP, VPN gateway, or RAS.  
  - **Authentication Server** → RADIUS/TACACS+.  
- Process:  
  1. Supplicant requests access.  
  2. Authenticator forwards credentials.  
  3. Server validates (e.g., via Active Directory).  
  4. Access granted/denied.
  ![centralized](images/decentralized.png)
     
- Protocol: **EAPoL (Extensible Authentication Protocol over LAN)**.  
- Example: **WPA2/WPA3-Enterprise** in corporate Wi-Fi.

### Comparison Table

| Feature            | Decentralized (PSK)            | Centralized (802.1X)                 |
|--------------------|--------------------------------|---------------------------------------|
| Who validates?     | Access Point itself            | Central server (RADIUS/TACACS+)       |
| Credential type    | Shared Wi-Fi password (PSK)    | Individual user credentials           |
| Scalability        | Poor (hard to manage many APs) | High (central policy control)         |
| Security level     | Weaker                         | Stronger, enterprise-grade            |
| Example use case   | Home Wi-Fi                     | Corporate Wi-Fi with AD integration   |

📌 **Key takeaway for Security+**:  
- **Decentralized = WPA2-Personal (PSK)**.  
- **Centralized = WPA2/WPA3-Enterprise with RADIUS**.  

---

## 🔹 Bluetooth Security
- **Bluetooth = Personal Area Network (PAN)** protocol (short range, cable replacement).  

### Modes
- **Discovery Mode** → device visible to others.  
- **Automatic Pairing** → convenience, but risk if insecure.

### Threats
- **Bluejacking**: Sending spam messages to nearby devices.  
- **Bluesnarfing**: Stealing information (contacts, files) from a device.  
- **Bluebugging**: More severe → attacker gains full control of the phone:  
  - Make calls.  
  - Send texts.  
  - Eavesdrop on conversations.  

---

✅ **Summary:**  
- Use **WPA3** wherever possible.  
- Avoid WEP/WPA.  
- For enterprise, implement **802.1X with RADIUS**.  
- Secure Bluetooth by turning off discoverability and disabling when not in use.

---

# 4.6 Proper Hardware, Software, and Data Asset Management

## Acquisition/Procurement of a System
- **Acquisition/procurement process**: Steps to evaluate, purchase, or develop a system.
- **Assignment/accounting**: Tracking system usage and financial accountability.
- **Ownership**: Clearly define who is responsible for the system.
- **Classification**: Labeling assets based on sensitivity (e.g., public, internal, confidential).
- **Monitoring/asset tracking**: Continuously track where systems and devices are located.
- **Inventory**: Maintain a complete list of assets.
- **Enumeration**: Numbering/recording assets for easier tracking.
- **Disposal/decommissioning**: Secure removal when assets are no longer used.
- **Sanitization**: Removing sensitive data before re-use or disposal.
- **Destruction**: Physical destruction of media or devices to prevent data recovery.
- **Certification**: Verification that systems meet requirements before use.
- **Data retention**: Defining how long data must be stored (for legal, compliance, or business needs).

---

## Acquisition or Development of a System: Feasibility Study
Factors to decide whether to **develop** or **acquire** a system:
- **Functionality**: Does the system meet required business needs?
- **Cost**: Compare cost of building vs. buying.
- **Resources**: Staff, hardware, and time needed for development.
- **Compatibility**: Must align with business plans, IT infrastructure, and risk appetite.

---

## Requirements Definition
Clearly define:
- What the system should do.
- How users will interact with it.
- Conditions under which the system must operate.
- Information criteria the system should meet.

**Example activities:**
- Identify and consult stakeholders.
- Identify relevant data privacy and governance requirements.
- Analyze requirements to detect/correct conflicts and set priorities.
- Define system boundaries.
- Identify security requirements.

---

## System Acquisition and Design
- **Software selection and acquisition**
  - Consider risks/benefits of developing in-house vs. buying a complete/tested system.
  - Decision depends on cost, availability, and time-to-deploy.
- **Design**
  - Develop a detailed design based on requirements.
  - Illustrate how data flows through the system (inputs, outputs, processing).
  - Develop test plans.

---

## Configuration or Development
- **Configuration (purchased system)**
  - Define, track, and control changes in the acquired system.
  - Integrate ERP or other systems into existing IT infrastructure.
  - Use change management policies (roles, impact assessment, approvals).

- **Development (in-house)**
  - Follow detailed design from earlier phase.
  - Activities include:
    - Coding and debugging.
    - Ensuring security by design (security is built in, not added later).
    - Converting data from old system to new system.

---

## Final Testing, Certification, and Implementation
- Perform **system testing** to ensure requirements are met.
- Certification confirms system is secure and functional.
- Implementation puts the system into production use.

---

## Post-Implementation Review
- Review performance, security, and compliance after deployment.
- Identify lessons learned for future projects.

---

## Decommissioning Systems
- When systems are retired, ensure:
  - Data is securely removed (sanitization or destruction).
  - Documentation of the retirement process.
  - No sensitive data remains accessible.

---

# 4.7 Vulnerability Assessments

## What are Vulnerabilities?
- Areas where an organization is **not fully protected** and can be exploited by attackers.
- Security+ expects you to know **types, methods, and tools** used to identify vulnerabilities.

---

## Examples of Vulnerabilities
- **Untrained staff** clicking on phishing links.  
- **Open network ports** in common areas that are live but not secured.  
- **No alarm system** to detect intrusions.  
- **Servers and critical systems** without access controls.  
- **Laptops with VPN access/sensitive data** not encrypted.  
- **Outdated/unsupported software** (legacy devices).  

*(Explanation: These are common weak spots that attackers exploit. Many map directly to Security+ test questions.)*

---

## Vulnerability Analysis Approaches
- **Static analysis**: Manually reviewing source code or using tools to detect coding errors.  
- **Dynamic analysis**: Evaluating software/system while it is running.  
- **Side-channel analysis**: Observing system behavior/data flows (e.g., sniffers).  
- **Reverse engineering**: Deconstructing software/hardware to see how it works.  

---

## Vulnerability Analysis Methods
- **Wireless vulnerability scan**: Identify signal coverage, configs, and weaknesses (e.g., Reaver, KRACK).  
- **Software composition analysis**: Check source code for open-source components with known flaws.  
- **Fuzzing**: Inject malformed data to test how an app handles unexpected input.  
- **Pivoting**: Using a compromised system to target others in the same network.  
- **Post-exploitation**: Actions after initial compromise to maintain access.  
- **Persistence**: Attacker’s ability to stay hidden and maintain control.  

---

## Vulnerability Analysis Tools
- **Protocol analyzer**: Captures network traffic (e.g., Wireshark).  
- **Network traffic analyzer**: Similar but sensor-based (e.g., Zeek).  
- **Port scanner**: Finds open ports and services (e.g., Nmap).  
- **HTTP interceptor**: Inspects/modifies HTTP(S) traffic (e.g., Burp Suite).  
- **SCAP scanner**: Uses SCAP to scan devices against baselines (e.g., DoD SCAP Scanner).  
- **Vulnerability scanner**: Finds known vulnerabilities, config issues, weak defaults (e.g., Nessus).  
- **Exploit framework**: Pre-built attack tools (e.g., Metasploit, PowerShell Empire).  
- **Password cracker**: Tests password strength (e.g., John the Ripper, Hashcat).  

---

## Dependency Management
- Keep track of all **software libraries and dependencies** since outdated ones may contain vulnerabilities.

---

## Vulnerability Analysis Dependencies
- **Permissions and access**: Testers may need ID badges, background checks, etc.  
- **Facility considerations**: Onsite escorting, restricted access, clearance requirements.  
- **Physical security**: Protects testers and data during assessment.  
- **Reason for corrections/changes**: Assessments should tie findings to business/IT needs.  

---

# 4.8 Security Assessments — Vulnerability Management

> Summary: vulnerability management is the continuous cycle of **discovering, assessing, remediating, and verifying** software/hardware weaknesses across an environment. This section covers scanners, patching, information sources, SCAP, honeypots, log reviews, and related controls.

---

## Vulnerability Management Activities (high-level)
- **Discover** technical vulnerabilities (vulnerability scanners, asset inventories, manual review).  
- **Assess / Prioritize** by risk (exploitability, impact, exposure).  
- **Remediate** (patch, configuration change, mitigation).  
- **Verify** fixes (re-scan, regression tests).  
- **Document & report** (tickets, SLAs, metrics).

**Note:** Performing a risk assessment helps identify areas you might have missed and prioritizes remediation.

---

## Vulnerability Scanners — critical components & modes
- **Credentials**
  - **Unauthenticated (credential-less)** scans: scan from outside without logging in; find only externally-visible issues.  
  - **Authenticated (credentialed)** scans: scanner logs in (e.g., via SSH, SMB, API) to inspect system internals; finds more issues (missing patches, insecure configs).
- **Agent vs Agentless**
  - **Agent-based**: small client runs on endpoints, reports to scanner — good for intermittent networks or deep local checks.  
  - **Agentless**: remote scanning only; easier to deploy but may be limited.
- **Intrusive vs Non-intrusive**
  - **Non-intrusive**: identifies and reports vulnerabilities without attempting exploitation. Safer in production.  
  - **Intrusive (active/exploit)**: attempts to validate/exploit vulnerabilities — provides stronger proof but carries risk of breaking services.

**Scanner examples (study only):** Nessus, OpenVAS/Greenbone, Qualys, Tenable (commonly seen on Security+).

---

## Patch Management
- **Purpose:** identify and install missing updates across OS, apps, firmware, network devices (firewalls, switches, UTM).  
- **Key activities**
  - Inventory & baseline systems.  
  - Test patches in staging before production.  
  - Schedule regular patch windows and emergency patching for critical CVEs.  
  - Track installation and rollback procedures.  
- **Devices beyond OS:** remember network equipment and appliances require firmware updates.

---

## Vulnerability Information Sources
- **Advisories:** vendor or CVE-specific notices describing vulnerabilities and fixes.  
- **Bulletins / Mailing lists:** high-level summaries or newsletters.  
- **ISACs / ISAO:** industry-specific information sharing & analysis centers (non-profit groups for sector intel).  
- **News & Security feeds:** headlines or blogs reporting new exploit activity.

**Tip:** subscribe to vendor and CVE feeds for proactive awareness.

---

## SCAP — Security Content Automation Protocol (overview)
- **What it is:** a suite of standards (open) to standardize naming, formatting, and reporting for security flaws and configuration issues. Used to automate assessment and reporting.
- **Goals:** enumerate software flaws, compare to baselines, and enable machine-readable assessments.

**SCAP language elements**
- **OVAL (Open Vulnerability and Assessment Language):** describes how to collect/check system information (system info, machine state, tests).  
- **ARF (Asset Reporting Format):** correlates/report findings about devices/assets.  
- **XCCDF (Extensible Configuration Checklist Description Format):** XML-based checklists/benchmarks used to define policies and checks.

**SCAP identification schemes**
- **CPE (Common Platform Enumeration):** standardized product naming.  
- **CVE (Common Vulnerabilities and Exposures):** unique vulnerability identifiers.  
- **CCE (Common Configuration Enumeration):** standardized config issue identifiers.

---

## Honeypots / Honeynets
- **Purpose:** attract attackers to monitor tactics, gather intelligence, and detect earlier.  
- **Design guidance:** should act as **enticement**, not **entrapment** — i.e., capture attacker activity while avoiding legal/ethical pitfalls.  
- **Examples:** low-interaction honeypots (emulated services) vs high-interaction honeypots (real systems for deeper intel).

---

## Log Reviews & Monitoring
- **Log sources:** system logs, application logs, firewall logs, IDS/IPS, authentication logs, network devices.  
- **Syslog:** common network-based logging protocol (text messages forwarded to a central log server).  
- **SIEM (Security Information and Event Management):**
  - Aggregates logs from many sources.
  - Normalizes, correlates, and alerts on suspicious patterns.
  - Enables searches, dashboards, and forensic timelines.
- **Log review best practices**
  - Centralize logs (retention & integrity).  
  - Tune alerts to reduce false positives.  
  - Keep retention aligned to compliance needs.  
  - Use correlation rules to detect multi-source attacks.

---

## Unified Threat Management (UTM)
- **UTM devices** combine multiple security functions (firewall, IDS/IPS, antivirus, content filtering) into a single appliance.  
- **Use case:** simplified management for small/medium networks; can reduce complexity but be cautious of single points of failure.

---

# 4.9 Threat Intelligence — Security+

> Summary: Threat intelligence turns raw data about threats into **actionable information** you can use to reduce risk. It helps teams prioritize, detect, and respond to attacks faster.

---

## Threat intelligence **types** (by audience & usage)
| Type | Audience / Purpose | Example |
|---|---|---|
| **Strategic** | Non-technical, high-level — for executives and policy decisions | Industry-level trends, risk to the business from geopolitical events |
| **Operational** | Mid-level: focuses on adversaries and their likely actions | Which threat groups target our sector and what assets they go after |
| **Tactical** | Immediate, technical — used by analysts and defenders | Signatures, IOCs, rules to detect a specific exploit |
| **Counterintelligence** | Offensive or defensive actions using intelligence to disrupt adversaries | Deception, takedown coordination with law enforcement |

**Note:** Strategic → Operational → Tactical is the usual funnel from broad context to immediate detection/remediation steps.

---

## Intelligence **source types**
- **OSINT (Open-Source INTelligence)** — public sources: blogs, paste sites, forums, social media, public malware repositories.  
- **Closed / Proprietary sources** — commercial feeds, subscription-based reports.  
- **Internal telemetry** — logs, EDR alerts, SIEM events, honeypot data.  
- **Information sharing bodies** — ISACs, vendor advisories, CERTs.

**Examples of orgs**
- **CERT / CSIRT** — incident response and coordination teams.  
- **ISAC / ISAOs** — sector-focused sharing groups (financial, healthcare, etc.).  
- **MITRE** — ATT&CK framework, enterprise resources and mappings.

---

## Threat awareness (what to track)
- **Known threats** — long-established malware/families that remain relevant.  
- **Current vulnerabilities** — documented vulnerabilities in HW/SW/processes.  
- **Trending attacks** — attacker tactics that are growing in popularity (e.g., supply-chain, living-off-the-land).  
- **Emerging threat sources** — new tools, new exploit kits, evolving business & tech changes.  
- **Zero-day vulnerabilities** — newly discovered flaws with no public patch — very high priority.

---

## Intelligence **gathering cycle** (how to turn data → intel)
1. **Define intelligence requirements** — what questions must intelligence answer? (e.g., "Which 3rd-party services expose customer data?")  
2. **Collect** — gather raw data from OSINT, sensors, vendor advisories, internal logs.  
3. **Process / Analyze** — enrich and contextualize; turn noise into meaningful indicators and TTPs.  
4. **Disseminate** — deliver actionable intelligence to the right teams (SOC, IR, execs) with recommended actions.  
5. **Feedback** — teams report back results to refine requirements and improve future cycles.

---

## Threat Hunting
- **Definition:** proactive, hypothesis-driven searches across telemetry to discover threats before alerts fire.  
- **Method:** use known TTPs (tactics, techniques, procedures) to form hypotheses, then search logs/EDR/SIEM for patterns.  
- **Inputs:** threat intelligence feeds, advisories, vendor notes, MITRE ATT&CK mappings.

---

## Advisories, Bulletins, & TTPs
- **Advisories / Bulletins:** vendor or researcher-published details about vulnerabilities or attacks.  
- **TTPs (Tactics, Techniques, Procedures):** patterns of attacker behavior (useful to map in MITRE ATT&CK).  
- **Use-case:** map detected indicators to TTPs to understand attacker intent and next likely steps.

---

## Indicators & Definitions (quick)
- **IoC (Indicator of Compromise):** forensic artifact showing a system was compromised (e.g., malicious hash, C2 IP).  
- **IoA (Indicator of Attack) / Behavioral indicator:** activity/behavior suggesting an ongoing attack (e.g., unusual PowerShell execution).  
- **Reputational indicators:** reputation data associated with an IP/domain (malicious, suspicious).  
- **TTPs:** higher-level behaviors describing how an adversary operates (not single artifacts).

---

## How to make intelligence actionable
- **Enrichment:** add context (asset owner, criticality, patch status) to raw indicators.  
- **Prioritization:** combine exploitability + CVSS + asset criticality + threat actor interest.  
- **Operationalization:** translate intel into detection rules, SIEM alerts, EDR playbooks, and SOC runbooks.  
- **Automation:** feed vetted indicators to blocking lists (firewall, proxy) and detection rules (SIEM/EDR).

---

# 4.10 Modify Enterprise Capabilities to Enhance Security

## Using Security Infrastructure in Responses
- **Firewall rules**  
  Define which traffic is allowed or denied on a network.

- **Access control list (ACL) rules**  
  Rules that specify which users or systems can access certain resources.

- **IPS/IDS rules**  
  - IDS (Intrusion Detection System): Detects malicious traffic/activity.  
  - IPS (Intrusion Prevention System): Detects and actively blocks malicious traffic.

- **Endpoint detection and response (EDR)**  
  Security solutions that monitor and respond to threats on endpoints (PCs, servers, mobile devices).

- **Extended detection and response (XDR)**  
  Integrates EDR with network, cloud, and email data to improve threat visibility and automated responses.

- **Data loss prevention (DLP) rules**  
  Policies to prevent sensitive data from leaving the organization (e.g., blocking SSNs in outgoing email).

- **Network access control (NAC)**  
  Enforces security policies on devices before they connect to the network (e.g., patch status, antivirus installed).

- **Scripts / regular expressions**  
  Custom automation or pattern-matching rules to detect/stop suspicious activity.

- **DNS filtering**  
  Blocks access to malicious or unauthorized websites by filtering DNS requests.

---

## Securing Mail

- **DomainKeys Identified Mail (DKIM)**  
  Uses **PKI (Public Key Infrastructure)** to verify the origin of email messages. Helps ensure emails haven’t been tampered with.

- **Domain-based Message Authentication, Reporting, and Conformance (DMARC)**  
  A policy that tells receiving mail servers what to do after checking SPF and DKIM records (e.g., accept, reject, or quarantine suspicious emails).

- **Sender Policy Framework (SPF)**  
  A DNS record listing the servers authorized to send emails for a domain. Prevents email spoofing.

---

## Securing the Operating System

### Windows
- **Active Directory (AD)**  
  Microsoft’s directory service for identity management, authentication, and access control.

### Linux
- **Secure Linux**  
  General hardening steps such as disabling root SSH login, keeping packages updated, using SELinux/AppArmor, and enforcing least privilege.

---

# 4.11 Protocols and Ports

## File Transfer Protocol (FTP)
- Standard protocol for transferring computer files.
- Client–server architecture.
- **Not secure** (plaintext).
- Operates on **TCP ports 20 (data), 21 (control)**.
- Secure alternatives:
  - **FTPS** (FTP over SSL/TLS).
  - **SFTP** (SSH File Transfer Protocol, uses port 22).

---

## Secure Shell (SSH)
- Provides secure communication over untrusted networks.
- Supports remote login & command execution.
- Client–server architecture.
- Versions: **SSH-1 (obsolete)**, **SSH-2 (secure)**.
- Operates on **TCP port 22**.
- Related: **SCP, SFTP** also use port 22.

---

## Telnet
- Early remote login protocol.
- **Not secure** (plaintext).
- Superseded by SSH.
- Operates on **TCP port 23**.

---

## Simple Mail Transfer Protocol (SMTP)
- Used for sending and relaying email.
- **Not secure by default** (plaintext).
- Operates on:
  - **TCP port 25** (legacy, unencrypted).
  - **TCP port 465** (SMTP over SSL).
  - **TCP port 587** (SMTP with STARTTLS, secure standard).

---

## Terminal Access Controller Access Control System Plus (TACACS+)
- Cisco AAA protocol.
- Encrypts the **entire packet** (more secure than RADIUS).
- Separates Authentication, Authorization, and Accounting.
- Uses **TCP port 49**.

---

## Domain Name System (DNS)
- Translates domain names → IP addresses.
- Hierarchical, decentralized.
- Operates on **UDP/TCP port 53**.
- Security risks: **DNS poisoning, spoofing**.
- Defense: **DNSSEC, DNS filtering**.

---

## Dynamic Host Configuration Protocol (DHCP)
- Automatically assigns IP addresses & configuration.
- Operates on:
  - **UDP port 67 (server)**.
  - **UDP port 68 (client)**.

---

## Trivial File Transfer Protocol (TFTP)
- Very simple version of FTP.
- **Not secure** (no authentication/encryption).
- Used for LAN booting or firmware updates.
- Operates on **UDP port 69**.

---

## Hypertext Transfer Protocol (HTTP / HTTPS)
- **HTTP**:
  - Foundation of web traffic.
  - Operates on **TCP port 80**.
  - **Not secure** (plaintext).
- **HTTPS**:
  - Secure HTTP with TLS/SSL.
  - Operates on **TCP port 443**.
  - Provides encryption + integrity.

---

## Post Office Protocol (POP3)
- Retrieves email from a mail server to a client.
- Operates on:
  - **TCP port 110** (plaintext).
  - **TCP port 995** (POP3S, secure).

---

## Internet Message Access Protocol (IMAP)
- Retrieves and synchronizes email across devices.
- Operates on:
  - **TCP port 143** (plaintext).
  - **TCP port 993** (IMAPS, secure).

---

## Network Time Protocol (NTP)
- Synchronizes clocks between devices.
- Operates on **UDP port 123**.

---

## Simple Network Management Protocol (SNMP)
- Used to monitor and manage network devices.
- Versions:
  - v1/v2: insecure (plaintext).
  - v3: secure (auth + encryption).
- Ports:
  - **UDP port 161** = Queries  
  - **UDP port 162** = Traps  

### Queries vs Traps
- **Queries (161)**: Manager → Agent.  
  - Manager pulls information (GET, GET-NEXT, SET).  
  - Example: “What’s the CPU usage?”  
- **Traps (162)**: Agent → Manager.  
  - Device pushes an alert without being asked.  
  - Example: “Interface went down!”  

---

## Lightweight Directory Access Protocol (LDAP)
- Provides directory services (user, group, resource info).
- Operates on:
  - **TCP/UDP port 389** (plaintext).
  - **TCP/UDP port 636** (LDAPS, secure with TLS/SSL).

---

## Remote Authentication Dial-In User Service (RADIUS)
- AAA protocol (Authentication, Authorization, Accounting).
- Encrypts only the password (less secure than TACACS+).
- Uses:
  - **UDP port 1812** (authentication).
  - **UDP port 1813** (accounting).

---

## Remote Desktop Protocol (RDP)
- Graphical remote access.
- Operates on **TCP port 3389**.

---

## Kerberos
- Authentication protocol using **tickets** (time-sensitive).
- Used in Active Directory.
- Provides mutual authentication.

---

## Diameter
- Successor to RADIUS.
- More robust AAA features.
- Operates on **TCP or SCTP port 3868**.

---

## Secure Real-Time Transport Protocol (SRTP)
- Provides encryption + authentication for **real-time voice/video**.
- Used in VoIP, streaming, video conferencing.
- Protects against eavesdropping and replay attacks.

---

# 🔐 AAA (Authentication, Authorization, Accounting)

- **Authentication** – Verifies identity (passwords, biometrics, MFA).  
- **Authorization** – Grants permissions (what user can do).  
- **Accounting** – Tracks user activity (logs, audits, billing).  

### Common AAA Protocols:
- **RADIUS** → UDP, encrypts only password.  
- **TACACS+** → TCP, encrypts entire packet.  

---

# 📑 Protocols & Ports Cheat Sheet

| Protocol | Port | Secure Version |
|----------|------|----------------|
| FTP | 20/21 (TCP) | FTPS (SSL/TLS), SFTP (SSH, 22) |
| SSH | 22 (TCP) | — |
| Telnet | 23 (TCP) | Replaced by SSH |
| SMTP | 25 (TCP) | 465 (SSL), 587 (STARTTLS) |
| DNS | 53 (UDP/TCP) | DNSSEC |
| DHCP | 67/68 (UDP) | — |
| TFTP | 69 (UDP) | — |
| HTTP | 80 (TCP) | HTTPS (443) |
| POP3 | 110 (TCP) | POP3S (995) |
| NTP | 123 (UDP) | — |
| IMAP | 143 (TCP) | IMAPS (993) |
| SNMP | 161 (UDP queries), 162 (UDP traps) | SNMPv3 (secure) |
| LDAP | 389 (TCP/UDP) | LDAPS (636) |
| TACACS+ | 49 (TCP) | — |
| RADIUS | 1812 (auth), 1813 (acct) (UDP) | — |
| RDP | 3389 (TCP) | — |
| Kerberos | 88 (TCP/UDP) | — |
| Diameter | 3868 (TCP/SCTP) | — |
| SRTP | Dynamic | — |

---


