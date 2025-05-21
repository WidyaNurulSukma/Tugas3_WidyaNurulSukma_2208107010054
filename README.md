# Rock-Paper-Scissors Classification Project 🪨📄✂️

## 📚 Deskripsi Proyek

Proyek ini bertujuan untuk membangun sistem klasifikasi gambar sederhana menggunakan **Deep Learning** dengan arsitektur **Transfer Learning** (menggunakan MobileNetV2).  
Gambar yang diklasifikasikan terdiri dari tiga kategori: **Rock**, **Paper**, dan **Scissors**.

Model yang dilatih kemudian akan diintegrasikan ke dalam aplikasi backend berbasis **FastAPI**, sehingga bisa menerima gambar dan memberikan hasil prediksi secara real-time.

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
├── model/
│   └── best_transfer.h5 # Model hasil training yang disimpan
├── dataset/
│   ├── rock/
│   ├── paper/
│   └── scissor/
├── README.md
└── requirements.txt
```

## 🚀 Langkah Penggunaan

### Clone repository
```bash
git clone https://github.com/WidyaNurulSukma/Tugas3_WidyaNurulSukma_2208107010054.git
cd rock-paper-scissors-classifier
```

### Buat virtual environment
```bash
python -m venv venv
```

### Aktifkan virtual environment
#### Untuk Windows:
```bash
venv\Scripts\activate
```
#### Untuk macOS/Linux:
```bash
source venv/bin/activate
```

### Install dependencies
```bash
pip install -r requirements.txt
```

### Dataset
Dari Kaggle:  
🔗 [Rock-Paper-Scissors Dataset – Kaggle](https://www.kaggle.com/datasets/drgfreeman/rockpaperscissors)

Setelah download dan ekstrak:
- Susun dataset ke dalam folder:
```
dataset/
    rock/
    paper/
    scissor/
```

### Menjalankan Aplikasi

Model sudah dilatih sebelumnya, jadi kita bisa langsung menjalankan aplikasi:

#### Jalankan backend FastAPI:
```bash
# Buka terminal baru
cd backend
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

#### Jalankan frontend Streamlit:
```bash
# Buka terminal baru
cd frontend
streamlit run app.py
```

Aplikasi Streamlit akan berjalan di `http://localhost:8501/`, dan backend API akan berjalan di `http://localhost:8000/`.

## 📊 Hasil Evaluasi Model

Model sudah dievaluasi dengan performa yang baik. Hasil evaluasi dapat dilihat pada folder `results/evaluation/`:

- **Confusion Matrix**: Visualisasi kesalahan prediksi antar kelas
- ![image](https://github.com/user-attachments/assets/e70f3cc0-9da7-439d-b284-b8943b55bb1c)

- **Classification Report**: Metrik precision, recall, dan f1-score untuk setiap kelas
- ![image](https://github.com/user-attachments/assets/bf9a9a39-3084-4086-945e-82d86ae30fbe)

### Ringkasan Performa Model

- **Accuracy**: 98,81% (0.9881)
- **Precision & Recall**: Precision berkisar antara 98,41% hingga 99,19%, dan Recall berkisar antara 97,70% hingga 99,20%
- **F1-Score**:  Berkisar antara 98,27% hingga 99,19%, dengan rata-rata tertimbang 98,81%

## 📱 Tampilan Aplikasi beserta hasil prediksi
 ![WhatsApp Image 2025-05-11 at 10 20 39_1c97f914](https://github.com/user-attachments/assets/e40c4be0-75ac-4db5-a907-25d32d76541a)
### Predict Paper
 ![WhatsApp Image 2025-05-11 at 10 03 37_94dd7cfa](https://github.com/user-attachments/assets/0d55b788-bfaf-4c76-ab5a-b056295252d7)

### Predict Rock
 ![WhatsApp Image 2025-05-11 at 10 06 32_15c836fd](https://github.com/user-attachments/assets/9e3cf35f-6bb7-4e45-9e97-58ae86211d45)

### Predict Scissors
 ![WhatsApp Image 2025-05-11 at 10 08 25_b8b24168](https://github.com/user-attachments/assets/906fb7a0-b87c-4a10-ba63-2cae1cc6905d)


## 📝 Catatan Penting

1. **Model Sudah Dilatih**: Model sudah dilatih sebelumnya dan disimpan di folder `model/`. Tidak perlu melakukan training ulang.
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
