# Analisis Sentimen Ulasan Aplikasi JakLingko Menggunakan SVM

## 📖 Pendahuluan (Latar Belakang)

Proyek ini adalah implementasi dari penelitian skripsi untuk menganalisis sentimen dari ulasan pengguna aplikasi **JakLingko** di Google Play Store. Seiring meningkatnya penggunaan aplikasi transportasi publik, masukan dari pengguna menjadi aset berharga untuk pengembangan aplikasi. Analisis sentimen secara otomatis memungkinkan pengembang untuk memahami opini publik (positif atau negatif) secara efisien dari ribuan ulasan.

Tujuan utama dari proyek ini adalah untuk membangun sebuah model *machine learning* yang mampu mengklasifikasikan ulasan pengguna ke dalam sentimen **positif** atau **negatif** dengan akurasi tinggi menggunakan metode **Support Vector Machine (SVM)**.

---

## 📊 Alur Kerja Proyek (Methodology)

Proses analisis sentimen ini dilakukan melalui beberapa tahapan kunci dalam *Natural Language Processing* (NLP), mulai dari pengumpulan data hingga evaluasi model.

1.  **Pengumpulan Data**
    * Data ulasan pengguna aplikasi JakLingko dikumpulkan (*scraping*) dari platform Google Play Store.

2.  **Text Preprocessing (Pembersihan Teks)**
    * Teks ulasan dibersihkan untuk menghilangkan *noise* dan menyeragamkan data. Tahapan ini meliputi:
        * **Cleansing**: Menghapus tanda baca, angka, dan karakter yang tidak relevan.
        * **Case Folding**: Mengubah seluruh teks menjadi huruf kecil.
        * **Normalisasi**: Mengubah kata-kata tidak baku (*slang*) menjadi kata baku sesuai kamus.
        * **Stemming**: Mengubah kata berimbuhan menjadi kata dasarnya menggunakan library Sastrawi.
        * **Stopword Removal**: Menghilangkan kata-kata umum yang tidak memiliki makna signifikan.

3.  **Feature Engineering dengan Word2Vec**
    * Kata-kata yang sudah bersih diubah menjadi representasi numerik (vektor) menggunakan model **Word2Vec**. Metode ini mampu menangkap makna dan konteks dari setiap kata, sehingga representasi vektornya lebih kaya makna.

4.  **Penanganan Ketidakseimbangan Kelas dengan SMOTE**
    * Distribusi data ulasan seringkali tidak seimbang. Teknik **SMOTE (Synthetic Minority Over-sampling Technique)** digunakan untuk menyeimbangkan jumlah data di setiap kelas dengan cara membuat data sintetis untuk kelas minoritas.

5.  **Pemodelan dengan Support Vector Machine (SVM)**
    * Vektor fitur yang telah seimbang digunakan untuk melatih model klasifikasi **Support Vector Machine (SVM)** dengan *kernel linear*. SVM dipilih karena kemampuannya yang sangat baik dalam menemukan *hyperplane* optimal untuk memisahkan dua kelas.

---

## 📈 Hasil dan Kesimpulan

Model yang telah dilatih dievaluasi secara menyeluruh menggunakan metode **10-Fold Cross Validation** untuk memastikan performanya stabil dan dapat diandalkan. Berdasarkan hasil pengujian, model berhasil mencapai performa yang **sangat baik dan memuaskan**.

| Metrik Evaluasi | Skor |
| :-------------- | :--- |
| 🎯 **Akurasi** | **95.82%** |
| ✒️ **Presisi** | **95.94%** |
| 🔄 **Recall** | **95.69%** |
| ⚖️ **F1-Score** | **95.81%** |

### **Kesimpulan:**

Kombinasi antara *text preprocessing* yang cermat, representasi kata menggunakan **Word2Vec**, penanganan data tidak seimbang dengan **SMOTE**, dan klasifikasi menggunakan **Support Vector Machine (SVM)** terbukti **sangat efektif** untuk tugas analisis sentimen pada ulasan aplikasi JakLingko. Dengan akurasi mencapai **95.82%**, model ini dapat diandalkan untuk membantu para pemangku kepentingan dalam memahami dan memonitor opini pengguna secara otomatis.

---

## 🔍 Insight Utama dari Analisis

Analisis ini tidak hanya menghasilkan model, tetapi juga memberikan wawasan mendalam mengenai kekuatan dan kelemahan aplikasi JakLingko dari sudut pandang pengguna, yang divisualisasikan melalui *Word Cloud*.

 ### **Ulasan Negatif (Keluhan Utama Pengguna)** 📉

* **Masalah Fungsionalitas & Teknis:** Sebagian besar sentimen negatif berpusat pada masalah teknis yang menghambat pengalaman pengguna.
    * **Kata kunci yang sering muncul:** `error`, `susah`, `sulit`, `lama`, `force close`, `logout`.

* **Kesulitan pada Fitur Kunci:** Pengguna sering mengeluhkan fitur-fitur vital seperti proses *top-up*, integrasi kartu transportasi, dan proses *login*.
    * **Kata kunci yang sering muncul:** `top up`, `kartu`, `masuk`, `login`, `daftar`.

### **Ulasan Positif (Apresiasi Pengguna)** 📈

* **Kemudahan dan Manfaat:** Ketika aplikasi berfungsi dengan baik, pengguna sangat mengapresiasi kemudahan dan manfaat yang ditawarkan untuk mobilitas sehari-hari.
    * **Kata kunci yang sering muncul:** `mudah`, `bantu`, `bermanfaat`, `bagus`, `cepat`, `keren`.

* **Apresiasi terhadap Layanan:** Banyak pengguna memberikan ulasan positif sebagai bentuk terima kasih dan penghargaan terhadap fungsi aplikasi yang berjalan lancar.
    * **Kata kunci yang sering muncul:** `terima`, `kasih`, `baik`, `mantap`.

### **Rekomendasi Praktis:**

Berdasarkan temuan ini, prioritas utama bagi tim pengembang JakLingko adalah **memperbaiki stabilitas aplikasi** dan **menyederhanakan alur fitur-fitur krusial** (terutama *top-up* dan integrasi kartu) untuk mengurangi friksi dan meningkatkan kepuasan pengguna.

---

## 💻 Teknologi yang Digunakan

* **Bahasa**: Python 3
* **Library Utama**:
    * `Pandas`: Manipulasi data
    * `NLTK` & `Sastrawi`: Text preprocessing
    * `Gensim`: Implementasi Word2Vec
    * `Scikit-learn`: Implementasi SVM, SMOTE, dan metrik evaluasi
    * `Matplotlib` & `Seaborn`: Visualisasi data
    * `WordCloud`: Visualisasi frekuensi kata

---
