# Cybersecurity Home Lab

## Objective

Build a hands-on cybersecurity home lab to develop practical skills in Linux administration, networking, system administration, SOC analysis, vulnerability assessment, and ethical hacking.

This repository documents the construction and continued development of a virtual cybersecurity environment using Kali Linux and Ubuntu Server. Each completed lab includes the objective, environment, commands used, results, screenshots, findings, and lessons learned.

## Lab Environment

### Host System

- Windows 11
- Oracle VirtualBox 7.2
- 32 GB RAM
- Intel Core i5 processor

### Kali Linux

- Kali Linux virtual machine
- 6 GB RAM
- 4 virtual CPUs
- VirtualBox prebuilt Kali image
- Adapter 1: NAT
- Adapter 2: VirtualBox Internal Network
- Internal network interface: `eth1`
- Internal lab IP: `192.168.56.10/24`
- Clean baseline snapshot created

### Ubuntu Server

- Ubuntu Server 26.04.1 LTS
- 4 GB RAM
- 2 virtual CPUs
- 40 GB virtual disk
- Hostname: `ubuntu-server-lab`
- Adapter 1: NAT
- Adapter 2: VirtualBox Internal Network
- NAT interface: `enp0s3`
- NAT IP during setup: `10.0.2.15`
- Internal lab interface: `enp0s8`
- Internal lab IP: `192.168.56.20/24`
- OpenSSH Server installed
- SSH service verified active and running
- Installation completed successfully

## Network Architecture

The lab currently uses two virtual network adapters on each virtual machine.

### Adapter 1 — NAT

Provides Internet access for:

- Operating system updates
- Package installation
- Software repositories
- Internet connectivity

### Adapter 2 — Internal Network

Provides isolated communication between lab systems.

Internal network name:

`cyber-lab`

Current lab addressing:

| System | Interface | IP Address |
|---|---|---|
| Kali Linux | `eth1` | `192.168.56.10/24` |
| Ubuntu Server | `enp0s8` | `192.168.56.20/24` |

This design allows Kali and Ubuntu to communicate with one another while maintaining a separate interface for Internet access.

## Skills Being Practiced

- Linux administration
- Virtualization
- Virtual machine provisioning
- TCP/IP networking
- Network interface configuration
- Static IP addressing
- SSH
- Remote system administration
- Nmap
- Wireshark
- Linux authentication logs
- Firewall configuration
- System hardening
- Vulnerability assessment
- SOC investigation
- SIEM analysis
- Ethical hacking in an authorized lab environment
- Technical documentation
- GitHub portfolio development

## Lab Progress

- [x] VirtualBox installation and configuration
- [x] Kali Linux deployment
- [x] Ubuntu Server deployment
- [x] OpenSSH Server installation
- [x] Isolated Kali-to-Ubuntu network configuration
- [x] Kali-to-Ubuntu connectivity
- [x] SSH remote access from Kali to Ubuntu
- [ ] Nmap service discovery
- [ ] Linux authentication log analysis
- [ ] Firewall configuration and testing
- [ ] Wireshark packet analysis
- [ ] SOC-style incident investigation
- [ ] SIEM / Splunk integration
- [ ] Additional vulnerable target systems
- [ ] Active Directory security lab

## Completed Labs

### Lab 01 — Kali to Ubuntu Network Connectivity and SSH

Built an isolated VirtualBox network between Kali Linux and Ubuntu Server, configured dedicated lab IP addresses, verified network connectivity, and successfully established an SSH session from Kali to Ubuntu.

[View Lab 01](01-network-connectivity/README.md)

## Planned Labs

### Lab 02 — Nmap Service Discovery

Use Kali Linux to perform authorized network and service discovery against the Ubuntu Server.

Planned activities include:

- Host availability testing
- Port discovery
- Service enumeration
- Service version identification
- Analysis of exposed services

### Lab 03 — Linux Authentication Log Analysis

Generate authentication activity and analyze Ubuntu logs to identify successful and unsuccessful SSH activity.

### Lab 04 — Firewall Configuration

Configure and test Ubuntu firewall rules while observing their effect on network connectivity and exposed services.

### Lab 05 — Wireshark Packet Analysis

Capture and analyze lab traffic including:

- ARP
- ICMP
- TCP
- SSH
- Source and destination addresses
- Source and destination ports
- TCP connection establishment

### Lab 06 — SOC-Style Investigation

Generate simulated security events inside the authorized lab and investigate them from a defensive security perspective.

### Future Expansion

Future additions may include:

- Windows target virtual machine
- Active Directory
- Windows Server
- Splunk
- SIEM monitoring
- Centralized logging
- IDS/IPS
- Vulnerability scanning
- Web application security labs
- Additional Linux servers
- Security hardening exercises

## Documentation Standard

Each lab will document:

1. Objective
2. Environment
3. Network configuration
4. Tools used
5. Commands used
6. Screenshots
7. Results
8. Findings
9. Remediation or defensive considerations
10. Lessons learned

## Legal and Ethical Scope

All security testing documented in this repository is conducted against systems owned and controlled within this private virtual lab environment.

Testing is performed for educational, defensive security, and authorized cybersecurity training purposes only.
