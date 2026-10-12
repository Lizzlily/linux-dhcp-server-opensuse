# Linux DHCP Server Configuration & Verification (openSUSE)

**Academic networking lab | NET2103 Network & System Administration | August 2026**  
**Focus:** DHCP service deployment, IPv4 addressing, validation, and troubleshooting  
**Environment:** openSUSE Linux, VirtualBox, NetworkManager, `dhcpd`

## Overview

This project was part of a team-built LAN demonstrating how a client obtains IP settings via DHCP, resolves an internal DNS name, and accesses a web server. **My primary individual responsibility was the DHCP server**, including its configuration, MAC-based address reservation, verification, and troubleshooting. Other team members worked on DNS, Apache and wireless access-point components.

The client network used an isolated `192.168.2.0/24` segment in VirtualBox.

```text
                 Isolated lab LAN: 192.168.2.0/24

   DHCP server                DNS server              Web server
   192.168.2.1                192.168.2.20            192.168.2.10
        |                           |                       |
        +---------------------------+-----------------------+
                                    |
                             Client VM / AP
                         DHCP pool: .100 - .200
                         MAC reservation: .50
```

## My individual contributions

1. Configured the DHCP server on **openSUSE** using `nmcli`, `/etc/sysconfig/dhcpd`, and `/etc/dhcpd.conf`.
2. Defined a dynamic pool (`192.168.2.100`-`192.168.2.200`), DNS/gateway options, lease duration, and a MAC-bound reservation (`192.168.2.50`).
3. Verified DHCP syntax with `dhcpd -t -cf /etc/dhcpd.conf`, monitored the service with `systemctl`, and performed client-side tests.
4. Troubleshot configuration issues such as an incorrect subnet declaration, using syntax validation and retesting to confirm corrections.

## Evidence of results

| Verification | Observed outcome |
| --- | --- |
| DHCP service | Running and enabled in the project tests |
| Dynamic IP leasing | Test client received `192.168.2.100/24` |
| DNS option | Test client received `192.168.2.20` as DNS server |
| MAC reservation | Reserved test client obtained `192.168.2.50` |

See **[DHCP Server Portfolio Case Study](Linux_DHCP_Server_Portfolio_Case_Study.pdf)** for the concise, recruiter-friendly summary.for the concise, recruiter-friendly summary.

## Example configuration

[DHCP Configuration Example](dhcpd.conf.example) contains a **sanitized illustrative** DHCP configuration based on the academic lab. Adapt subnet/interfaces to your own environment before using it. The original complete course report is intentionally not published because it contains teammate information and setup-specific material.

## Tools and skills

- Linux network administration (`openSUSE`, `nmcli`, `systemctl`)
- DHCP / IP allocation / reservations
- IPv4 network addressing and subnetting
- Lab validation and systematic troubleshooting
- Team integration with DNS, web and wireless services

## Project attribution

This was a **team assignment**. The content above describes the contributions that I personally made to the DHCP portion. Other parts of the wider LAN were developed collaboratively and by other group members. This repository is a public-facing portfolio summary, not the original 71-page coursework report.
