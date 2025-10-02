# 1. Walking an Application #

---

# 2. Content Discovery #

---

# 3. subdomain enumeration #
**Subdomain enumeration** is the process of finding valid subdomains for a domain to expand our attack surface to try and discover more potential points of vulnerability.
## 3.1 OSINT - SSL/TLS Certificates ##
- When an SSL/TLS certificate is issued by a Certificate Authority (CA), it is logged into Certificate Transparency logs.
- These logs are publicly accessible and list every certificate issued.
- Purpose: Prevent malicious or accidental misuse of certificates.
- Tool: [crt.sh](https://crt.sh) → allows searching CT logs.
## 3.2 OSINT - Search Engines ##
- Search engines index billions of links → can be leveraged for OSINT subdomain discovery.
- Use advanced operators:
- ```bash
  site:*.domain.com -site:www.domain.com
This shows subdomains of domain.com while excluding the www version.
## 3.3 DNS Bruteforce ##
## 3.4 OSINT - Sublist3r ##
## 3.5 Virtual Hosts ##
