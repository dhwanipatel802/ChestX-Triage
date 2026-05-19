# 🫁 ChestX Triage Using Transfer Learning

## 📘 Project Overview

This project uses **Transfer Learning** to classify public chest X-ray images and translate model outputs into a simple human-review workflow.

The project focuses on three classes:

- **No Finding**
- **Nodule**
- **Effusion**

The goal is to show how a computer vision model can support triage by surfacing:

- predicted finding
- confidence score
- review priority
- model performance
- cases that may require additional review

This is an educational portfolio project and is **not** intended for diagnostic use.

---

## 🔍 Understanding Transfer Learning

Transfer Learning allows us to reuse the convolutional layers of a model trained on a large dataset, such as ImageNet, and apply that visual knowledge to a new image classification problem.

In Convolutional Neural Networks, early layers learn general visual features such as edges, gradients, textures, and shapes. These learned features can be reused for related computer vision tasks, including chest X-ray classification.

For this project, a pre-trained CNN backbone is used as a feature extractor. Custom dense layers are added for the chest X-ray classification task.

---

## 🧰 Tools and Libraries Used

| Library | Purpose |
|---|---|
| Pandas | Metadata handling and data analysis |
| NumPy | Numerical computations |
| Matplotlib | Data visualization |
| OpenCV | Image processing and resizing |
| scikit-learn | Data splitting, preprocessing, and model evaluation |
| TensorFlow / Keras | Transfer learning and deep learning model development |
| KaggleHub | Downloading the public Kaggle dataset into Colab |

---

## 📦 Dataset Information

**Dataset:** NIH Chest X-ray Dataset  
**Source:** Kaggle / NIH Clinical Center  
**Images:** 112,120 chest X-ray images  
**Patients:** 30,805 unique patients  
**Labels:** 14 thoracic disease labels plus No Finding

For this portfolio project, I use a smaller balanced sample of selected labels to keep training lightweight and notebook-friendly.

Target classes:

- No Finding
- Nodule
- Effusion

---

## 🖼️ Visual Outputs

The notebook includes visual outputs for:

- sample X-ray image grid
- class distribution chart
- training accuracy and loss curves
- confusion matrix
- product workflow diagram

---

## ⚠️ Disclaimer

This project is for educational and portfolio purposes only. It is not a medical device, diagnostic system, or clinical decision-making tool.

Any real-world medical use would require clinical validation, expert review, privacy assessment, regulatory review, and extensive safety testing.
