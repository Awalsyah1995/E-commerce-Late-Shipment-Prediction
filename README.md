# Final Project: Ecommerce Latement Shipping Data

Kelompok 3 Asklepios <br>
Rakamin Academy Data Science Bootcamp Batch 26: <br>
1. Awalsyah Rinanto Putra.
2. Devi Ayu Pujiningsih
3. Hermawan Febrianto.
4. Fathah Oscar.
5. M. Rizky Septiansyah
6. Anggita Citra Lubis

Datataset dapat diakses pada [Ecommerce Latement Shipping Data](https://www.kaggle.com/datasets/prachi13/customer-analytics)

## 1. Problem Statement
Suatu perusahaan ecommerce mempunyai dataset yang terdiri atas 10999 delivery dengan berbagai fitur dan target berupa *late shipment* atau keterlambatan pengiriman. Pada dataset ini, jumlah pengiriman terlambat (59,7%) lebih banyak daripada pengiriman on-time (40,3%). Keterlambatan pengiriman ini akan mempengaruhi kepuasan customer yang juga berpengaruh pada customer rating dan *potential revenue loss*.

![Late Shipment](https://user-images.githubusercontent.com/116500936/205496824-d3955a83-9dc1-4c2e-a219-9c1b010e7690.png)

## 2. Objective, Business Metrics dan Goal
Objective:
1. Meningkatkan on-time rating.
2. Meningkatkan customer rating.
3. Mengurangi *potential revenue loss*.

Business Metrics:
1. On-time rating.
2. Customer rating.
3. Potential revenue loss.

Goal: <br>
Memprediksi apakah pengiriman produk akan terlambat/ontime dengan algoritma pemodelan dan memberikan rekomendasi metode pengiriman.

## 3. Exploratory Data Analysis (EDA)
### Descriptive Analysis
![eda](https://user-images.githubusercontent.com/116500936/205497278-398479e6-aecb-4492-8099-2f8fb1a33320.png)
Dataset terdiri atas 10 feature dan 1 target, yaitu Late (keterlambatan pengiriman)

### Univariate Analysis

![eda numerik](https://user-images.githubusercontent.com/116500936/205497329-4cdb1872-d95d-4137-81df-4198a09f8b8a.png)
Dengan menggunakan boxplot, ditemukan adanya outlier pada feature discount dan purchases. Setelah dilihat menggunakan distribution plot, feature discount dan purchases juga menunjukan adanya kemencengan positif/*positively skewed* dengan nilai skewness masing-masing yaitu 1.79 dan 1.68.

![eda rating](https://user-images.githubusercontent.com/116500936/205497340-056da9ab-588e-460c-a67f-a2456fc12319.png)

Sementara pada category-plot terdapat insight menarik pada feature rating, dengan asumsi customer yang puas memberi rating 4 dan 5, terlihat lebih banyak customer yang memberi rating tidak puas (1, 2 dan 3) dibanding rating puas (rating 4 dan 5).


### Multivariate Analysis
![eda heatmap](https://user-images.githubusercontent.com/116500936/205497372-9e16745f-540a-4b58-bcad-7637b18aa122.png)
Dari heatmap plot, terlihat feature discount dan weight punya korelasi paling tinggi dengan target Late dengan nilai masing-masing 0,4 dan -0,27.


## 4. Data Pre-Processing
Kami melakukan beberapa tahap data pre-processing terhadap dataset agar data siap dilakukan pemodelan, keseluruhan tahapan data pre-processing dapat dilihat pada tabel berikut ini.
![data preprocessing](https://user-images.githubusercontent.com/116500936/205497389-e8695308-82f6-48b4-8a68-0c879803f67b.png)

Tidak dilakukan feature engineering pada tahap data pre-processing.

## 5. Pemodelan
Setelah menggunakan beberapa algoritma pemodelan machine learning, kami menyimpulkan dengan menggunakan algoritma adaboost kami medapatkan hasil terbaik dengan skor ROC-AUC pada data training 0.76 dan data test 0.74. Skor ROC-AUC Adaboost ini merupakan skor roc-auc yang paling tinggi dibanding skor ROC-AUC pada algoritma lain dan gap antara skor data train dan test tidak terlalu jauh (tidak overfitting dan underfitting).

![modelling](https://user-images.githubusercontent.com/116500936/205497405-cded5eef-9e9f-4073-89da-a44f1f618a50.png)

Kami menggunakan skor evaluasi ROC-AUC karena sifatnya robust terhadap dataset yang sedikit imbalance pada target (59,7% late dan 40,3% ontime) dan mengkonsiderasi value *false positive* dan *false negative* pada perhitungannya.

## 6. *Insight* Bisnis dan Rekomendasi
![business insight](https://user-images.githubusercontent.com/116500936/205497426-7644ea31-8406-4075-9095-b91c175f7f87.png)
![custcall](https://user-images.githubusercontent.com/116500936/205497430-e3a73126-9c0f-4cb9-b815-e3d1bcb401d8.png)

Business Insight:
1. Pengiriman produk dengan diskon produk di atas 10% hampir pasti akan mengalami keterlambatan.
2. Pengiriman produk dengan berat yang rendah, terutama di antara 2-4 kg, berpotensi besar mengalami keterlambatan pengiriman.
3. Jumlah customer call yang diterima justru lebih sedikit seiring dengan banyaknya banyaknya late delivery, perusahaan perlu mengetahui informasi isi pembicaraan telepon yang diterima customer care untuk mendapatkan gambaran korelasi customer care call dan late delivery

Business Recommendation:
1. Pembuatan notifikasi untuk produk yang berpotensi mengalami keterlambatan, terutama produk ringan dengan berat di bawah 4 kg dan/atau yang diberi diskon di atas 10%. Notifikasi ini bertujuan untuk memberi estimasi konsumen agar tingkat kepuasan konsumen terjaga, bahkan meningkat.
2. Pemberian rekomendasi pengiriman beserta waktu pengirimannya untuk meminimalisir keterlambatan. Misal pengiriman dengan pesawat (3 hari) punya waktu pengiriman yang lebih cepat daripada menggunakan kapal (5 hari).
![notif](https://user-images.githubusercontent.com/116500936/205497444-f75831be-2c99-4e8c-836d-5939a00c0f9f.png)

## 7. Simulasi Model terhadap Dataset
Simulasi model terhadap dataset ini bertujuan untuk mengetahui seberapa besar pengaruh model terhadap 3 business metric, yaitu on-time delivery rate, customer rating dan potential revenue loss.
![comparation](https://user-images.githubusercontent.com/116500936/205497466-71f7b702-98c6-41c7-a969-324d635f0d7f.png)

Secara umum, terjadi kenaikan on-time delivery rate dari 40,3% menjadi 84,48%, kenaikan rata-rata customer rating dari 2,99 menjadi 3,14 dan potential revenue loss yang bisa ditekan hingga 74%.
Proses perhitungan dapat dilihat pada source code dan file ppt.
