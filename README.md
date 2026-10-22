# Perbandingan Performa KNN dan SVM dalam Pengenalan Aktivitas Manusia Menggunakan Smartphone

Final Project mata kuliah Pembelajaran Mesin. Project ini membandingkan performa K-Nearest Neighbors (KNN) dan Support Vector Machine (SVM) dalam mengenali enam aktivitas manusia (berjalan, naik tangga, turun tangga, duduk, berdiri, berbaring) dari data sensor accelerometer dan gyroscope pada smartphone.

## Dataset

Human Activity Recognition with Smartphones, dikumpulkan oleh Reyes-Ortiz dkk. (2013) dari 30 subjek berusia 19 sampai 48 tahun yang membawa smartphone di pinggang saat melakukan enam aktivitas sehari-hari. Data mentah berupa sinyal accelerometer dan gyroscope sudah diolah menjadi 561 fitur domain waktu dan frekuensi.

Sumber: [Kaggle - Human Activity Recognition with Smartphones](https://www.kaggle.com/datasets/uciml/human-activity-recognition-with-smartphones/data)

Dataset tidak disertakan di repo ini karena ukurannya cukup besar untuk di-commit langsung. Unduh dari tautan di atas, lalu taruh `train.csv` dan `test.csv` di folder `data/raw/`.

## Struktur Folder

```
har-knn-svm/
├── data/
│   ├── raw/                  # Dataset asli (train.csv, test.csv), tidak di-commit
│   └── processed/            # Hasil preprocessing (scaled, PCA, dsb)
├── notebooks/
│   ├── 01_eda.ipynb          # Eksplorasi data
│   ├── 02_preprocessing.ipynb
│   ├── 03_modeling_knn.ipynb
│   ├── 04_modeling_svm.ipynb
│   └── 05_evaluation.ipynb
├── src/
│   ├── __init__.py
│   ├── preprocessing.py      # Fungsi scaling, PCA, split
│   ├── models.py             # Wrapper training KNN & SVM
│   ├── evaluate.py           # Fungsi metrik, confusion matrix
│   └── utils.py
├── results/
│   ├── figures/               # Grafik, confusion matrix, hasil tuning
│   └── metrics/                # Tabel hasil evaluasi (csv/json)
├── models/                    # Model terlatih (pkl/joblib), tidak di-commit
├── reports/
│   └── laporan_final.pdf      # Laporan akhir
├── tests/
│   └── test_preprocessing.py
├── .gitignore
├── requirements.txt
└── README.md
```

Susunan ini pakai pemisahan umum antara data, notebook eksplorasi, kode yang bisa dipakai ulang di `src/`, dan hasil eksperimen. Notebook cocok untuk eksplorasi awal, tapi fungsi yang dipakai berulang (preprocessing, evaluasi) sebaiknya dipindah ke modul Python supaya tidak ada duplikasi kode antar notebook.

## Metode

Dua model dibandingkan pada data yang sama:

- **KNN**, diuji dengan beberapa nilai k dan dua metrik jarak (Euclidean, Manhattan).
- **SVM**, diuji dengan kernel linear dan RBF, dengan tuning parameter C dan gamma lewat grid search.

Kedua model dievaluasi dengan akurasi, precision, recall, F1-score per kelas, serta confusion matrix untuk melihat kelas mana yang paling sering tertukar (biasanya sitting dan standing, karena karakteristik sinyalnya mirip saat tubuh diam).

## Cara Menjalankan

```bash
# Clone repo
git clone https://github.com/<username>/har-knn-svm.git
cd har-knn-svm

# Buat virtual environment
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# Install dependensi
pip install -r requirements.txt

# Jalankan notebook secara berurutan
jupyter notebook notebooks/
```

## Anggota Kelompok

| Nama | NIM | Kontribusi |
|---|---|---|
| Diandra Adilah Akbar | 163241078 | - |
| Farel Hansel Suryadhinata | 163241016 | ... |
| Shiraz Akhiru Ramadhan | 163241063 | ... |

## Referensi

- Anguita, D., Ghio, A., Oneto, L., Parra, X., & Reyes-Ortiz, J. L. (2013). A Public Domain Dataset for Human Activity Recognition Using Smartphones. ESANN.
- Reyes-Ortiz, J., Anguita, D., Ghio, A., Oneto, L., & Parra, X. (2013). Human Activity Recognition Using Smartphones [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C54S4K