# Task 10 — Full Network Security Assessment Report

## Objective
Conduct a structured, end-to-end security assessment of a local test network using Nmap, Wireshark, and Nikto, and produce a professional security report suitable for a technical team or management.

*This task consolidates the work from Task 1 (Nmap), Task 7 (Nikto), and Task 8 (Wireshark) into one full assessment report.*

## Scope Definition
*(Define here: which IP range(s), which services, which time window you assessed.)*

## Checklist

- [ ] Scope defined in writing (IP ranges, services, time window)
- [ ] Phase 1 — Reconnaissance: `nmap -sV -O [target range]` run; hosts, ports, services documented
- [ ] Phase 2 — Traffic Analysis: 5+ min Wireshark capture; HTTP/DNS/ARP filtered and analysed; unencrypted data noted
- [ ] Phase 3 — Web Vulnerability Scan: Nikto run against any web server found; findings documented
- [ ] Findings register table built (Finding ID, Description, Severity, Affected Asset, Recommended Fix)
- [ ] Executive Summary written (1 page, non-technical, for a manager)
- [ ] Technical Report written (detailed findings per phase, with screenshots)
- [ ] Remediation roadmap: findings prioritised with effort estimate (Easy/Medium/Hard)
- [ ] All files committed: `network_security_assessment.md`, `nmap_results.txt`, `wireshark_capture.pcap`

## Findings Register

| Finding ID | Description | Severity | Affected Asset | Recommended Fix |
|-----------|--------------|----------|-----------------|------------------|
|           |              |          |                 |                  |

## Executive Summary
*(1 page, plain language, for a non-technical manager — overall risk posture.)*

## Remediation Roadmap

| Priority | Finding | Fix | Effort |
|----------|---------|-----|--------|
|          |         |     |        |

## Files in This Folder
- `network_security_assessment.md` — full consolidated report (main deliverable)
- `nmap_results.txt` — reused/expanded from Task 1
- `wireshark_capture.pcap` — reused/expanded from Task 8
- Nikto output referenced from Task 7
