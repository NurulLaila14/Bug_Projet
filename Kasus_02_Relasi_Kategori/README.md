# KASUS – PENCARIAN BUKU DAN FILTER KATEGORI

## Deskripsi

Project ini merupakan pengembangan fitur pencarian dan filter kategori pada aplikasi manajemen buku berbasis Laravel.

Fitur ini digunakan untuk memudahkan user menemukan buku berdasarkan judul atau nama penulis serta menyaring daftar buku berdasarkan kategori tertentu.

## Permasalahan

Terdapat beberapa gejala yang perlu diselidiki pada fitur pencarian dan filter buku:

1. Kata kunci yang dikirim dari form tidak terbaca oleh Controller.
2. Pencarian hanya menemukan data dengan kecocokan persis.
3. Filter kategori tidak berfungsi sesuai pilihan.
4. Variabel hasil pencarian tidak tersedia pada Blade.
5. Input pencarian tidak dipertahankan setelah form dikirim.

## Perbaikan yang Dilakukan

### 1. Menyamakan Parameter Form dan Controller

Nama parameter yang digunakan pada form pencarian disesuaikan dengan nama parameter yang dibaca oleh Controller agar kata kunci dapat diterima dengan benar.

### 2. Menerapkan Pencarian Parsial

Pencarian menggunakan operator `LIKE` agar sistem dapat menemukan data berdasarkan sebagian kata atau karakter yang dimasukkan.

### 3. Menggabungkan Pencarian Judul dan Penulis

Kondisi pencarian judul dan penulis digabungkan menggunakan pengelompokan kondisi agar hasil pencarian dapat mencakup kedua kolom tersebut.

### 4. Menerapkan Filter Kategori

Sistem memeriksa kategori yang dipilih. Jika kategori dipilih, hasil pencarian hanya menampilkan buku dari kategori tersebut.

### 5. Mengirim Data ke View

Controller mengirimkan hasil pencarian dan nilai filter kategori ke Blade agar data dapat ditampilkan sesuai input user.

### 6. Menampilkan Pesan Hasil Kosong

Jika tidak ditemukan buku yang sesuai dengan kata kunci atau kategori, halaman menampilkan pesan bahwa data buku tidak ditemukan.

## Skenario Pengujian

Pengujian dilakukan untuk memastikan seluruh fungsi pencarian dan filter berjalan sesuai kebutuhan.

| No. | Skenario | Hasil yang Diharapkan |
|---|---|---|
| 1 | Mencari berdasarkan judul lengkap | Buku yang sesuai ditampilkan |
| 2 | Mencari sebagian judul | Buku dengan judul yang mengandung kata kunci ditemukan |
| 3 | Mencari berdasarkan nama penulis | Buku dari penulis yang sesuai ditampilkan |
| 4 | Mencari sebagian nama penulis | Buku yang mengandung kata kunci ditemukan |
| 5 | Memilih kategori tertentu | Hanya buku dari kategori tersebut yang ditampilkan |
| 6 | Menggabungkan pencarian dan filter kategori | Hasil sesuai kata kunci dan kategori |
| 7 | Menggunakan kata kunci yang tidak ditemukan | Pesan data tidak ditemukan ditampilkan |
| 8 | Mengirim form pencarian | Kata kunci dan pilihan kategori tetap ditampilkan |

## Kesimpulan

Perbaikan dilakukan pada proses pengiriman parameter pencarian, pengolahan query, penerapan filter kategori, serta pengiriman data dari Controller ke Blade.

Melalui pengujian tersebut, fitur pencarian dan filter kategori diharapkan dapat bekerja dengan baik sehingga user dapat menemukan buku berdasarkan judul, penulis, maupun kategori yang dipilih.