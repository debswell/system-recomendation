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
* Kesulitan Personalisasi : Wisatawan mengalami kesulitan menemukan destinasi wosata yang sesuai dengan preferensi pribadi mereka.
* Inefficinet Discovery : Proses pencarian destinasi wisata yang cocok memakan waktu lama dan sering menghasilkan pilihan yang tidak sesuai ekspektasi.
* Cold Start Probelem : Pengguna baru atau destinasi baru sulit mendapatkan rekomendasi yang relevan karena kurangnya data historis interaksi.
  
**2. Tujuan**
* Meningkatkan User Experience : Mengembangkan sistem rekomendasi yang dapat memberikan saran destinasi wisata yang relevan untuk setiap pengguna baik pengguna baru maupun lama.
* Optimasi Proses Perencanaan : Mengurangi waktu dan effort yang diperlukan wisatawan dalam merencanakan perjalanan wisata.

  **Pendekatan Solusi**
  
  Dalam mencapai tujuan yang akan dibuat, berikut beberapa solusi yang dapat digunakan sehingga tujuan dan masalah yang dihadapi dapat dicapai dengan baik.
  * Membangun sistem rekomendai berbasis *Content-Based Filtering*
    : Merekomendasi destinasi wisata berdasarkan kemiripan atribut pengguna, cocok untuk pengguna baru yang belum memiliki riwayat rating.
  * Membangun sistem rekomendasi untuk
    : Merekomendasikan destinasi berdasarkan preferensi pengguna lain yang memiliki kesamaan minat, efektif untuk pengguna yang sudah memiliki riwayat rating.

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
* Menyatukan kategori yang serupa untuk memudahkan analisis dan visualisasi yang lebih jelas dan terstruktur.
* Mengatasi fitur duplikat dengan cara di drop pada file tourism_rating
* Melakukan encoding pada fitur Category dan City
* Melakukan normalisasi menggunakan MinMaxScaler terhadap Fitur Price dan Rating dan mengubahnya menajdi kolom Price_normalized dan Rating_normalized
* Menyalin data yang digunakan kedalam content_features
* Membuat fitur baru Popularity_score untuk membuat skor popularitas tempat wisata
* Melakukan normalisasi price dibagi kedalam 3 kategori (Low,Medium,High) dan menyimpannya pada kolom baru yaitu Price_normalized
* Menyimpan semua data yang sudah di proses untuk diguankan ke tahap pembuatan model Collaboration
* Menyimpan encoders dan scaler format .pkl untuk dapat digunakan dalam tahap pembuatan model collaboration
* Memilih fitur relevan untuk analisis similarity atau rekomendasi tempat wisata berbasis konten agar model dapat mengenali kemiripan antar objek dengan lebih baik.

## Modelling
### Content-Based Filtering
* Membuat matriks similarity dengan menggunakan cosine_similarity yang menunjukkan seberapa mirip tiap objek wisata satu dengan lainnya berdasarkan fitur numerik yang sudah dipilih.
* membuat fungsi 'get_content_recommendations' untuk memeriksa keberadaan kolom Place_Name dan mengurutkan similarity score dan mengambil top-N rekomendasi.

| Aspek           | Content-Based Filtering |
|----------------|--------------------------|
| **Keunggulan**  | - Tidak butuh banyak data pengguna  <br> - Bisa rekomendasi item baru |
| **Kelemahan**   | - Tidak bisa memahami selera pengguna secara kolektif              |


## Evaluation
### Content-Based Filtering
* Menggunakan metrik Cosine Similarity sebagai metrik utama untuk mengevaluasi seberapa mirip sebuah tempat wisata dengan tempat lainnya berdasarkan fitur-fitur numerik (seperti Rating Normalized, Price Normalized, dll).
* Metrik Cosine Similarity berhasil menunjukkan kemiripan konten antar tempat wisata, terkusus bagi wisatawan baru yang belum melakukan rating sesuai dengan personalisasi wisatawan.
  
![image](https://github.com/user-attachments/assets/fcb08054-3569-45a1-8671-98e9f6ec0ca7)


