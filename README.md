# AntrianFarmasi

**Sistem Informasi Antrian Farmasi Rumah Sakit**

AntrianFarmasi adalah aplikasi berbasis PHP untuk membantu pelayanan antrean farmasi, meliputi pengambilan/penanganan antrean, pemanggilan nomor, tampilan monitor, dan dukungan suara pemanggilan.

Repository: https://github.com/RokhmanCore/AntrianFarmasi

## Fitur dan modul

- Halaman utama aplikasi.
- Modul administrasi di direktori `admin/`.
- Halaman monitor antrean di direktori `display/` dan file terkait.
- Endpoint pelayanan dan API di direktori `public/`.
- Modul tambahan di direktori `new/`.
- Aplikasi panel pemanggilan berbasis Python di direktori `python_app/`.
- Konfigurasi koneksi database dan layanan di direktori `config/`.

## Persyaratan

- Web server Apache (misalnya XAMPP).
- PHP dengan ekstensi MySQLi aktif.
- MySQL atau MariaDB.
- Browser modern.
- Composer untuk memasang dependensi PHP.
- Python dan dependensi pada `python_app/requirements.txt` jika menggunakan aplikasi panel pemanggilan Python.

## Instalasi lokal dengan XAMPP

### 1. Siapkan web server

Instal XAMPP, kemudian jalankan Apache dan MySQL.

### 2. Unduh source code

Clone repository:

```bash
git clone https://github.com/RokhmanCore/AntrianFarmasi.git
```

Atau unduh ZIP dari halaman GitHub, lalu ekstrak ke direktori web server.

Lokasi contoh:

**Windows**
```text
C:\xampp\htdocs\AntrianFarmasi
```

**macOS (XAMPP)**
```text
/Applications/XAMPP/xamppfiles/htdocs/AntrianFarmasi
```

### 3. Buat database

1. Buka phpMyAdmin melalui `http://localhost/phpmyadmin`.
2. Buat database bernama `antrian_farmasi`.
3. Impor dump SQL database AntrianFarmasi yang diperoleh dari pemilik/pengelola proyek atau dari salinan instalasi yang sah.

**Penting:** dump database `antrian_farmasi.sql` tidak disertakan di repository saat ini. Berkas SQL diabaikan oleh aturan `.gitignore` (`*.sql`) agar dump database tidak terunggah tanpa pemeriksaan. Karena itu, proses instalasi belum dapat menyelesaikan pembuatan tabel hanya dengan clone repository ini; siapkan dump SQL secara terpisah terlebih dahulu.

### 4. Atur koneksi database

Buka `config/db.php` dan sesuaikan nilai berikut dengan lingkungan lokal:

- `$host`: alamat server database (umumnya `localhost`).
- `$user`: username MySQL/MariaDB.
- `$pass`: password database.
- `$db`: nama database (default pada source: `antrian_farmasi`).

Jangan gunakan kredensial produksi pada komputer pengembangan. Jangan commit password, token, atau kredensial server ke repository publik.

### 5. Pasang dependensi PHP

Di direktori utama proyek, jalankan:

```bash
composer install
```

Dependensi Composer yang dideklarasikan pada `composer.json` mencakup `google/cloud-text-to-speech`. Jika Composer belum terpasang, ikuti petunjuk instalasi resmi Composer terlebih dahulu.

### 6. Jalankan aplikasi

Pastikan Apache dan MySQL aktif, lalu buka:

```text
http://localhost/AntrianFarmasi/
```

Jika proyek dipasang pada nama folder atau virtual host berbeda, sesuaikan URL-nya.

## Aplikasi panel pemanggilan Python (opsional)

Jika fitur panel pemanggilan Python digunakan:

1. Pastikan Python tersedia.
2. Masuk ke direktori `python_app/`.
3. Pasang dependensi yang tercantum:

```bash
python -m pip install -r requirements.txt
```

4. Periksa dan sesuaikan konfigurasi server pada `config_server.json` sebelum menjalankan aplikasi.

File executable Windows yang tersedia berada di `python_app/dist/`. Penggunaan executable dan konfigurasi perangkat perlu diuji pada komputer tujuan.

## Struktur direktori

```text
AntrianFarmasi/
├── admin/              # Modul administrasi
├── config/             # Konfigurasi aplikasi dan database
├── display/            # Modul monitor antrean dan pemanggilan
├── new/                # Modul aplikasi tambahan
├── nginx/              # Berkas Nginx yang disertakan
├── public/             # Modul pelayanan dan API
├── python_app/         # Panel pemanggilan berbasis Python
├── composer.json       # Dependensi PHP
├── index.php           # Halaman utama
└── display_antrian.php # Halaman tampilan antrean
```

## Catatan keamanan dan operasional

- Lakukan pengujian di lingkungan lokal/staging sebelum digunakan pada layanan rumah sakit.
- Backup database secara berkala.
- Batasi akses ke panel administrasi sesuai kebutuhan.
- Pastikan file konfigurasi tidak berisi kredensial yang dapat diakses publik.
- Jangan mengunggah dump database pasien, data pribadi, log operasional sensitif, password, atau token ke repository publik.
- Komponen dan konfigurasi Nginx/Python yang disertakan perlu disesuaikan dengan sistem operasi dan infrastruktur masing-masing.

## Status dokumentasi

Panduan ini menjelaskan instalasi dasar berdasarkan struktur repository saat ini. Instalasi penuh memerlukan dump SQL database yang tidak disertakan di repository. Detail konfigurasi layanan suara dan perangkat pemanggilan dapat berbeda sesuai lingkungan pemasangan.

