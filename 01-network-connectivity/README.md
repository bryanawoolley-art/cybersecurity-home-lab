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
