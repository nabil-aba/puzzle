# 🧩 Game Public Collection

Selamat datang di Game Public Collection! Repositori ini adalah etalase publik yang berisi kumpulan hasil _build_ dari berbagai proyek game interaktif. Setiap folder di sini adalah sebuah aplikasi web mandiri yang siap digunakan, di-hosting, atau dijadikan template untuk proyekmu sendiri.

Tujuan utama repositori ini adalah untuk menyediakan versi _production-ready_ dari setiap game, yang bisa dengan mudah diambil oleh siapa saja tanpa perlu mengakses source code aslinya yang bersifat privat.

---

## Cara Menggunakan Salah Satu Game

Jika kamu ingin mengambil salah satu game (misalnya, `game1`) untuk dijadikan proyekmu sendiri, kamu tidak perlu meng-clone seluruh repositori ini yang mungkin akan menjadi sangat besar.

Metode yang kami rekomendasikan adalah menggunakan **Git Sparse Checkout**. Dengan cara ini, kamu hanya akan mengunduh folder yang kamu butuhkan sambil tetap mempertahankan koneksi dan _history_ ke repositori ini, sehingga kamu bisa mendapatkan pembaruan di masa depan.

### Metode Utama: Git Sparse Checkout (Direkomendasikan)

Ikuti langkah-langkah ini di terminalmu.

#### Langkah 1: Clone Repositori Tanpa Mengunduh File

Pertama, kita akan meng-clone repositori ini dalam mode "kosong". Perintah ini sangat cepat karena tidak mengunduh file apa pun, hanya struktur dan history Git.

```bash
git clone --filter=blob:none --no-checkout https://github.com/nabil-aba/game-public.git
```

#### Langkah 2: Masuk ke Direktori Proyek

```bash
cd game-public
```

#### Langkah 3: Inisialisasi Sparse Checkout

Aktifkan fitur sparse checkout. Mode `--cone` adalah mode modern yang lebih sederhana dan intuitif.

```bash
git sparse-checkout init --cone
```

#### Langkah 4: Pilih Folder yang Ingin Diunduh

Sekarang, beri tahu Git folder mana yang ingin kamu "wujudkan" di komputermu. Ganti `game1` dengan nama game yang kamu inginkan.

```bash
# Untuk mengambil satu folder saja
git sparse-checkout set game1

# Jika kamu ingin mengambil beberapa folder sekaligus
# git sparse-checkout set game1 game2
```

Git akan secara otomatis mengunduh semua file yang ada di dalam folder `game1`. Sekarang, jika kamu lihat isi direktori `game-public`, hanya akan ada folder `game1` di dalamnya.

---

### Langkah Selanjutnya: Menjadikannya Proyekmu Sendiri

Setelah kamu berhasil mendapatkan folder game-mu, tujuanmu adalah menjadikannya repositori Git milikmu sendiri.

#### 1. Salin Folder ke Lokasi Baru

Keluar dari direktori `game-public` dan salin folder game yang sudah kamu unduh ke tempat lain.

```bash
# Keluar dari direktori game-public
cd ..

# Salin folder game1 menjadi proyek-game-baru
cp -r game-public/game1 proyek-game-baru
```

#### 2. Inisialisasi sebagai Repositori Git Baru

Masuk ke folder proyek barumu dan inisialisasi sebagai repositori Git.

```bash
cd proyek-game-baru
git init
git add .
git commit -m "Initial commit from game-public template"
```

#### 3. Buat Repositori Baru di Akun GitHub-mu

Pergi ke GitHub dan buat sebuah repositori baru (misalnya, `proyek-game-saya`) tanpa menginisialisasinya dengan README.

#### 4. Hubungkan dan Push Proyekmu

Kembali ke terminal, hubungkan repositori lokalmu ke remote yang baru saja kamu buat di GitHub, lalu lakukan push.

```bash
# Ganti URL dengan URL repo barumu
git remote add origin https://github.com/USERNAME-KAMU/proyek-game-saya.git

# Ganti nama branch jika perlu (misal: main atau master)
git branch -M main

# Push untuk pertama kali
git push -u origin main
```

**Selesai!** Sekarang kamu memiliki salinan game tersebut di repositorimu sendiri dan bisa mulai mengeditnya, misalnya mengubah data di dalam folder `assets`.

---

### Bagaimana Cara Mendapatkan Update?

Keuntungan menggunakan metode Sparse Checkout adalah kamu masih terhubung dengan repositori `game-public` asli. Jika suatu saat ada pembaruan pada `game1`, kamu bisa mendapatkannya dengan mudah.

```bash
# Masuk kembali ke direktori game-public hasil clone awal
cd ../game-public

# Tarik perubahan terbaru dari remote
git pull
```

Setelah itu, kamu bisa membandingkan perubahan dan mengaplikasikannya secara manual ke repositori `proyek-game-baru` milikmu.

### Metode Alternatif: `degit`

Jika kamu tidak peduli dengan history Git dan hanya ingin salinan bersih dari sebuah folder, `degit` adalah alat yang fantastis.

```bash
# Perintah ini akan membuat folder 'proyek-game-saya'
# yang berisi salinan bersih dari folder 'game1'
npx degit nabil-aba/game-public/game1 proyek-game-saya
```
