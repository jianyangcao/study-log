# Module 2 – Threats, Attacks, and Vulnerabilities

---

## 2.1 Threat Actors
Threat Actors:  
- Nation state -- Advanced Persistent Threats (APTs)  
- Unskilled attacker (script kiddies)  
- Hacktivist  
- Insider threat  
- Organized crime  
- Shadow IT  

Attributes of Threat Actors: internal vs external, resource/funding, motivation, capability  

Motivation: exfiltration, espionage, service disruption, blackmail/extortion, hacktivism  

---

## 2.2 Threat Vectors
Threat Vector: A means of creating a compromise and accessing a system  
- direct access  
- backdoor software  
- email  
- images  
- unsecure networks -- wired, wireless  
- supply chains (managed service providers, vendors, suppliers)  
- social engineering  

---

## 2.3 Social Engineering (Part 1)
What is social engineering: impersonation in order to gain access or information  
- non-technical means of gaining access to resources without being subjected to normal means of authentication  
- social engineers often use impersonation of an authorized party to gain trust or access  
- according to Webroot Inc., social engineering is responsible for approximately 93% of data breaches at financial institutions  

Social Engineering Attacks:  
- **Phishing**: an attempt by unauthorized entities posing as legitimate individuals, usually via email, to obtain sensitive information from an indiscriminate group of individuals. "If you cast a large enough net, you're going to catch some fish".  
  - spear phishing: phishing targeted to a specific group, organization, or demographic  
    - whaling: a type of spear phishing geared toward the senior leaders of an organization  
  - vishing/smishing: VOIP or SMS phishing  
- **Spam**: unrequested bulk messages sent in large quantities  
- **SPIM**: spam of instant messaging  
- **Bluejacking**: spam over Bluetooth  
- **Prepending**: adding information to a message to legitimize a message. For instance, adding "Re:" in the subject line makes it look like the message is a reply  
- **Pretexting**: An attacker presents a fabrication of a legitimate reason they would need access to a system or resource even though they've not been granted access  
- **Identity Fraud**: Using information (often obtained through social engineering attacks) to present oneself as another. Loans and even mortgages are often fraudulently obtained through this means  
- **Invoice Scams**: sending invoices purporting to be from legitimate companies in hopes that they will be paid without further investigation  
- **Hoaxes**: chain letters, promises of financial gain are types of hoaxes. Other hoaxes may suggest a user delete files or perform an action for what seems like a legitimate reason.  
- **Credential harvesting**: specifically designed to steal account and authentication credentials  
- **Reconnaissance Attack**: using publicly available sources to collect information  
- **Impersonation**: presenting oneself as another  
- **Watering hole attack**: inject malware through an insecure, frequently used third party. For instance, if users of an organization frequent a less secure site, an attacker may be able to introduce malware through the less secure site  
- **Typosquatting**: registering a domain name similar to a legitimate site in hopes that users will mistype the correct location and wind up on a spoofed site  
- **Dumpster diving**: retrieving information from a user or organization’s trash or recycling or some other discarded material  
- **Shoulder surfing**: looking over an authorized user's shoulder hoping to see sensitive information like passwords or PINs  
- **Tailgating**: following an authorized user into a secure area without having to provide credentials  
- **Piggybacking**: similar to tailgating, except the authorized user willingly allows the attacker to access the area  

---

## 2.4 Social Engineering (Part 2)
Influence Campaigns:  
- Large scale program, often launched by a hostile nation  
- Geared towards swaying public opinion  
- Often used in an attempt to sway election results  
  - hybrid warfare includes both traditional and social means to accomplish the same military goals  
  - social media is frequently exploited by bots and used to spread misinformation  

Principles (Reasons for Effectiveness):  
- Authority  
- Intimidation  
- Consensus  
- Scarcity  
- Familiarity  
- Trust  
- Urgency  

---

## 2.5 Indicators of Attacks

### Malware Threat Vectors
- Threat Vectors: describes how the malicious code is replicated and spread  
- Viruses: usually require a host file and user interaction (fileless viruses do not need a host)  
- Worms: a memory resident type of malware that can self-propagate and does not need a host file  
- Trojans: present themselves as a desirable application or tool, yet contain malware  
- PUPs/PUAs (Potentially Unwanted Programs/Applications): software that is installed in addition to the app the user has chosen. Sometimes called grayware, as it is not necessarily malicious  
- Other classifications are determined by the payload. For instance, a RAT (Remote Access Trojan) can be delivered by a trojan.  

### Unauthorized Access
- Backdoor: network software that opens a port on the compromised system. The host is then "listening" for traffic on the port and allows access to the system, bypassing normal authentication methods  
- RATs: a type of backdoor software that allows covert administrative access to a system  
- Bot: an automated script or tool that performs malicious activity  
- Botnet: a collection of systems controlled by the same threat actor  
- Command and Control (C2 or C&C): host or network that communicates with the exploited hosts  
- Rootkit: operates at executive level or can be used to escalate privileges  

### Ransomware
- Ransomware: computer-based attack that allows an attacker to extort money from the victim. May display threatening messages in relation to illegal activities supposedly performed on the compromised system  
- Cryptomalware: encrypts critical systems or files and requires the user to pay a fee or ransom in exchange for the key, which will unlock the encrypted files  
- Logic and Time Bombs (not all malware runs immediately)  
  - Time bombs wait until a specific date or time to unleash the payload of the attack  
  - Logic Bombs wait until a logical event, such as the tenth time a file is accessed, before delivering the payload  

### Spyware
- Spyware: malware used to track the activities of users  
- Tracking cookies: plain text files stored on the user's system that can record pages visited, purchases made, shopping cart contents, search queries, etc., often used in conjunction with adware  
- Adware: often reconfigures browsers to target marketing to an individual based on previous activities. May reconfigure browser to load an ad-filled home page  
- Keylogger: records keystrokes  

### Attacks on Passwords
- Dictionary: every word in a file  
- Brute Force: every combination of characters  
- Hybrid: every word in file plus some frequently used character combinations  
- Rainbow table: stored results from a brute force attack matched against the password hash. MUCH faster than running the brute force attack itself  
- Plaintext/unencrypted databases or protocols  
- Spraying: attempting a common password like "Password1" to numerous accounts  

### Physical Security Threats
- Malicious USB cable: can act as a skimmer over legitimate charging stations at public locations such as airports  
- Flash Drives: can provide the means to distribute malware, as well as to remove sensitive information  
- Card Cloning: making multiple copies of an existing card  
- Skimming: installing a counterfeit card reader over a legitimate device  

### Adversarial AI
- AI can be used to analyze activities of users and systems  
- Tainted Training Data For ML: AI systems "learn" based on data retrieved from customer systems and security devices like honeypots. By injecting spurious code or traffic into training environment, an attacker can corrupt the learning process, therefore rendering the AI software skewed  
- ML Algorithms: ML algorithms can be targeted, just as others  

### 3rd Party Attacks
- Supply Chain: compromising elements of a system provided by another party. For instance, if the processor is compromised at the vendor, then the system will never be secure. Could also exploit 3rd party access to a system or environment  
- Cloud-based attacks: attacks at the CSP (cloud service provider) itself or protocols/apps/accounts used to access and transmit data to and from CSP  
- Poorly written APIs (application programming interfaces)  

### On-Premises vs Cloud-Based Attacks
- Most risks are similar, but it is the location/responsibility for risk management that varies  
  - Facility Security  
  - Hardware/Software Vulnerabilities  
  - Malicious Insiders  
  - Weak Configurations  
  - 3rd party issues  

### Cryptographic attacks
- Collision Attacks: attempting to create a cryptographic collision to identify another series of characters that will produce the same hash as the legitimate password  
- Birthday Attacks: attempts to cause a collision based on the fact that it is mathematically infeasible to cause collisions with a specific hash, and that it is more likely to find two hashes that just happen to match. Again, mathematically infeasible but more probable  
- Downgrade Attacks: requests access to the server at a lower level of security than the default in hopes that passwords would be transmitted in a less secure manner  

### Pass the Hash
- Password Hashes are stored in protected memory on systems  
- If these hashes are accessed by an attacker (who would need administrative rights to do so), then the attacker may be able to exploit the SSO authentication to use the hashes elsewhere to authenticate  
- There may be numerous hashes stored in memory, for instance, the current user, remote users, service accounts  
- Users should not have debug privileges or be administrators on their local machines  

---

## 2.6 Indicators for Application Attacks
**Code Injection**: an attack where an attacker supplies malicious input into a program, and the program mistakenly executes it as code. (SQL, DLL, LDAP, XML)  
- Input validation and sanitization can be used to mitigate risk of code injection  
- Fuzzing tests application for weak input control  

---

## 2.7 Cross-Site Attacks
**Cross-Site Scripting: Persistent**  
1. Adversary finds a site vulnerable to script injection  
2. Adversary injects site with malicious script that steals user's session cookies  
3. User activates malicious script each time they access the site  
4. User's session cookie is sent to adversary  

**Cross-Site Scripting: Reflective (Non-Persistent)**  
1. Adversary sends URL with malicious string to User  
2. User tricked into opening link and requesting malicious URL from site  
3. Site includes malicious string in its response to User  
4. User's browser interprets malicious script as part of the legitimate webpage and executes the code  
5. User's sensitive information is sent to adversary's server  

**Cross-Site Request Forgery (XSRF)**  
1. Adversary forges a request for a fund transfer to a site  
2. Adversary embeds request in a link and sends it to users who may be logged in to site  
3. User clicks link, unintentionally sending request to site  
4. Site validates request and transfers funds from the visitor's account to the adversary  

Cross-Site Scripting (XSS) takes advantage of a user's trust in a website.  
XSRF takes advantage of a website's trust in a user.  

---

## 2.8 Timing Attacks
- Physical Access: Gain access to a location before security requirements are verified  
- Race Conditions: Technical in nature. Revolve around technical timing exploits  
- TOC/TOU: Time of Check/Time of Use  
  - Example:  
    ```
    3*5+10
    process 1: multiplication  
    process 2: addition
    ```
    Ideally, process 1 needs to be performed because multiplication takes precedence. Result = 25  
    However, if process 2 takes place first, the result will be different (something not in order)  

- Replay Attacks: traffic is captured and then used again later  
  - Password Replays / Session Replays  

- Error Handling  
  - As a result of a violation of system policy, the system should respond in a fail-secure manner  
  - Processes should terminate in such a way that no further compromise can happen  
  - Error messages should not disclose too much information to the attacker  

---

## 2.9 Memory Issues
- Integer Overflow: Values out of expected range  
- Memory Leak: Application does not release its memory as expected  
- Buffer Overflow: More entries than expected

## 2.10 Network-based Attacks

---

### Network-based attacks
- **Port scans**  
- **XMas Scans** → sends a packet with all flags set in a combination normal conversation never uses – can be used to determine operating system and open ports  
- **Man-in-the-middle** → attacker inserts himself into a communication path  
  - Passive → sniffing  
  - Active → session hijack  
- **Fuzzing** → attempting to inject code in vulnerable applications; also used in software penetration testing  
- **Banner grabbing** → some network services return information in response to a service request  

---

### Spoofing
- IP spoofing  
- MAC spoofing / cloning  
- Email spoofing  
- Caller ID spoofing  
- Smurf attacks  
- Fraggle attacks  

---

### Redirection
- **ARP (Address Resolution Protocol)**  
  - Poisoning  
- **DNS**  
  - Rogue infrastructure  
  - Poisoning  
  - Pharming  
  - Hosts file  
- **URL redirection**  

---

### Wi-Fi
- Wardriving / Warchalking  
- Encryption  
- Sniffing  
  - WEP  
  - WPA  
  - WPA II  
- WPS attacks  
- Rogue Access Points / Evil Twins  
- Disassociation / Deauthentication  
- Jamming  

---

### Bluetooth
- Bluejacking  
- Bluesnarfing  
- Bluebugging  

## 2.11 Indicators of Attacks

- Account Lockouts  
- Concurrent Sessions  
- Blocked Content  
- Impossible Travel  
- Resource Consumption  
- Out-of-cycle Logging  
- Missing Logs  

---

## 2.12 Mitigation Techniques

- **Segmentation**  
  - Isolation of "trusted" resources from "untrusted" entities  
  - Network Segmentation  
  - APIs (Application Programming Interfaces)  
  - Firewalls  
  - "Zero Trust"  

- **Access Control Lists**  
  - Firewalls  
  - Permissions  
  - Principle of Least Privilege (POLP)  

---

## 2.13 Security Assessments

### Vulnerability Management Activities
- **Vulnerability Scanner** → scans devices on your network to see what areas might be vulnerable.  
  - May test known exploits, missing patches, misconfigured settings, and defaults.  
  - Examples: Nikto, Nessus  

**Critical components of a Vulnerability Scanner**  
- **Credentials**  
  - Uncredentialed Scan → no trusted access  
  - Credentialed Scan → requires login, deeper access  
- **Agent / Agentless** → runs with or without local agents  
- **Intrusive / Non-intrusive**  
  - Non-intrusive → identifies and reports vulnerability  
  - Intrusive → attempts to exploit found vulnerability  

- **Patch Management**  
  - Identifies missing updates/patches (OS, firewalls, switches firmware)  
  - Installs updates to keep systems secure  

- **Risk Assessment** → helps find areas not previously considered vulnerable  

### Vulnerability Information Sources
- **Advisories** → specific data on identified vulnerability  
- **Bulletins** → summaries/newsletters of advisories  
- **Information Sharing and Analysis Centers (ISACs)** → nonprofit sector-specific groups  
- **News Reports** → articles or headlines  

### Security Content Automation Protocol (SCAP)
- A suite of interoperable specs to standardize naming/formatting of vulnerabilities.  
- Open standards to enumerate flaws and configuration issues.  

**SCAP Languages**  
- **OVAL (Open Vulnerability and Assessment Language)** → collects and assesses system info, machine state, reporting  
- **ARF (Asset Reporting Format)** → correlates reporting formats to device info  
- **XCCDF (Extensible Configuration Checklist Description Format)** → XML format for benchmarks/checks  

**SCAP Identification Schemes**  
- **CPE (Common Platform Enumeration)** → standardized naming of systems/software  
- **CVE (Common Vulnerabilities and Exposures)** → list of known vulnerabilities (format: CVE-YEAR-XXXX)  
- **CCE (Common Configuration Enumeration)** → focuses on configuration issues  

### Honeypots
- **Deployment**  
  - Pseudo flaws → loopholes purposely added to trap intruders  
  - Sacrificial lamb system → enticing target with open ports and services  
  - Goal → attackers target honeypot instead of production systems  

- **Enticement vs. Entrapment** → honeypots must be careful not to cross legal/ethical boundaries  

### Log Reviews
- Examine system log files for events or control effectiveness  
- **Standardize time** → use NTPv4 (RFC 5905) across devices  
- Logs often stored locally → harder to correlate events  
- Limited size → risk of overwrite or stop logging  
- **Syslog** → standard protocol to send text logs to central server  

### Security Information and Event Managers (SIEMs)
- Centralize, correlate, retain event data → generate alerts  
- Provide dashboard highlighting incidents  
- Analysts investigate and act  
- Useful for forecasting and trend analysis  

### Unified Threat Management (UTM) Systems
- All-in-one solution:  
  - Firewall  
  - Proxy  
  - NAT/PAT  
  - Web Filtering  
  - Wi-Fi Security  

---

## 2.14 Monitoring Sources

- SIEM devices  
- IDS / IPS  
- File Integrity Monitoring (FIM)  
- Data Leak / Loss Prevention (DLP)  
- Antivirus (AV)  
