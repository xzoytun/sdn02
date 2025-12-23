# 🚀 AutoScript Installer

<div align="center">

![Debian](https://img.shields.io/badge/Debian-10%20%7C%2011%20%7C%2012%20%7C%2013-red?style=flat-square&logo=debian)
![Ubuntu](https://img.shields.io/badge/Ubuntu-18%20%7C%2020%20%7C%2022%20%7C%2024%20%7C%2025-orange?style=flat-square&logo=ubuntu)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Status](https://img.shields.io/badge/Status-Stable-green?style=flat-square)

**Automated VPN Server Installer with Multi-Distro Support**

</div>

---

## 📋 Overview

Automated installer untuk VPN server setup dengan multi-distro support. Complete setup dengan single command.

## ✨ Features

- **One-Click Installation** - Complete setup dengan satu command
- **Multi-Distro Support** - Debian 10-13 & Ubuntu 18-25
- **Security First** - Integrated Fail2ban protection
- **Optimized Performance** - Pre-configured untuk maximum efficiency
- **Auto Security** - Automatic brute force protection

## 🚀 Installation

### Quick Install
```bash
sysctl -w net.ipv6.conf.all.disable_ipv6=1 && \
sysctl -w net.ipv6.conf.default.disable_ipv6=1 && \
apt update --allow-releaseinfo-change && \
apt upgrade -y && \
apt install -y curl wget unzip dos2unix sudo gnupg lsb-release software-properties-common build-essential libcap-ng-dev libssl-dev libffi-dev python3 python3-pip && \
echo -e "\nDependencies installed\n" && \
curl -s -O https://raw.githubusercontent.com/xzoytun/sdn02/main/gerhana && \
chmod +x gerhana && \
./gerhana
Configure DNS (Recommended)
echo "nameserver 1.1.1.1" > /etc/resolv.conf
bash -c 'echo -e "[Resolve]\nDNS=1.1.1.1" > /etc/systemd/resolved.conf && systemctl enable systemd-resolved'
Install Fail2ban
curl -o /usr/local/bin/extrimer https://raw.githubusercontent.com/xzoytun/sdn02/main/jail.sh && \
chmod +x /usr/local/bin/extrimer && \
extrimer
💻 Supported Operating Systems
Distribution
Version
Status
Debian
10 (Buster)
✅
Debian
11 (Bullseye)
✅
Debian
12 (Bookworm)
✅
Debian
13 (Trixie)
✅
Ubuntu
18.04 LTS
✅
Ubuntu
20.04 LTS
✅
Ubuntu
22.04 LTS
✅
Ubuntu
24.04 LTS
✅
Ubuntu
25.04
✅
📊 System Requirements
Minimum:
RAM: 512 MB
Storage: 1 GB
CPU: 1 Core
Recommended:
RAM: 1 GB+
Storage: 5 GB+
CPU: 2 Cores+
🎯 Usage
menu          # Access main menu
adduser       # Create new user
status        # Check service status
bandwidth     # View bandwidth usage
📄 License
MIT License - lihat file LICENSE
🌟 Support
Jika bermanfaat, berikan ⭐ di repository!
�

Made with ❤️ by xzoytun
�
```
