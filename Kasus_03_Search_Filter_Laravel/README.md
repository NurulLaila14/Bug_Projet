# Kasus 03 — Pencarian dan Filter Buku

## Deskripsi Project

Project ini merupakan aplikasi web sederhana untuk menampilkan, mencari, dan memfilter data buku berdasarkan judul, penulis, dan kategori.

Project dibuat menggunakan Laravel dengan memanfaatkan Request, Eloquent ORM, query database, dan Blade sebagai template untuk menampilkan halaman.

Project ini merupakan bagian dari tugas Bug Battle dengan fokus utama memperbaiki fitur pencarian dan filter buku agar dapat berjalan sesuai kebutuhan.

## Tujuan

Tujuan pengerjaan project ini adalah:

1. Memperbaiki pengambilan kata kunci dari form ke Controller.
2. Menerapkan pencarian parsial menggunakan `LIKE`.
3. Menggabungkan pencarian judul dan penulis menggunakan `where` dan `orWhere`.
4. Memperbaiki filter buku berdasarkan kategori.
5. Mengirimkan data hasil pencarian dan nilai filter dari Controller ke View.
6. Menampilkan pesan ketika data buku tidak ditemukan.

## Teknologi yang Digunakan

- PHP
- Laravel
- MySQL
- Blade Template
- Bootstrap
- Eloquent ORM

## Instalasi dan Konfigurasi

### 1. Clone Repository

Clone repository kasus dari GitLab atau gunakan folder project yang sudah tersedia.

### 2. Install Dependency

Jalankan perintah berikut pada terminal:

```bash
composer install
```

### 3. Konfigurasi Environment

Salin file `.env.example` menjadi `.env`, kemudian sesuaikan konfigurasi database.

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=bug_battle_case_03
DB_USERNAME=root
DB_PASSWORD=
```

### 4. Generate Application Key

```bash
php artisan key:generate
```

### 5. Membuat Database

Buat database MySQL dengan nama:

`bug_battle_case_03`

### 6. Migrasi dan Seeder

Jalankan perintah berikut:

```bash
php artisan optimize:clear
php artisan migrate
php artisan db:seed
```

### 7. Menjalankan Aplikasi

```bash
php artisan serve
```

Buka aplikasi melalui browser:

http://127.0.0.1:8000/books

## Fitur Aplikasi

1. Menampilkan seluruh data buku.
2. Mencari buku berdasarkan judul.
3. Mencari buku berdasarkan nama penulis.
4. Memfilter buku berdasarkan kategori.
5. Menggabungkan pencarian dengan filter kategori.
6. Mempertahankan kata kunci dan kategori setelah pencarian.
7. Menampilkan pesan ketika buku tidak ditemukan.

## Perbaikan Bug

Perbaikan dilakukan pada dua file utama:

### 1. BookController.php

Perbaikan yang dilakukan:

- Menggunakan `$request->input()` untuk mengambil parameter pencarian dan kategori.
- Menggunakan `LIKE` untuk pencarian berdasarkan sebagian kata.
- Menggunakan `where` dan `orWhere` untuk mencari berdasarkan judul atau penulis.
- Menambahkan kondisi filter berdasarkan `category_id`.
- Mengirimkan variabel `$books`, `$categories`, `$keyword`, dan `$category` ke halaman Blade.

### 2. resources/views/books/index.blade.php

Perbaikan yang dilakukan:

- Menyesuaikan nama parameter form dengan Controller.
- Menampilkan kembali kata kunci setelah form dikirim.
- Mempertahankan kategori yang dipilih setelah pencarian.
- Memperjelas penggunaan variabel kategori pada perulangan.
- Menampilkan pesan "Buku tidak ditemukan" ketika hasil pencarian kosong.

## Hasil Perbaikan

Setelah perbaikan dilakukan, fitur pencarian dan filter buku dapat berjalan sesuai kebutuhan.

Pengguna dapat mencari buku berdasarkan sebagian judul maupun nama penulis, memilih kategori tertentu, serta menggabungkan pencarian dengan filter kategori.

Nilai pencarian dan kategori tetap ditampilkan setelah form dikirim. Apabila tidak terdapat buku yang sesuai dengan pencarian, aplikasi akan menampilkan pesan bahwa buku tidak ditemukan.

## Pengujian

Pengujian dilakukan dengan beberapa skenario berikut:

| No. | Skenario Pengujian | Hasil |
|---|---|---|
| 1 | Menampilkan seluruh buku | Berhasil |
| 2 | Mencari berdasarkan judul | Berhasil |
| 3 | Mencari berdasarkan penulis | Berhasil |
| 4 | Memfilter berdasarkan kategori | Berhasil |
| 5 | Menggabungkan pencarian dan filter | Berhasil |
| 6 | Mencari data yang tidak tersedia | Berhasil |

## Kesimpulan

Melalui pengerjaan kasus ini, dilakukan perbaikan pada fitur pencarian dan filter buku dengan berfokus pada pengolahan parameter Request, query Eloquent, serta pengiriman data dari Controller ke View.

Perbaikan dilakukan pada `BookController.php` dan `resources/views/books/index.blade.php`. Setelah dilakukan pengujian, seluruh fitur pencarian dan filter dapat berjalan sesuai dengan tujuan pengerjaan.
