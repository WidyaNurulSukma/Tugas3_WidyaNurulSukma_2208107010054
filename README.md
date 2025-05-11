# Rock-Paper-Scissors Classification Project 🪨📄✂️

## 📚 Project Description

This project builds a simple image classification system using **Deep Learning** with **Transfer Learning** architecture (MobileNetV2). The system classifies images into three categories: **Rock**, **Paper**, and **Scissors**.

The trained model is integrated into a **FastAPI**-based backend application, enabling real-time image prediction through an API.

## 🛠️ Technologies Used

- **TensorFlow / Keras** — Building and training the image classification model
- **FastAPI** — Creating the REST API backend
- **Uvicorn** — ASGI server for running FastAPI
- **PIL (Pillow)** — Image processing
- **NumPy** — Numerical data manipulation
- **scikit-learn** — Model evaluation (classification report, confusion matrix)

## 📂 Project Structure

```
project-root/
├── backend/
│   └── main.py         # FastAPI backend code
├── model/
│   └── best_transfer.h5 # Saved trained model
├── dataset/
│   ├── rock/
│   ├── paper/
│   └── scissor/
├── README.md
└── requirements.txt
```

## 🚀 Getting Started

### Clone the repository
```bash
git clone https://github.com/WidyaNurulSukma/Tugas3_WidyaNurulSukma_2208107010054.git
cd rock-paper-scissors-classifier
```

### Set up virtual environment
```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# For Windows:
venv\Scripts\activate
# For macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### Dataset
Download the dataset from Kaggle:  
🔗 [Rock-Paper-Scissors Dataset – Kaggle](https://www.kaggle.com/datasets/drgfreeman/rockpaperscissors)

After downloading and extracting, organize the dataset into folders:
```
dataset/
    rock/
    paper/
    scissor/
```

### Running the Application

The model has been pre-trained, so you can immediately run the application:

#### Run the FastAPI backend:
```bash
cd backend
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

#### Run the Streamlit frontend:
```bash
cd frontend
streamlit run app.py
```

The Streamlit application will run at `http://localhost:8501/`, and the backend API will run at `http://localhost:8000/`.

## 📊 Model Evaluation Results

The model has been evaluated with good performance. Evaluation results can be found in the `results/evaluation/` folder:

- **Confusion Matrix**: Visualization of prediction errors between classes
- **Classification Report**: Precision, recall, and f1-score metrics for each class
- **Training History**: Accuracy and loss graphs during the training process

### Model Performance Summary

- **Accuracy**: ~97% on validation dataset
- **Precision & Recall**: >95% for all classes
- **F1-Score**: >95% average

## 📱 Application Interface

The application has a user-friendly and intuitive interface. Screenshots can be found in the `results/screenshots/` folder.

## 📝 Important Notes

1. **Pre-trained Model**: The model has been pre-trained and saved in the `model/` folder. No need to retrain.
2. **Consistent Preprocessing**: The backend is configured with the same preprocessing as during training.
3. **Model Path**: Ensure the model path in `backend/main.py` points to the correct model file location.
4. **Dependencies**: Make sure TensorFlow and Keras versions are compatible to avoid issues when loading the model.
5. **CORS**: The backend is configured to accept requests from the Streamlit frontend.

## 💡 Technical Model Explanation

The model uses MobileNetV2 as the base model with transfer learning, followed by several fully connected layers for classification. Model configuration:

- Input size: 224x224x3
- Base model: MobileNetV2 (pre-trained on ImageNet)
- Custom layers: GlobalAveragePooling2D, Dense(128, ReLU), Dropout(0.5), Dense(3, Softmax)
- Optimizer: Adam with learning rate 0.001
- Loss function: Categorical Cross-Entropy

## 👨‍💻 Contributors

* Widya Nurul Sukma - widyasukma934@gmail.com

## 📜 License

This project is licensed under the MIT License.
