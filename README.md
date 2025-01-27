# Penerapan Deep Learning untuk Mengklasifikasikan Gambar Vandalisme dan Bukan Vandalisme

## Kelompok 3
1. Boy Aditya Rohmaulana (2203488)
2. Defrizal Yahdiyan Risyad (2206131)
3. Muhamad Furqon Al-Haqqi (2207207)
4. Raya Cahya Nurani (2205714)
5. Septiani Eka Putri (2206000)

## Pendahuluan
Notebook ini bertujuan untuk membahas penerapan algoritma deep learning pada tugas klasifikasi gambar vandalisme dan bukan vandalisme. Dengan urbanisasi yang pesat, monitoring tanda-tanda vandalisme menjadi penting untuk menjaga keindahan dan kebersihan lingkungan. 

### Pengertian Vandalisme dan Perbedaannya dengan Graffiti dan Mural
- Vandalisme: Aksi yang merusak hasil karya orang lain dan barang berharga secara kasar.
- Graffiti: Coretan di dinding dengan pertimbangan seni (warna, garis, bentuk, volume).
- Mural: Lukisan pada bidang permanen seperti tembok atau dinding.

Kami mengelompokkan graffiti dan mural ke kelas `not_vandalized` dengan asumsi bahwa graffiti dan mural bukanlah vandalisme jika dilakukan dengan izin.

## Setup
- **Framework**: TensorFlow
- **Dataset**: Gambar vandalisme dan bukan vandalisme diunggah ke Google Drive.

## Preprocessing Dataset
### Jumlah Data
- **Kelas awal**:
  - `vandalized`: 168 gambar
  - `not_vandalized`: 133 gambar

### Split Dataset
- Training: 80%
- Validation: 20%

### Augmentasi Data
Augmentasi dilakukan untuk meningkatkan variasi dataset dengan teknik seperti:
- Horizontal flip
- Random rotation
- Random zoom

### Normalisasi Data
Nilai RGB dari [0, 255] dinormalisasi menjadi [0, 1].

## Arsitektur Model Deep Learning
### Model 1 (Baseline)
1. **Layer Konvolusi**:
   - 3 lapisan dengan filter 16, 32, 64.
2. **Pooling**: MaxPooling.
3. **Dense Layer**: 128 unit.
4. **Output Layer**: Berdasarkan jumlah kelas (2 kelas).

### Model 2 (Dengan Dropout)
Penambahan dropout (0.2) untuk mengurangi overfitting.

### Model 3 (Dataset Direvisi)
Data `not_vandalized` diperbaiki dengan memindahkan 51 gambar graffiti/mural yang dianggap vandalisme ke kelas `vandalized`. Dataset baru:
- **`vandalized`: 219 gambar**
- **`not_vandalized`: 82 gambar**

## Pelatihan Model
- Optimizer: Adam
- Loss Function: SparseCategoricalCrossentropy
- Epochs: 10-15

### Evaluasi Hasil
Hasil evaluasi menunjukkan bahwa model memiliki akurasi validasi yang lebih baik setelah revisi dataset. Model sebelumnya sulit mengklasifikasikan gambar karena asumsi awal yang ambigu.

## Kesimpulan
- Deep learning efektif untuk klasifikasi gambar vandalisme dengan preprocessing yang tepat.
- Revisi dataset berpengaruh signifikan pada performa model.
- Akurasi validasi meningkat setelah pemindahan data graffiti/mural ke kelas `vandalized`.

## Catatan Tambahan
- Dataset dapat diperluas untuk meningkatkan generalisasi model.
- Perlu dilakukan hyperparameter tuning untuk performa yang lebih optimal.

---
Dibuat oleh Kelompok 3 sebagai bagian dari studi kasus penerapan deep learning.
