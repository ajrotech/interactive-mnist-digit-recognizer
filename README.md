# Interactive MNIST Digit Recognizer

An interactive, full-stack web application that allows users to draw handwritten digits on a canvas or upload digital images to see real-time classification predictions. This project features a high-accuracy Convolutional Neural Network (CNN) built with TensorFlow/Keras and served via a lightweight Flask REST API.

---

## 🚀 Features

* **Interactive Drawing Canvas**: Draw numbers from `0` to `9` directly in your web browser with smooth mouse or touch controls.
* **Image Upload Support**: Upload raw digit images (like those from the Kaggle MNIST dataset) to evaluate the model's prediction accuracy.
* **High-Accuracy CNN Classifier**: Features a pre-trained Convolutional Neural Network (CNN) utilizing Max Pooling and Dropout layers, trained directly on the classic MNIST database to achieve **~98.5% validation accuracy**.
* **Real-Time Predictions**: Instantly shows the classified digit along with the network's statistical confidence level.
* **Auto-Fallback Training**: If no pre-trained weights are present, the backend automatically boots an optimized training cycle (~15 seconds) to construct and save a fresh CNN model.

---

## 🛠️ Tech Stack & Architecture

The application is split into a decoupled frontend and backend:

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Frontend** | HTML5 Canvas, CSS3, Vanilla JavaScript | Interactive UI, canvas vector drawing, and `fetch`-based asynchronous API requests. |
| **Backend** | Python, Flask, Flask-CORS | Handles API routing, CORS preflight checks, and receives base64/blob image streams. |
| **ML Engine** | TensorFlow (Keras), Pillow, NumPy | Preprocesses input matrices (resizing to 28x28, converting to grayscale, inversion thresholds) and executes model forward passes. |

---

## 📂 Project Structure

```text
Project-01/
├── app.py                 # Flask Server & TensorFlow Inference/Training Pipeline
├── index.html             # Front-end Interactive UI & Canvas Drawing Module
├── mnist_model.keras      # Saved weights of the high-accuracy trained CNN model
└── README.md              # Documentation
```

---

## ⚙️ Installation & Setup

Follow these steps to run this application locally on your machine.

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/mnist-digit-recognizer.git
cd mnist-digit-recognizer
```

### 2. Set Up a Python Virtual Environment
Keep your system packages clean by creating an isolated virtual environment:
```bash
# Create the virtual environment
python3 -m venv venv

# Activate the virtual environment (Linux/macOS)
source venv/bin/activate

# Activate the virtual environment (Windows)
# venv\Scripts\activate
```

### 3. Install Dependencies
Install all required machine learning and web server packages:
```bash
pip install --upgrade pip
pip install flask flask-cors pillow tensorflow numpy
```

### 4. Run the Application

Start the Flask backend server:
```bash
python app.py
```
On the first run, the backend will automatically download the MNIST dataset, train a highly accurate CNN model (takes ~15 seconds), and save it locally as `mnist_model.keras`. Subsequent boots will load this model instantly.

### 5. Launch the Frontend
You do **not** need to host the frontend on a web server. 
Simply navigate to your directory and open the **`index.html`** file directly in any modern web browser (Double-click the file or drag it into Chrome/Firefox).

---

## 🧠 Neural Network Architecture

The backend implements a deep Convolutional Neural Network designed to handle spatial variations in handwritten lines:

1. **Conv2D**: 32 filters, 3x3 kernel, ReLU activation. Identifies basic edges and corners.
2. **MaxPooling2D**: 2x2 pool size. Reduces spatial dimension and ensures translation invariance.
3. **Conv2D**: 64 filters, 3x3 kernel, ReLU activation. Extracts complex spatial features.
4. **MaxPooling2D**: 2x2 pool size.
5. **Flatten**: Flattens structural matrices into a single-dimension array.
6. **Dense (Hidden)**: 128 units, ReLU activation. Fully connected layer for pattern classification.
7. **Dropout (0.2)**: Regularization layer to prevent overfitting.
8. **Dense (Output)**: 10 units, Softmax activation. Yields probability distributions over classes `0` through `9`.

---

## 🖼️ Screenshots

Below is a look at the live user interface in action:

| Interactive Drawing & Prediction | Real-Time Response |
| :---: | :---: |
| Drawing canvas with white-on-black brush strokes | Instant classification prediction with confidence stats |
<img width="1182" height="655" alt="image" src="https://github.com/user-attachments/assets/205550b6-04a7-4c70-9bc6-20ffa631b222" />


---

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to fork this repository, make changes, and submit a Pull Request.
