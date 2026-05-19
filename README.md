[README.md](https://github.com/user-attachments/files/28028379/README.md)
# 🫁 ChestX Triage Using Transfer Learning

## 📘 Project Overview

This project uses **Transfer Learning** to classify public chest X-ray images and translate model outputs into a simple review workflow.

The project focuses on three classes:

- **No Finding**
- **Nodule**
- **Effusion**

The goal is to show how a computer vision model can support a human-review workflow by surfacing:

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

For this portfolio project, I used a smaller balanced sample of selected labels to keep training lightweight and notebook-friendly.

Target classes:

- No Finding
- Nodule
- Effusion

---

## 🧠 Data Preparation

Images were:

- Loaded from the public NIH Chest X-ray dataset
- Filtered to selected single-label classes
- Balanced by class using a fixed sample size
- Resized to **224×224 pixels**
- Converted into NumPy arrays
- Normalized to pixel values between 0 and 1
- Split into training and validation datasets

### Hyperparameters

```python
IMG_SIZE = 224
BATCH_SIZE = 32
EPOCHS = 5
SAMPLE_PER_CLASS = 300
```

---

## 🏗️ Model Development

The model uses **MobileNetV2**, a pre-trained convolutional neural network trained on ImageNet.

The base model is frozen to retain pre-learned image features. Custom classification layers are added on top.

### Model Architecture

- Pre-trained MobileNetV2 base
- GlobalAveragePooling2D
- Dense(256, activation='relu')
- BatchNormalization
- Dropout(0.3)
- Dense(128, activation='relu')
- Dropout(0.2)
- Dense(3, activation='softmax')

### Model Compilation

```python
model.compile(
    optimizer=tf.keras.optimizers.Adam(learning_rate=0.0001),
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)
```

---

## 📊 Model Evaluation

The notebook evaluates the model using:

- accuracy
- precision
- recall
- F1 score
- confusion matrix
- sample prediction confidence

Because this is a health-related classification workflow, recall and false-negative review are especially important.

---

## 🖥️ Product Translation

The notebook also includes a simple product logic layer:

```text
prediction + confidence → review priority
```

Example:

- High confidence + higher-severity label → high review priority
- Lower confidence → manual review
- No Finding → audit sample

This turns the model from a pure classifier into a product workflow.

---

## ⚠️ Disclaimer

This project is for educational and portfolio purposes only. It is not a medical device, diagnostic system, or clinical decision-making tool.

Any real-world medical use would require clinical validation, expert review, privacy assessment, regulatory review, and extensive safety testing.

---

## 🚀 Future Improvements

- Train on a larger image subset
- Add multi-label classification
- Add Grad-CAM visual explanations
- Add model calibration
- Add active learning for uncertain cases
- Add radiologist feedback simulation
- Add fairness and subgroup analysis
- Build a full Streamlit review dashboard
