# 🧠 Brain Tumor Detection System

A deep learning-powered web application that classifies brain MRI scans to detect the presence of tumors. Built with a fine-tuned VGG19 convolutional neural network and served through a Flask web interface.

---

## 📌 Overview

Brain tumor detection from MRI images is a critical and time-sensitive task in medical diagnosis. This project automates the classification process using transfer learning on the VGG19 architecture, allowing users to upload an MRI image and receive an instant prediction — **Tumor Detected** or **No Tumor Detected**.

---

## ✨ Features

- Upload brain MRI images directly through the web interface
- Instant binary classification: tumor vs. no tumor
- Transfer learning using pre-trained VGG19 (ImageNet weights)
- Custom classification head with dropout regularization
- Lightweight Flask backend for easy local deployment

---

## 🗂️ Project Structure

```
Brain_Tumor_Detection_System/
│
├── Tumor_Dataset/          # MRI image dataset (tumor / no tumor)
├── flagged/                # Flagged/logged prediction outputs
├── static/                 # CSS, JS, and other static assets
├── tempelates/             # HTML templates for the Flask app
├── uploads/                # Temporarily stores uploaded images
│
├── Advance DL Project Brain Tumor Image Classification.ipynb
│                           # Jupyter notebook: model training & evaluation
├── app.py                  # Flask application entry point
├── vgg_unfrozen.h5         # Trained model weights (required, not in repo)
└── README.md
```

---

## 🧬 Model Architecture

The model uses **VGG19** as a feature extractor (pre-trained on ImageNet, top layers excluded), with a custom classification head:

```
VGG19 (base, frozen) → Flatten → Dense(4608, ReLU) → Dropout(0.2) → Dense(1152, ReLU) → Dense(2, Softmax)
```

Input image size: **240 × 240 × 3 (RGB)**  
Output classes: `0` → No Brain Tumor, `1` → Brain Tumor Detected

---

## 🛠️ Tech Stack

| Component       | Technology                        |
|-----------------|-----------------------------------|
| Deep Learning   | TensorFlow / Keras                |
| Base Model      | VGG19 (ImageNet weights)          |
| Image Processing| OpenCV, Pillow                    |
| Web Framework   | Flask                             |
| Frontend        | HTML / CSS / JavaScript           |
| Notebook        | Jupyter                           |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.7+
- pip

### 1. Clone the Repository

```bash
git clone https://github.com/bittuprojs/Brain_Tumor_Detection_System.git
cd Brain_Tumor_Detection_System
```

### 2. Install Dependencies

```bash
pip install tensorflow keras flask opencv-python pillow numpy werkzeug
```

### 3. Add Model Weights

Place the trained weights file `vgg_unfrozen.h5` in the project root directory. You can generate it by running the training notebook:

```
Advance DL Project Brain Tumor Image Classification.ipynb
```

### 4. Run the Application

```bash
python app.py
```

Then open your browser and navigate to:

```
http://127.0.0.1:5000/
```

### 5. Use the App

1. Click **Choose File** and select a brain MRI image (JPG/PNG).
2. Click **Predict**.
3. The result will display: `No Brain Tumor` or `Yes Brain Tumor`.

---

## 📊 Dataset

The `Tumor_Dataset/` directory contains MRI scan images organized for binary classification:

- **Tumor** — images confirmed to contain a brain tumor
- **No Tumor** — healthy brain MRI scans

> If you are using a public dataset, consider citing [Kaggle Brain MRI Images for Brain Tumor Detection](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection) or similar sources.

---

## 📁 API Endpoints

| Route      | Method     | Description                              |
|------------|------------|------------------------------------------|
| `/`        | GET        | Renders the upload/home page             |
| `/predict` | GET, POST  | Accepts image upload and returns result  |

---

## ⚠️ Disclaimer

This project is intended for **educational and research purposes only**. It is not a substitute for professional medical diagnosis. Always consult a qualified medical professional for clinical decisions.

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📄 License

This project is open source. Please add a `LICENSE` file to specify usage terms.

---

## 👤 Author

**bittuprojs** — [GitHub Profile](https://github.com/bittuprojs)
