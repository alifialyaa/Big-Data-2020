# Tugas 02 - Explorasi KNIME Big Data



## Data
Bagian ini terdiri dari empat soal, yaitu DB Connect, lalala, yeyeye, dan huhuhu.

### 01. DB Connect
Sebelum melakukan koneksi ke SQLite, saya sudah mengubah nama-nama tabel yang ada dengan menggunakan SQLite CLI. 

***isi sc tables di cli***

Gunakan node SQLite Connector untuk menghubungkan KNIME dengan SQLite. Masukkan path file .sqlite ke dalam konfigurasi, lalu jalankan.


<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_SQLite%20Connector%20configuration.png" alt="drawing" width="500"/>

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_Connector.png" alt="drawing" width="150"/>


Gunakan node table selector untuk memilih tabel yang ingin dibuka. Sambungkan dengan node sebelumnya dan pilih tabel yang akan dibuka. Dalam eksplorasi ini, tabel yang akan dibuka adalah tabel nrp05111740000011_ss13pme.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_DB%20Table%20Selector%20configuration.png" alt="drawing" width="500"/>

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_connector%20dan%20table%20selector.png" width="250"/>

Gunakan node DB Reader untuk membuka tabel yang dipilih. Sambungkan dengan node DB Table Selector.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_full.png" alt="drawing" width="350"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_Data%20table.png" width="500"/>
