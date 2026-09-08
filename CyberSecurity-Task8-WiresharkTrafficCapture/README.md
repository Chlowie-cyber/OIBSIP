# Task 8 — Capture Network Traffic with Wireshark

**OIBSIP — Security Analyst Track**
**Analyst:** Lehlogonolo Mpye
**Tool:** Wireshark v4.6.6 on Kali Linux 2026.2 (VMware)
**Interface Captured:** eth0

---

## Objective
Capture live network traffic using Wireshark, apply filters to isolate specific protocols, analyse packet contents, and document findings with security observations.

---

## Ethics Note
Traffic was captured only on the local network interface (`eth0`) of a personal Kali Linux VM under my own control. No traffic belonging to any other person, device, or network was captured or inspected.

---

## Installation
Wireshark v4.6.6 was already installed on Kali Linux — confirmed with `wireshark --version`, no separate installation required.

## Capture Setup
1. Opened Wireshark and selected the **eth0** interface (confirmed active via the live traffic waveform indicator)
2. Started the capture
3. Generated live traffic by browsing to `http://neverssl.com` in Firefox — this site intentionally stays on plain HTTP, making it ideal for observing unencrypted traffic
4. Captured continuously for over 2 minutes (4,274 total packets captured)
5. Stopped the capture and exported the full capture as `wireshark_capture.pcap`

---

## Filters Applied

### 1. HTTP Filter
**Filter used:** `http`

Captured multiple real HTTP requests and responses, including `GET /canonical.html HTTP/1.1` requests and `200 OK` responses, plus a `301 Moved Permanently` redirect and various `GET /favicon.ico`, `/success.txt?ipv4` requests — all in plain, unencrypted HTTP.
1
### 2. DNS Filter
**Filter used:** `dns`

Captured standard DNS queries resolving domain names to IP addresses before each connection, including queries for `neverssl.com`, `detectportal.firefox.com`, `en.wikipedia.org`, and various Mozilla telemetry/update domains — showing the DNS resolution step that happens before any HTTP or HTTPS connection can begin.

### 3. TCP Filter + Three-Way Handshake
**Filter used:** `tcp`, then narrowed to a single conversation using **Conversation Filter → TCP** on one SYN packet.

Isolated one clean TCP three-way handshake between my machine (`192.168.81.132`) and a remote server (`34.223.124.45`) on port 443:

| Step | Packet | Info |
|------|--------|------|
| 1 | #1938 | `[SYN]` — client initiates connection, Seq=0 |
| 2 | #1954 | `[SYN, ACK]` — server acknowledges and responds, Seq=0 Ack=1 |
| 3 | #1955 | `[ACK]` — client confirms, connection established |

This is the standard TCP handshake that precedes every reliable connection, whether it's plain HTTP or encrypted HTTPS — this particular connection went on to become a TLS 1.3 session (visible via `Client Hello (SNI=...neverssl.com)` immediately following the handshake).

---

## Unencrypted Data Identified

One HTTP GET request (packet #197) was inspected in full. The packet bytes pane showed the entire HTTP request in **readable plain text**, including:

```
GET /canonical.html HTTP/1.1
Host: detectportal.firefox.com
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept: */*
Accept-Language: en-US,en;q=...
Accept-Encoding: gzip, deflate
Connection: keep-alive
```

Every field here — including the browser's exact version, requested page, and connection details — is visible to **anyone able to observe the traffic**, since none of it is encrypted.

### Why Unencrypted HTTP Traffic Is Dangerous
When traffic travels over plain HTTP, anyone positioned to intercept it (on the same network, at an ISP, or via a compromised router) can read every byte of the request and response — this is exactly the mechanism behind Man-in-the-Middle attacks covered in Task 4. If this had been a login form instead of a simple page request, credentials would be visible in exactly the same way: as plain, readable text.

### How HTTPS Prevents This
HTTPS wraps the same HTTP request inside a TLS-encrypted tunnel. An observer can still see *that* a connection is happening (source/destination IPs, timing, packet sizes) but cannot read the actual content — the request, headers, and any submitted data are encrypted before leaving the device and only decrypted by the legitimate destination server.

---

## Glossary

- **Packet:** A single unit of data transmitted across a network, containing both the actual content and header information (like source/destination addresses) needed to deliver it correctly.
- **Protocol:** An agreed-upon set of rules that determines how devices communicate — e.g., HTTP for web pages, DNS for domain name lookups, TCP for reliable data delivery.
- **Port:** A numbered endpoint on a device that identifies which specific service or application traffic is meant for (e.g., port 443 for HTTPS, port 53 for DNS).
- **Payload:** The actual data being carried inside a packet, separate from the header/addressing information wrapped around it.
- **Handshake:** The initial exchange of messages (like TCP's SYN, SYN-ACK, ACK) that two devices use to establish a connection before actual data transfer begins.

---

## Files in This Repository

| File | Description |
|------|--------------|
| `wireshark_capture.pcap` | Full exported packet capture (all 4,274 packets) |
| `/screenshots` | HTTP, DNS, and TCP filtered views; handshake annotation; unencrypted packet detail |
| Demo video | Screen recording of the full capture, filtering, and export process |

**Demo video:** *[add your video link here once uploaded]*

---

## Checklist

- [x] Install Wireshark (pre-installed on Kali; confirmed with `wireshark --version`)
- [x] Capture 2+ minutes of live local traffic
- [x] HTTP filter applied + screenshot
- [x] DNS filter applied + screenshot
- [x] TCP filter applied — 3-way handshake identified and annotated
- [x] Capture exported as `wireshark_capture.pcap`
- [x] Unencrypted data packet identified and explained
- [x] README explains HTTP vs HTTPS risk
- [x] Glossary completed
- [x] Demo video recorded