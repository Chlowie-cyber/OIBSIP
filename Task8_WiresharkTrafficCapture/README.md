# Task 8 — Capture Network Traffic with Wireshark

## Objective
Capture live network traffic using Wireshark, apply filters to isolate specific protocols, analyse packet contents, and document findings with security observations.

## Glossary
- **Packet:** *(define in your own words)*
- **Protocol:** *(define)*
- **Port:** *(define)*
- **Payload:** *(define)*
- **Handshake:** *(define)*

## Why Unencrypted HTTP Traffic Is Dangerous
*(Explain — and how HTTPS prevents eavesdropping.)*

## Installation Steps
*(Document install + any permissions needed, e.g. running as admin.)*

## Checklist

- [ ] Install Wireshark (steps + permissions documented)
- [ ] Capture 2+ minutes of live local traffic
- [ ] HTTP filter (`http`) applied — screenshot taken
- [ ] DNS filter (`dns`) applied — screenshot taken
- [ ] TCP filter (`tcp`) applied — 3-way handshake (SYN, SYN-ACK, ACK) annotated
- [ ] Capture exported as `wireshark_capture.pcap`
- [ ] At least one unencrypted-data packet identified and explained
- [ ] README explains HTTP vs HTTPS risk
- [ ] Glossary completed

⚠️ **Ethics Note:** Only capture traffic on networks you own or administer.

## Demo Video
*(Link here once recorded)*

## Files in This Folder
- `wireshark_capture.pcap` — exported capture
- `/screenshots` — filtered views, handshake annotation
- `/code` — n/a unless custom filter scripts used
