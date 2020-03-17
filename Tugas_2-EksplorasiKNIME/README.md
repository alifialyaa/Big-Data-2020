# Tugas 02 - Explorasi KNIME Big Data



## Data
Bagian ini terdiri dari empat soal, yaitu DB Connect, InDB Processing, yeyeye, dan huhuhu.

### 01. DB Connect
Sebelum melakukan koneksi ke SQLite, saya sudah mengubah nama-nama tabel yang ada dengan menggunakan SQLite CLI. 

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_daftar%20tabel.png" alt="drawing" width="500"/>

Gunakan node SQLite Connector untuk menghubungkan KNIME dengan SQLite. Masukkan path file .sqlite ke dalam konfigurasi, lalu jalankan.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_SQLite%20Connector%20configuration.png" alt="drawing" width="500"/>

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_Connector.png" alt="drawing" width="150"/>


Gunakan node table selector untuk memilih tabel yang ingin dibuka. Sambungkan dengan node sebelumnya dan pilih tabel yang akan dibuka. Dalam eksplorasi ini, tabel yang akan dibuka adalah tabel nrp05111740000011_ss13pme.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_DB%20Table%20Selector%20configuration.png"  width="500"/>

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_connector%20dan%20table%20selector.png" width="250"/>

Gunakan node DB Reader untuk membuka tabel yang dipilih. Sambungkan dengan node DB Table Selector dan DB sudah bisa dibaca.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_full.png" alt="drawing" width="350"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_Data%20table.png" width="900"/>

### 02. InDB processing
 **1. Gabungkan ss13hme dan ss13pme menggunakan variabel serialno, dan hapus kolom dengan nama PUMA dan PWGTP dari masing-masing tabel.**

Gunakan node **SQLite Connector** untuk menghubungkan KNIME dengan SQLite. Masukkan path file .sqlite ke dalam konfigurasi, lalu jalankan.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_SQLite%20Connector%20configuration.png" width="500"/>

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_Connector.png" width="150"/>

Selanjutnya, pilih tabel-tabel yang akan digunakan menggunakan node **DB Table Selector**. Ada dua tabel yang akan digunakan, yaitu nrp05111740000011_ss13hme dan nrp05111740000011_ss13pme.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_konfigurasi%20ss13hme.png" width="500"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_config%20ss13pme.png" width="500"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_connector%20dan%20table%20selector.png" width="300"/>

Gabungkan dua tabel menggunakan node DB Joiner dengan mode inner join berdasarkan variabel serialno. Lalu, sambungkan dengan node **DB Reader** untuk membuka hasil join.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_konfigurasi%20joiner%20inner%20join%20dengan%20serialno.png" width="500"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_filter%20puma%20dan%20pwgtp.png" width="500"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_A%20full.png" width="350"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_hasil%20A.png" width="500"/>


 **2. Saring semua baris dengan nilai cow `NULL`.**
 
 **3. Saring semua baris dengan nilai cow `NOT NULL`.**

Untuk melakukan filter pada baris, dapat digunakan node DB Row Filter. Pada latihan ini, gunakan dua row filter. Satu row filter akan digunakan untuk mencari baris dengan nilai cow `NULL` dan satunya lagi digunakan untuk mencari nilai cow `NOT NULL`. Gabungkan masing-masing node row filter dengan DB reader jika ingin melihat hasil filter.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_cow%20is%20not%20null.png" width="500"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_cow%20is%20null.png" width="500"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_ABC%20full.png" width="350"/>

 **4. Hitung rata-rata nilai agep dari nilai sex yang berbeda.**

Gunakan node **DB GroupBy** untuk mengelompokkan data berdasarkan variabel sex. Node ini juga bisa digunakan untuk melakukan penghitungan rata-rata pada pengaturan Manual Aggregation.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_group%20by%20sex.png" width="500"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_calculate%20average.png" width="500"/>

Gunakan node DB Reader untuk melihat hasilnya.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_full.png" width="500"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_hasil%20avg.png" width="400"/>

 **5. (Opsional) Urutkan baris berdasarkan nilai agep secara descending dan ambil 10 nilai teratas.**

Untuk mengurutkan nilai agep, gunakan node DB Sorter, lalu atur sehingga node dapat mengurutkan data berdasarkan nilai agep secara descending.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_config%2010%20nilai%20teratas.png" width="500"/>


Setelah itu, gunakan node DB Query untuk memilih 10 nilai teratas. Syntax yang akan dijalankan adalah `SELECT * FROM #table# AS "table" limit 10`

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_config%20query.png" width="500"/>

Gunakan node DB Reader untuk melihat hasilnya.


<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_hasil%20query.png" width="900"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_full%20poin%20e.png" width="500"/>


### 03. Modelling

**1. Lakukan training Decision Tree pada variabel cow dimana nilai cow `NOT NULL`.**

Gunakan node **SQLite Connector** untuk menghubungkan KNIME dengan SQLite. Masukkan path file .sqlite ke dalam konfigurasi, lalu jalankan.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/1_DBConnect/1_1_SQLite%20Connector%20configuration.png" width="500"/>

Selanjutnya, pilih tabel-tabel yang akan digunakan menggunakan node **DB Table Selector**. Pilih tabel nrp05111740000011_ss13pme.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_config%20ss13pme.png" width="500"/>

Buang kolom PUMA dan PWGTP menggunakan node **DB Column Filter**.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/3_Modelling/1_3_config%20column%20filter%20puma%20pwgtp.png" width="500"/>

Untuk melakukan filter pada baris, dapat digunakan node DB Row Filter. Pada latihan ini, gunakan dua row filter. Satu row filter akan digunakan untuk mencari baris dengan nilai cow `NULL` dan satunya lagi digunakan untuk mencari nilai cow `NOT NULL`. Gabungkan masing-masing node row filter dengan DB reader jika ingin melihat hasil filter.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_cow%20is%20not%20null.png" width="500"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/2_InDBProcessing/1_2_cow%20is%20null.png" width="500"/>

Ubah angka pada hasil filter cow `IS NULL` menjadi string sebelum dilakukan training menggunakan node **Number to String**.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/3_Modelling/1_3_config%20num%20to%20string.png" width="500"/>

Untuk melakukan training, gunakan node **Decision Tree Learner** yang disambungkan dengan node Number to String.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/3_Modelling/1_3_dt%20learner.png" width="500"/>

**2. Gunakan decision tree untuk memprediksi nilai cow yang hilang.**
Sambungkan DB Reader dengan nilai cow NULL dengan node **Decision Tree Predictor**. Node ini membutuhkan dua input, yaitu DB Reader dan hasil training sebelumnya.

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/3_Modelling/1_3_hasil%20prediksi.png" width="900"/>
<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Tugas_2-EksplorasiKNIME/Gambar/1_Data/3_Modelling/1_3_alur.png" width="500"/>


