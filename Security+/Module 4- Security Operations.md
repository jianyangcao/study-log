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

  
