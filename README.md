# EEE385L_Project_BI-RADS-Classification
# 🩺 Breast Cancer Classification using Deep Learning on KAUMDS Dataset

This project implements deep learning models to classify mammogram images into BI-RADS categories using the King Abdulaziz University Medical Dataset (KAUMDS). We explore both custom and pretrained models (CNN, ResNet50, EfficientNetB0, MobileNetV2) to support clinical decision-making in early breast cancer detection.

---
## 🙋 Author 
| Name                        | Email                                                                         |
| --------------------------- | ----------------------------------------------------------------------------- |
| Mohammad Fasiul Abedin Khan | [fasiul.abedin.khan@g.bracu.ac.bd](mailto:fasiul.abedin.khan@g.bracu.ac.bd)   |
| Farrdin Nowshad             | [farrdin.nowshad@g.bracu.ac.bd](mailto:farrdin.nowshad@g.bracu.ac.bd)         |
| Abrar Maksud Nahean         | [abrar.maksud.nahean@g.bracu.ac.bd](mailto:abrar.maksud.nahean@g.bracu.ac.bd) |
| MD. Abu Anas Mridul         | (Email not provided)                                                          |


## 📊 Project Overview

- **Objective:** Automate BI-RADS classification (1, 3, 4, 5) using mammogram images.
- **Dataset:** King Abdulaziz University Mammogram Dataset  
  DOI: [10.21227/a4cs-ax02](https://dx.doi.org/10.21227/a4cs-ax02)
- **Challenges:** Class imbalance, low-data learning, explainability
- **Highlights:**
  - Four deep learning models compared
  - Data augmentation and class weights applied
  - Evaluation with class-sensitive metrics
  - Grad-CAM visualization (for interpretability)

---

## 🗂️ Dataset Details

The KAUMDS dataset includes:
- Over 6,000 mammogram images
- BI-RADS classes:  
  - **1:** Normal  
  - **3:** Probably Benign  
  - **4:** Suspicious  
  - **5:** Highly Suggestive of Malignancy  
- Views: CC and MLO  
- Format: JPEG images + Excel-based metadata

---

## 🧠 Model Architectures

| Model           | Type        | Key Layers                        | Parameters |
|----------------|-------------|-----------------------------------|------------|
| CNN Baseline    | Custom      | Conv2D + BatchNorm + Dropout      | ~1.2M      |
| ResNet50        | Pretrained  | Residual Blocks + GAP + Dense     | ~23M       |
| EfficientNetB0  | Pretrained  | Compound Scaled CNN               | ~5M        |
| MobileNetV2     | Pretrained  | Depthwise Separable Conv + Dense  | ~3.4M      |

---

## ⚙️ Training Details

- **Train/Val/Test Split:** 75% / 15% / 10%
- **Input Size:** 224x224 RGB
- **Loss Function:** Sparse Categorical Crossentropy
- **Optimizer:** Adam with learning rate scheduling
- **Regularization:** Dropout, BatchNorm, Early Stopping
- **Augmentation:** Horizontal flipping, brightness, rotation
- **Class Imbalance Handling:** Class Weights, Oversampling

---

## 📈 Performance Summary

| Model         | Accuracy | Macro F1 | Weighted F1 |
|---------------|----------|----------|-------------|
| CNN Baseline  | 82%      | 0.51     | 0.84        |
| ResNet50      | 12%      | 0.05     | 0.03        |
| EfficientNetB0| 84%      | 0.23     | 0.76        |
| MobileNetV2   | **88%**  | **0.65** | **0.89**    |

---

## 📊 Evaluation Metrics

- **Accuracy**
- **Precision, Recall, F1-score (Macro & Weighted)**
- **Confusion Matrix**
- **ROC-AUC**
- **Grad-CAM Visualizations**

---

## 📌 Ablation Studies

| Change                  | Result                       |
|-------------------------|------------------------------|
| No BatchNorm            | ~10% drop in accuracy         |
| No Dropout              | Increased overfitting         |
| No Data Augmentation    | Poor generalization observed  |

---

## 🔍 Error Analysis

- BI-RADS 3 was often confused with BI-RADS 4.
- BI-RADS 5 (malignant) was rarely predicted due to low representation.
- Misclassifications reflect dataset imbalance and visual similarity in dense tissue.

---

---

## 🚀 Getting Started

```bash
# Clone this repository
git clone https://github.com/your-org/breast-cancer-birads-kaumds.git
cd breast-cancer-birads-kaumds

# Install required packages
pip install -r requirements.txt

# Launch the training pipeline
jupyter notebook main_pipeline.ipynb
```

## 📄 License
This project is licensed under the MIT License.
See the LICENSE file for full license information.



## 📬 Contact
For questions, feel free to contact any of the contributors.
We welcome collaboration and suggestions!



