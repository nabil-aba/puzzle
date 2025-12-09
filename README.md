# 🧩 Puzzle Public Collection

Selamat datang di Puzzle Public Collection! Repositori ini adalah etalase publik yang berisi kumpulan hasil _build_ dari berbagai proyek puzzle interaktif. Setiap folder di sini adalah sebuah aplikasi web mandiri yang siap digunakan, di-hosting, atau dijadikan template untuk proyekmu sendiri.

Tujuan utama repositori ini adalah untuk menyediakan versi _production-ready_ dari setiap puzzle, yang bisa dengan mudah diambil oleh siapa saja tanpa perlu mengakses source code aslinya yang bersifat privat.

---

## Cara Menggunakan Salah Satu Puzzle

Jika kamu ingin mengambil salah satu puzzle (misalnya, `puzzle1`) untuk dijadikan proyekmu sendiri, kamu tidak perlu meng-clone seluruh repositori ini yang mungkin akan menjadi sangat besar.

Metode yang kami rekomendasikan adalah menggunakan **Git Sparse Checkout**. Dengan cara ini, kamu hanya akan mengunduh folder yang kamu butuhkan sambil tetap mempertahankan koneksi dan _history_ ke repositori ini, sehingga kamu bisa mendapatkan pembaruan di masa depan.

### Metode Utama: Git Sparse Checkout (Direkomendasikan)

Ikuti langkah-langkah ini di terminalmu.

#### Langkah 1: Clone Repositori Tanpa Mengunduh File

Pertama, kita akan meng-clone repositori ini dalam mode "kosong". Perintah ini sangat cepat karena tidak mengunduh file apa pun, hanya struktur dan history Git.

```bash
git clone --filter=blob:none --no-checkout https://github.com/nabil-aba/puzzle-public.git
```

#### Langkah 2: Masuk ke Direktori Proyek

```bash
cd puzzle-public
```

#### Langkah 3: Inisialisasi Sparse Checkout

Aktifkan fitur sparse checkout. Mode `--cone` adalah mode modern yang lebih sederhana dan intuitif.

```bash
git sparse-checkout init --cone
```

#### Langkah 4: Pilih Folder yang Ingin Diunduh

Sekarang, beri tahu Git folder mana yang ingin kamu "wujudkan" di komputermu. Ganti `puzzle1` dengan nama puzzle yang kamu inginkan.

```bash
# Untuk mengambil satu folder saja
git sparse-checkout set puzzle1

# Jika kamu ingin mengambil beberapa folder sekaligus
# git sparse-checkout set puzzle1 puzzle2
```

Git akan secara otomatis mengunduh semua file yang ada di dalam folder `puzzle1`. Sekarang, jika kamu lihat isi direktori `puzzle-public`, hanya akan ada folder `puzzle1` di dalamnya.

---

### Langkah Selanjutnya: Menjadikannya Proyekmu Sendiri

Setelah kamu berhasil mendapatkan folder puzzle-mu, tujuanmu adalah menjadikannya repositori Git milikmu sendiri.

#### 1. Salin Folder ke Lokasi Baru

Keluar dari direktori `puzzle-public` dan salin folder puzzle yang sudah kamu unduh ke tempat lain.

```bash
# Keluar dari direktori puzzle-public
cd ..

# Salin folder puzzle1 menjadi proyek-puzzle-baru
cp -r puzzle-public/puzzle1 proyek-puzzle-baru
```

#### 2. Inisialisasi sebagai Repositori Git Baru

Masuk ke folder proyek barumu dan inisialisasi sebagai repositori Git.

```bash
cd proyek-puzzle-baru
git init
git add .
git commit -m "Initial commit from puzzle-public template"
```

#### 3. Buat Repositori Baru di Akun GitHub-mu

Pergi ke GitHub dan buat sebuah repositori baru (misalnya, `proyek-puzzle-saya`) tanpa menginisialisasinya dengan README.

#### 4. Hubungkan dan Push Proyekmu

Kembali ke terminal, hubungkan repositori lokalmu ke remote yang baru saja kamu buat di GitHub, lalu lakukan push.

```bash
# Ganti URL dengan URL repo barumu
git remote add origin https://github.com/USERNAME-KAMU/proyek-puzzle-saya.git

# Ganti nama branch jika perlu (misal: main atau master)
git branch -M main

# Push untuk pertama kali
git push -u origin main
```

**Selesai!** Sekarang kamu memiliki salinan puzzle tersebut di repositorimu sendiri dan bisa mulai mengeditnya, misalnya mengubah data di dalam folder `assets`.

---

### Bagaimana Cara Mendapatkan Update?

Keuntungan menggunakan metode Sparse Checkout adalah kamu masih terhubung dengan repositori `puzzle-public` asli. Jika suatu saat ada pembaruan pada `puzzle1`, kamu bisa mendapatkannya dengan mudah.

```bash
# Masuk kembali ke direktori puzzle-public hasil clone awal
cd ../puzzle-public

# Tarik perubahan terbaru dari remote
git pull
```

Setelah itu, kamu bisa membandingkan perubahan dan mengaplikasikannya secara manual ke repositori `proyek-puzzle-baru` milikmu.

### Metode Alternatif: `degit`

Jika kamu tidak peduli dengan history Git dan hanya ingin salinan bersih dari sebuah folder, `degit` adalah alat yang fantastis.

```bash
# Perintah ini akan membuat folder 'proyek-puzzle-saya'
# yang berisi salinan bersih dari folder 'puzzle1'
npx degit nabil-aba/puzzle-public/puzzle1 proyek-puzzle-saya
```
