# Laporan Proyek Machine Learning - Muhammad Dhafi Alfaridzi

### Domain Proyek

Domain yang saya pilih adalah tentang keuangan, dan judulnya adalah moneyCompany_Predictive Analytics

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

#### Univariate Analysis

mari kita lihat terlebih dahulu grafik yang saya dapatkan:

<img width="513" alt="paint 33" src="https://user-images.githubusercontent.com/93527916/190047190-292c84fa-133e-48c1-a5b5-c9f3b7969741.png">

Mari kita berfokus ke variabel 'price' yang merupakan target utama kita. dari hasil tersebut, didapatkan analisa bahwa grafik 'price' akan semakin turun seiring dengan banyak nya jumlah sample.

#### Multivariate Analysis

mari kita lihat terlebih dahulu grafik yang saya dapatkan:

<img width="325" alt="paint 44" src="https://user-images.githubusercontent.com/93527916/190048284-cb2bafb4-e72b-49c3-809b-23a116b63584.png">

sama seperti sebelumnya, kita akan berfokus ke variabel 'price'. Dalam hal tersebut, artinya kita akan berfokus ke baris ke 3 dari atas. dimana sumbu y nya adalah 'price'. lalu kita lihat korelasi fitur 'price' tersebut dengan fitur numerik lainnya. pada pola tersebut, terlihat fitur 'Rank' memiliki korelasi negatif dengan 'price'. Ditandai dengan menurunnya variabel y saat terjadi kenaikan pada variabel x, namun untuk korelasi nya masih lemah karena sebarannya tidak membentuk pola sempurna. Sedangkan fitur 'earnings' memiliki korelasi acak dengan fitur 'price'. hal tersebut karena sebarannya tidak membentuk pola dan naik turun variabel y saat terjadi kenaikan pada variabel x.

#### Correlation Matrix

mari kita lihat terlebih dahulu korelasi yang saya dapatkan:

<img width="381" alt="paint5" src="https://user-images.githubusercontent.com/93527916/190049962-a14e1e9f-4ded-4241-bc02-46d00f5c5c99.png">

disini kita akan berfokus ke korelasi fitur 'price' dengan fitur numerik lainnya. Adapun koefisien korelasi berkisar antara -1 dan +1. dari gambar tersebut, dapat dianalisa bahwa fitur 'earnings' memiliki kolerasi yang lebih kecil. Korelasi 'price' dengan 'earnings' bernilai 0.27, dan nilai tersebut hampir mendekati nilai 0.

### Modeling

model yang akan digunakan adalah KNN, RandomForest, dan Boosting

#### K-Nearest Neighboor (KNN)

Algoritma KNN menggunakan ‘kesamaan fitur’ untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan.
* n_neighbors = membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah  tetangga terdekat. pada laporan ini saya menggunakan n_neighbors = 5

#### Random Forest

Random Forest ini adalah kombinasi dari masing-masing tree (pohon) kemudian disatukan dalam satu model. Random Forest ini adalah salah satu metode dalam Decission Tree

* n_estimator: jumlah trees di forest. pada laporan ini saya menggunakan n_estimator = 20
* max_depth: kedalaman atau panjang pohon. pada laporan ini saya menggunakan max_depth = 10
* random_state: digunakan untuk mengontrol random number generator yang digunakan. pada laporan ini saya menggunakan random_state = 10
* n_jobs: jumlah job (pekerjaan) yang digunakan secara paralel. Ia merupakan komponen untuk mengontrol thread atau proses yang berjalan secara paralel. pada laporan ini saya menggunakan n_jobs = -1

#### Boosting

Boosting ini bertujuan untuk meningkatkan performa atau akurasi prediksi. Algoritma yang menggunakan teknik boosting bekerja dengan membangun model dari data latih, kemudian ia membuat model kedua yang bertugas memperbaiki kesalahan dari model pertama. 

* Learning_rate : bobot yang diterapkan pada setiap regressor di masing-masing proses iterasi boosting. pada laporan ini saya menggunakan Learning_rate = 0.01
* random_state: digunakan untuk mengontrol random number generator yang digunakan. pada laporan ini saya menggunakan random_state = 20

### Evaluation

untuk evaluasi ini saya menggunakan metrik MSE (Mean Squad Error) yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi. MSE didefinisikan dengan persamaan berikut:

<img width="335" alt="paint66" src="https://user-images.githubusercontent.com/93527916/190052691-b022d0d4-e0d7-424d-b8f2-529a1e6683f2.png">

dengan nilai N = jumlah dataset, yi = nilai sebenarnya, dan y_pred = nilai prediksi.


adapun grafik yang saya dapatkan setelah menggunakan metrik ini, yaitu:


<img width="340" alt="paint11" src="https://user-images.githubusercontent.com/93527916/189922308-d65ce867-c07b-45b3-a6fc-f9b7bc04a6e0.png">


dan prediksi yang saya dapatkan adalah:


<img width="371" alt="pain22" src="https://user-images.githubusercontent.com/93527916/189922533-155f10de-61b0-4a61-9d5c-c1b1984cb931.png">

Dari hasil tersebut, didapatkan informasi bahwa model dengan algoritma KNN memiliki tingkat prediksi yang terbaik

#### Kesimpulan

Dari hasil model yang telah saya buat, tentu saja hasilnya belum memuaskan. saya harus melakukan improvisasi lagi terkait model tersebut. melakukan data cleaning mungkin pilihan terbaik agar model dapat berjalan secara maksimal.


