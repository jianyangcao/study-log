# Module 1 – General Security Concepts

---

## 1.1 CIA Triad

- **Confidentiality** → Keep data secret  
  - Issues:  
    - Social engineering  
    - Sniffing (unencrypted data)  
    - Media reuse  

- **Integrity** → Ensure data is not altered  
  - Mechanisms:  
    - Hash functions  
    - MACs (Message Authentication Codes)  
    - Digital signatures  

- **Availability** → Ensure services/data are accessible when needed  
  - Issues: DoS, DDoS, disasters  
  - Solutions:  
    - **Redundancy** → duplicate systems/components to avoid downtime  
    - **Content Delivery Networks (CDNs)** → distribute content across servers worldwide for speed/reliability  
    - **Data Dispersion** → break data into pieces, scatter, and later reconstruct (security + availability)  

---

## 1.2 Other Security Concerns

### ✍️ Non-Repudiation
- Proof of origin + proof of integrity → prevents denial of action  
- Provides assurance of sender + message integrity  
- Achieved via **digital signatures**  

### 🔑 Access Control
- **Identification** → Claim identity (username, ID)  
- **Authentication** → Prove identity (passwords, tokens, biometrics)  
- **Authorization** → Decide what actions are allowed  

**Access Control Models**  
- **DAC (Discretionary Access Control)** → owner controls access (ACLs, identity-based)  
- **MAC (Mandatory Access Control)** → based on classifications/labels  
- **RBAC (Role-Based Access Control)** → access via organizational role  
- **ABAC (Attribute-Based Access Control)** → access based on attributes (user, resource, environment)  

---

## 1.3 Security Controls

- **Definition**: Implementation/enforcement of CIA triad.  
- **Types**:  
  - **Technical (Logical)** → firewalls, encryption  
  - **Operational** → training, incident response  
  - **Managerial** → risk management, policies  
  - **Physical** → guards, locks, mantraps  

- **Functions**:  
  - Preventive  
  - Detective  
  - Corrective  
  - Deterrent  
  - Compensating  
  - Directive  

---

## 1.4 Zones of Trust

- **Security Zones**  
  - Group assets into zones with different trust levels  
  - Interfaces between zones require access control  
  - **DMZ (Demilitarized Zone)** → hosts public-facing services (web, mail, DNS) without exposing internal network  

- **Zero Trust**  
  - No inherent trust; each entity must authenticate individually  
  - Mitigates rogue processes/malware  
  - Often implemented by splitting network into **planes**  

- **Control Plane vs. Data Plane**  
  - **Control Plane (brains)** → makes decisions (routing, management)  
  - **Data Plane (muscles)** → forwards packets, enforces policies  

---

## 1.5 Policy Framework (PEP / PDP / PIP)

- **Policy Enforcement Point (PEP)**  
  - The “guard” → enforces access decisions, monitors connections  

- **Policy Decision Point (PDP)**  
  - The “brain” → evaluates policies and decides allow/deny  
  - PEP queries PDP for access decisions  

- **Policy Information Point (PIP)**  
  - Supplies additional info (user attributes, device health, environment)

# 1.6 Physical Security

## Site Layout and Access

* **Layers of security** – multiple barriers (fences, gates, checkpoints) slow attackers.
* **Zones with different access** – critical areas require stricter control.
* **ID badges** – confirm identity of staff/visitors.
* **Barriers and access points** – control entry to facilities.
* **Site layout** – designed for surveillance and controlled traffic.
* **Fencing** – establishes clear boundaries.

## Gateways and Locks

* **Lock types** – conventional, deadbolt, electronic, smart card, biometric, multifactor.
* **Turnstiles / Mantraps** – prevent tailgating, enforce one-at-a-time entry.
* **Unauthorized entry points** – windows, roof, or side doors must be secured.
* **Fail-safe vs Fail-secure** – fail-safe unlocks during power loss, fail-secure stays locked.

## Alarm Systems

* **Circuit alarms** – detect intrusion when a circuit is broken.
* **Motion sensors** – radar or infrared detect movement in a space.
* **Duress alarms** – silent/manual alerts for emergencies.

## Surveillance

* **Guard dogs** – deter intruders.
* **Security guards** – provide monitoring and response.
* **Video / CCTV** – continuous observation and recording.
* **Lighting** – discourages intrusion and aids cameras.
* **Physical access logs** – record who enters/exits.
* **Staff training** – employees enforce challenge policy.

## Hardware Security

* **Lockable cabinets** – secure networking gear.
* **Device locks** – prevent theft of laptops and PCs.
* **Safes** – protect sensitive items.
* **Protected distribution** – secure cabling against interception.

## Environmental Controls

* **Site location** – consider accessibility, utilities, hazards.
* **Building controls** – HVAC regulates dust, humidity, and temperature.

## Hot and Cold Aisles

* **Optimize airflow** – servers aligned front-to-front and back-to-back.
* **Hot/cold separation** – prevents mixing of hot exhaust with cooled air.

## RFI / EMI

* **Radio Frequency Interference (RFI)** – microwaves, motors, or wireless overlap cause errors.
* **Electromagnetic Interference (EMI)** – nearby equipment/cables create noise; mitigate with fiber or shielding.

## Fire Prevention

* **Prevention** – inspections, fire doors, remove flammable material.
* **Detection** – smoke/flame detectors with alarms.
* **Emergency procedures** – escape plans, evacuation routes, drills.

## Fire Suppression

* **Extinguishers** – for small/localized fires.
* **Sprinklers** – facility-wide protection (dry pipe, pre-action).
* **Clean agent systems** – safe suppression for sensitive equipment.

---

# 1.7 Change Management

## Baseline Configuration

* **Baseline** – minimum acceptable security settings.
* **Authorization required** – prevents vulnerabilities from unauthorized changes.

## Change Management

* **Even small changes matter** – can impact large systems.
* **Policy** – ensures a consistent process with testing.

## Change Management Process

1. Owner submits change request.
2. Change Control Board (CCB) reviews risk & cost/benefit.
3. Approve or deny request.
4. Approved change tested in non-production environment.
5. Schedule rollout and create rollback plan.
6. Rollout change.
7. Owner verifies results.
8. Schedule maintenance.
9. Update SOPs and documentation.

## Restricted Activities

* **Scope changes** – only allowed if properly documented and approved.

## Implications of Change Control

* **Possible impacts** – downtime, restarts, legacy failures, unavailable dependencies.

## Updating Documentation

* **Stay current** – include versioning, revisions, network diagrams, support docs, policies, and procedures.

## 1.8 Cryptography Basics

- **Security services provided by cryptography**  
  - **Privacy** – prevents unauthorized disclosure of information.  
  - **Authenticity** – verifies the claimed identity of the sender.  
  - **Integrity** – detects unauthorized modification or corruption of data.  
  - **Non-repudiation** – combines authenticity + integrity; a sender cannot deny sending a message.  

- **Core equation**  
  - Plaintext + Initialization Vector (IV) + Algorithm (cipher) + Key → Ciphertext  
  - Each element ensures encryption is unique and secure.  

---

## 1.9 Initialization Vectors (IVs)

- **Purpose** – IV adds randomness at the start of encryption so identical plaintexts don’t produce identical ciphertext.  
- **Randomness** – prevents attackers from spotting patterns, even with reused keys.  
- **Real-world example** – Cloudflare famously uses **lava lamps** to generate entropy for random numbers, since computers can only produce pseudo-random values.  

---

## 1.10 Algorithms and Keys

- **Algorithms** – mathematical functions used in encryption; must be strong and public (Kerckhoff’s principle).  
- **Keys** – provide instructions for using the algorithm; should be random, long enough, and kept secret.  
- **Terminology**:  
  - **Plaintext** – unencrypted data.  
  - **Initialization Vector (IV)** – randomness to strengthen encryption.  
  - **Algorithm** – the mathematical cipher itself.  
  - **Key** – secret input that makes the cipher unique.  

---

## 1.11 Symmetric Cryptography

- **Definition** – same key used for encryption and decryption.  
- **Pros** – very fast and efficient, good for bulk data transfer.  
- **Cons** – key distribution is difficult, doesn’t scale well, and cannot provide non-repudiation.  
- **Types**:  
  - **Stream ciphers** – encrypt data one bit at a time (fast, less secure, e.g., RC4).  
  - **Block ciphers** – encrypt fixed-size chunks using substitution/permutation functions (e.g., AES).  
- **Common algorithms** – DES, 3DES, AES, RC4, RC5, Blowfish, Twofish, IDEA, CAST, MARS, Skipjack.  

---

## 1.12 Asymmetric Cryptography

- **Definition** – uses a mathematically related key pair: public (shared) + private (kept secret).  
- **Property** – data encrypted with one key can only be decrypted by the other.  
- **Use case** – enables secure communication without pre-shared secrets.  

---

## 1.13 Authenticity

- **Asymmetric method** – the sender encrypts a small item (e.g., timestamp) with their private key.  
- **Verification** – the receiver decrypts with the sender’s public key, proving the message came from the sender’s private key.  

---

## 1.14 Integrity and Non-Repudiation

- **Hashing** – one-way, fixed-length representation of data; changes in data cause changes in the hash.  
  - **Collisions** – two inputs producing the same hash (rare, but possible).  
  - **Birthday attack** – exploits probability to find collisions more easily.  
  - **Common algorithms** – MD5 (128-bit), SHA-1 (160-bit), SHA-2 (256/384/512-bit), HAVAL, TIGER, RIPEMD.  

- **Digital signatures (non-repudiation)**  
  - Sender hashes the message → encrypts hash with private key.  
  - Receiver decrypts hash with sender’s public key → proves authenticity and integrity.  
  - **Digital signature = Encrypted hash with sender’s private key.**  

- **PAIN Model**  
  - **Privacy** → receiver’s public key.  
  - **Authenticity** → sender’s private key.  
  - **Integrity** → hash.  
  - **Non-repudiation** → hash encrypted by sender’s private key.  

---

## 1.15 Common Asymmetric Algorithms

- **RSA** – based on factoring large primes; standard for digital signatures; trapdoor function.  
- **DSA** – Digital Signature Algorithm, used for signing only.  
- **ECC (Elliptic Curve Cryptography)** – efficient for small devices; used for key agreement, signatures, pseudo-random generation.  
- **Diffie-Hellman** – first asymmetric algorithm; enables secure key exchange over insecure channels.  
- **ElGamal** – used for encryption and key exchange.  

---

## 1.16 Hybrid Cryptography

- **Concept** – combines asymmetric for key exchange with symmetric for bulk data encryption.  
- **Example (SSL/TLS Handshake)**:  
  1. Client requests secure site.  
  2. Server sends certificate with its public key.  
  3. Client generates symmetric session key.  
  4. Client encrypts session key with server’s public key.  
  5. Server decrypts with private key.  
  6. Both use the symmetric key for fast encrypted communication.  

---

## 1.17 Public Key Infrastructure (PKI)

- **Digital Certificates** – X.509 standard, bind public keys to identities, prevent MITM attacks.  
- **Components**:  
  - **Certificate Authority (CA)** – issues and signs certificates.  
  - **Registration Authority (RA)** – verifies requests before passing to CA.  
  - **Certificate Repository** – stores valid certificates.  
  - **Certificate Revocation List (CRL)** – list of revoked certificates.  
  - **OCSP (Online Certificate Status Protocol)** – real-time certificate validity check.  

---

## 1.18 Message Authentication Codes (MACs)

- **Integrity + authenticity** – confirm that data wasn’t modified.  
- **Hash alone** – only protects against accidental corruption.  
- **MAC** – uses a symmetric key + hash → reasonable authenticity, but no non-repudiation.  
- **Digital signature** – stronger, uses asymmetric keys for full non-repudiation.  
- **HMAC / CBC-MAC** – practical implementations of keyed hashing.  

---

## 1.19 Quantum Computing

- **Definition** – uses qubits, which can represent both 0 and 1 simultaneously (superposition).  
- **Comparison** – classical bits = 0 or 1; qubits = 0 and 1 at once → exponential power.  
- **Potential uses** – fast database search, AI, medicine, scientific simulations.  
- **Threat** – could brute-force current asymmetric algorithms like RSA and ECC.  

---

## 1.20 Blockchain

- **Definition** – distributed ledger that records transactions across many nodes.  
- **Integrity** – each transaction is verified and added to the chain; once recorded, it’s very hard to alter.  
- **Trust model** – enables untrusted parties to interact with confidence.  
- **Uses** – cryptocurrencies, supply chain tracking, digital asset integrity.  
---
  
  


  

---
