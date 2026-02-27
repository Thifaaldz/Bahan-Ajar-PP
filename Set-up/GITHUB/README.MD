# 🔐 SETUP GITHUB DI WSL UBUNTU (SSH & HTTPS)

Dokumentasi ini menjelaskan cara:

- Setup koneksi GitHub menggunakan SSH
- Alternatif login menggunakan HTTPS (Personal Access Token)
- Test koneksi
- Clone repository via SSH & HTTPS
- Push repository baru
- Update repository

Berlaku untuk:
- Ubuntu di WSL2
- Ubuntu 22.04 LTS / Non-LTS

---

# 1️⃣ PERSIAPAN AWAL

Pastikan Git sudah terinstall:

```bash
sudo apt update
sudo apt install git -y
```

Cek versi:

```bash
git --version
```

Konfigurasi global (jika belum pernah):

```bash
git config --global user.name "Nama Anda"
git config --global user.email "email_anda@example.com"
git config --global init.defaultBranch main
```

---

# ==========================================
# 🚀 METODE 1 — MENGGUNAKAN SSH (RECOMMENDED)
# ==========================================

SSH lebih aman dan tidak perlu login berulang kali.

---

# 2️⃣ CEK KUNCI SSH YANG SUDAH ADA

```bash
ls -al ~/.ssh
```

Jika terdapat:

```
id_rsa
id_rsa.pub
```

atau

```
id_ed25519
id_ed25519.pub
```

Maka Anda sudah memiliki SSH key.

Jika tidak ada, lanjut ke langkah berikutnya.

---

# 3️⃣ MEMBUAT SSH KEY BARU (RECOMMENDED: ED25519)

Gunakan metode modern:

```bash
ssh-keygen -t ed25519 -C "email_anda@example.com"
```

Jika sistem lama dan tidak mendukung:

```bash
ssh-keygen -t rsa -b 4096 -C "email_anda@example.com"
```

Saat diminta:

- Tekan Enter untuk lokasi default
- Masukkan passphrase (disarankan) atau Enter untuk kosong

---

# 4️⃣ JALANKAN SSH AGENT

```bash
eval "$(ssh-agent -s)"
```

Tambahkan key:

```bash
ssh-add ~/.ssh/id_ed25519
```

Jika menggunakan RSA:

```bash
ssh-add ~/.ssh/id_rsa
```

---

# 5️⃣ SALIN PUBLIC KEY

```bash
cat ~/.ssh/id_ed25519.pub
```

Salin seluruh output.

---

# 6️⃣ TAMBAHKAN KE GITHUB

1. Login ke GitHub
2. Klik foto profil → Settings
3. Pilih "SSH and GPG keys"
4. Klik **New SSH key**
5. Isi Title (misal: WSL Ubuntu)
6. Paste key ke kolom Key
7. Klik **Add SSH key**

---

# 7️⃣ TEST KONEKSI SSH

```bash
ssh -T git@github.com
```

Jika berhasil, akan muncul:

```
Hi username! You've successfully authenticated...
```

Jika muncul konfirmasi fingerprint, ketik:

```
yes
```

---

# 8️⃣ CLONE REPOSITORY VIA SSH

Format:

```bash
git clone git@github.com:username/repository.git
```

Contoh:

```bash
git clone git@github.com:john/project-api.git
```

---

# ==========================================
# 🌐 METODE 2 — MENGGUNAKAN HTTPS
# ==========================================

HTTPS membutuhkan Personal Access Token (PAT).

---

# 9️⃣ BUAT PERSONAL ACCESS TOKEN (PAT)

1. Login ke GitHub
2. Settings → Developer Settings
3. Personal Access Tokens
4. Generate new token (classic atau fine-grained)
5. Pilih scope:
   - repo
6. Generate token
7. Salin token (tidak bisa dilihat lagi)

---

# 🔟 CLONE VIA HTTPS

Format:

```bash
git clone https://github.com/username/repository.git
```

Contoh:

```bash
git clone https://github.com/john/project-api.git
```

Saat diminta:

- Username: username GitHub
- Password: isi dengan Personal Access Token (bukan password akun)

---

# 1️⃣1️⃣ MENYIMPAN CREDENTIAL HTTPS (AGAR TIDAK LOGIN TERUS)

```bash
git config --global credential.helper store
```

Atau lebih aman:

```bash
git config --global credential.helper cache
```

---

# ==========================================
# 📦 MEMBUAT REPOSITORY BARU & PUSH
# ==========================================

---

# 1️⃣2️⃣ BUAT REPOSITORY DI GITHUB

1. Klik "+"
2. New repository
3. Isi nama repository
4. Pilih Public / Private
5. Klik Create repository

---

# 1️⃣3️⃣ HUBUNGKAN PROJECT LOKAL

Masuk ke folder project:

```bash
cd /path/to/project
```

Inisialisasi:

```bash
git init
```

Tambahkan file:

```bash
git add .
```

Commit:

```bash
git commit -m "first commit"
```

Set branch ke main:

```bash
git branch -M main
```

---

# 1️⃣4️⃣ TAMBAHKAN REMOTE

## Jika menggunakan SSH

```bash
git remote add origin git@github.com:username/repository.git
```

## Jika menggunakan HTTPS

```bash
git remote add origin https://github.com/username/repository.git
```

---

# 1️⃣5️⃣ PUSH KE GITHUB

```bash
git push -u origin main
```

---

# ==========================================
# 🔄 UPDATE REPOSITORY
# ==========================================

Tambahkan perubahan:

```bash
git add .
```

Commit:

```bash
git commit -m "Deskripsi perubahan"
```

Push:

```bash
git push
```

---

# 🧠 CEK REMOTE REPOSITORY

```bash
git remote -v
```

---

# 🔁 MENGGANTI REMOTE HTTPS KE SSH

```bash
git remote set-url origin git@github.com:username/repository.git
```

---

# 🔁 MENGGANTI REMOTE SSH KE HTTPS

```bash
git remote set-url origin https://github.com/username/repository.git
```

---

# ✅ REKOMENDASI

Gunakan SSH karena:

- Lebih aman
- Tidak perlu login berulang
- Lebih nyaman untuk development jangka panjang

Gunakan HTTPS jika:

- Menggunakan komputer publik
- Tidak bisa menggunakan SSH

---

# 🎯 SELESAI

Sekarang Anda bisa:

- Clone via SSH
- Clone via HTTPS
- Push repository baru
- Update repository
- Mengganti metode remote kapan saja

Environment GitHub di WSL Ubuntu siap digunakan 🚀