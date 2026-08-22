# Task 1 — Basic Network Scanning with Nmap
 
**OIBSIP — Security Analyst Track**
**Analyst:** Lehlogonolo Mpye
**Tool:** Nmap 7.99 on Kali Linux 2026.2 (VMware)
 
---
 
## Objective
Perform a network scan to identify open ports and services running on a local machine or virtual machine using Nmap, and document findings with security analysis.
 
---
 
## What is Nmap?
Nmap (Network Mapper) is a free, open-source tool used to discover devices on a network and identify what services and ports are active on them. It's one of the most widely used tools in cybersecurity for reconnaissance — figuring out what's actually running on a system before deciding how to secure it (or, from an attacker's perspective, how to attack it).
 
## Why Network Scanning Matters
Before you can secure a system, you need to know what's exposed on it. Every open port represents a potential entry point — a running service that could have a vulnerability, weak configuration, or default credentials. Network scanning is the first step in both offensive security (penetration testing) and defensive security (knowing your own attack surface). SOC analysts and security teams use scanning regularly to build an accurate picture of what's actually running across their environment, rather than what's assumed to be running.
 
## Ethical Use Guidelines
Only scan machines you own or have explicit permission to scan. All scans in this task were performed against `localhost` on a personal Kali Linux VM set up specifically for this exercise — no external, third-party, or production systems were scanned at any point.
 
---
 
## Installation
 
Nmap comes pre-installed on Kali Linux, so no separate installation was required. Verified with:
 
```bash
nmap --version
```
 
Output:
```
Nmap version 7.99 ( https://nmap.org )
```
 
---
 
## Scans Performed
 
### 1. Basic Scan
**Command:**
```bash
nmap localhost | tee nmap_basic.txt
```
 
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-08-18 08:03 -0400
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000059s latency).
Other addresses for localhost (not scanned): ::1
All 1000 scanned ports on localhost (127.0.0.1) are in ignored states.
Not shown: 1000 closed tcp ports (reset)
 
Nmap done: 1 IP address (1 host up) scanned in 0.40 seconds
```
 
---
 
### 2. Service Version Scan
**Command:**
```bash
nmap -sV localhost | tee nmap_service.txt
```
 
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-08-18 08:04 -0400
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0000050s latency).
Other addresses for localhost (not scanned): ::1
All 1000 scanned ports on localhost (127.0.0.1) are in ignored states.
Not shown: 1000 closed tcp ports (reset)
 
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.10 seconds
```
 
---
 
### 3. OS Detection Scan
**Command:**
```bash
sudo nmap -O localhost | tee nmap_os.txt
```
 
**Output:**
```
Starting Nmap 7.99 ( https://nmap.org ) at 2026-08-18 08:04 -0400
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000093s latency).
Other addresses for localhost (not scanned): ::1
All 1000 scanned ports on localhost (127.0.0.1) are in ignored states.
Not shown: 1000 closed tcp ports (reset)
Too many fingerprints match this host to give specific OS details
Network Distance: 0 hops
 
OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 2.12 seconds
```
 
---
 
## Findings & Security Analysis
 
### Open Ports Summary
 
| Port | Service | Status |
|------|---------|--------|
| — | — | No open ports detected across 1000 scanned ports |
 
**No open ports were found on this system.** This is a legitimate and expected result for a freshly installed Kali Linux VM with no services manually configured or started — there is currently nothing listening for external connections on `localhost`.
 
### Analysis
 
This is actually a secure baseline: an idle system with zero exposed services has effectively no network-based attack surface at the time of scanning. That said, it's worth noting the broader security context that a SOC analyst would apply to a result like this:
 
- **In a real environment, "all closed" is only good news if that's the expected state.** If a host is *supposed* to be running a service (e.g., a web server that should have port 80/443 open, or an SSH server that should have port 22 open) and a scan comes back with everything closed, that's a red flag — it could indicate the service crashed, was misconfigured, was intentionally taken down by an attacker to cover tracks, or the host has become unreachable. Closed ports on a system that should have open ones is itself worth investigating, not just an open port on a system that shouldn't have one.
- **OS detection returning inconclusive is normal for loopback/localhost scans.** OS fingerprinting relies on analyzing subtle variations in how a real network stack responds to specially crafted packets sent across an actual network path. Traffic looped back to the same machine doesn't always generate those distinguishing signals cleanly, which is why Nmap reported "too many fingerprints match this host" rather than a confident OS guess.
- **Network Distance: 0 hops** confirms this was a loopback scan (scanning the machine from itself), which is expected and consistent with the localhost target.
---
 
## Files in This Repository
 
| File | Description |
|------|--------------|
| `nmap_basic.txt` | Raw output of the basic scan |
| `nmap_service.txt` | Raw output of the service version scan |
| `nmap_os.txt` | Raw output of the OS detection scan |
| `/screenshots` | Terminal screenshots of each scan |
| Demo video | Screen recording of all three scans being run live (linked below) |
 
**Demo video:** *[add your video link here once uploaded]*
 
---
 
## Checklist
 
- [x] Install Nmap (pre-installed on Kali; verified with `nmap --version`)
- [x] Basic scan: `nmap localhost` — results recorded
- [x] Service version scan: `nmap -sV localhost`
- [x] OS detection scan: `sudo nmap -O localhost`
- [x] Open ports identified and analyzed (result: none open — documented and explained above)
- [x] Security risk analysis written
- [x] Findings documented in structured `.txt` files
- [x] Screenshots of terminal output added
- [x] README explains Nmap, scanning, and ethics
- [x] Demo video recorded