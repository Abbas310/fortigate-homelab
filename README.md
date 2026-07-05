# 🛡️ FortiGate Homelab – Virtual Firewall Deployment

## 📖 Project Overview

This project documents the complete deployment of a **FortiGate Next‑Generation Firewall (NGFW)** as a virtual machine on **VMware Workstation**. The lab creates an isolated, enterprise‑like network environment to learn firewall administration, network segmentation, and security policy implementation.

The final setup provides a secure gateway for a Windows 10 client, routing traffic from an internal LAN to the internet via Network Address Translation (NAT).

## 🎯 Objectives

- Deploy and license a FortiGate VM (FortiOS) on a Type‑2 hypervisor.
- Design a segmented network with distinct WAN and LAN zones.
- Configure the FortiGate as the gateway and DHCP server for a Windows 10 client.
- Implement a firewall policy to allow controlled internet access for the client.
- Document the entire process, including all troubleshooting steps, for portfolio展示.

## 🏗️ Architecture & Topology


| Component | Interface | IP Address | Subnet |
|-----------|-----------|------------|--------|
| **Host PC (Windows 11)** | Physical NIC | 10.1.1.218 | 255.255.255.0 |
| **Home Router** | Gateway | 10.1.1.1 | 255.255.255.0 |
| **FortiGate port1 (WAN)** | Bridged (VMnet0) | 10.1.1.220 | 255.255.255.0 |
| **FortiGate port2 (LAN)** | Host‑only (VMnet1) | 192.168.1.1 | 255.255.255.0 |
| **Windows 10 Client** | Host‑only (VMnet1) | DHCP (192.168.1.100-200) | 255.255.255.0 |

## 🛠️ Technologies Used

- **Virtualization:** VMware Workstation 17 Pro
- **Firewall:** FortiGate VM (FortiOS v7.x)
- **Client OS:** Microsoft Windows 10 Pro
- **Documentation:** GitHub Markdown, draw.io (for diagrams)

## 🚀 Key Achievements

- Successfully deployed a multi‑node virtual network with full internet connectivity.
- Resolved a Layer‑2 connectivity issue by manually binding VMware's VMnet0 to the host's physical Wi‑Fi adapter – demonstrating strong troubleshooting skills.
- Fixed a persistent `curl 28` licensing timeout by synchronising system time via NTP and correcting DNS settings.
- Gained hands‑on experience with FortiOS CLI and GUI, covering interface configuration, DHCP, and firewall policies.

## 📂 Repository Structure
