# 🚀 AutoScript Installer

<div align="center">

![Debian](https://img.shields.io/badge/Debian-10%20|%2011%20|%2012%20|%2013-A81D33?style=for-the-badge&logo=debian&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-18%20|%2020%20|%2022%20|%2024%20|%2025-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Stable-brightgreen?style=for-the-badge)

**Installer otomatis untuk setup VPN Server dengan dukungan multi-distro**

[📦 Installation](#-instalasi-lengkap) • [🔧 Components](#-komponen-installer) • [💡 Usage](#-cara-penggunaan) • [❓ FAQ](#-faq)

</div>

---

## 📋 Deskripsi

AutoScript installer adalah solusi otomatis untuk setup VPN server dengan dukungan penuh untuk berbagai distro Linux. Script ini dirancang untuk mempermudah instalasi dan konfigurasi server VPN dengan satu perintah.

### ✨ Fitur Utama

- 🎯 **One-Click Installation** - Instalasi lengkap dengan satu perintah
- 🐧 **Multi-Distro Support** - Mendukung Debian 10-13 & Ubuntu 18-25
- 🔒 **Security First** - Terintegrasi dengan Fail2ban
- ⚡ **Optimized Performance** - Konfigurasi optimal untuk performa maksimal
- 🛡️ **Auto Security** - Proteksi otomatis terhadap brute force attack

---

## 🖥️ Sistem Operasi yang Didukung

<table>
<thead>
<tr>
<th>Distro</th>
<th>Versi</th>
<th>Status</th>
<th>Rekomendasi</th>
</tr>
</thead>
<tbody>
<tr>
<td rowspan="4"><strong>Debian</strong></td>
<td>Debian 10 (Buster)</td>
<td>✅ Supported</td>
<td>⭐⭐⭐</td>
</tr>
<tr>
<td>Debian 11 (Bullseye)</td>
<td>✅ Supported</td>
<td>⭐⭐⭐⭐</td>
</tr>
<tr>
<td>Debian 12 (Bookworm)</td>
<td>✅ Supported</td>
<td>⭐⭐⭐⭐⭐</td>
</tr>
<tr>
<td>Debian 13 (Trixie)</td>
<td>✅ Supported</td>
<td>⭐⭐⭐⭐⭐</td>
</tr>
<tr>
<td rowspan="5"><strong>Ubuntu</strong></td>
<td>Ubuntu 18.04 LTS</td>
<td>✅ Supported</td>
<td>⭐⭐⭐</td>
</tr>
<tr>
<td>Ubuntu 20.04 LTS</td>
<td>✅ Supported</td>
<td>⭐⭐⭐⭐</td>
</tr>
<tr>
<td>Ubuntu 22.04 LTS</td>
<td>✅ Supported</td>
<td>⭐⭐⭐⭐⭐</td>
</tr>
<tr>
<td>Ubuntu 24.04 LTS</td>
<td>✅ Supported</td>
<td>⭐⭐⭐⭐⭐</td>
</tr>
<tr>
<td>Ubuntu 25.04</td>
<td>✅ Supported</td>
<td>⭐⭐⭐⭐</td>
</tr>
</tbody>
</table>

---

## 📦 Instalasi Lengkap

### 🎯 Quick Install (Recommended)

Copy dan paste perintah berikut ke terminal Anda:

```bash
sysctl -w net.ipv6.conf.all.disable_ipv6=1 && \
sysctl -w net.ipv6.conf.default.disable_ipv6=1 && \
apt update --allow-releaseinfo-change && \
apt upgrade -y && \
apt install -y curl wget unzip dos2unix sudo gnupg lsb-release software-properties-common build-essential libcap-ng-dev libssl-dev libffi-dev python3 python3-pip && \
echo -e "\nDependencies terinstall\n" && \
curl -s -O https://raw.githubusercontent.com/xzoytun/sdn02/main/gerhana && \
chmod +x gerhana && \
./gerhana
```

#### 📝 Penjelasan Tahapan:

1. **Disable IPv6** - Menonaktifkan IPv6 untuk stabilitas
2. **System Update** - Update dan upgrade sistem
3. **Install Dependencies** - Instalasi paket yang diperlukan
4. **Download Script** - Download script installer utama
5. **Execute** - Menjalankan instalasi otomatis

---

## 🔧 Komponen Installer

### 1️⃣ DNS Configuration

Mengkonfigurasi DNS menggunakan Cloudflare (1.1.1.1) untuk performa dan keamanan optimal:

```bash
echo "nameserver 1.1.1.1" > /etc/resolv.conf
```

**Manfaat:**
- ⚡ Resolusi DNS lebih cepat
- 🔒 Privacy protection
- 🌍 Global coverage

---

### 2️⃣ Fix MESG Error (Debian 13)

Memperbaiki error "mesg: ttyname failed" pada Debian 13:

```bash
sed -i '/mesg n/d' ~/.bashrc ~/.profile 2>/dev/null
```

**Kapan digunakan:**
- ✅ Setelah instalasi pada Debian 13
- ✅ Jika muncul warning saat login
- ✅ Untuk membersihkan output terminal

---

### 3️⃣ Fail2ban Security

Instalasi dan konfigurasi Fail2ban untuk proteksi brute force:

```bash
curl -o /usr/local/bin/extrimer https://raw.githubusercontent.com/xzoytun/sdn02/main/jail.sh \
&& chmod +x /usr/local/bin/extrimer \
&& extrimer
```

**Fitur Security:**
- 🛡️ Auto-ban IP yang mencurigakan
- 📊 Monitoring real-time
- ⚙️ Konfigurasi optimal
- 🔄 Auto-restart service

---

### 4️⃣ Install AT Scheduler

Instalasi AT untuk task scheduling:

```bash
apt install at -y
```

**Kegunaan:**
- ⏰ Schedule task otomatis
- 🔄 Backup berkala
- 🧹 Maintenance otomatis
- 📅 Cron job management

---

## 💡 Cara Penggunaan

### Step-by-Step Installation

#### 📌 Step 1: Persiapan

```bash
# Login sebagai root
sudo su

# Pastikan sistem up-to-date
apt update && apt upgrade -y
```

#### 📌 Step 2: Jalankan Installer Utama

```bash
sysctl -w net.ipv6.conf.all.disable_ipv6=1 && \
sysctl -w net.ipv6.conf.default.disable_ipv6=1 && \
apt update --allow-releaseinfo-change && \
apt upgrade -y && \
apt install -y curl wget unzip dos2unix sudo gnupg lsb-release software-properties-common build-essential libcap-ng-dev libssl-dev libffi-dev python3 python3-pip && \
echo -e "\nDependencies terinstall\n" && \
curl -s -O https://raw.githubusercontent.com/xzoytun/sdn02/main/gerhana && \
chmod +x gerhana && \
./gerhana
```

#### 📌 Step 3: Konfigurasi DNS

```bash
echo "nameserver 1.1.1.1" > /etc/resolv.conf
```

#### 📌 Step 4: Fix MESG (Khusus Debian 13)

```bash
sed -i '/mesg n/d' ~/.bashrc ~/.profile 2>/dev/null
```

#### 📌 Step 5: Install Fail2ban

```bash
curl -o /usr/local/bin/extrimer https://raw.githubusercontent.com/xzoytun/sdn02/main/jail.sh \
&& chmod +x /usr/local/bin/extrimer \
&& extrimer
```

#### 📌 Step 6: Install AT Scheduler

```bash
apt install at -y
```

#### 📌 Step 7: Reboot System

```bash
reboot
```

---

## 🔍 Verifikasi Instalasi

Setelah instalasi selesai, verifikasi dengan perintah berikut:

### Check Services Status

```bash
# Check Fail2ban
systemctl status fail2ban

# Check AT scheduler
systemctl status atd

# Check DNS
cat /etc/resolv.conf
```

### Check Network Configuration

```bash
# Check IPv6 status
sysctl net.ipv6.conf.all.disable_ipv6

# Check network interfaces
ip a
```

---

## 🛠️ Troubleshooting

<details>
<summary><strong>❌ Error: Unable to locate package</strong></summary>

**Solusi:**
```bash
apt update --allow-releaseinfo-change
apt update && apt upgrade -y
```
</details>

<details>
<summary><strong>❌ Error: Permission denied</strong></summary>

**Solusi:**
```bash
# Pastikan login sebagai root
sudo su
# Atau gunakan sudo untuk setiap perintah
sudo [command]
```
</details>

<details>
<summary><strong>❌ Error: DNS not working</strong></summary>

**Solusi:**
```bash
# Reset DNS configuration
echo "nameserver 1.1.1.1" > /etc/resolv.conf
echo "nameserver 8.8.8.8" >> /etc/resolv.conf

# Restart networking
systemctl restart networking
```
</details>

<details>
<summary><strong>❌ Error: Fail2ban not starting</strong></summary>

**Solusi:**
```bash
# Check logs
journalctl -u fail2ban -n 50

# Restart service
systemctl restart fail2ban
systemctl enable fail2ban
```
</details>

---

## 📊 System Requirements

### Minimum Requirements

| Component | Requirement |
|-----------|-------------|
| **RAM** | 512 MB |
| **Storage** | 10 GB |
| **CPU** | 1 Core |
| **Network** | 100 Mbps |

### Recommended Requirements

| Component | Requirement |
|-----------|-------------|
| **RAM** | 2 GB+ |
| **Storage** | 20 GB+ SSD |
| **CPU** | 2 Cores+ |
| **Network** | 1 Gbps |

---

## ❓ FAQ

<details>
<summary><strong>Q: Apakah script ini aman digunakan?</strong></summary>

**A:** Ya, script ini sudah terintegrasi dengan Fail2ban untuk keamanan maksimal. Selalu download dari repository resmi.
</details>

<details>
<summary><strong>Q: Berapa lama proses instalasi?</strong></summary>

**A:** Waktu instalasi bervariasi tergantung spesifikasi server dan koneksi internet, umumnya 5-15 menit.
</details>

<details>
<summary><strong>Q: Apakah bisa diinstall di VPS dengan RAM kecil?</strong></summary>

**A:** Ya, minimum 512MB RAM sudah cukup, namun untuk performa optimal disarankan 2GB+.
</details>

<details>
<summary><strong>Q: Bagaimana cara uninstall?</strong></summary>

**A:** Uninstall dapat dilakukan dengan menghapus paket yang terinstall atau reinstall ulang OS.
</details>

<details>
<summary><strong>Q: Apakah support IPv6?</strong></summary>

**A:** Script ini menonaktifkan IPv6 untuk stabilitas. Jika butuh IPv6, modifikasi script sesuai kebutuhan.
</details>

---

## 🔐 Security Features

### Built-in Security

- ✅ **Fail2ban Protection** - Auto-ban IP mencurigakan
- ✅ **Firewall Rules** - Konfigurasi firewall optimal
- ✅ **SSH Hardening** - Keamanan SSH ditingkatkan
- ✅ **Port Security** - Port management otomatis
- ✅ **Log Monitoring** - Real-time log monitoring

### Best Practices

```bash
# Ubah SSH port default
nano /etc/ssh/sshd_config
# Port 22 -> Port 2222

# Disable root login
PermitRootLogin no

# Restart SSH
systemctl restart sshd
```

---

## 📞 Support & Contact

<div align="center">

### Butuh Bantuan?

📧 **Email**: support@xtrimertunnel.com  
💬 **Telegram**: [@XtrimerSupport](https://t.me/XtrimerSupport)  
🌐 **Website**: [xtrimertunnel.com](https://xtrimertunnel.com)  
📚 **Documentation**: [docs.xtrimertunnel.com](https://docs.xtrimertunnel.com)

</div>

---

## 📝 Changelog

### Version 1.0.0 (Latest)
- ✅ Initial release
- ✅ Support Debian 10-13
- ✅ Support Ubuntu 18-25
- ✅ Fail2ban integration
- ✅ DNS optimization
- ✅ AT scheduler support

---

## 📄 License

This project is licensed under the **MIT License**.

---

## ⚠️ Disclaimer

Script ini disediakan "as-is" tanpa garansi. Pengguna bertanggung jawab penuh atas penggunaan script ini. Pastikan Anda memahami setiap perintah sebelum menjalankannya di production server.

---

## 🤝 Contributing

Contributions are welcome! Silakan submit Pull Request atau buka Issue untuk bug reports dan feature requests.

---

## ⭐ Star History

Jika project ini membantu Anda, berikan ⭐ di repository!

---

<div align="center">

**Made with ❤️ by XTRIMER TUNNEL**

© 2024 AutoScript Installer. All rights reserved.

</div>
