# 🛡️ Cybersecurity Home Lab

<p align="center">

<img src="https://img.shields.io/badge/Cybersecurity-Home%20Lab-00D9FF?style=for-the-badge&logo=hackthebox&logoColor=white">
<img src="https://img.shields.io/badge/SIEM-Wazuh-7C3AED?style=for-the-badge">
<img src="https://img.shields.io/badge/Firewall-OPNsense-D94F00?style=for-the-badge">
<img src="https://img.shields.io/badge/Virtualization-Proxmox-E57000?style=for-the-badge">
<img src="https://img.shields.io/badge/Linux-Kali-557C94?style=for-the-badge&logo=linux&logoColor=white">
<img src="https://img.shields.io/badge/Windows-11-0078D6?style=for-the-badge&logo=windows&logoColor=white">

</p>

<p align="center">

### Learn • Build • Break • Investigate • Defend

</p>

---

## 👋 About This Project

This repository documents my **cybersecurity home lab** and my journey toward developing practical skills in:

- 🔐 Security Operations
- 🛡️ Network Security
- 🚨 Threat Detection
- 🔎 Incident Response
- 🧪 Security Testing
- 📊 SIEM & Log Analysis
- 💻 Windows & Linux Security
- 🌐 Network Segmentation
- 🔬 Digital Forensics

I am building this environment to move beyond cybersecurity theory and gain practical experience by creating, testing, investigating, and documenting security scenarios in an isolated lab.

> **Learn → Build → Break → Investigate → Defend**

---

# 🌐 Network Architecture

![Cybersecurity Home Lab Diagram](assets/homelab-diagram.png)

The lab is designed around an **OPNsense firewall**, with isolated VLANs for management, targets, security monitoring, attack simulation, and services.

```text
                         🌐 INTERNET
                              │
                              │
                              ▼
                    ┌──────────────────┐
                    │     OPNsense     │
                    │     FIREWALL     │
                    │    10.10.10.1    │
                    └────────┬─────────┘
                             │
                             │
                        VLAN NETWORK
                             │
        ┌────────────────────┼────────────────────┐
        │                    │                    │
        ▼                    ▼                    ▼
   MANAGEMENT             TARGETS               SIEM
   VLAN 10                VLAN 20               VLAN 30
        │                    │                    │
        │                    │                    │
   ┌──────────┐        ┌────────────┐       ┌───────────┐
   │ Proxmox  │        │ Windows 11 │       │   Wazuh   │
   │10.10.10.10│       │10.10.20.50 │       │10.10.30.50│
   └──────────┘        └────────────┘       └───────────┘


                             │
             ┌───────────────┴───────────────┐
             │                               │
             ▼                               ▼
        SECURITY                         SERVICES
        VLAN 40                          VLAN 50
             │                               │
       ┌──────────┐                    ┌────────────┐
       │   Kali   │                    │ Portainer  │
       │10.10.40.50│                   │10.10.20.51 │
       └──────────┘                    └────────────┘
