# Rekonstruksi Artificial Neural Network untuk Peramalan Kurs Jual Rupiah terhadap Dolar Amerika

## 1. Deskripsi Proyek

Proyek ini merupakan rekonstruksi dan pengembangan eksperimen dari penelitian berjudul *"Implementasi Artificial Neural Network (ANN) dalam Memprediksi Nilai Tukar Rupiah terhadap Dolar Amerika"* oleh Adam Indra Sakti, Lianda Saputra, Helen Suhendra, Nikken Halim, Irfaliani Alviari, Muhammad Rozan Nur Ilham, Marwah Hotimah Nada Putri, dan Desy Yuliana Dalimunthe (2024).

Penelitian tersebut diterbitkan dalam Euler: Jurnal Ilmiah Matematika, Sains dan Teknologi, Volume 12, Nomor 2, halaman 124–130.

Proyek ini bertujuan untuk merekonstruksi tahapan pemodelan Artificial Neural Network (ANN) berdasarkan paper tersebut dengan menggunakan data kurs jual dari Bank Indonesia.

Implementasi dilakukan menggunakan dua pendekatan, yaitu perhitungan manual menggunakan NumPy dan implementasi menggunakan TensorFlow/Keras. Kedua pendekatan digunakan untuk membandingkan hasil pembelajaran dan performa model.

Rekonstruksi ini juga melibatkan penyesuaian terhadap data dan beberapa parameter eksperimen, sehingga hasil yang diperoleh tidak harus identik dengan hasil penelitian asli.

## 2. Tujuan

- Merekonstruksi penerapan ANN berdasarkan penelitian terdahulu.
- Memahami proses forward propagation dan backpropagation.
- Mengimplementasikan ANN secara manual menggunakan NumPy.
- Membandingkan implementasi manual dengan TensorFlow/Keras.
- Menganalisis pengaruh variasi jumlah neuron dan pembagian data.
- Mengevaluasi kemampuan model dalam melakukan peramalan kurs jual Rupiah.

## 3. Dataset

Data yang digunakan merupakan data historis kurs jual Rupiah terhadap Dolar Amerika yang diperoleh dari Bank Indonesia.

| Keterangan | Informasi |
|---|---|
| Sumber data | Bank Indonesia |
| Periode data | 1 Maret 2019–28 Februari 2024 |
| Jumlah input | 4 variabel |
| Jumlah output | 1 variabel |
| Periode peramalan | Maret 2024–Februari 2025 |

Tahapan preprocessing meliputi:
- Pemeriksaan dan pembersihan data.
- Penanganan tanggal yang tidak memiliki data.
- Penyesuaian data berdasarkan kalender pengamatan.
- Normalisasi menggunakan Min-Max Scaling dengan rentang 0,1–0,9.
- Pembagian data training dan testing secara kronologis.

## 4. Metode dan Arsitektur Model

Model yang digunakan adalah Multilayer Perceptron (MLP) dengan satu hidden layer dan satu output neuron.

Arsitektur umum:

`4 Input → Hidden Layer → 1 Output`

Variasi jumlah neuron pada hidden layer:
- 5 neuron
- 10 neuron
- 15 neuron
- 20 neuron
- 25 neuron
- 30 neuron

Skenario pembagian data:

| Skenario | Training | Testing |
|---|---:|---:|
| 1 | 90% | 10% |
| 2 | 80% | 20% |
| 3 | 70% | 30% |

Dengan demikian, terdapat 18 kombinasi model yang diuji.

Fungsi aktivasi yang digunakan adalah sigmoid pada hidden layer dan output layer.

## 5. Implementasi Model

### A. Implementasi NumPy

Model ANN dibangun secara manual menggunakan NumPy tanpa menggunakan package khusus neural network untuk proses training.

Tahapan perhitungan meliputi:

1. Inisialisasi bobot dan bias.
2. Forward propagation.
3. Perhitungan error menggunakan Mean Squared Error (MSE).
4. Backpropagation untuk memperoleh gradien.
5. Pembaruan bobot dan bias menggunakan Gradient Descent.
6. Evaluasi hasil training dan testing.

### B. Implementasi TensorFlow/Keras

Sebagai pembanding, model juga dibangun menggunakan TensorFlow/Keras.

Arsitektur, bobot awal, fungsi aktivasi, learning rate, epoch, dan ukuran batch disesuaikan dengan implementasi NumPy agar hasil keduanya dapat dibandingkan.

## 6. Evaluasi Model

Evaluasi dilakukan menggunakan beberapa pendekatan:

- MSE training untuk mengukur kesalahan pada data pelatihan.
- MSE testing untuk mengukur kesalahan pada data pengujian.
- Grafik konvergensi untuk mengamati penurunan error selama training.
- Grafik prediksi terhadap data aktual.
- Perbandingan hasil NumPy dan TensorFlow/Keras.
- Analisis indikasi underfitting.

## 7. Hasil Peramalan

Model digunakan untuk melakukan peramalan selama 365 hari, yaitu periode Maret 2024 hingga Februari 2025.

Pengujian juga dilakukan menggunakan dua skenario input, yaitu input A dan input B.

Berdasarkan hasil visualisasi, prediksi model cenderung lebih stabil dibandingkan fluktuasi data aktual. Hal ini menunjukkan bahwa model belum sepenuhnya mampu menangkap variasi dan perubahan pola kurs secara optimal.

Kondisi tersebut mengindikasikan adanya underfitting, sehingga kemampuan model dalam mempelajari pola data masih perlu ditingkatkan.

## 8. Catatan Pengembangan dan Rekomendasi

Rekonstruksi ini masih memiliki beberapa keterbatasan, terutama pada kemampuan model dalam mengikuti fluktuasi data aktual.

Pada implementasi saat ini, pembaruan parameter menggunakan Full-batch Gradient Descent. Untuk pengembangan selanjutnya, disarankan mencoba metode optimisasi stokastik, seperti:

- Stochastic Gradient Descent (SGD).
- Mini-batch Gradient Descent.

Metode tersebut dapat diuji sebagai alternatif untuk melihat pengaruh pembaruan parameter terhadap proses pembelajaran dan kemampuan model dalam menangkap variasi data.

Perbandingan sebaiknya tetap didasarkan pada MSE testing, pola konvergensi, dan kemampuan prediksi pada data yang belum digunakan dalam training.

## 9. Tools dan Libraries

- Python
- Google Colab
- NumPy
- Pandas
- Matplotlib
- TensorFlow/Keras

## 10. Struktur File

| File | Keterangan |
|---|---|
| `hasil_numpy_18_model.csv` | Hasil training 18 model NumPy |
| `hasil_keras_18_model.csv` | Hasil training 18 model Keras |
| `perbandingan_numpy_keras.csv` | Perbandingan kedua implementasi |
| `hasil_forecast_2024_2025.csv` | Hasil peramalan 365 hari |
| `forecast_inputs_norm.csv` | Data input peramalan ternormalisasi |
| `diagnostik_underfitting.csv` | Hasil pemeriksaan underfitting |
| `split_90_10.csv` | Dataset skenario 90:10 |
| `split_80_20.csv` | Dataset skenario 80:20 |
| `split_70_30.csv` | Dataset skenario 70:30 |

## 11. Kesimpulan

Proyek ini merekonstruksi penerapan Artificial Neural Network dalam peramalan kurs jual Rupiah terhadap Dolar Amerika berdasarkan penelitian terdahulu.

Melalui implementasi NumPy dan TensorFlow/Keras, proses pembelajaran ANN dapat dipelajari dari sisi matematis maupun komputasi.

Hasil eksperimen menunjukkan bahwa model masih memiliki keterbatasan dalam menangkap fluktuasi data aktual. Oleh karena itu, pengembangan lebih lanjut disarankan dengan menguji metode optimisasi stokastik dan mengevaluasi kembali kemampuan generalisasi model.

## Referensi

Sakti, A. I., Saputra, L., Suhendra, H., Halim, N., Alviari, I., Ilham, M. R. N., Putri, M. H. N., & Dalimunthe, D. Y. (2024). Implementasi Artificial Neural Network (ANN) dalam Memprediksi Nilai Tukar Rupiah terhadap Dolar Amerika. *Euler: Jurnal Ilmiah Matematika, Sains dan Teknologi, 12*(2), 124–130.

https://doi.org/10.37905/euler.v12i2.26654

---

**Project Type:** Academic Project / Machine Learning  
**Method:** Artificial Neural Network (MLP)  
**Implementation:** NumPy & TensorFlow/Keras  
**Environment:** Google Colab
