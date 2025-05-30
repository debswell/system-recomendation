# Laporan Proyek Machine Learning - Debi Welani Christin Saragih

## Ulasan Proyek
Indonesia meruapkan negara dengan kekayaan pariwisata yang sangat beragam, mulai dari wisata alam, budaya,kuliner, hingga wisata buatan.
Namun, banyak wisatawan baik lokal maupun internasional kesulitan dalam menemukan destinasi wisata yang benar-benar sesuai dengan preferensi dan kebutuhan mereka.
Permasalahan ini muncul karena beberapa faktor sepert : 
* Banyaknya pilihan destinasi wisata yang membuat pengguna bingung dalam menentukan pilihan
* Rekomendasi yang diberikan oleh orang lain maupun platform wisata seringkali tidak sesuai dengan minat atau kebutuhan spesifik pengguna.
* Kurangnya personalisasi dalam sistem rekomendasi yang ada,sehingga saran yang diberikan cenderung umum dan kurang relevan.

**Mengapa dan Bagaimana Masalah ini Harus Diselesaikan**

Permasalahan diatas berdampak langsung pada pengalaman wisatawan. Informasi yang diterima terlalu banyak dan tanpa penyaringan yang tepat, membuat wisatawan kewalahan dan akhirnya sulit mengambil keputusan [1].
Selain itu, rekomendasi yang tidak personal dapat menyebabkan ketidakpuasan, menurunkan minat untuk berwisata dan pada akhirnya menghambat pertumbuhan industri pariwisata Indonesia.

Untuk mengatasi hal ini, dibutuhkan sistem rekomendasi destinasi wisata yang mampu melakukan personalisasi berdasarkan data preferensi, prilaku dan riwayat pengguna.
Sistem seperti ini tela terbukti efektif meningkatkan kepuasan pengguna, mempercepat proses pengambilan keputusan serta mendorong wisatawan untuk mengeksplorasi destinasi yang lebih luas dan beragam [2].

**Referensi**

[1] Prasad et al. (2025). Personalized Travel Recommendations Using Hybrid Filtering Techniques. Journal of Information Systems Engineering.

[2] Badouch & Boutaounte (2023). Machine Learning Approaches in Tourism. Journal of AI and Neural Networks.

## Pemahaman Bisnis
**1. Pernyataan Masalah**
* Personalisasi yang Tidak Optimal : Wisatawan mengalami kesulitan dalam menemukan destinasi wisata yang sesuai dengan preferensi pribadi mereka karena belum adanya sistem yang dapat mempelajari kebutuhan unik setiap individu.
* Cold Start Problem : Pengguna baru atau destinasi baru sulit mendapatkan rekomendasi yang relevan karena kurangnya data historis interaksi atau rating.

**2. Tujuan**
* Meningkatkan Personalisasi Rekomendasi : Mengembangkan sistem rekomendasi yang mampu memberikan saran destinasi wisata yang relevan dan sesuai dengan preferensi pribadi pengguna, termasuk bagi pengguna lama.
* Mengatasi Masalah Cold Start : Membangun pendekatan yang dapat memberikan rekomendasi yang tetap akurat bagi pengguna atau item baru meskipun tidak memiliki data historis.

  **Pendekatan Solusi**

  Dalam mencapai tujuan yang akan dibuat, berikut beberapa solusi yang dapat digunakan sehingga tujuan dan masalah yang dihadapi dapat dicapai dengan baik.
  * Content-Based Filtering : Memberikan rekomendasi berdasarkan kesamaan antara profil pengguna dan atribut destinasi. Pendekatan ini cocok untuk pengguna baru karena tidak bergantung pada riwayat interaksi pengguna lain.
  * Collaborative Filtering (User-Based & Item-Based) : Memberikan rekomendasi berdasarkan pola interaksi antar pengguna dan item. Pendekatan ini efektif untuk pengguna aktif karena memanfaatkan data historis (rating) dari pengguna lain yang serupa.

## Data Understanding
sumber dataset : https://www.kaggle.com/datasets/aprabowo/indonesia-tourism-destination

Dataset terdiri dari 4 files :
### tourism_ dengan _id.csv yang berisi informasi tempat wisata di 5 kota besar di Indonesia yang berjumlah 437 baris, 13 kolom
     1. Place_Id : merupakan kolom id tempat wisata
     2. Place_Name : merupakan kolom nama wisata
     3. Description : merupakan keterangan mengenai tempat wisata
     4. Category : merupakan kolom kategori dari tempat wisata
     5. City : merupakan letak di kota atau daerah mana tempat wisata
     6. Price : merupakan harga untuk masuk ke tempat wisata 
     7. Rating : merupakan rating tempat wisata
     8. Time_Minutes : estimasi waktu yang dibutuhkan untuk menikmati aktivitas di tempat wisata tersebut (dalam menit).
     9. Coordinate : Gabungan koordinat lokasi, biasanya dalam format (latitude, longitude) sebagai string.
     10. Lat :	Koordinat garis lintang (latitude) tempat wisata.
     11. Long : Harusnya ini adalah Longitude (garis bujur) dari tempat wisata.
     12. Unnamed: 11 : Kolom kosong yang tidak berguna
     13. Unnamed: 12 : Kolom kosong yang tidak berguna
 * Terdapat 2 fitur dengan missing value (Time_minutes dan Unnamed : 11)
 * Tipe data pada file 8 kolom numerik dan 4 kolom kategorikal
 * Terdapat beberapa kolom yang tidak dibutuhkan dalam pembuatan model (Coordinate, Lat,Long,Unamed : 11 dan Unamed : 12)

### user.csv yang berisi data pengguna dummy untuk membuat fitur rekomendasi berdasarkan pengguna terdiri dari 300 baris, 3 kolom
    1. User_Id : kolom id untuk user(pengguna/pengunjung)
    2. Location : lokasi atau alamat dari user
    3. Age : usia dari user
  * tipe data pad file ini 2 kolom numerik dan 1 kolom kategorikal

### tourism_rating.csv berisi 3 kolom yaitu pengguna, tempat, dan rating yang diberikan, berfungsi untuk membuat sistem rekomendasi berdasarkan rating terdiri dari 10000 baris dan 3 kolom
    1. User_Id : id dari pengunjung
    2. Place_Id : id tempat wisata yang dikunjungi
    3. Place_Ratings : Rating dari tempat wisata 
  * Semua data bertipe numerik
  * Terdapat 79 data yang duplikat

### package_tourism.csv berisi rekomendasi tempat terdekat berdasarkan waktu, biaya, dan rating, teridiri dari 100 baris, 7 kolom
    1. Package : id dari paket turis
    2. City : Kota atau daerah tujuan utama dari paket wisata.
    3. Place_tourism1 : Tempat wisata pertama dalam paket. Wajib ada.
    4. Place_tourism2 : Tempat wisata kedua.
    5. Place_tourism3 : Tempat wisata ketiga.
    6. Place_tourism4 : Tempat wisata keempat.
    7. Place_tourism5 : Tempat wisata kelima.
  * Tipe data pada file ini, 1 bertipe numerik dan 6 kategorikal
  * terdapat missing value pada 2 kolom (Place_tourism4 dan place_tourism5)
### Hasil Visualiasi Data 
![image](https://github.com/user-attachments/assets/e9585ba8-c1f3-4309-b188-6073d0f46a12)
![image](https://github.com/user-attachments/assets/f458b428-74fa-4e5e-98e7-8204dae2bc87)

*Hasil dari grafik, kategori tempat wisata yang paling banyak dikunjungi adalah Taman hiburan*

![image](https://github.com/user-attachments/assets/cc4ae1bf-3499-4e63-bf0b-8e180e6d3a80)

*Hasil dari grafik, kota yang paling banyak memiliki tempat wisata adalah kota yograkarta dan berbeda sedikit dengan kota Bandung*

![image](https://github.com/user-attachments/assets/a63bf93e-4c09-4895-b7a7-d3f6489d3930)

*Berdasarkan tabel tourism_with_id, jumlah rating terbanyak terdapat di rentang rating 4-5*

![image](https://github.com/user-attachments/assets/8b9c802c-4bbb-4a3f-bed4-646abebca5ee)

*Berdasarkan rating, tempat wisata yang paling disukai oleh wisatawan adalah Keraton Surabaya, dilihat dari rating rata-ratanya hampir mencapai 4*

## Data Preparation
* Hal pertama yang dilakukan adalah mengatasi nilai kosong / missing value dengan mengisi nilai rata-rata
* Menghapus kolom yang tidak dibutuhkan,('Unnamed: 11','Unnamed: 12','Coordinate','Lat','Long')
* Mengatasi fitur duplikat dengan cara di drop pada file tourism_rating
* Melakukan encoding pada fitur Category dan City
* Melakukan normalisasi menggunakan MinMaxScaler terhadap Fitur Price dan Rating dan mengubahnya menajdi kolom Price_normalized dan Rating_normalized
* Mmebuat fitur baru total_ratings untuk menghitung total rating pada setiap tempat wisata
* Menyalin data yang digunakan kedalam content_features
* Membuat fitur baru Popularity_score untuk membuat skor popularitas tempat wisata berdasarkan total ratings
* Membuat fitur baru Catgeory_price untuk membagi kategori price menjadi 3 bagian (low,medium dan high)

## Modelling & Results
### Content-Based Filtering
* Memilih fitur relevan untuk analisis similarity atau rekomendasi tempat wisata berbasis konten agar model dapat mengenali kemiripan antar objek dengan lebih baik.
* Membuat matriks similarity dengan menggunakan cosine_similarity yang menunjukkan seberapa mirip tiap objek wisata satu dengan lainnya berdasarkan fitur numerik yang sudah dipilih.
* membuat fungsi 'get_content_recommendations' untuk memeriksa keberadaan kolom Place_Name dan mengurutkan similarity score dan mengambil top-N rekomendasi.
* Hasil top-N rekomendasi

  ![image](https://github.com/user-attachments/assets/539f4fd7-19af-455b-900a-ae3eefecb1bf)

### Collaborative-Based Filtering
* Membuat user similarity menggunakan cosine similarity
* Mmebuat fungsi 'get_user_based_recommendations' untuk  memberikan rekomendasi wisata berdasarkan kemiripan antar pengguna.Program menghitung user similarity matrix menggunakan cosine similarity dari matriks user-item. Lalu, fungsi get_user_based_recommendations dibuat untuk memberikan rekomendasi bagi pengguna tertentu. Fungsi ini akan mencari pengguna yang mirip.
* Membuat item similarity menggunakan cosine similarity
* Membuat fungsi 'get_item_based_recommendations' untuk memberikan rekomendasi tempat wisata berdasarkan kemiripan antar tempat. Proses dimulai dengan menghitung item similarity matrix menggunakan cosine similarity antar kolom (tempat) dalam matriks user-item. Fungsi get_item_based_recommendations kemudian digunakan untuk memprediksi rating tempat yang belum dikunjungi oleh pengguna berdasarkan rating pengguna terhadap tempat lain yang mirip.
* Menampilkan top-N rekomendasi dari collaborative-based filtering

  ![image](https://github.com/user-attachments/assets/cb58ed75-69e0-4452-9737-6f0ed040052d)


### Keunggulan dan Kelemahan setiap model

| Aspek           | Content-Based Filtering | Collaborative Filtering |
|----------------|--------------------------|-------------------------|
| **Keunggulan**  | - Tidak butuh banyak data pengguna  <br> - Bisa rekomendasi item baru | - Personalisasi lebih baik  <br> - Bisa menemukan item tak serupa |
| **Kelemahan**   | - Tidak bisa memahami selera pengguna secara kolektif              | - Butuh banyak data pengguna  <br> - Tidak bisa rekomendasi item baru |
| **Cold-start**  | Tidak bisa handle user baru dengan preferensi tidak diketahui      | Tidak bisa handle item baru tanpa rating|


## Evaluation
### Content-Based Filtering
* Menggunakan metrik Precision@
![image](https://github.com/user-attachments/assets/ecdf94ec-4fe5-4529-9c85-d7fe7b8bdb43)

Dari hasil evaluasi yang didapat Rata-rata Precision@5 sebesar 0.8733 (atau 87.33%), artinya: Dari 5 rekomendasi yang diberikan untuk setiap tempat, rata-rata 4-5 rekomendasi memiliki kategori yang sama → relevan secara konten.Dievaluasi pada 30 tempat sebagai sampel: cukup representatif untuk pengukuran awal.

**Rentang precision antara 0.0 dan 1.0:**

Ada kasus sangat bagus (1.0) → semua rekomendasi 100% sesuai kategori.

Ada juga kasus gagal (0.0) → tidak ada rekomendasi yang sesuai kategori.

### Collaborative-Based Filtering
* Menggunakan metrik RMSE (Root Mean Squared Error) untuk Mengukur seberapa besar perbedaan antara rating aktual dengan rating prediksi secara kuadrat, kemudian diakarkan.
* Menggunakan metrik MAE (Mean Absolute Error) untuk Mengukur rata-rata kesalahan absolut antara nilai aktual dan prediksi.

![image](https://github.com/user-attachments/assets/11bf7078-5dbe-472e-a702-260c03e4f9bd)

MAE (Mean Absolute Error) menunjukkan rata-rata kesalahan prediksi. Nilai ~1.17 dan ~1.16 berarti rata-rata prediksi rating meleset sekitar 1 poin dari nilai sebenarnya.

RMSE (Root Mean Squared Error) lebih sensitif terhadap kesalahan besar. Nilai RMSE yang sedikit lebih tinggi dari MAE menunjukkan ada beberapa prediksi dengan error yang lebih besar.

### Evaluasi summary Kedua model
![image](https://github.com/user-attachments/assets/54a7be4e-532b-4b26-a8c6-abae59b29aa1)

**Content-Based Filtering**

Precision@5: 0.8733
Artinya, dari setiap 5 rekomendasi yang diberikan oleh sistem berbasis konten, sekitar 87.33% di antaranya relevan bagi pengguna.

Ini menunjukkan bahwa Content-Based Filtering sangat efektif dalam memberikan rekomendasi yang sesuai dengan preferensi pengguna.

**User-Based Collaborative Filtering**

RMSE: 1.3683, MAE: 1.1731

Model ini memiliki performa cukup baik, namun masih terdapat deviasi rata-rata lebih dari 1 poin dari rating aktual pengguna.

**Item-Based Collaborative Filtering**

RMSE: 1.3387, MAE: 1.1602

Memiliki kinerja sedikit lebih baik dibandingkan user-based CF, menunjukkan bahwa pola kesamaan antar item lebih stabil dan dapat diandalkan dalam prediksi rating.

**Dari model yang sudah dibangun, model dapat mengatasi permasalahan yang dialami. Model content based dapat membantu wisatawan untuk mendapatkan rekomendasi walaupun belum pernah melakukan rating atau interaksi terhadap suatu tempat wisata. Begitupun dengan model collaborative dapat memebrikan rekomendasi kepada wisatawan berdasarkan data historynya. Berdasarkan hasil evaluasi, memang model yang paling baik adalah model content-based, dan seharuanya bisa manggunakan model hybrid untuk pembangunan model ini, tetapi saya membangun 2 model content dan collaborative dan mungkin bisa ditingkatkan selanjutnya ketahap hybrid**
