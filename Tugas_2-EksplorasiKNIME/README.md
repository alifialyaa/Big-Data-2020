# Tugas 02 - Explorasi KNIME Big Data



## Data
Bagian ini terdiri dari empat soal, yaitu DB Connect, lalala, yeyeye, dan huhuhu.

### 01. DB Connect
Sebelum melakukan koneksi ke SQLite, saya sudah mengubah nama-nama tabel yang ada dengan menggunakan SQLite CLI. 

***isi sc tables di cli***

Gunakan node SQLite Connector untuk menghubungkan KNIME dengan SQLite. Masukkan path file .sqlite ke dalam konfigurasi, lalu jalankan.

![Konfigurasi SQLite Connector](/Gambar/1_Data/1_DBConnect/1_1_DB Table Selector configuration.png)

***isi sc config***

Gunakan node table selector untuk memilih tabel yang ingin dibuka. Sambungkan dengan node sebelumnya dan pilih tabel yang akan dibuka. Dalam eksplorasi ini, tabel yang akan dibuka adalah tabel nrp05111740000011_ss13pme.

***isi sc node***
***isi sc config***

Gunakan node DB Reader untuk membuka tabel yang dipilih. Sambungkan dengan node DB Table Selector.

***isi sc node***
***isi sc config***
