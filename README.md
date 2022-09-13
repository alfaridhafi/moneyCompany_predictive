# Laporan Proyek Machine Learning - Muhammad Dhafi Alfaridzi

### Domain Proyek

Domain yang saya pilih adalah tentang keuangan, dan judulnya adalah moneyCompany_predictive Analysis

#### Latar Belakang

Perusahaan merupakan suatu lembaga yang melakukan transaksi jual beli didalamnya. Setiap perusahaan dapat didirikan baik secara perorangan maupun kelompok. Adapun tujuan dibentuk perusahaan ini pastinya untuk mendapatkan Pendapatan. Pendapatan ini merupakan hasil yang didapatkan perusahaan baik besar atau kecilnya dari Laba.sebab Laba merupakan Selisih dari pendapatan dikurangi dengan beban.

Pendapatan ini pasti lah masalah yang sangat penting karena pendapatan ini adalah salah satu tolak ukur yang digunakan perusahaan dalam kemakmuran perushaan tersebut. Pendapatan ini umumnya timbul dari kegiatan utama perushaan maupun dari sumber pendapatan lainnya.

Untuk itulah saya tertarik mengambil topik ini dalam submission saya, dengan menggunakan model machine learning, diharapkan nantinya prediksi saya mampu menilai keadaan di masa depan dengan data yang ada sekarang.

### Business Understanding

#### Problem Statement

berdasarkan hal tersebut, adapun permasalahan yang diangkat adalah:

* Bagaimana menganalisa Pendapatan Perusahaan?
* Berapa pendapatan Perusahaan?

#### Goals

Adapun tujuan dari dibentuk nya Proyek ini, adalah:

* mengetahui prediksi pendapatan Perusahaan
* melakukan analisa dan pengolahan yang baik dengan machine learnings

#### Solution Statement

Adapun solusi yang diberikan yaitu:

* menangani missing value
* menangangi Outlinier 
* melakukan normalisasi

### Data Understanding

Dataset yang digunakan pada proyek ini diambil dari website kaggle dengan judul $$ Big Company Money $$ 

[https://www.kaggle.com/datasets/programmerrdai/-big-company-money]

Dataset ini memiliki total 6276 data dengan 6 kolom, dan memiliki 4 missing value. Adapun penjelasan dari masin-masing kolom tersebut

* Rank : ranking perusahaan secara global
* Name : nama perusahaan tersebut
* symbol : simbol perusahaan tersebut
* earnings: pendapatan perusahaan tersebut selama 12 bulan
* price : harga perusahaan
* Country : negara perushaan tersebut

### Data Preparation

Adapun tahap - tahap yang saya gunakan pada Data Preparation ini, adalah: 

#### melakukan split pada train dan test

hal pertama adalah membagi train dan test. dengan menggunakan library train_test_split, saya membagi variabel X dan variabel Y. X adalah data bertipe numerik tanpa tanpa adanya 'price' (hanya 'Rank' dan 'earnings'). Dan variabel Y adalah data bertipe numerik yang isinya 'price'. lalu saya bagi dengan ration 80:20. lalu didapatkan x_train yaitu 3905, x_test = 977, dan untuk total nya adalah 4882

#### Standarisasi 

Standarisasi ini adalah teknik machine learning yang digunakan agar model dapat dengan mudah dilatih. disini saya menggunakan StandardScaler agar nilai nya berada diantara -1 dan 1

### Modeling

model yang akan digunakan adalah KNN, RandomForest, dan Boosting

#### K-Nearest Neighboor

Algoritma KNN menggunakan ‘kesamaan fitur’ untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan.

* n_neighbors = membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah  tetangga terdekat 

#### Random Forest

Random Forest ini adalah kombinasi dari masing-masing tree kemudian disatukan dalam satu model. Random Forest ini adalah salah satu metode dalam Decission Tree

* n_estimator: jumlah trees di forest
* max_depth: kedalaman atau panjang pohon
* random_state: digunakan untuk mengontrol random number generator yang digunakan
* n_jobs: jumlah job (pekerjaan) yang digunakan secara paralel. Ia merupakan komponen untuk mengontrol thread atau proses yang berjalan secara paralel

#### Boosting

Boosting ini bertujuan untuk meningkatkan performa atau akurasi prediksi. Algoritma yang menggunakan teknik boosting bekerja dengan membangun model dari data latih, kemudian ia membuat model kedua yang bertugas memperbaiki kesalahan dari model pertama. 

### Evaluation

untuk evaluasi ini saya menggunakan metrik MSE (Mean Squad Error) yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi


adapun grafik yang saya dapatkan setelah menggunakan metrik ini, yaitu:


<img width="340" alt="paint11" src="https://user-images.githubusercontent.com/93527916/189922308-d65ce867-c07b-45b3-a6fc-f9b7bc04a6e0.png">


dan prediksi yang saya dapatkan adalah:


<img width="371" alt="pain22" src="https://user-images.githubusercontent.com/93527916/189922533-155f10de-61b0-4a61-9d5c-c1b1984cb931.png">

Dari hasil evaluasi tersebut, didapatkan informasi bahwa model dengan KNN memiliki performa yang paling besar


