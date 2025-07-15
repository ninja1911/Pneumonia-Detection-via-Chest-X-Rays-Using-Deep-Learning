# Pneumonia Detection via Chest X-Rays Using Deep Learning

**Course**: DATA 255 Deep Learning Technologies, San Jose State University  
**Instructor**: Dr. Simon Shim  
**Date**: December 09, 2024  
**Full Report**: [Pneumonia Detection_Report.pdf](./Pneumonia%20Detection_Report.pdf) :contentReference[oaicite:0]{index=0}  

---

## 🚀 Highlights for Recruiters

- **Accuracy**: Up to 97 – 98% across state-of-the-art architectures (InceptionV3, ResNet50, CheXNet).  
- **Explainable AI**: Integrated SHAP & LIME to visualize pixel-wise and superpixel-wise attributions.  
- **Ensemble Boost**: Weighted voting ensemble improved stability and edge-case performance.  
- **Clinical Impact**: Matches radiologist-level performance; deployable “second-opinion” tool.  

---

## 📁 Repository Structure

```text
Code_files_Submission_New/
├── Pneumonia_Detection_Report.pdf
├── ResNet50/
│   ├── ResnetDLProj_v2.ipynb
│   └── Resnet50_model.pth
├── Inception_V3/
│   ├── inception_V2.ipynb
│   └── chest_xray_inceptionv3.pth
├── CNN_Basic/
│   ├── CNN_Basic_V2.ipynb
│   └── CNN_Basic_best_model.pth
├── CNN_Improved/
│   ├── CNN_Improved_64b_V2.ipynb
│   ├── CNN_Improved_16b_32b_V2.ipynb
│   └── CNN_improved_best_model.pth
├── CheXNet/
│   ├── chexnet-v2.ipynb
│   └── chexnet_model_V2.pth
└── Ensemble/
    └── X_ray_pneumonia_preprocessing_and_XAI_V4.ipynb
```


---

## 📊 Dataset & Preprocessing

- **Source**: Guangzhou Women’s & Children’s Medical Center pediatric X-rays (ages 1–5), Kaggle.  
- **Total Images**: 5,863 (Normal vs. Pneumonia) :contentReference[oaicite:2]{index=2}  
- **Original Split**  
  - Train: 1,341 Normal / 3,875 Pneumonia  
  - Test: 234 Normal / 390 Pneumonia  
  - Validation: 8 each :contentReference[oaicite:3]{index=3}  
- **Redistributed Split**  
  - Train: 70% (4,099 images)  
  - Val: 15% ( 878 images)  
  - Test: 15% ( 879 images)  
  - Maintained ~74% Pneumonia / 26% Normal balance.  
- **Transformations**  
  - Resize → 256×256 px  
  - Grayscale → 3-channel RGB  
  - Normalize pixel values to [–1, 1] :contentReference[oaicite:4]{index=4}  
- **Class Weights** (to correct imbalance)  
  - Pneumonia: 0.6852  
  - Normal:    1.8497  

---

## 🧠 Models & Results

| Model          | Accuracy | Precision (N / P) | Recall (N / P) | F1-Score (N / P) |
| -------------- | -------- | ----------------- | -------------- | ---------------- |
| **CNN_Basic**  | 96%      | 0.93 / 0.98       | 0.94 / 0.98    | 0.94 / 0.98      |
| **InceptionV3**| 97%      | 0.96 / 0.97       | 0.92 / 0.98    | 0.94 / 0.98      |
| **ResNet50**   | 97%      | 0.96 / 0.97       | 0.91 / 0.99    | 0.94 / 0.98      |
| **CheXNet**    | 97%      | 0.92 / 0.99       | 0.97 / 0.97    | 0.95 / 0.98      |
| **Ensemble**   | **98%+** | **0.97 / 0.99**   | **0.94 / 0.99**| **0.96 / 0.99**  |

> *Metrics reported on held-out test set* :contentReference[oaicite:5]{index=5}

---

## 🔍 Explainable AI (XAI)

- **SHAP**: Pixel-wise attribution (red → Pneumonia, blue → Normal).  
- **LIME**: Superpixel highlights (yellow outlines critical regions).  
- **Value**: Enables radiologists to audit AI decisions and build trust in automated diagnoses.  
