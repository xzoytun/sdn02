# AutoScript Installer

![Debian](https://img.shields.io/badge/Debian-10%20|%2011%20|%2012%20|%2013-A81D33?style=flat-square&logo=debian&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-18%20|%2020%20|%2022%20|%2024%20|%2025-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Status](https://img.shields.io/badge/Status-Stable-brightgreen?style=flat-square)

Automated installer for VPN server setup with multi-distro support.

## Features

- **One-Click Installation** - Complete setup with a single command
- **Multi-Distro Support** - Debian 10-13 & Ubuntu 18-25
- **Security First** - Integrated Fail2ban protection
- **Optimized Performance** - Pre-configured for maximum efficiency
- **Auto Security** - Automatic brute force protection

## Supported Operating Systems

| Distribution | Version | Status |
|--------------|---------|--------|
| Debian | 10 (Buster) | ✅ Supported |
| Debian | 11 (Bullseye) | ✅ Supported |
| Debian | 12 (Bookworm) | ✅ Supported |
| Debian | 13 (Trixie) | ✅ Supported |
| Ubuntu | 18.04 LTS | ✅ Supported |
| Ubuntu | 20.04 LTS | ✅ Supported |
| Ubuntu | 22.04 LTS | ✅ Supported |
| Ubuntu | 24.04 LTS | ✅ Supported |
| Ubuntu | 25.04 | ✅ Supported |

## Quick Installation

Run the following command in your terminal:

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
```

## Installation Components

### 1. DNS Configuration

Configure DNS using Cloudflare for optimal performance:

```bash
echo "nameserver 1.1.1.1" > /etc/resolv.conf
bash -c 'echo -e "[Resolve]\nDNS=1.1.1.1" > /etc/systemd/resolved.conf && systemctl enable systemd-resolved'
```

### 2. Fix MESG Error (Debian 13)

Fix "mesg: ttyname failed" error on Debian 13:

```bash
sed -i '/mesg n/d' ~/.bashrc ~/.profile 2>/dev/null
```

### 3. Fail2ban Security

Install and configure Fail2ban for brute force protection:

```bash
curl -o /usr/local/bin/extrimer https://raw.githubusercontent.com/xzoytun/sdn02/main/jail.sh && \
chmod +x /usr/local/bin/extrimer && \
extrimer
```

### 4. AT Scheduler

Install AT for task scheduling:

```bash
apt install at -y
```

## Step-by-Step Installation

1. **Login as root**
   ```bash
   sudo su
   ```

2. **Update system**
   ```bash
   apt update && apt upgrade -y
   ```

3. **Run main installer** (use the quick installation command above)

4. **Configure DNS**
   ```bash
   echo "nameserver 1.1.1.1" > /etc/resolv.conf
   bash -c 'echo -e "[Resolve]\nDNS=1.1.1.1" > /etc/systemd/resolved.conf && systemctl enable systemd-resolved'
   ```

5. **Fix MESG (Debian 13 only)**
   ```bash
   sed -i '/mesg n/d' ~/.bashrc ~/.profile 2>/dev/null
   ```

6. **Install Fail2ban**
   ```bash
   curl -o /usr/local/bin/extrimer https://raw.githubusercontent.com/xzoytun/sdn02/main/jail.sh && \
   chmod +x /usr/local/bin/extrimer && \
   extrimer
   ```

7. **Install AT scheduler**
   ```bash
   apt install at -y
   ```

8. **Reboot system**
   ```bash
   reboot
   ```

## Verification

Check installation status:

```bash
# Check Fail2ban
systemctl status fail2ban

# Check AT scheduler
systemctl status atd

# Check DNS
cat /etc/resolv.conf

# Check IPv6 status
sysctl net.ipv6.conf.all.disable_ipv6
```

## System Requirements

### Minimum
- **RAM**: 512 MB
- **Storage**: 10 GB
- **CPU**: 1 Core
- **Network**: 100 Mbps

### Recommended
- **RAM**: 2 GB+
- **Storage**: 20 GB+ SSD
- **CPU**: 2+ Cores
- **Network**: 1 Gbps

## Troubleshooting

### Unable to locate package
```bash
apt update --allow-releaseinfo-change
apt update && apt upgrade -y
```

### Permission denied
```bash
sudo su
```

### DNS not working
```bash
echo "nameserver 1.1.1.1" > /etc/resolv.conf
bash -c 'echo -e "[Resolve]\nDNS=1.1.1.1" > /etc/systemd/resolved.conf && systemctl enable systemd-resolved'
systemctl restart networking
```

### Fail2ban not starting
```bash
journalctl -u fail2ban -n 50
systemctl restart fail2ban
systemctl enable fail2ban
```

## Security Features

- Fail2ban protection against brute force attacks
- Optimized firewall rules
- SSH hardening
- Automated port security
- Real-time log monitoring

## FAQ

**Q: Is this script safe to use?**  
A: Yes, the script includes Fail2ban integration for security. Always download from the official repository.

**Q: How long does installation take?**  
A: Installation time varies by server specs and internet connection, typically 5-15 minutes.

**Q: Can I install on a low-RAM VPS?**  
A: Yes, 512MB RAM minimum is sufficient, but 2GB+ is recommended for optimal performance.

**Q: Does it support IPv6?**  
A: The script disables IPv6 for stability. Modify the script if IPv6 is required.

## Support

- **Email**: support@xtrimertunnel.com
- **Telegram**: [@XtrimerSupport](https://t.me/XtrimerSupport)
- **Website**: [xtrimertunnel.com](https://xtrimertunnel.com)

## License

This project is licensed under the MIT License.

## Disclaimer

This script is provided "as-is" without warranty. Users are fully responsible for its use. Ensure you understand each command before running it on a production server.

---

**Made by XTRIMER TUNNEL**  
© 2024 AutoScript Installer. All rights reserved.
