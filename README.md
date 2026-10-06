# Cybersecurity Home Lab

## Objective
Build a hands-on cybersecurity lab to develop practical skills in Linux administration, networking, SOC analysis, vulnerability assessment, and ethical hacking.

## Lab Environment
- Windows 11 host
- Oracle VirtualBox
- Kali Linux
- Ubuntu Server
- Future additions: Windows target VM, SIEM, Active Directory lab

## Current VM Configuration

### Kali Linux
- 6 GB RAM
- 4 CPUs
- VirtualBox prebuilt Kali image
- NAT interface: 10.0.2.15
- Internal lab interface: 192.168.56.10/24
- Clean baseline snapshot created

### Ubuntu Server
- 4 GB RAM
- 2 CPUs
- 40 GB virtual disk
- Ubuntu Server 26.04.1 LTS
- OpenSSH Server installed and verified active
- NAT interface: 10.0.2.15
- Internal lab interface: 192.168.56.20/24
- Hostname: ubuntu-server-lab
- Installation completed successfully



## Skills Being Practiced
- Linux administration
- Virtualization
- TCP/IP networking
- SSH
- Nmap
- Wireshark
- Log analysis
- Vulnerability assessment
- System hardening
- SOC investigation
- Ethical hacking in an authorized lab

## Lab Progress

1. ✅ Kali-to-Ubuntu network connectivity
2. ✅ SSH configuration and remote access
3. ⬜ Nmap service discovery
4. ⬜ Linux authentication log analysis
5. ⬜ Firewall configuration
6. ⬜ Wireshark packet analysis
7. ⬜ SOC-style incident investigation
8. ⬜ SIEM / Splunk integration
9. ⬜ Network-connectivity/

## Documentation
Each lab will include:
- Objective
- Environment
- Commands used
- Screenshots
- Findings
- Remediation
- Lessons learned



# Lab 01 - Kali to Ubuntu Network Connectivity and SSH

## Objective

Build an isolated virtual lab network between Kali Linux and Ubuntu Server, verify connectivity, and establish a remote SSH session from Kali to Ubuntu.

## Environment

### Kali Linux
- Operating System: Kali Linux
- Lab interface: eth1
- Lab IP: 192.168.56.10/24

### Ubuntu Server
- Operating System: Ubuntu Server 26.04.1 LTS
- Hostname: ubuntu-server-lab
- Lab interface: enp0s8
- Lab IP: 192.168.56.20/24
- OpenSSH Server enabled

## Network Design

Both systems use two virtual network adapters:

- Adapter 1: NAT for Internet access
- Adapter 2: VirtualBox Internal Network for isolated lab traffic

Internal network name:

cyber-lab

## Configuration

Ubuntu lab interface:

```bash
sudo ip addr add 192.168.56.20/24 dev enp0s8
sudo ip link set enp0s8 up
