# Cybersecurity Lab Environment Setup

## Overview

This document describes the setup of my personal cybersecurity laboratory environment.

The lab was created to provide a safe and controlled environment for practicing cybersecurity concepts such as network reconnaissance, port scanning, service enumeration, system monitoring, and security analysis.

## Host System

The laboratory is hosted on:

- MacBook Air M1
- Apple Silicon (ARM64)
- macOS
- UTM virtualization platform

Because the host computer uses Apple Silicon, ARM64-compatible operating systems were used for the virtual machines.

---

## Lab Architecture

The initial laboratory consists of two virtual machines:

| System | Purpose |
|---|---|
| Kali Linux ARM64 | Security testing and analysis machine |
| Windows 11 ARM | Target and monitoring machine |

Both virtual machines are hosted using UTM.

The initial network configuration allows the Kali Linux machine to communicate with the Windows 11 machine in a controlled virtual environment.

---

# 1. UTM Installation

UTM was installed on macOS to provide the virtualization environment for the cybersecurity lab.

UTM allows ARM-based operating systems to run efficiently on Apple Silicon.

After installation, separate virtual machines were created for Kali Linux and Windows 11.

---

# 2. Kali Linux Installation

Kali Linux ARM64 was installed as the primary cybersecurity testing machine.

### Configuration

- Architecture: ARM64 (aarch64)
- Virtualization platform: UTM / QEMU
- Memory: 4096 MiB
- Operating System: Kali Linux
- Desktop Environment: XFCE
- Network Interface: eth0

Kali Linux provides the security tools used throughout the laboratory exercises.

Examples include:

- Nmap
- Network diagnostic utilities
- Security assessment tools
- Traffic analysis tools
- Vulnerability assessment tools

---

# 3. Windows 11 ARM Installation

Windows 11 ARM was installed as the target system for laboratory exercises.

The Windows VM provides a controlled system where services, firewall configurations, logging, and security monitoring can be tested.

### Configuration

- Operating System: Windows 11 ARM
- Architecture: ARM64
- Virtualization platform: UTM
- Network Adapter: Ethernet
- Windows Defender Firewall enabled

---

# 4. Network Verification

After both virtual machines were configured, their IP addresses were identified.

### Kali Linux

The following command was used:

```bash
ip addr
```

Kali Linux received the address:

```text
192.168.64.3
```

### Windows 11

The Windows network configuration was checked using:

```powershell
ipconfig
```

Windows received the address:

```text
192.168.64.4
```

Both systems were therefore located on the same virtual subnet:

```text
192.168.64.0/24
```

---

# 5. Connectivity Test

Connectivity between Kali Linux and Windows was tested using ICMP.

From Kali Linux:

```bash
ping -c 4 192.168.64.4
```

Initially, Windows did not respond because ICMP traffic was blocked by the Windows firewall.

A Windows Firewall rule was created to allow ICMP echo requests.

After enabling the rule, Kali successfully received responses from Windows with:

```text
4 packets transmitted, 4 received, 0% packet loss
```

This confirmed successful communication between the two virtual machines.

---

# Environment Status

The basic cybersecurity laboratory environment is now operational.

Kali Linux can communicate with the Windows 11 target system, allowing controlled cybersecurity exercises to be performed.

Future laboratory exercises will be documented separately in this repository.
