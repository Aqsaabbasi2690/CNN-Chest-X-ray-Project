# Explainable Deep Learning for Pneumonia Detection from Chest X-ray Images

## 📖 Overview
Pneumonia is a serious respiratory infection and a leading cause of mortality worldwide, particularly in low-resource regions. Chest X-ray imaging is a primary diagnostic tool, but interpretation requires expert radiologists.

This project presents an **explainable deep learning system** for automated pneumonia detection from chest X-ray images using **DenseNet121** with transfer learning and Grad-CAM–based visual explanations.

---

## 🗂 Dataset
- Source: Kaggle – Chest X-ray Pneumonia Dataset
- Classes: Normal, Pneumonia
- Total images: 5,856
- Data split:
  - Training: ~85%
  - Validation: ~15% (created from training data)
  - Test: 624 images

> The original validation set was extremely small; therefore, a stratified validation split was used for stable evaluation.

---

## 🧠 Model Architecture
- Base model: DenseNet121 (ImageNet pretrained)
- Custom classifier:
  - Global Average Pooling
  - Dense (128 units, ReLU)
  - Dropout (0.5)
  - Sigmoid output layer

### Training Strategy
- Phase 1: Frozen DenseNet backbone
- Phase 2: Fine-tuning last 30 layers
- Optimizer: Adam
- Loss: Binary Cross-Entropy
- Class imbalance handled using class weights

---

## 📊 Evaluation Metrics
The model was evaluated using clinically relevant metrics:

- Accuracy
- Precision
- Recall (Sensitivity)
- Specificity
- F1-score
- ROC-AUC

### ✅ Test Set Performance
- Accuracy: **90.06%**
- Precision: **90.59%**
- Recall (Pneumonia): **93.85%**
- Specificity (Normal): **83.76%**
- Macro F1-score: **0.89**
- ROC-AUC: **~0.95**

High recall ensures pneumonia cases are rarely missed, which is critical in clinical screening scenarios.

---

## 🔍 Explainability (Grad-CAM)
To improve transparency and trust, **Grad-CAM** was used to visualize regions influencing the model’s predictions. The heatmaps highlight lung regions associated with pneumonia-related abnormalities.

This makes the model suitable as a **clinical decision-support system**, not a black-box classifier.

---

## ⚖️ Ethical Considerations
This system is intended to assist healthcare professionals and should not replace medical judgment. Explainability and performance trade-offs were carefully considered to minimize diagnostic risk.

---

## ⚠️ Limitations
- Dataset is limited to a single source
- No external clinical validation
- X-ray interpretation can be ambiguous even for experts

---

## 🔮 Future Work
- Multi-class disease classification
- External dataset validation
- Integration with clinical workflows
- Comparison with EfficientNet architectures

---

## 🛠 Technologies Used
- Python
- TensorFlow / Keras
- DenseNet121
- OpenCV
- Scikit-learn
- Matplotlib / Seaborn

---

## 📌 Author
**Aqsa Abbasi**  

