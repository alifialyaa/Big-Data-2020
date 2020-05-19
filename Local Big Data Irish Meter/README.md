# Local Big Data Irish Meter

Folder ini berisi laporan mengenai *workflow* [Local Big Data Irish Meter](https://hub.knime.com/knime/spaces/Education/latest/Courses/L4-BD%20Introduction%20to%20Big%20Data%20with%20KNIME%20Analytics%20Platform/3_Spark/4_Examples/09_Big_Data_Irish_Meter_on_Spark_only) sebagai tugas mata kuliah Big Data. Laporan ini dibuat oleh Alifiannisa Alyahasna Wighneswara (05111740000011)


## Business Understanding

Workflow ini menggunakan sebagian dari dataset Irish Energy Meter. Dataset dibuat berdasarkan hasil dari uji coba The Smart Metering Electricity Customer Behaviour Trials (CBTs) pada tahun 2009-2010 oleh [Commission for Energy Regulation (CER)](http://www.cer.ie/), Irlandia.

Ada beberapa hal yang bisa digali dari dataset ini, di antaranya:

 1. Bagaimana penggunaan listrik di Irlandia?
 2. Bagaimana pengukuran cerdas dapat membantu membentuk perilaku penggunaan energi di seluruh berbagai demografi, gaya hidup, dan ukuran rumah?
 3. Seperti apa analisis pada runtutan waktu penggunaan listrik di Irlandia?

## Data Understanding

<img src="https://github.com/alifialyaa/Big-Data-2020/blob/master/Local%20Big%20Data%20Irish%20Meter/screenshot/1_File%20Reader.png" width="500"/>

Data berasal dari hampir 6.000 rumah dan bisnis yang berpartisipasi dalam uji coba - satu *smart meter* per entitas. *Smart meter* menghasilkan informasi setiap setengah jam, 24 jam sehari, dan ada satu tahun data tersedia. Selain itu, survei pra-percobaan dan pasca-uji coba dilakukan untuk rumah tangga dan bisnis.

Dataset yang digunakan memiliki 1.226.830 *record* dan 3 *field*. Berikut adalah penjelasan dari masing-masing *field*:

 1. **meterID**	: nomor ID dari masing-masing *smart meter* yang berpartisipasi dalam uji coba.
 2. **enc_datetime**	: penanda waktu yang sudah dikodekan. Berdasarkan artikel [ini](https://files.knime.com/sites/default/files/inline-images/knime_bigdata_energy_timeseries_whitepaper.pdf), tiga digit pertama kolom "datetime" menghitung jumlah hari mulai dari 1 hingga 1 Januari 2009. 2 digit terakhir dari "datetime" menghitung angka cap waktu yang diperbarui setiap tiga puluh menit: yaitu 01 = 00:30 dan 11 = 05:30.
 3. **reading** : besar listrik yang dihitung oleh *smart meter*.
