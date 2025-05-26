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
  * Membangun sistem rekomendasi berbasis *Collaborative Filtering*
    : Merekomendasikan destinasi berdasarkan preferensi pengguna lain yang memiliki kesamaan minat, efektif untuk pengguna yang sudah memiliki riwayat rating.
