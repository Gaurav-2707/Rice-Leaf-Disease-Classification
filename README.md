# Rice Leaf Disease Classification Using Deep Learning 🌾

> **A Comparative Study of Custom CNN and Pre-trained Models**

## 📖 Overview
Rice is one of the most critical staple crops worldwide, yet it is highly susceptible to leaf diseases that significantly reduce agricultural yield. Early and accurate detection of these diseases is essential for timely intervention. 

This repository contains the codebase and experimental results for a comprehensive comparative study of deep learning models for automated rice leaf disease classification. We designed a custom Convolutional Neural Network (CNN) from scratch and benchmarked it against five widely adopted pre-trained architectures fine-tuned via transfer learning.

### Diseases Classified:
1. **Bacterial Leaf Blight (BLB)**
2. **Brown Spot (BS)**
3. **Leaf Smut (LS)**

---

## 🚀 Key Contributions
1. **Custom CNN Baseline:** Designed and evaluated a custom 3-block CNN trained from scratch.
2. **Transfer Learning Benchmark:** Fine-tuned and systematically compared 5 pre-trained models: `ResNet18`, `VGG16`, `EfficientNet-B0`, `DenseNet121`, and `MobileNetV2`.
3. **Quantitative Analysis:** Evaluated models using accuracy, precision, recall, F1-score, confusion matrices, and loss/accuracy curves.
4. **Architecture Recommendations:** Provided insights into why dense feature reuse (DenseNet) excels on small-scale agricultural imaging tasks.

---

## 📊 Experimental Results

We evaluated all models on a 70/15/15 (Train/Validation/Test) split over 10 epochs. 

| Rank | Model | Test Accuracy | Params | Speed | Edge-Ready |
|:---:|:---|:---:|:---:|:---:|:---:|
| 🏆 **1** | **DenseNet121** | **100.0%** | 7.0M | Moderate | Yes |
| 🥈 **2** | **ResNet18** | **94.4%** | 11.2M | Fast | Moderate |
| 🥉 **3** | **EfficientNet-B0** | **88.9%** | 5.3M | Fast | Yes |
| 4 | MobileNetV2 | 66.7% | 3.4M | Fastest | Yes |
| 5 | Custom CNN | 61.1% | ~25.7M | Fast | No |
| 5 | VGG16 | 61.1% | 138.4M | Slow | No |

### Key Findings:
* **DenseNet121** achieved perfect test accuracy (100%), proving that dense connectivity and feature reuse are highly effective for preserving fine-grained lesion texture and color cues on smaller datasets.
* **ResNet18** provided a very strong trade-off between accuracy (94.4%) and efficiency.
* Larger parameter counts do not guarantee better transfer learning outcomes on limited data; **VGG16** performed poorly (61.1%), tying with the scratch-trained Custom CNN.

---

## 🗂️ Dataset
The project utilizes the public [Rice Leaf Diseases Dataset](https://www.kaggle.com/datasets/vbookshelf/rice-leaf-diseases) from Kaggle.

**Data Augmentation applied during training:**
* Random Resized Crop (224x224)
* Random Horizontal Flip (p=0.5)
* Random Rotation (±15°)
* Color Jitter (Brightness/Contrast ±0.2)
* ImageNet Normalization

---

## ⚙️ Hyperparameter Configuration
* **Input Image Size:** 224 x 224
* **Batch Size:** 16
* **Epochs:** 10
* **Optimizer:** Adam ($\beta_1$ = 0.9, $\beta_2$ = 0.999)
* **Loss Function:** Cross-Entropy Loss
* **Learning Rate:** 
  * Custom CNN: $1 \times 10^{-3}$ 
  * Pre-trained Models: $1 \times 10^{-4}$
* **Hardware:** CUDA-enabled NVIDIA GPU

---
