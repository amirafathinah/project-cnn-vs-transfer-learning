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

## Bagian A: Operasi pada Sinyal 1D
* **Pembangkitan Sinyal Diskrit:** Membuat sinyal sinus diskrit $x_1[n] = \sin(0.5\pi n)$ dan sinyal *unit step* $x_2[n]$ menggunakan pustaka NumPy.
* **Operasi Penjumlahan:** Menggabungkan dua sinyal sekuensial dan menganalisis perubahan nilai amplitudo hasil kombinasi.
* **Operasi Penggeseran (*Shifting*):** Menggeser posisi sinyal pada sumbu waktu dengan variasi nilai konstanta $k$ ($k = -3, 0, 4$) untuk simulasi efek *delay* (keterlambatan sinyal).
* **Operasi Amplifikasi:** Mengalikan sinyal dengan faktor penguat $\alpha$ (0.5, 1, 2, -1) guna mengamati perubahan skala amplitudo dan pembalikan fase.

## Bagian B: Operasi pada Citra 2D
* **Ekstraksi Metadata Citra:** Membaca properti spasial meliputi dimensi resolusi, tipe data, serta nilai minimum dan maksimum piksel citra masukan.
* **Penjumlahan Citra (*Image Blending*):** Melakukan kombinasi linier dua citra berdimensi sama (melalui proses *resizing* jika diperlukan) untuk menganalisis efeknya terhadap kecerahan (*brightness*) dan detail visual.
* **Penggeseran Citra (Translasi Spasial):** Menggeser koordinat piksel secara horizontal dan vertikal ($\Delta i$ dan $\Delta j$) serta menganalisis area kosong (*padding*) yang terbentuk.
* **Amplifikasi Citra & Analisis Histogram:** Mengalikan intensitas piksel menggunakan faktor pengali α untuk mengamati perubahan brightness, distribusi histogram, dan potensi saturasi nilai piksel.

## Bagian C: Uji Sistem Linier
* Melakukan pengujian matematis dan visual terhadap sistem $T_1(x) = 2x$ dan sistem $T_2(x) = x^2$ untuk membuktikan pemenuhan syarat properti **Homogenitas** T(\alpha x) = \alpha T(x) dan **Additivitas** $T(x_1 + x_2) = T(x_1) + T(x_2).
  
## Struktur Direktori Repositori
Tata kelola berkas di dalam repositori ini diisolasi berdasarkan fungsi masing-masing komponen sebagai berikut:

```text
├── notebook/
│   └── operasi_sinyal_citra.ipynb  # Sumber kode utama eksperimen (Jupyter Notebook)
├── images/
│   └── citra_input.jpg             # Aset citra digital yang digunakan dalam Bagian B
│   └── citra_input2.jpg            \
├── report/
│   └── laporan.pdf                 # Laporan analisis teknis 
├── README.md                       # Dokumentasi utama proyek 
└── requirements.txt                # Daftar pustaka (*dependencies*) Python yang diperlukan
```

## Requirements

- Python 3.10+
- NumPy
- Matplotlib
- OpenCV (opencv-python)

Install dependency menggunakan:

```bash
pip install -r requirements.txt
```

## Cara Menjalankan

1. Clone repositori

```bash
git clone https://github.com/username/repo.git
```

2. Install dependency

```bash
pip install -r requirements.txt
```

3. Jalankan notebook

```
notebook/operasi_sinyal_citra.ipynb
```

## Output

Eksperimen menghasilkan:

- Visualisasi sinyal diskrit
- Operasi penjumlahan sinyal
- Operasi penggeseran sinyal
- Operasi amplifikasi sinyal
- Operasi penjumlahan citra
- Operasi translasi citra
- Histogram sebelum dan sesudah amplifikasi
- Pengujian homogenitas sistem
- Pengujian additivitas sistem
