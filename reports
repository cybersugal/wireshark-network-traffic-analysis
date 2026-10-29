
# Network Traffic Analysis with Wireshark

## Overview

This project involves analysing network traffic captured using Wireshark. The purpose was to understand how computers communicate over a network by examining DNS requests, TLS connections, TCP packets, and ICMP error messages.

Through this hands-on project, I gained practical experience in packet inspection, protocol identification, and basic network troubleshooting.

## Objectives

- Understand how DNS resolves domain names into IP addresses.
- Identify TLS traffic and understand encrypted HTTPS communication.
- Analyse TCP packets, flags, sequence numbers, and acknowledgements.
- Examine ICMP messages and identify network-related errors.
- Practise using Wireshark display filters to investigate network traffic.

## Tools Used

- **Wireshark** — Network protocol analyser.
- **Operating System** — macOS.
- **Network Protocols** — DNS, TLS, TCP, and ICMP.

## 1. DNS Analysis

DNS (Domain Name System) translates domain names into IP addresses so computers can locate servers.

**Findings:**
- **Domain queried:** `www.wikipedia.org`
- **Resolved IP address:** `103.102.166.224`
- **Associated hostname:** `dyna.wikimedia.org`

The packet capture showed a DNS request for Wikipedia and a response containing an IP address. This demonstrated how DNS helps a computer identify the destination server before communicating with a website.

**Wireshark display filter:**

```text
dns
```

## 2. TLS Analysis

TLS (Transport Layer Security) helps protect data exchanged between a client and a server. HTTPS commonly uses TLS to secure web communication.

**Findings:**
- **Local IP address:** `192.168.1.73`
- **Remote IP address:** `103.102.166.224`
- **Destination port:** `443`
- **Observed packets:** Server Hello, Change Cipher Spec, and Application Data.

The capture showed encrypted application data exchanged over a secure connection. The webpage content could not be read directly from the encrypted application data packets.

**Wireshark display filters:**

```text
tls
```

To identify TLS Client Hello packets:

```text
tls.handshake.type == 1
```

## 3. TCP Analysis

TCP (Transmission Control Protocol) provides reliable data delivery between communicating devices. It uses sequence numbers, acknowledgement numbers, and control flags to manage data transmission.

**Findings:**
- **Local IP address:** `192.168.1.73`
- **Remote IP address:** `103.102.166.224`
- **Observed flags:** ACK and PSH, ACK.
- **Observed payload size:** Some TCP segments contained 1,400 bytes of payload data.

The ACK flag indicates acknowledgement-related information, while PSH indicates that data should be pushed toward the receiving application. Sequence and acknowledgement numbers help track the flow of data between communicating devices.

**Wireshark display filters:**

To display TCP traffic:

```text
tcp
```

To identify TCP SYN packets:

```text
tcp.flags.syn == 1
```

To identify TCP retransmissions:

```text
tcp.analysis.retransmission
```

## 4. ICMP Analysis

ICMP (Internet Control Message Protocol) is used for network diagnostics and reporting certain delivery errors.

**Findings:**
- The capture contained ICMP messages associated with network communication involving the local computer.
- Some messages reported `Destination unreachable (Port unreachable)`.
- Remote IP addresses involved included `172.248.216.68` and `172.248.216.69`.

These messages indicated that certain packets could not be delivered to the required destination port. A port-unreachable message commonly occurs when a UDP packet reaches a destination where the specified port is unavailable. The exact cause depends on the packet details and network conditions.

**Wireshark display filter:**

```text
icmp
```

## 5. Display Filters Summary

The following Wireshark display filters were used during the investigation.

| Purpose | Display Filter |
|---|---|
| DNS investigation | `dns` |
| TLS traffic | `tls` |
| TLS Client Hello | `tls.handshake.type == 1` |
| TCP traffic | `tcp` |
| TCP SYN packets | `tcp.flags.syn == 1` |
| TCP retransmissions | `tcp.analysis.retransmission` |
| ICMP messages | `icmp` |

## 6. Key Learnings

By completing this project, I learned how to:

- Capture and inspect network packets using Wireshark.
- Identify DNS requests and responses.
- Recognise TLS handshakes and encrypted application data.
- Examine TCP flags, payload sizes, sequence numbers, and acknowledgements.
- Interpret ICMP destination-unreachable messages.
- Apply display filters to investigate specific types of network traffic.
- Use packet-level evidence to understand basic network behaviour and troubleshooting.

## Conclusion

This project provided practical experience in network traffic analysis using Wireshark. By examining DNS, TLS, TCP, and ICMP packets, I developed a better understanding of how network protocols support communication, security, and error reporting.

Packet inspection is an important foundational skill in cybersecurity and network analysis. This project is part of my ongoing learning journey toward developing practical skills in network security and cybersecurity analysis.

## Ethical Considerations

All packet analysis was performed on network traffic available to me for educational purposes. Network captures may contain sensitive information, so packet data should be handled responsibly. Always obtain appropriate permission before capturing or analysing traffic on networks you do not own or administer.
