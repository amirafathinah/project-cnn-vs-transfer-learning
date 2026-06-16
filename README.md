# Analisis Efektivitas CNN dari Scratch dan Transfer Learning MobileNetV2 pada Klasifikasi Citra Kucing dan Anjing
Repositori ini berisi proyek eksperimen berbasis Python untuk membandingkan dua pendekatan dalam klasifikasi citra: Convolutional Neural Network (CNN) from scratch dan Transfer Learning dengan MobileNetV2. Proyek ini disusun untuk memenuhi tugas individu mata kuliah Pembelajaran Mesin 2.

## Identitas Mahasiswa
* **Nama Lengkap:** Amira Fathinah
* **NIM:** 452024618075
* **Program Studi:** Teknik Informatika C1
* **Semester:** 5

## Tujuan Eksperimen
Eksperimen ini bertujuan untuk membandingkan secara kuantitatif dan kualitatif dua pendekatan utama dalam klasifikasi citra:
- CNN from Scratch: Membangun dan melatih model Convolutional Neural Network dari awal pada dataset berukuran kecil (CIFAR-10, 2 kelas, 200 gambar).
- Transfer Learning: Memanfaatkan model pretrained MobileNetV2 yang telah dilatih pada dataset ImageNet untuk klasifikasi pada dataset Cats vs Dogs.

## Bagian A: CNN from Scratch

- **Dataset**: CIFAR-10 (2 kelas: kucing dan anjing, 100 gambar per kelas)
- **Arsitektur**: 3 blok konvolusional (32, 64, 128 filter) dengan BatchNormalization, MaxPooling, Flatten, Dense (128), Dropout (0.5), dan output Sigmoid.
- **Preprocessing**: Normalisasi [0,1], augmentasi (rotasi 20°, flip horizontal).
- **Hasil**: Akurasi testing 77.89%, menunjukkan overfitting karena rasio parameter:sampel yang tinggi (2.543:1).


## Bagian B: Transfer Learning dengan MobileNetV2

- **Dataset**: Cats vs Dogs (Kaggle, 24.998 gambar valid)
- **Arsitektur**: MobileNetV2 pretrained sebagai feature extractor dengan classifier tambahan (GlobalAveragePooling, Dense 128, Dropout 0.5, output Sigmoid).
- **Strategi**: Feature extraction (epoch 1-10) dan fine-tuning (epoch 11-20) dengan learning rate yang diturunkan.
- **Preprocessing**: Resize 224x224, normalisasi [-1,1] dengan `preprocess_input`, augmentasi (rotasi, shift, zoom, flip).
- **Hasil**: Akurasi testing 97.82%, stabil, tanpa overfitting signifikan.

## Struktur Direktori Repositori
Tata kelola berkas di dalam repositori ini diisolasi berdasarkan fungsi masing-masing komponen sebagai berikut:

```text
├── dataset/
│ └── link_dataset.txt
├── notebook/
│ └── cnn_vs_transfer_learning.ipynb # Sumber kode utama eksperimen (Jupyter Notebook)
├── report/
│ └── laporan.pdf # Laporan analisis teknis lengkap
├── README.md # Dokumentasi utama proyek
└── requirements.txt # Daftar pustaka Python yang diperlukan
```


> **Catatan**: Dataset CIFAR-10 diunduh otomatis melalui TensorFlow Keras, sedangkan dataset Cats vs Dogs diunduh otomatis melalui `kagglehub`. Kedua dataset tidak disertakan dalam repositori untuk menghemat ukuran.

---

## Requirements

| Pustaka | Fungsi |
|---------|--------|
| **tensorflow** | Framework deep learning untuk membangun dan melatih model CNN & MobileNetV2 |
| **numpy** | Manipulasi data numerik dan array multidimensi |
| **matplotlib** | Visualisasi data, kurva training, dan confusion matrix |
| **scikit-learn** | Pembagian data (train_test_split) dan metrik evaluasi |
| **Pillow (PIL)** | Memeriksa dan memproses file gambar (filter gambar corrupt) |
| **kagglehub** | Mengunduh dataset Cats vs Dogs langsung dari Kaggle |

### Install dependency menggunakan:

```bash
pip install -r requirements.txt
