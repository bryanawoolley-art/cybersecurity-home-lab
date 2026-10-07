# Lab 01 - Kali to Ubuntu Network Connectivity and SSH

## Objective

Build an isolated virtual network between Kali Linux and Ubuntu Server, configure dedicated lab IP addresses, verify network connectivity, and establish a remote SSH session from Kali to Ubuntu.

This lab establishes the networking foundation that will be used for future cybersecurity exercises.

## Environment

### Kali Linux

- Operating System: Kali Linux
- Hypervisor: Oracle VirtualBox
- NAT interface: `eth0`
- Internal lab interface: `eth1`
- Internal lab IP: `192.168.56.10/24`

### Ubuntu Server

- Operating System: Ubuntu Server 26.04.1 LTS
- Hostname: `ubuntu-server-lab`
- Hypervisor: Oracle VirtualBox
- NAT interface: `enp0s3`
- Internal lab interface: `enp0s8`
- Internal lab IP: `192.168.56.20/24`
- OpenSSH Server installed and running

## Network Design

Both systems use two VirtualBox network adapters.

### Adapter 1 — NAT

Used to provide Internet access for operating system updates, packages, and software repositories.

### Adapter 2 — Internal Network

Used exclusively for communication between systems inside the cybersecurity lab.

Internal network name:

`cyber-lab`

Lab addressing:

| System | Interface | IP Address |
|---|---|---|
| Kali Linux | `eth1` | `192.168.56.10/24` |
| Ubuntu Server | `enp0s8` | `192.168.56.20/24` |

## Ubuntu Network Configuration

The Ubuntu Server's second network interface was identified using:

```bash
ip addr
```

The internal lab IP was assigned with:

```bash
sudo ip addr add 192.168.56.20/24 dev enp0s8
sudo ip link set enp0s8 up
```

The configuration was verified using:

```bash
ip addr show enp0s8
```

Expected result:

```text
inet 192.168.56.20/24 scope global enp0s8
```

## Kali Linux Network Configuration

The Kali Linux second interface was identified as:

```text
eth1
```

The internal lab IP was assigned with:

```bash
sudo ip addr add 192.168.56.10/24 dev eth1
sudo ip link set eth1 up
```

The configuration was verified using:

```bash
ip addr show eth1
```

Expected result:

```text
inet 192.168.56.10/24 scope global eth1
```

## Connectivity Test

Connectivity from Kali Linux to Ubuntu Server was tested with:

```bash
ping -c 4 192.168.56.20
```

The Ubuntu Server responded successfully, confirming communication across the isolated VirtualBox Internal Network.

## SSH Configuration

OpenSSH Server was installed during the Ubuntu Server installation.

SSH service status was verified using:

```bash
systemctl status ssh
```

The service reported:

```text
Active: active (running)
```

SSH was listening on TCP port 22.

## SSH Connection Test

From Kali Linux, a remote SSH session was initiated with:

```bash
ssh bryan@192.168.56.20
```

The SSH host fingerprint was accepted during the first connection and authentication was completed using the Ubuntu user account.

A successful connection resulted in the remote shell prompt:

```text
bryan@ubuntu-server-lab:~$
```

## Remote System Verification

After connecting from Kali to Ubuntu through SSH, the following commands were executed:

```bash
whoami
hostname
ip addr show enp0s8
```

### Results

`whoami` returned:

```text
bryan
```

`hostname` returned:

```text
ubuntu-server-lab
```

The network interface confirmed:

```text
192.168.56.20/24
```

These results verified that the terminal session running from Kali Linux was successfully controlling the Ubuntu Server remotely.

## Result

The lab was completed successfully.

The following objectives were achieved:

- Created an isolated VirtualBox Internal Network
- Maintained NAT connectivity for Internet access
- Configured a dedicated Kali lab interface
- Configured a dedicated Ubuntu lab interface
- Assigned static lab IPv4 addresses
- Verified Kali-to-Ubuntu connectivity
- Verified the Ubuntu SSH service
- Established a successful SSH connection from Kali to Ubuntu
- Remotely executed Linux commands on Ubuntu from Kali

## Skills Practiced

- VirtualBox networking
- Virtual machine networking
- Linux network administration
- TCP/IP fundamentals
- IPv4 addressing
- Network interface identification
- Static IP configuration
- ICMP connectivity testing
- OpenSSH
- TCP port 22
- Remote Linux administration
- Linux command-line navigation
- Network troubleshooting
- Technical documentation

## Evidence

![Successful SSH connection from Kali to Ubuntu](ssh-success.png)

## Important Note

The IP addresses in this lab were initially assigned using the Linux `ip` command.

These settings are temporary and may be lost when the virtual machines reboot.

A future lab step will configure persistent network addressing.

## Security Context

This lab demonstrates a basic client/server relationship.

Kali Linux acts as an administrative and security-testing workstation while Ubuntu Server acts as the remote Linux server.

Future labs will use this same isolated environment to perform:

- Service discovery
- Port scanning
- Log analysis
- Firewall testing
- Packet analysis
- Security monitoring
- Vulnerability assessment

All testing will remain confined to systems owned and controlled within this authorized virtual lab.

## Lessons Learned

This lab demonstrated that virtual machines can function as independent networked systems even though they run on the same physical computer.

Key concepts reinforced include:

- NAT and internal networks serve different purposes.
- Linux systems can have multiple network interfaces.
- IP addresses must exist on the same subnet for direct communication in this lab design.
- SSH provides encrypted remote administration.
- Services such as SSH must be running and listening before another system can connect.
- Linux networking commands can be used to configure and troubleshoot interfaces directly.

## Next Lab

### Lab 02 — Nmap Service Discovery

The next lab will use Kali Linux to perform authorized service discovery against the Ubuntu Server.

Planned activities include:

- Verify host availability
- Scan TCP ports
- Identify open services
- Determine service versions
- Compare Nmap results with services actually running on Ubuntu
- Document findings and screenshots
