# 5.1 Framework and Standards

---

## General Data Protection Regulation (GDPR)
- EU regulation focused on **data protection and privacy**.  
- Key points:
  - Right to access and erase data.  
  - Requirement for breach notifications.  
  - Penalties for non-compliance.  

---

## ISO 27000 Series (Information Security Management)
- Provides international standards for **information security management systems (ISMS)**.  

- **ISO 27001**: Requirements for establishing an ISMS.  
- **ISO 27002**: Security controls best practices.  
- **ISO 27003:2017**: Implementation guidance.  
- **ISO/IEC 27004:2016**: Information security measurement.  
- **ISO 27005**: Risk management.  

📌 *Explanation*: ISO 27000 series helps organizations **manage and certify** information security practices.  

---

## Cloud Security Alliance (CSA)
- Provides **best practices for cloud security**.  
- Known for:  
  - **Security Guidance** – Cloud-specific security recommendations.  
  - **Enterprise Reference Architecture** – Framework for secure cloud deployments.  
  - **Cloud Controls Matrix (CCM)** – Security controls mapped to industry standards.  

---

## ISO 31000
- **Enterprise Risk Management Framework**.  
- Provides guidance on risk assessment, management, and governance.  

---

## SSAE / SOC
- **SSAE** (Statements on Standards for Attestation Engagements).  
- **SOC (Service Organizational Controls)** reports:  
  - **SOC 1** – Financial reporting controls.  
  - **SOC 2** – Security, availability, processing integrity, confidentiality, privacy.  
  - **SOC 3** – Public SOC 2 summary for marketing purposes.  

---

## Center for Internet Security (CIS)
- Provides **CIS Controls** and **CIS Benchmarks** for secure configurations.  
- Widely used for system hardening and compliance.  

---

## NIST (National Institute of Standards and Technology)
### NIST Cybersecurity Framework (CSF)
Organized into **five core functions**:
1. **Identify**: Asset management, business environment, governance, risk assessment.  
2. **Protect**: Access control, awareness & training, data security, maintenance, protective technologies.  
3. **Detect**: Anomalies, continuous monitoring, detection processes.  
4. **Respond**: Response planning, communications, analysis, mitigation, improvements.  
5. **Recover**: Recovery planning, improvements, communication.  

📌 *Explanation*: NIST CSF is a **high-level framework** used by U.S. government and private sector to manage cybersecurity risk.  

---

### NIST 800-37 (RMF Revision 1)
**Risk Management Framework** steps:
1. Categorize information systems.  
2. Select security controls.  
3. Implement security controls.  
4. Assess security controls.  
5. Authorize information systems.  
6. Monitor security state.  

📌 *Explanation*: NIST RMF is more **detailed and operational** than CSF. Often used in federal government compliance (e.g., FedRAMP, FISMA).  

---

## Benchmarks and Secure Configuration Guides
- **Vendor-specific materials** (e.g., Microsoft, Cisco security baselines).  
- **NCP (National Checklist Program)** – NIST repository of secure configuration checklists.  
- **DoD STIGs (Security Technical Implementation Guides)** – Department of Defense hardening guides.  
- **OWASP** – Focus on web application security (e.g., OWASP Top 10 vulnerabilities).  
- **CIS Benchmarks** – Industry-standard secure configurations.  

---

## ✅ Cheat Sheet
- **GDPR** → EU data privacy law.  
- **ISO 27000** → International ISMS standards.  
- **CSA** → Cloud security best practices (Cloud Controls Matrix).  
- **ISO 31000** → Risk management framework.  
- **SSAE / SOC** → Attestation and service control reports.  
- **CIS** → Secure configuration benchmarks.  
- **NIST CSF** → Identify, Protect, Detect, Respond, Recover.  
- **NIST RMF** → Categorize → Select → Implement → Assess → Authorize → Monitor.  
- **STIGs / OWASP / CIS** → Hardening and application security guides.  

---

# 5.2 Organizational Security Policies

Organizational security policies define **how people, processes, and technology are governed** to maintain security.

---

## Personnel Policies
- **Acceptable Use Policy (AUP)**  
  - Defines how enterprise resources (devices, internet, email) are to be used properly.  

- **Job Rotation**  
  - Employees transition between jobs to gain exposure to multiple areas.  
  - Also acts as a **detective control** (prevents fraud by ensuring no one person always controls a process).  

- **Mandatory Vacation**  
  - Common in banking/finance as a **detective control**.  
  - Fraud may be discovered when someone else takes over responsibilities.  

- **Separation of Duties (SoD)**  
  - Splits responsibilities so no single person has excessive control.  
  - Prevents fraud and collusion.  

- **Least Privilege**  
  - Users are granted only the minimum privileges needed to perform their job.  

- **Clean Desk Policy**  
  - Desks cleared of sensitive materials when unattended.  

- **Non-Disclosure Agreement (NDA)**  
  - Legally binding agreement preventing disclosure of proprietary information.  

- **Onboarding/Offboarding**  
  - Procedures for granting and revoking access when employees join or leave.  

- **User Training / Computer-Based Training (CBT)**  
  - Includes awareness campaigns, phishing simulations, capture-the-flag exercises, and gamification.  

---

## Third-Party Management
- **Vendors** – Security requirements for suppliers.  
- **Supply Chain** – Security checks for product integrity and sourcing.  
- **Business Partners** – Ensure partners meet security obligations.  
- **Service Level Agreement (SLA)** – Defines expected service performance.  
- **Memorandum of Understanding (MOU)** – Formal but non-legally binding agreement.  
- **Business Partnership Agreement (BPA)** – Defines partner obligations and responsibilities.  
- **End of Life (EOL)** – Product no longer sold or supported.  
- **End of Service Life (EOSL)** – Product no longer supported at all (no patches).  
- **NDA** – Protects proprietary/shared information in partnerships.  

📌 *Explanation*: Third-party management ensures outside vendors and partners don’t introduce risks.  

---

## Data Policies
- **Classification** – Defines sensitivity levels (public, internal, confidential, secret).  
- **Governance** – Policies on ownership and stewardship of data.  
- **Retention** – Defines how long data must be kept and how it should be securely destroyed.  

---

## Credential Policies
- **Personal** – Individual user accounts.  
- **Third-Party** – Vendor or external accounts.  
- **Device Accounts** – Used for device authentication (e.g., printers, IoT).  
- **Service Accounts** – Used by applications or services, not people.  
- **Administrator/Root Accounts** – Privileged accounts requiring strict control.  

---

## Organizational Processes
- **Change Management**  
  - Formal process for requesting, reviewing, approving, and documenting changes.  

- **Change Control**  
  - Focuses on ensuring changes are **tested, reviewed, and approved** before implementation.  

- **Asset Management**  
  - Tracking and managing organizational assets (hardware, software, data).  
  - Ensures assets are properly secured and maintained.  

---

# 5.3 Information Security Risk Management (ISRM)

**ISRM**: The process of managing risks associated with the use of information technology.  
- Involves **identifying, assessing, and treating risks** to the **confidentiality, integrity, and availability (CIA)** of an organization’s assets.

---

## Key Definitions

- **Asset**: Anything of value to the company (e.g., data, systems, reputation).  
- **Vulnerability**: A weakness; the absence of a safeguard (e.g., unpatched software).  
- **Threat**: Something that could cause a loss to an asset (e.g., ransomware, flood).  
- **Threat Agent**: The entity that carries out the attack (e.g., hacker, malware).  
- **Exploit**: An instance of compromise — when a vulnerability is successfully used.  

- **Risk**:  
  - The probability of a threat exploiting a vulnerability **and the resulting impact**.  
  - *Formula*:  
    ```
    Risk = Likelihood × Impact
    ```

- **Controls**: Protections to reduce risk.  
  - **Safeguards** → Deterrents or preventives.  
  - **Countermeasures** → Detective or corrective actions.  

---

## Types of Risk
- **Total Risk**: Risk that exists before any controls are applied.  
- **Residual Risk**: Risk left over after controls are implemented.  
- **Secondary Risk**: A new risk that emerges as a result of applying a control.  

---

## Incident
- **Incident**: A risk event that has occurred (i.e., an attack or compromise that has already transpired).  

---

# 5.4 The Risk Management Lifecycle

Risk management involves **identifying, assessing, mitigating, and monitoring risks**.  

---

## 1. Risk Identification
- *Formula*:  
```
Asset Value (AV) × Threat × Vulnerability = Risk
```
- At this stage, risks are identified (risk register is created).  
- Models used:
- **STRIDE** (Threats: Spoofing, Tampering, Repudiation, Information Disclosure, DoS, Elevation of Privilege).  
- **DREAD** (Vulnerabilities scored: Damage potential, Reproducibility, Exploitability, Affected users, Discoverability).  

---

## 2. Risk Assessment / Analysis / Evaluation

### Qualitative Assessment
- **Subjective** analysis (high, medium, low).  
- May use Delphi technique (expert consensus).  
- Inexpensive, quick way to prioritize risks.  

### Quantitative Assessment
- **Objective** analysis, assigns dollar values to risk events.  
- More difficult, requires expertise, but supports business decisions.  
- Relies on both qualitative + empirical data.

**Key Terms:**
- **AV (Asset Value)** – Dollar value of an asset.  
- **EF (Exposure Factor)** – % of loss expected if event occurs.  
- **SLE (Single Loss Expectancy)** – AV × EF → cost of one incident.  
- **ARO (Annual Rate of Occurrence)** – How often a threat is expected to occur.  
- **ALE (Annual Loss Expectancy)** – SLE × ARO → yearly cost of risk.  
- **TCO (Total Cost of Ownership)** – Cost of implementing safeguard (initial + ongoing).  
- **ROI (Return on Investment)** – Money saved by implementing safeguard.  

**Process Steps:**
1. Assign AV.  
2. Calculate EF.  
3. Calculate SLE.  
4. Assess ARO.  
5. Drive ALE.  
6. Perform cost/benefit analysis of controls.  

---

## 3. Risk Mitigation / Response

### Options:
- **Risk Reduction / Avoidance**
- Lessen frequency/impact of risk.  
- Examples:  
  - Stronger security processes.  
  - New access control systems.  
  - Incident response plan & BCP (Business Continuity Plan).  
  - Compensating controls.  

- **Risk Transference**
- Share the risk with another org.  
- Examples: Insurance, SLA clauses, outsourcing.  
- ⚠️ Liability cannot be fully transferred.  

- **Risk Acceptance**
- Do nothing beyond monitoring.  
- Chosen when cost of mitigation > potential loss.  
- Still requires documentation and due diligence.  

---

## 4. Risk Monitoring / Reporting
- Ongoing monitoring is essential because:  
- Controls can weaken over time.  
- Environments, threats, and vulnerabilities change.  
- Risk level and impact are not static → **continuous review needed**.  

---

# 5.5 Classification of Sensitive Data

---

## Considerations for Determining an Asset’s Value
- Value to the organization.  
- Loss if compromised (financial, operational, reputational).  
- Legislative/regulatory requirements.  
- Legal liabilities.  
- Value to competitors.  
- Acquisition/replacement costs.  
- Other strategic importance.  

---

## Data Classification
- Development of **sensitivity labels** for data.  
- Assign labels to configure **baseline security** based on value.  
- Cost: classification should reflect the **value of the data**.  
- Classification determines:  
  - Security configuration baseline.  
  - Access control requirements.  
  - Retention & destruction policies.  

### Roles
- **Data Owner**: Determines classification of data.  
- **Data Custodian**: Maintains and enforces controls (storage, access, encryption, backups).  

---

## Government & Military Classification
- **Top Secret** – Grave damage if disclosed.  
- **Secret** – Serious damage if disclosed.  
- **Confidential** – Damage if disclosed.  
- **Sensitive but Unclassified (SBU)** – Limited harm.  
- **Unclassified** – Minimal impact.  

---

## Private Sector Data Classification
- **Confidential** – Business-critical, limited access.  
- **Private** – Personal/employee information.  
- **Sensitive** – Needs protection but less critical.  
- **Public** – No restriction, freely shareable.  

---

## Data Roles
- **Data Owner**  
  - Senior role with ultimate responsibility for **confidentiality, integrity, and availability (CIA)**.  
  - Decides classification and access levels.  

- **Data Custodian / Steward**  
  - Manages the system hosting the data.  
  - Enforces access control, encryption, backup/recovery.  

---

## Regulatory Roles (Privacy/GDPR Context)
- **Data Controller**  
  - Entity responsible for determining **why and how** data is collected, stored, and used.  
  - Ensures compliance with law.  
  - Holds ultimate responsibility for privacy breaches.  

- **Data Processor**  
  - Processes data **on behalf of the controller**.  
  - Handles technical tasks: collection, storage, analysis.  
  - Must follow the controller’s instructions.  

---

## ✅ Cheat Sheet
- **Government labels** → Top Secret > Secret > Confidential > SBU > Unclassified.  
- **Private sector** → Confidential > Private > Sensitive > Public.  
- **Roles**:  
  - Data Owner = decides classification.  
  - Data Custodian = enforces security & operations.  
  - Data Controller = defines purpose/means (legal responsibility).  
  - Data Processor = executes tasks under controller’s instruction.  
