# Langkah-langkah Setup Zsh & Oh My Zsh di WSL Ubuntu

---

## Install Zsh di Ubuntu

### Install Zsh

```bash
sudo apt update
sudo apt install zsh -y
```

Set Zsh sebagai default shell:

```bash
chsh -s $(which zsh)
```

Restart WSL atau logout terlebih dahulu:

```powershell
wsl --shutdown
```

---

## Install Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

## Download zsh-autosuggestions

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

---

## Download zsh-syntax-highlighting

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

---

## Konfigurasi Zsh

Buka file konfigurasi Zsh:

```bash
nano ~/.zshrc
```

Cari baris berikut:

```
plugins=(git)
```

Kemudian ganti dengan:

```
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

Simpan lalu keluar dari nano.

---

## Memuat Ulang Konfigurasi

```bash
source ~/.zshrc
```

---

## Selesai

Sekarang Zsh + Oh My Zsh sudah aktif dengan:

- Plugin autosuggestions
- Plugin syntax highlighting
- Shell lebih interaktif dan produktif