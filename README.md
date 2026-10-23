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
│   └── raw/
├── results/
│   └── figures/
├── reports/
│   └── laporan_final.pdf
├── har_knn_svm.ipynb
├── .gitignore
├── requirements.txt
└── README.md
```
 
Semua tahapan, mulai dari eksplorasi data sampai evaluasi model, ada dalam satu notebook `har_knn_svm.ipynb`.
 
## Metode
 
Dua model dibandingkan pada data yang sama:
 
- **KNN**, diuji dengan beberapa nilai k dan dua metrik jarak (Euclidean, Manhattan).
- **SVM**, diuji dengan kernel linear dan RBF, dengan tuning parameter C dan gamma lewat grid search.
Kedua model dievaluasi dengan akurasi, precision, recall, F1-score per kelas, serta confusion matrix untuk melihat kelas mana yang paling sering tertukar (biasanya sitting dan standing, karena karakteristik sinyalnya mirip saat tubuh diam).
 
## Cara Menjalankan
 
```bash
# Clone repo
git clone https://github.com/AnchorXV/har-knn-svm.git
cd har-knn-svm
 
# Buat virtual environment
python -m venv venv
source venv/bin/activate
 
# Install dependensi
pip install -r requirements.txt
 
# Jalankan notebook
jupyter notebook har_knn_svm.ipynb
```

## Anggota Kelompok

| Nama | NIM | Kontribusi |
|---|---|---|
| Diandra Adilah Akbar | 163241078 | - |
| Farel Hansel Suryadhinata | 163241016 | - |
| Shiraz Akhiru Ramadhan | 163241063 | - |

## Referensi

- Anguita, D., Ghio, A., Oneto, L., Parra, X., & Reyes-Ortiz, J. L. (2013). A Public Domain Dataset for Human Activity Recognition Using Smartphones. ESANN.
- Reyes-Ortiz, J., Anguita, D., Ghio, A., Oneto, L., & Parra, X. (2013). Human Activity Recognition Using Smartphones [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C54S4K
