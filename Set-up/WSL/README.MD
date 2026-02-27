# 🚀 FULL SETUP WSL2 + UBUNTU (VERSI LTS & NON-LTS) DI WINDOWS

Dokumentasi ini menjelaskan instalasi lengkap:

- WSL2
- Ubuntu 22.04 LTS
- Ubuntu versi terbaru (non-LTS / default)
- Konfigurasi default user
- Setup dasar development
- Troubleshooting
- Best practice

Support untuk:
- Windows 10 (2004+)
- Windows 11

---

# 📌 1. PERSYARATAN

Pastikan:

- Virtualization aktif di BIOS (Intel VT-x / AMD-V)
- Akses Administrator
- Internet aktif
- Windows sudah update

---

# 🔧 2. INSTALL WSL2

## 2.1 Buka PowerShell sebagai Administrator

- Klik Start
- Ketik `PowerShell`
- Klik kanan → **Run as Administrator**

---

## 2.2 Install WSL Otomatis (Direkomendasikan)

```powershell
wsl --install
```

Perintah ini akan:

- Mengaktifkan Windows Subsystem for Linux
- Mengaktifkan Virtual Machine Platform
- Menginstall WSL2
- Menginstall Ubuntu default

Restart komputer setelah selesai.

---

## 2.3 Pastikan Menggunakan WSL2

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

# 🐧 3. INSTALL UBUNTU 22.04 LTS

## 3.1 Install Ubuntu 22.04 LTS

```powershell
wsl --install -d Ubuntu-22.04
```

Atau install via Microsoft Store:
Cari: **Ubuntu 22.04 LTS**

---

## 3.2 Jalankan Ubuntu 22.04 LTS

```powershell
wsl -d Ubuntu-22.04
```

Saat pertama kali dijalankan akan muncul:

```
Enter new UNIX username:
```

User yang dibuat di sini akan menjadi default user.

---

## 3.3 Set Default User ke root (Opsional)

```powershell
ubuntu2204 config --default-user root
```

Atau:

```powershell
ubuntu2204.exe config --default-user root
```

Cek:

```powershell
wsl -d Ubuntu-22.04 whoami
```

---

# 🐧 4. INSTALL UBUNTU VERSI TERBARU (NON-LTS / DEFAULT)

## 4.1 Install Ubuntu (Versi Default Store)

```powershell
wsl --install -d Ubuntu
```

Atau install dari Microsoft Store:
Cari: **Ubuntu**

Versi ini biasanya versi terbaru non-LTS.

---

## 4.2 Jalankan Ubuntu Non-LTS

```powershell
wsl -d Ubuntu
```

Akan diminta membuat username & password.

---

## 4.3 Set Default User ke root (Opsional)

```powershell
ubuntu config --default-user root
```

Cek:

```powershell
wsl -d Ubuntu whoami
```

---

# 🔄 5. UPDATE SISTEM (BERLAKU UNTUK SEMUA VERSI)

Masuk ke Ubuntu lalu jalankan:

```bash
apt update && apt upgrade -y
```

Install paket dasar:

```bash
apt install build-essential curl wget git unzip software-properties-common -y
```

---

# 📦 6. INSTALL TOOLS DEVELOPMENT

## Install Git

```bash
apt install git -y
git --version
```

---

## Install NodeJS LTS

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

## Install Docker

```bash
apt install docker.io -y
service docker start
docker --version
```

---

# 📁 7. AKSES FILE SYSTEM

## Akses File Linux dari Windows

Buka File Explorer:

```
\\wsl$\Ubuntu-22.04\
```

atau

```
\\wsl$\Ubuntu\
```

---

## Akses Drive Windows dari Ubuntu

```bash
/mnt/c
/mnt/d
```

---

# 🧠 8. PERINTAH PENTING WSL

## Lihat semua distro

```powershell
wsl -l -v
```

## Masuk ke distro tertentu

```powershell
wsl -d Ubuntu-22.04
wsl -d Ubuntu
```

## Shutdown WSL

```powershell
wsl --shutdown
```

## Uninstall distro

```powershell
wsl --unregister Ubuntu-22.04
wsl --unregister Ubuntu
```

---

# ⚙ 9. TROUBLESHOOTING

## Virtualization Not Enabled

Masuk BIOS → Aktifkan:
- Intel VT-x
- AMD-V

---

## Kernel Update Error

Download manual:

https://aka.ms/wsl2kernel

Install lalu restart.

---

## WSL Lambat

Rekomendasi:

- Simpan project di dalam `/home`
- Hindari bekerja langsung di `/mnt/c`

---

# 🔐 10. BEST PRACTICE

- Gunakan user biasa untuk development
- Gunakan root hanya jika diperlukan
- Update rutin:

```bash
apt update && apt upgrade -y
```

- Simpan project di:

```
/home/username/project
```

---

# 🧹 11. RESET TOTAL WSL

Uninstall distro:

```powershell
wsl --unregister Ubuntu-22.04
wsl --unregister Ubuntu
```

Uninstall WSL:

```powershell
wsl --uninstall
```

Restart lalu install ulang.

---

# ✅ SELESAI

Sekarang Anda memiliki:

- WSL2 aktif
- Ubuntu 22.04 LTS terinstall
- Ubuntu versi terbaru (non-LTS) terinstall
- Default user dapat diatur
- Environment siap untuk development

---

🚀 Selamat menggunakan WSL2 + Ubuntu