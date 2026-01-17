# 🧠 Brain Tumor Detection System Using Deep Learning

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?style=flat&logo=tensorflow)](https://www.tensorflow.org/)
[![Gradio](https://img.shields.io/badge/UI-Gradio-orange?style=flat)](https://gradio.app/)

## 📌 Project Overview
Brain tumors are complex conditions that require rapid and accurate diagnosis to improve patient survival rates. Manual analysis of MRI scans is time-consuming and prone to human error. This project provides an automated solution using a Convolutional Neural Network (CNN) based on the **ResNet50V2** architecture to classify images as "Tumor" or "No Tumor".

---

## 🛠️ Methodology & Architecture
Our system follows a four-stage pipeline: **Data Preprocessing**, **Data Augmentation**, **Model Training**, and **Interface Deployment**.

### 1. Data Preprocessing
To handle noise and varying lighting, we implemented a robust workflow:
* **Non-Local Means (NLM) Denoising:** Removes noise while preserving critical edge details essential for tumor boundaries.
* **CLAHE Enhancement:** Applied to the LAB color space to highlight textures and contrast without distorting original colors.



### 2. Data Augmentation
Dynamic augmentation is used during training to prevent overfitting and improve the model's ability to generalize to new data:
* **Random Flip:** Horizontal mirroring.
* **Random Rotation:** ±15% rotation.
* **Random Zoom:** ±10% zoom.
* **Adjustments:** Random brightness and contrast tweaks.

### 3. Model Architecture (Transfer Learning)
* **Backbone:** Pre-trained **ResNet50V2** (using ImageNet weights) acts as the feature extractor.
* **Fine-Tuning:** The backbone was initially frozen, followed by un-freezing the top 40 layers for specialized medical imaging training.
* **Classification Head:** Includes GlobalAveragePooling2D, a Dense layer (256 units), BatchNormalization, and a Dropout layer (0.5) to ensure stability.



---

## 📊 Performance & Results
The model was evaluated on a held-out test set, demonstrating high diagnostic reliability and a strong ability to distinguish between classes.

| Metric | Result |
| :--- | :--- |
| **Accuracy** | ≈ 87% |
| **AUC Score** | 0.9168 |

> **Note:** High recall is prioritized in this system to ensure that potential tumors are not missed during initial screening.

### Confusion Matrix Breakdown
The detailed breakdown of the model's predictions:
* **True Positives (TP):** 30 (Tumors correctly identified)
* **True Negatives (TN):** 15 (Healthy scans correctly identified)
* **False Negatives (FN):** 1 (Critical error — missed tumor)
* **False Positives (FP):** 4 (Healthy brain flagged as tumor)



---

## 🖥️ User Interface
The system is deployed via a **Gradio** GUI, providing an accessible tool for medical professionals:
* **Drag-and-Drop:** Simple interface for uploading MRI images.
* **Real-time Processing:** The app applies the full preprocessing pipeline before providing a prediction.
* **Instant Output:** Displays "TUMOR DETECTED" or "NO TUMOR" with a confidence percentage.

---

