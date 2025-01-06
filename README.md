# Laporan Proyek Machine Learning - Manutur Pandapotan Siregar
## 1.Domain Proyek
### Latar Belakang

Air merupakan kebutuhan yang sangat mendasar bagi manusia. Tubuh manusia membutuhkan konsumsi air putih yang disarankan yaitu sekitar delapan gelas berukuran 230 ml per hari atau total 2 liter.Kebutuhan air bersih atau layak dikonsumsi merupakan suatu keharusan.Pengetahuan akan air yang layak atau tidak dikonsumsi sangat diperlukan agar air yang dikonsumsi memiliki manfaat yang sebenarnya bukan malah menimbulkan penyakit
 ### Mengapa masalah ini perlu diselesaikan ?
- Agar dapat menentukan air yang layak untuk dikonsumsi atau tidak
- Dapat memiliki prediksi air yang layak konsumsi atau tidak dengan parameter yang ada

## 2.Business Understanding
### Problem Statements

- Bagaimana cara memprediksi air yang layak dikonsumsi atau tidak berdasarkan parameter yang ada seperti ph,Hardness,Kepadatan,Chloramines,Kandungan  Sulfat, Organic_carbon, Trihalomethanes dan kekeruhan ?
- Parameter apa saja yang paling berpengaruh untuk menentukan kelayakan air minum ?
- Bagaimana meningkatkan prediksi kelayakan air minum dengan algoritma Machine Learning?
### Goals

- Membangun model machine learning yang dapat memprediksi layak tidaknya air minum dikonsusmsi
- Mengidentifikasi parameter yang paling berpengaruh dalam menentukan kelayakan air minum
- Meningkatkan akurasi model prediksi melalui hyperparameter tuning dan teknik machine learning yang tepat.
### Solution statements
- Menggunakan beberapa algoritma machine learning seperti SVC, Random Forest,KNN Untuk memprediksi kelayakan air
- Membandingkan performa model dan memilih model terbaik 
## 3.Data Understanding
Dataset yang digunakan berasal dari [kaggle](https://www.kaggle.com/datasets/adityakadiwal/water-potability). Dataset ini berisi informasi tentang pH air,Hardness,Tingkat Kekentalan air,Kandungan Kloramin,Sulfate,Conductivity, Organic_carbon,Trihalometana,Kekeruhan
