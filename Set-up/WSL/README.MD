# 🚀 FULL SETUP WSL2 + Ubuntu 22.04 LTS di Windows

Dokumentasi ini berisi panduan lengkap untuk:

- Install WSL2
- Install Ubuntu 22.04 LTS
- Set default user menjadi root
- Konfigurasi dasar sistem
- Setup environment development
- Troubleshooting
- Best practice

Support untuk:
- Windows 10 (versi 2004 ke atas)
- Windows 11

---

# 📌 1. Persyaratan Sistem

Pastikan sistem memenuhi syarat berikut:

- Windows 10 (2004+) / Windows 11
- Virtualization aktif di BIOS (Intel VT-x / AMD-V)
- Akses Administrator
- Koneksi internet aktif

---

# 🔧 2. Install WSL2

## 2.1 Buka PowerShell sebagai Administrator

1. Klik **Start**
2. Ketik: `PowerShell`
3. Klik kanan → **Run as Administrator**

---

## 2.2 Install WSL (Metode Otomatis - Direkomendasikan)

```powershell
wsl --install
```

Perintah ini akan otomatis:

- Mengaktifkan Windows Subsystem for Linux
- Mengaktifkan Virtual Machine Platform
- Menginstall WSL2
- Menginstall Ubuntu default

Setelah selesai → **Restart komputer**

---

## 2.3 Set Default WSL ke Versi 2

```powershell
wsl --set-default-version 2
```

Cek status:

```powershell
wsl --status
```

Cek daftar distro:

```powershell
wsl -l -v
```

---

# 🐧 3. Install Ubuntu 22.04 LTS

## Opsi 1 (Direkomendasikan - Command Line)

```powershell
wsl --install -d Ubuntu-22.04
```

## Opsi 2 (Microsoft Store)

1. Buka **Microsoft Store**
2. Cari: **Ubuntu 22.04 LTS**
3. Klik **Install**

---

# ▶ 4. Menjalankan Ubuntu

```powershell
wsl
```

atau

```powershell
ubuntu
```

Pada first launch Anda akan diminta membuat:

- Username
- Password

---

# 👑 5. Set Default User Menjadi Root

Secara default Ubuntu menggunakan user biasa.

Jika ingin login langsung sebagai root:

Jalankan di PowerShell:

```powershell
ubuntu config --default-user root
```

atau

```powershell
ubuntu.exe config --default-user root
```

Verifikasi:

```powershell
wsl
whoami
```

Output harus:

```
root
```

---

# 🔄 6. Update dan Upgrade Ubuntu

Masuk ke Ubuntu lalu jalankan:

```bash
apt update && apt upgrade -y
```

Install package dasar:

```bash
apt install build-essential curl wget git unzip software-properties-common -y
```

---

# 📦 7. Install Tools Development (Opsional)

## Install Git

```bash
apt install git -y
git --version
```

---

## Install NodeJS (LTS)

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | bash -
apt install nodejs -y
node -v
npm -v
```

---

## Install Python

```bash
apt install python3 python3-pip -y
python3 --version
pip3 --version
```

---

## Install Docker (Opsional)

```bash
apt install docker.io -y
service docker start
docker --version
```

---

# 📁 8. Struktur File System

## Akses File Linux dari Windows

Buka File Explorer dan akses:

```
\\wsl$\Ubuntu-22.04\
```

---

## Akses Drive Windows dari Ubuntu

```bash
/mnt/c
/mnt/d
```

---

# 🧠 9. Perintah Penting WSL

## Melihat daftar distro

```powershell
wsl -l -v
```

## Masuk ke distro tertentu

```powershell
wsl -d Ubuntu-22.04
```

## Shutdown WSL

```powershell
wsl --shutdown
```

## Restart WSL

```powershell
wsl --shutdown
wsl
```

## Uninstall Ubuntu

```powershell
wsl --unregister Ubuntu-22.04
```
