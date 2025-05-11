# Rock-Paper-Scissors Classification Project 🪨📄✂️

## 📚 Deskripsi Proyek

Proyek ini bertujuan untuk membangun sistem klasifikasi gambar sederhana menggunakan **Deep Learning** dengan arsitektur **Transfer Learning** (menggunakan MobileNetV2).  
Gambar yang diklasifikasikan terdiri dari tiga kategori: **Rock**, **Paper**, dan **Scissors**.

Model yang dilatih kemudian diintegrasikan ke dalam aplikasi backend berbasis **FastAPI**, sehingga bisa menerima gambar dan memberikan hasil prediksi secara real-time.

## 🛠️ Teknologi yang Digunakan

- **TensorFlow / Keras** — Untuk membangun dan melatih model klasifikasi gambar.
- **FastAPI** — Untuk membangun backend REST API.
- **Uvicorn** — Sebagai ASGI server untuk menjalankan FastAPI.
- **PIL (Pillow)** — Untuk memproses gambar.
- **NumPy** — Untuk manipulasi data numerik.
- **scikit-learn** — Untuk evaluasi model (classification report, confusion matrix).

## 📂 Struktur Folder Proyek

```
project-root/
├── backend/
│   └── main.py         # Kode backend FastAPI
├── frontend/
│   └── app.py          # Kode frontend Streamlit
├── model/
│   └── best_transfer.h5 # Model hasil training yang disimpan
├── dataset/
│   ├── rock/
│   ├── paper/
│   └── scissor/
├── results/
│   ├── evaluation/
│   │   ├── confusion_matrix.png   # Confusion matrix hasil evaluasi
│   │   ├── classification_report.txt  # Laporan klasifikasi
│   │   └── training_history.png   # Grafik history training
│   └── screenshots/
│       ├── app_screenshot1.png    # Screenshot tampilan aplikasi
│       └── app_screenshot2.png    # Screenshot hasil prediksi
├── README.md
└── requirements.txt
```

## 🔄 Dataset

Dataset Rock-Paper-Scissors yang digunakan dalam proyek ini tersedia di:
* [Rock-Paper-Scissors Dataset - Kaggle](https://www.kaggle.com/datasets/drgfreeman/rockpaperscissors)

## 🚀 Langkah Penggunaan

### 1. Clone Repository
```bash
git clone https://github.com/WidyaNurulSukma/Tugas3_WidyaNurulSukma_2208107010054.git
cd rock-paper-scissors-classifier
```

### 2. Siapkan Environment Python
```bash
# Buat virtual environment
python -m venv venv

# Aktifkan virtual environment
# Untuk Windows:
venv\Scripts\activate
# Untuk macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### 3. Struktur Dataset
Setelah download dan ekstrak dataset, susun folder menjadi:
```
dataset/
├── rock/
├── paper/
└── scissor/
```

### 4. Menjalankan Aplikasi
Model sudah dilatih sebelumnya, jadi kita bisa langsung menjalankan aplikasi:

Jalankan backend FastAPI:
```bash
cd backend
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

Jalankan frontend Streamlit:
```bash
cd frontend
streamlit run app.py
```

Aplikasi Streamlit akan berjalan di `http://localhost:8501/`, dan backend API akan berjalan di `http://localhost:8000/`.

## 📊 Hasil Evaluasi Model

Hasil evaluasi model dapat dilihat pada folder `results/evaluation/`:

- **Confusion Matrix**: Visualisasi kesalahan prediksi antar kelas
- **Classification Report**: Metrik precision, recall, dan f1-score untuk setiap kelas
- **Training History**: Grafik akurasi dan loss selama proses training

### Ringkasan Performa Model

- **Accuracy**: ~97% pada dataset validasi
- **Precision & Recall**: >95% untuk semua kelas
- **F1-Score**: >95% rata-rata

## 📱 Tampilan Aplikasi

Screenshot tampilan aplikasi dapat dilihat di folder `results/screenshots/`.

## 📝 Catatan Penting

1. **Model Sudah Dilatih**: Model sudah dilatih sebelumnya dan disimpan di folder `model/`.
2. **Preprocessing Konsisten**: Backend sudah dikonfigurasi dengan preprocessing yang sama seperti saat training.
3. **Model Path**: Pastikan path model pada `backend/main.py` mengarah ke lokasi file model yang benar.
4. **Dependensi**: Pastikan versi TensorFlow dan Keras kompatibel untuk menghindari masalah saat loading model.
5. **CORS**: Backend sudah dikonfigurasi untuk menerima request dari frontend Streamlit.

## 💡 Penjelasan Teknis Model

Model menggunakan MobileNetV2 sebagai base model dengan transfer learning, yang diikuti dengan beberapa fully connected layer untuk klasifikasi. Konfigurasi model:

- Input size: 224x224x3
- Base model: MobileNetV2 (pre-trained pada ImageNet)
- Custom layers: GlobalAveragePooling2D, Dense(128, ReLU), Dropout(0.5), Dense(3, Softmax)
- Optimizer: Adam dengan learning rate 0.001
- Loss function: Categorical Cross-Entropy

## 👨‍💻 Kontributor

* Widya Nurul Sukma - widyasukma934@gmail.com

## 📜 Lisensi

Project ini dilisensikan di bawah MIT License.
