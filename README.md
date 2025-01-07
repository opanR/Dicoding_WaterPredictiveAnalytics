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
Dataset yang digunakan berasal dari [kaggle](https://www.kaggle.com/datasets/adityakadiwal/water-potability). Dataset ini berisi informasi tentang pH air,Hardness,Tingkat Kekentalan air,Kandungan Kloramin,Sulfate,Conductivity, Organic_carbon,Trihalometana,Kekeruhan dan kelayakan

Dataset memiliki jumlah 3276 baris dan 10 kolom.

|#| Column | Dtype |
| ------ | ------ |------ |
| 1 | ph                |float64|
| 2 | Hardness         |float64|
| 3 | Solids            |float64|
| 4 | Chloramines |float64|
| 5 | Sulfate           |float64|
| 6 | Conductivity      |float64|
| 7 | Organic_carbon |float64|
| 8 | Trihalomethanes   |float64|
| 9 | Turbidity         |float64|
| 10 | Potability        |float64|
Dataset mempunyai beberapa fitur yang terdapat missing value atau NaN.
Kolom yang memiliki nilai Null beserta tipe datanya:
|Column|  Tipe Data|  Jumlah Null|
| ------ | ------ |------ |
|ph              |  float64          |491|
|Sulfate          | float64          |781|
|Trihalomethanes   |float64          |162|

Dataset mempunyai nilai outliers pada feature.
![Outlier](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/Outlier.png)](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/Outlier.png)

### Variabel-variabel pada dataset adalah sebagai berikut:
> 1. pH:  pH air (0 - 14).
> 2. Kekerasan (Hardness): Kapasitas air untuk mengendapkan sabun dalam mg/L.
> 3. Padatan(Solids): Total padatan terlarut dalma ppm.
> 4. Kloramin: Jumlah Kloramin dalam ppm.
> 5. Sulfat: Jumlah Sulfat yang terlarut dalam mg/L.
> 6. Konduktivitas: Konduktivitas listrik air dalam μS/cm.
> 7. Karbon_organik: Jumlah karbon organik dalam ppm.
> 8. Trihalomethanes: Jumlah Trihalomethanes dalam μg/L.
> 9. Kekeruhan: Ukuran sifat air yang memancarkan cahaya
> 10. Potabilitas: Menunjukkan apakah air aman untuk dikonsumsi manusia. Dapat diminum atau  Tidak dapat diminum 
### Lakukan EDA (Exploratory Data Analysis)
### EDA - Univariate Analysis
![EDA- Univariate Analysis](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/EDA%20-%20Univariate%20Analysis.png)](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/EDA%20-%20Univariate%20Analysis.png)

### EDA - Multivariate Analysis
![EDA - Multivariate Analysis](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/Lakukan%20EDA%20-%20Multivariate%20Analysis.png)](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/Lakukan%20EDA%20-%20Multivariate%20Analysis.png)

### EDA - Matriks Korelasi Antar Kolom
![EDA - Matriks Korelasi Antar Kolom](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/Matriks%20Korelasi%20Antar%20Kolom.png)](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/Matriks%20Korelasi%20Antar%20Kolom.png)

## Data Preparation
### Teknik Data Preparation
- Menghapus outliers yang ada pada dataset
- Handling Missing Values: Mengimputasi nilai yang hilang pada dataset.
- Pembagian dataset untuk train-test (80:20)

### Proses Data Preparation
- Outlier diatasi menggunakan IQR method.

## Modeling
Pada proyek ini,menggunakan LazyClassifier untuk membandingkan kinerja berbagai model klasifikasi secara cepat.
```sh
from lazypredict.Supervised import LazyClassifier
clf = LazyClassifier()
models,predicts = clf.fit(x_train,x_test,y_train,y_test)
print(models.sort_values(by="Accuracy",ascending=False))
```
Lakukan visualisasi akurasi,sehingga diperoleh perbandingan beberapa model
```sh
temp = models.sort_values(by="Accuracy",ascending=True)
plt.figure(figsize=(10, 8))
plt.barh(temp.index,temp["Accuracy"])
plt.show()
```
![EDA - Matriks Korelasi Antar Kolom](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/Accuration_Model.png)

Lakukan Sampling dengan 4 model 
- K-Nearest Neighbors (KNN)
- Random Forest
- SVM
- Naive Bayes

### Hyperparameter Tunning
Untuk meningkatkan akurasi.Lakukan hyperparamtere tunning untuk ke-4 model diatas 
#### Hyperparameter Tunning untuk KNN
```sh
from sklearn.model_selection import GridSearchCV

# Define the parameter grid to search
param_grid = {
    'n_neighbors': [3, 5, 7, 9, 11],  # Explore different values for k
    'weights': ['uniform', 'distance'],  # Explore different weight functions
    'metric': ['euclidean', 'manhattan']  # Explore different distance metrics
}

# Create a KNeighborsClassifier object
knn = KNeighborsClassifier()

# Create a GridSearchCV object
grid_search = GridSearchCV(estimator=knn, param_grid=param_grid, cv=5, scoring='accuracy')

# Fit the GridSearchCV object to the training data
grid_search.fit(x_train, y_train)

# Print the best hyperparameters found
print("Best hyperparameters:", grid_search.best_params_)

# Get the best model
best_knn = grid_search.best_estimator_

# Evaluate the best model on the test data
knn_pred = best_knn.predict(x_test)
models.loc['accuracy_score', 'KNN'] = accuracy_score(y_test, knn_pred)

print(f"Accuracy of the best KNN model: {accuracy_score(y_test, knn_pred)}")
```
Lakukan proses training dengan parameter yang didapat dari hasil tunning
```sh
model_knn = KNeighborsClassifier(n_neighbors=11, weights='uniform', metric= 'manhattan')
model_knn.fit(x_train, y_train)
```    
Lakukan Prediksi
```sh
knn_pred = model_knn.predict(x_test)
models.loc['accuracy_score','KNN'] = accuracy_score(y_test, knn_pred)
```   
#### Lakukan Training untuk model Random Forest dengan max-depth=20
```sh
model_rf = RandomForestClassifier(max_depth= 20)
model_rf.fit(x_train, y_train)
```   
Lakukan Prediksi
```sh
rf_pred = model_rf.predict(x_test)
models.loc['accuracy_score','RandomForest'] = accuracy_score(y_test, rf_pred)
```  
#### Lakukan Training untuk model SVC
```sh
model_svc = SVC()
model_svc.fit(x_train, y_train)
```   
Lakukan Prediksi
```sh
svc_pred = model_svc.predict(x_test)
models.loc['accuracy_score','SVM'] = accuracy_score(y_test, svc_pred)
```  
#### Lakukan Training untuk model Naive Bayes
```sh
model_nb = BernoulliNB()
model_nb.fit(x_train, y_train)
```   
Lakukan Prediksi
```sh
nb_pred = model_nb.predict(x_test)
models.loc['accuracy_score','Naive Bayes'] = accuracy_score(y_test, nb_pred)
```  
#### Tampilkan hasil dari ke-4 model
```sh
plt.bar('KNN', models['KNN'])
plt.bar('RandomForest', models['RandomForest'])
plt.bar('SVM', models['SVM'])
plt.bar('Naive Bayes', models['Naive Bayes'])
plt.title("Perbandingan Akurasi Model");
plt.xlabel('Model');
plt.ylabel('Akurasi');
plt.show()
```  
![Hasil 4 Model](https://github.com/opanR/Dicoding_WaterPredictiveAnalytics/blob/main/hasil%204%20model.png)

# Kesimpulan
Melalui proses pemodelan , telah berhasil membangun model yang akurat untuk memprediksi kelayakan air minum untuk dikonsumsi. Model SVC terbukti menjadi model terbaik dalam hal akurasi prediksi. Dampak dari solusi yang diimplementasikan sangat positif, memenuhi problem statement dan goals yang telah ditetapkan.
