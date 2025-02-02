# Laravel 11 Blog CMS

## 📌 Persyaratan Minimum
Sebelum menginstal, pastikan server/lokal kamu memenuhi persyaratan berikut:

- PHP 8.2 atau lebih baru
- Composer 2.0 atau lebih baru
- MySQL / MariaDB
- Ekstensi PHP yang dibutuhkan:
  - OpenSSL
  - PDO
  - Mbstring
  - Tokenizer
  - XML
  - Ctype
  - JSON
  - Fileinfo

---

## 🚀 Cara Instalasi di Lokal

### 1. Clone Repository
```bash
git clone https://github.com/username/repository.git
cd repository
```
> Ganti `username/repository` dengan URL GitHub proyekmu.

### 2. Install Dependensi dengan Composer
```bash
composer install
```

### 3. Copy dan Konfigurasi `.env`
```bash
cp .env.example .env
```
Lalu ubah konfigurasi database di `.env` sesuai dengan setting lokal kamu:
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nama_database
DB_USERNAME=root
DB_PASSWORD=
```

### 4. Generate Application Key
```bash
php artisan key:generate
```

### 5. Migrate dan Seed Database
```bash
php artisan migrate --seed
```

### 6. Jalankan Server
```bash
php artisan serve
```
Akses di browser: [http://127.0.0.1:8000](http://127.0.0.1:8000)

---

## 🌍 Cara Instalasi di Hosting Hostinger (Tanpa SSH)

### 1. Upload Project ke Hostinger
- **Kompres** folder Laravel menjadi **ZIP** (tanpa folder `vendor`).
- **Upload** ke **File Manager** di Hostinger.
- **Ekstrak** file ZIP di dalam direktori public_html atau subfolder yang diinginkan.

### 2. Konfigurasi `.env`
Edit file `.env` dan sesuaikan dengan database Hostinger:
```
DB_CONNECTION=mysql
DB_HOST=your_hostinger_host
DB_PORT=3306
DB_DATABASE=your_db_name
DB_USERNAME=your_db_user
DB_PASSWORD=your_db_password
```
> **Catatan:** Kamu bisa mendapatkan informasi database di menu **Database MySQL** di Hostinger.

### 3. Upload Vendor (Tanpa SSH)
Karena tidak bisa menjalankan `composer install`, gunakan langkah berikut:
1. **Di lokal**, jalankan:
   ```bash
   composer install --no-dev --optimize-autoloader
   ```
2. **Kompres** folder `vendor` dalam ZIP.
3. **Upload & Ekstrak** di hosting (di root proyek Laravel).

### 4. Setel Public Folder sebagai Root
1. Masuk ke **File Manager** di Hostinger.
2. Pindahkan semua file di dalam folder `public` ke root (`public_html`).
3. Edit file `index.php` di `public_html`:
   ```php
   require __DIR__.'/../bootstrap/autoload.php';
   $app = require_once __DIR__.'/../bootstrap/app.php';
   ```
   Ubah menjadi:
   ```php
   require __DIR__.'/bootstrap/autoload.php';
   $app = require_once __DIR__.'/bootstrap/app.php';
   ```

### 5. Setel Permission Folder
Pastikan folder berikut memiliki izin **775 atau 777**:
```bash
storage/
bootstrap/cache/
```

### 6. Jalankan Migrasi Database Secara Manual
Karena tidak ada SSH, buat tabel secara manual dengan import file SQL dari hasil perintah ini di lokal:
```bash
php artisan schema:dump --prune
```
Lalu **import** hasil dump ke database Hostinger via **phpMyAdmin**.

### 7. Selesai 🎉
Akses website di **domain kamu** dan pastikan semuanya berjalan dengan baik.

---

## 🔑 Login Admin
- **URL:** `yourdomain.com/login`
- **Default Admin:**
  - Email: `admin@example.com`
  - Password: `password`

> **Jangan lupa untuk mengganti password setelah login pertama kali!**

---

## 📌 Lisensi
Proyek ini dirilis di bawah lisensi **MIT**. Silakan gunakan dan modifikasi sesuai kebutuhan.

---

## 🎯 Kontribusi
Jika ingin berkontribusi, silakan buat **Pull Request** atau laporkan **Issue** di GitHub.

💡 Happy Coding! 🚀

