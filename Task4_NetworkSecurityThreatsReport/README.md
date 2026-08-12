# OIBSIP — Security Analyst Internship Tasks

**Author:** Lehlogonolo Elizabeth Mpye  
**Track:** Cyber Security (Security Analyst)  
**Program:** AICTE Oasis Infobyte Internship Program (OIBSIP)  
**Submission Deadline:** 15 September 2026  

---

## 📌 Repository Overview

This repository houses all deliverables, code, scripts, and reports completed during my **Security Analyst Internship** at **Oasis Infobyte**. Each task focuses on core security operations, threat analysis, network traffic monitoring, and vulnerability management.

---

## 📁 Project Deliverables

### Task 4 — Research Report: Common Network Security Threats
* **Status:** Completed
* **Deliverable File:** [`network_security_threats_report.pdf`](./network_security_threats_report.pdf)
* **Description:** A comprehensive research report examining four critical network security threats:
  1. **Denial-of-Service (DoS / DDoS) Attacks**
  2. **Man-in-the-Middle (MITM) Attacks**
  3. **IP Spoofing**
  4. **DNS Poisoning / Spoofing**

#### Key Report Highlights & Case Studies
* **DoS/DDoS Attacks:** Analyzes volumetric, protocol, and application-layer attacks. Analyzes the **2016 Mirai Botnet Attack on Dyn**, which impacted over 50 major web services (Twitter, Netflix, Spotify).
* **Man-in-the-Middle (MITM) Attacks:** Details ARP spoofing, TLS stripping, and rogue access points. Covers the **2011 DigiNotar Certificate Authority Breach**, where forged SSL certificates compromised Google domain traffic.
* **IP Spoofing:** Examines source address forgery and TCP handshake hijacking. Highlights the **2006 Florida Banks Incident**, where compromised routing enabled financial credential harvesting.
* **DNS Poisoning:** Covers cache corruption mechanics and reviews the **2015 Malaysia Airlines DNS Redirection Attack**.

#### Summary Matrix

| Threat Vector | Attack Mechanism | Primary Target / Risk | Difficulty to Execute | Ease of Mitigation |
| :--- | :--- | :--- | :--- | :--- |
| **DoS / DDoS** | Resource/traffic flooding via botnets | Internet-facing services, DNS providers | Low–Medium | Medium (Cloud scrubbers, CDNs) |
| **MITM** | Interception between communicating endpoints | Unencrypted public Wi-Fi & HTTP traffic | Medium | Medium–High (TLS 1.3, HSTS, VPNs) |
| **IP Spoofing** | Source packet header forgery | Unfiltered networks; DDoS amplifier | Medium | Medium (Ingress/Egress BCP 38 filtering) |
| **DNS Poisoning** | Corrupting DNS cache resolution | Unencrypted DNS resolution workflows | Medium–High | High (DNSSEC, DoH / DoT implementation) |

#### 💡 Key Takeaways for Network Administrators
1. **Protect Availability & Confidentiality:** DoS threatens uptime, while MITM, IP spoofing, and DNS poisoning degrade trust and confidentiality. Defense strategies must address both.
2. **Standardize Encryption & Verification:** Universal adoption of TLS, DNSSEC, DoH/DoT, and strict packet filtering prevents identity impersonation.
3. **Defense-in-Depth Prevents Attack Chaining:** Threat vectors rarely occur in isolation; IP spoofing and DNS poisoning are frequently chained to execute credential harvesting.

---

## 📚 Primary References

1. **CISA, FBI, MS-ISAC:** *Understanding and Responding to Distributed Denial-of-Service Attacks.*
2. **NIST Special Publications & MITRE ATT&CK Framework.**
3. **DigiNotar & Dyn Real-World Breach Analysis Reports.**

---

## ⚙️ Submission Compliance Checklist
- [x] Official repository naming convention followed (`OIBSIP`)
- [x] File named according to guidelines (`LehlogonoloMpye_Task4.pdf` / `network_security_threats_report.pdf`)
- [x] Clear documentation and structured README included
