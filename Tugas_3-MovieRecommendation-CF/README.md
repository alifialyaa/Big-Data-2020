# Tugas 03 - Implementasi Algoritma Rekomendasi

Folder ini berisi jawaban tugas 3 kelas Big Data oleh Alifiannisa Alyahasna Wighneswara (05111740000011), yaitu implementasi implementasi algoritma colaborative filtering pada rekomendasi film.

 ![Workflow Movie Recommendation](https://github.com/alifialyaa/BigData_Tugas01_ETLmenggunakanKNIME/blob/master/Gambar/0_Workflow%20benar.png)

## Business Understanding
**MovieLens 20M Ratings dataset** adalah sebuah dataset yang berisi kumpulan penilaian user terhadap film. Dataset ini dibuat oleh GroupLens, sebuah lab riset milik Department of Computer Science and Engineering, University of Minnesota.

Ada beberapa hal yang bisa digali dari dataset ini, di antaranya:

 1. Film apa yang bisa direkomendasikan kepada seorang user?
 2. Apa saja film-film yang memiliki rating terbaik?

## Data Understanding

Dataset ini terdiri dari 6 file, yaitu genome-scores.csv, genome-tags.csv, links.csv, movies.csv, ratings.csv, dan tags.csv. Namun untuk tugas kali ini, hanya digunakan 2 file csv, yaitu:

 1. **movies.csv** : berisi kolom id film (movieId), judul film (title), dan genre (genres). Ada 131.262 film yang tercatat pada dataset ini.
 2. **ratings.csv** : berisi kolom id user (userId), id film (movieId), rating (rating), dan timestamp (timestamp). Ada 1.048.576 rating yang tercatat dari 7.120 user.

## Data Preparation
Sebelumnya, buat local big data environment terlebih dahulu menggunakan node **Create Local Big Data Environment**.

### movies.csv
Pada data preparation, file CSV harus dibuka terlebih dahulu menggunakan node **File Reader**. Adapun pengaturannya adalah sebagai berikut.

![Pengaturan File Reader](https://github.com/alifialyaa/BigData_Tugas01_ETLmenggunakanKNIME/blob/master/Gambar/3_Konfigurasi%20CSV%20Reader.png)

![Hasil File Reader](https://github.com/alifialyaa/BigData_Tugas01_ETLmenggunakanKNIME/blob/master/Gambar/3_Screenshot%20CSV%20Reader.png)
Setelah itu, tambahkan timestamp dan user ID menggunakan **add fields**. Di dalamnya terdapat beberapa node, yaitu **Component Input, Shuffle, Constant Value Column (untuk memasukkan timestamp), Constant Value Column (untuk memasukkan userID), dan Component Output**.

![Rangkaian add fields](https://github.com/alifialyaa/BigData_Tugas01_ETLmenggunakanKNIME/blob/master/Gambar/3_Screenshot%20CSV%20Reader.png)
Selanjutnya, data dibagi menjadi 2. Bagian pertama merupakan data yang diambil 20 baris teratas menggunakan node **Row Splitter**, dan bagian kedua adalah sisanya. 

![Top Partition](https://github.com/alifialyaa/BigData_Tugas01_ETLmenggunakanKNIME/blob/master/Gambar/3_Top%20partitions.png)

![Bottom partition](https://github.com/alifialyaa/BigData_Tugas01_ETLmenggunakanKNIME/blob/master/Gambar/3_Bottom%20partitions.png)
Top partition akan masuk ke field **Ask User for Movie Ratings**, dan bottom partition akan masuk ke dalam field **no rating**.

Node Ask User for Movie Ratings berisi beberapa komponen, yaitu **Component Input, Constant Value Column, Table Editor, Column Filter, Column Resorter, Row Filter, Text Output, dan Component Output.**


Node no ratings berisi beberapa komponen, yaitu **Component Input, Constant Value Column, Column Filter, Column Resorter, dan Component Output.**


Setelah itu, kmasing-masing tabel dimasukkan ke dalam Spark menggunakan node **Table to Spark**.

### ratings.csv
File CSV ratings.csv dimasukkan ke Spark menggunakan node **CSV to Spark**.

Selanjutnya, bagi data menjadi 2 dengan perbandingan 80%-20% untuk dijadikan data training dan data testing menggunakan **Spark Partitioning**.


## Modeling

Proses pembuatan model/training set dibuat dengan menggabungkan tabel dari node Ask User for Move Ratings dengan data training (80%) menggunakan node **Spark Concatenate**.

Setelah itu, model dibuat menggunakan node **Spark Collaborative Filtering Learner.**



## Evaluation
Model dievaluasi menggunakan node **Spark Predictor**, dengan membandingkan model dengan data testing.

Setelah menghilangkan nilai NaN dengan **Spark Missing Value**, error akan dihitung menggunakan node **Spark Numeric Scorer**.


## Deployment
Deployment merupakan proses pembuatan rekomendasi untuk user tertentu. Dibuat dengan node Spark Predictor, node ini digunakan untuk membuat rating user pada film yang didak dinilai.

Setelah itu, hasil prediksi dibawa ke KNIME menggunakan node Spark to Table untuk diolah lebih lanjut.

Data tersebut dibawa ke node Top 20 Recommended movies yang berisi beberapa node, yaitu **Row Filter (untuk menghilangkan nilai NaN), Sorter (untuk mengurutkan hasil prediksi), Row Filter (untuk mengambil 10 film teratas), File Reader (untuk mengambil id, judul, dan genre film), dan Joiner (untuk menggabungkan kolom dari Row Filter dengan File Reader).**

Setelah itu, hasil rekomendasi ditampilkan menggunakan Display Recommendations berupa tampilan web. Hasil prediksi juga bisa disimpan ke dalam bentuk file sesuai kebutuhan, misal CSV.
