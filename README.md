# Customer Segmentation Clustering

## Project Overview

Project ini merupakan analisis clustering untuk melakukan segmentasi pelanggan berdasarkan data transaksi online retail. Tujuan dari project ini adalah mengelompokkan pelanggan ke dalam beberapa segmen berdasarkan perilaku transaksi mereka, sehingga setiap kelompok pelanggan dapat dipahami berdasarkan karakteristik pembelian yang berbeda.

Metode yang digunakan pada project ini adalah **K-Means Clustering** dengan pendekatan fitur **RFM**, yaitu Recency, Frequency, dan Monetary. Fitur tersebut digunakan untuk melihat seberapa baru pelanggan melakukan transaksi, seberapa sering pelanggan bertransaksi, dan seberapa besar nilai pembelian pelanggan.

## Dataset

Dataset yang digunakan adalah **Online Retail.xlsx**. Dataset ini berisi data transaksi pelanggan, seperti nomor invoice, kode produk, deskripsi produk, jumlah pembelian, tanggal transaksi, harga produk, ID pelanggan, dan negara pelanggan.

Beberapa kolom utama pada dataset:

* InvoiceNo
* StockCode
* Description
* Quantity
* InvoiceDate
* UnitPrice
* CustomerID
* Country

## Project Workflow

Tahapan yang dilakukan dalam project ini meliputi:

1. Import library yang dibutuhkan
2. Load dataset Online Retail
3. Data understanding
4. Data cleaning
5. Feature engineering
6. Exploratory Data Analysis
7. Log transformation
8. Outlier handling
9. Feature scaling
10. Menentukan jumlah cluster optimal
11. Membuat model K-Means Clustering
12. Visualisasi cluster menggunakan PCA
13. Evaluasi hasil clustering
14. Menyimpan model dan hasil clustering

## Data Preprocessing

Pada tahap preprocessing, dilakukan beberapa proses pembersihan data agar data siap digunakan untuk clustering. Proses yang dilakukan antara lain menghapus missing values, menghapus data duplikat, menghapus transaksi yang dibatalkan, serta menghapus data dengan nilai Quantity dan UnitPrice yang tidak valid.

Selain itu, kolom CustomerID diubah menjadi tipe integer dan kolom InvoiceNo diubah menjadi tipe string agar lebih mudah diproses.

## Feature Engineering

Pada tahap feature engineering, dibuat beberapa fitur baru dari data transaksi. Fitur utama yang digunakan dalam proses clustering adalah:

* **Recency**: menunjukkan jumlah hari sejak pelanggan terakhir melakukan transaksi.
* **Frequency**: menunjukkan jumlah transaksi unik yang dilakukan oleh pelanggan.
* **Monetary**: menunjukkan total nilai pembelian pelanggan.

Selain fitur RFM, dibuat juga beberapa fitur tambahan seperti:

* **TotalPrice**: hasil perkalian antara Quantity dan UnitPrice.
* **TotalQuantity**: total jumlah barang yang dibeli pelanggan.
* **UniqueProduct**: jumlah jenis produk berbeda yang pernah dibeli pelanggan.
* **AverageOrderValue**: rata-rata nilai pembelian pelanggan dalam setiap transaksi.

## Exploratory Data Analysis

Pada tahap EDA, dilakukan analisis korelasi antar fitur menggunakan heatmap, visualisasi hubungan antar fitur menggunakan pairplot, pengecekan skewness, serta scatter plot untuk melihat hubungan antara Frequency dan Monetary.

Hasil pengecekan skewness menunjukkan bahwa beberapa fitur memiliki distribusi yang cukup miring, terutama pada fitur Monetary dan Frequency. Oleh karena itu, dilakukan log transformation menggunakan `np.log1p()` untuk mengurangi tingkat skewness pada data.

## Modeling

Algoritma yang digunakan dalam project ini adalah **K-Means Clustering**. Sebelum model dibuat, data terlebih dahulu melalui proses scaling menggunakan **StandardScaler** agar setiap fitur memiliki skala yang seimbang.

Jumlah cluster optimal ditentukan dengan membandingkan nilai **Silhouette Score** dari beberapa nilai K, yaitu dari K=2 sampai K=10. Berdasarkan hasil pengujian, jumlah cluster terbaik adalah:

```text
K optimal: 2
Silhouette Score: 0.4339
```

Setelah model dibuat, data pelanggan berhasil dikelompokkan menjadi 2 cluster dengan distribusi sebagai berikut:

```text
Cluster 0: 2586 pelanggan
Cluster 1: 1685 pelanggan
```

## Evaluation

Evaluasi model clustering dilakukan menggunakan beberapa metrik, yaitu:

```text
Silhouette Score       : 0.4339
Davies-Bouldin Index   : 0.8883
Calinski-Harabasz Score: 4516.5182
Inertia                : 6226.0069
```

Nilai Silhouette Score sebesar 0.4339 menunjukkan bahwa hasil clustering sudah memiliki pemisahan antar cluster yang cukup, meskipun masih terdapat ruang untuk pengembangan lebih lanjut. Nilai Davies-Bouldin Index digunakan untuk melihat tingkat kedekatan antar cluster, sedangkan Calinski-Harabasz Score digunakan untuk melihat kualitas pemisahan cluster secara keseluruhan.

## Visualization

Visualisasi hasil clustering dilakukan menggunakan **PCA** untuk mereduksi dimensi data menjadi 2 komponen utama. Hasil PCA menunjukkan bahwa dua komponen utama mampu menjelaskan sebagian besar variasi data.

```text
PC1: 74.1%
PC2: 19.5%
Total variance explained: 93.6%
```

Visualisasi PCA digunakan untuk melihat sebaran pelanggan pada masing-masing cluster dalam bentuk dua dimensi.

## Output

Project ini menghasilkan beberapa output, yaitu:

* Model clustering yang disimpan dalam file `Clustering_KMeans.h5`
* Dataset hasil clustering yang disimpan dalam file `data_clustering.csv`
* Visualisasi hasil clustering menggunakan PCA
* Evaluasi performa clustering

## Tools and Libraries

Project ini dibuat menggunakan:

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* SciPy
* Joblib
* Jupyter Notebook

## Conclusion

Berdasarkan hasil clustering, pelanggan berhasil dikelompokkan menjadi 2 cluster berdasarkan perilaku transaksi mereka. Fitur Recency, Frequency, dan Monetary digunakan sebagai dasar segmentasi karena mampu merepresentasikan pola pembelian pelanggan.

Hasil evaluasi menunjukkan bahwa model memiliki Silhouette Score sebesar 0.4339, yang berarti pemisahan antar cluster sudah cukup baik untuk analisis awal. Project ini masih dapat dikembangkan lebih lanjut dengan menambahkan analisis karakteristik setiap cluster, mencoba algoritma clustering lain seperti DBSCAN atau Hierarchical Clustering, serta melakukan interpretasi bisnis yang lebih mendalam terhadap masing-masing segmen pelanggan.

## Author

Patrick
