# Glaucoma Detection (HYGD) 👁️

Binary classifier detecting glaucoma from retinal fundus images using deep learning. Trained and compared two architectures — a custom CNN and MobileNetV2 transfer learning — with Grad-CAM explainability overlays.

## Results

| Model | Val Accuracy | Epochs |
|---|---|---|
| Custom CNN (scratch) | **92.6%** | 10 |
| MobileNetV2 (transfer learning) | **98.7%** | 10 |

## Dataset

**Hillel-Yaffe Dataset for Glaucoma Detection**
- Source: [Kaggle](https://www.kaggle.com/datasets/bharathry/hillel-yaffe-dataset-for-glaucoma-detection)
- Classes: `Glaucoma`, `Normal`
- Clinical retinal fundus images

## Models

### Model 1 — Custom CNN (from scratch)



Input (256×256×3)
→ Conv2D(32) → MaxPool
→ Conv2D(64) → MaxPool
→ Conv2D(128) → MaxPool
→ Flatten → Dense(64) → Dense(1, sigmoid)


### Model 2 — MobileNetV2 (transfer learning)
- Pretrained on ImageNet, top layers frozen
- Custom classification head: Dense(64) → Dense(1, sigmoid)
- 10 epochs, binary cross-entropy loss

## Explainability — Grad-CAM

Gradient-weighted Class Activation Mapping (Grad-CAM) applied to MobileNetV2's final convolutional layer (`out_relu`) to generate visual heatmaps highlighting regions influencing the glaucoma prediction.

## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat&logo=keras&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=flat&logo=googlecolab&logoColor=white)

- **TensorFlow / Keras** — Model training
- **OpenCV + Matplotlib** — Image processing & visualization
- **Grad-CAM** — Explainable AI (XAI)
- **Kaggle API** — Dataset download

## Run on Google Colab

1. Open the notebook in Google Colab
2. Add your Kaggle API token
3. Run all cells in order

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/gorap50/glaucoma-detection/blob/main/HYGD.ipynb)
