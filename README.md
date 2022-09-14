# Laporan Proyek Machine Learning - Muhammad Dhafi Alfaridzi

### Domain Proyek

Domain yang saya pilih adalah tentang keuangan, dan judulnya adalah moneyCompany_predictive Analysis

#### Latar Belakang

Perusahaan merupakan suatu lembaga yang melakukan transaksi jual beli didalamnya. Setiap perusahaan dapat didirikan baik secara perorangan maupun kelompok. Adapun tujuan dibentuk perusahaan ini pastinya untuk mendapatkan Pendapatan. Pendapatan ini merupakan hasil yang didapatkan perusahaan. Pendapatan ini juga terkait dengan laba, sebab laba merupakan selisih dari pendapatan dikurangi dengan beban.

Untuk Mendapatkan pendapatan secara maksimal tersebut, pasti perusahaan akan mematok harga terbaik terkait produk yang mereka tawarkan. Tentu bukan hal yang mudah untuk melakukan hal tersebut. Perusahaan harus melakukan riset terlebih dahulu bagaimana produk tersebut dapat diterima oleh konsumen. 

Untuk itulah saya tertarik mengambil topik ini dalam submission saya. Dengan menggunakan algoritma _Time Series_ pada machine learning, diharapkan harga produk yang ditawarkan dapat sesuai dengan masa sekarang dan berguna di masa depan.

### Business Understanding

#### Problem Statement

berdasarkan hal tersebut, adapun permasalahan yang diangkat adalah:

* Bagaimana menganalisa harga produk yang terbaik?
  
  
* Bagaimana memprediksi harga terbaik untuk masa depan?

#### Goals

Adapun tujuan dari dibentuk nya Proyek ini, adalah:

* mengetahui harga terbaik terkait produk
* mampu memprediksi harga di masa depan

### Data Understanding

Dataset yang digunakan pada proyek ini diambil dari website kaggle dengan judul $$ _Big Company Money_ $$ 

[https://www.kaggle.com/datasets/programmerrdai/-big-company-money]

Dataset ini memiliki total 6276 data dengan 6 kolom, dan memiliki 4 _missing value_. Adapun penjelasan dari masin-masing kolom tersebut

* Rank : ranking perusahaan secara global
* Name : nama perusahaan tersebut
* symbol : simbol perusahaan tersebut
* earnings_ttm: pendapatan perusahaan tersebut selama 12 bulan
* price : harga yang ditetapkan peruhaan terkait produk nya
* Country : negara tempat perushaan tersebut

### Data Preparation

Adapun tahap - tahap yang saya gunakan pada Data Preparation ini, adalah: 

#### melakukan split pada dataset

hal pertama adalah membagi dataset menjadi train data dan test data. dengan menggunakan library train_test_split, saya membagi variabel X dan variabel Y. X adalah data bertipe numerik tanpa tanpa adanya 'price' (hanya 'Rank' dan 'earnings'). Dan variabel Y adalah data bertipe numerik yang isinya 'price'. lalu saya bagi dengan ration 80:20. lalu didapatkan x_train yaitu 3905, x_test = 977, dan untuk total data nya adalah 4882

#### Standarisasi 

Standarisasi ini adalah teknik machine learning yang digunakan agar model dapat dengan mudah dilatih. disini saya menggunakan StandardScaler agar nilai nya berada diantara -1 dan 1

### Modeling

model yang akan digunakan adalah KNN, RandomForest, dan Boosting

#### K-Nearest Neighboor (KNN)

Algoritma KNN menggunakan ‘kesamaan fitur’ untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan.

* n_neighbors = membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah  tetangga terdekat 

#### Random Forest

Random Forest ini adalah kombinasi dari masing-masing tree (pohon) kemudian disatukan dalam satu model. Random Forest ini adalah salah satu metode dalam Decission Tree

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

Dari hasil tersebut, didapatkan informasi bahwa model dengan algoritma KNN memiliki tingkat prediksi yang terbaik

#### Kesimpulan

Dari hasil model yang telah saya buat, tentu saja hasilnya belum memuaskan. saya harus melakukan improvisasi lagi terkait model tersebut. melakukan data cleaning mungkin pilihan terbaik agar model dapat berjalan secara maksimal.


