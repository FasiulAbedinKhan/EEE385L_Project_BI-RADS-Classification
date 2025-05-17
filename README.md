# EEE385L_Project_BI-RADS-Classification
#  BI-RADS Classification Using Deep Learning

This project applies deep learning models to classify mammogram images into BI-RADS categories (1, 3, 4, 5), aiding in early breast cancer detection. We compare a custom CNN against pretrained architectures including ResNet50, EfficientNetB0, and MobileNetV2. Our best-performing model, MobileNetV2, achieved 88% accuracy on local Saudi medical imaging data.

---

## Dataset

- **KAUMDS Dataset**
- Mammogram images with labels: BI-RADS 1, 3, 4, 5
- Resized to `224x224`, normalized
- 75% training, 15% validation, 10% testing split

---

##  Models Compared

| Model           | Accuracy | Macro F1 | Macro Precision | Macro Recall | Weighted F1 | Weighted Precision | Weighted Recall |
|----------------|----------|----------|------------------|---------------|-------------|---------------------|------------------|
| **CNN**        | 0.82     | 0.51     | 0.47             | 0.60          | 0.84        | 0.87                | 0.82             |
| **ResNet50**   | 0.12     | 0.05     | 0.03             | 0.24          | 0.03        | 0.01                | 0.12             |
| **EfficientNetB0** | 0.84 | 0.23     | 0.21             | 0.25          | 0.76        | 0.70                | 0.84             |
| **MobileNetV2** | **0.88** | **0.65** | **0.63**         | **0.69**      | **0.89**    | **0.91**            | **0.88**         |

---

##  Methodology

- **Preprocessing**: Resize, normalization, augmentation
- **Loss**: Categorical cross-entropy
- **Optimizer**: Adam
- **Metrics**: Accuracy, Precision, Recall, F1-score
- **Evaluation**: Confusion matrix, classification report, training/validation curves
- **Regularization**: Dropout, batch normalization

---

## 📊 Results Summary

- **MobileNetV2** was the best performer across all metrics.
- **CNN** gave strong baseline results and responded well to regularization.
- **ResNet50** underfit the small dataset and performed poorly.
- **EfficientNetB0** showed moderate precision but poor generalization.
- **Dropout Ablation** revealed the importance of regularization: without dropout, the CNN's accuracy dropped from 85% to 1%.

---

##  Ablation Studies

We turned off key components like Dropout to observe performance effects. The CNN without dropout overfit severely and achieved only 1% accuracy and 0.005 F1-score. The misclassified samples were visually similar and showed the model struggled to generalize without regularization.

---

##  Grad-CAM Insights (Unavailable)

Due to backend restrictions and frozen graph errors in TensorFlow, Grad-CAM visualizations failed during integration for several models. The models had no defined outputs during graph extraction, which hindered Grad-CAM generation. These issues stem from the model not being called with input shapes after loading or having incompatible layers for backprop.

---

##  Misclassification Analysis

- BI-RADS 3 and 4 often misclassified as each other due to subtle density differences.
- BI-RADS 5 (malignant) cases were occasionally misclassified as BI-RADS 1, indicating potential for real-world risk.
- MobileNetV2 performed the best at avoiding critical errors.

---

## How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/birads-classification.git
   cd birads-classification
