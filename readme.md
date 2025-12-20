# Comparative Analysis of CNNs vs. Vision Transformers on Chest X-Rays

## 📄 Abstract
This project conducts a comprehensive comparative analysis of **Convolutional Neural Networks (CNNs)** and **Vision Transformers (ViTs)** for the classification of thoracic diseases. Using the **VinDr-CXR (Adult)** and **VinDr-PCXR (Pediatric)** datasets, we evaluated state-of-the-art architectures including **ResNet, EfficientNet, ConvNeXt, Swin Transformer, and CoAtNet**.

Our findings indicate that while CNNs (like CoAtNet) excel in capturing fine-grained local features, Vision Transformers (like Swin) offer superior performance in modeling long-range dependencies, achieving competitive AUC scores across both multi-label and multi-class tasks.

---

## 🚀 Key Results

We implemented a robust training pipeline including **CLAHE preprocessing** and **Albumentations** for data augmentation.

### 1. Adult Dataset (VinDr-CXR) - Multi-Label
| Model | Accuracy | AUC | Precision |
| :--- | :--- | :--- | :--- |
| **Swin Transformer** | **95.22%** | **0.9328** | 0.5959 |
| **CoAtNet** | 95.09% | 0.9302 | **0.7021** |
| **ConvNeXt** | 95.43% | 0.9267 | 0.6999 |

### 2. Pediatric Dataset (VinDr-PCXR)
* **Multi-Label:** **CoAtNet** achieved the highest AUC of **0.7316**, slightly outperforming Swin Transformer (0.7259).
* **Multi-Class:** **PVT** and **EfficientNet** showed the highest accuracy (~67%), highlighting the difficulty of pediatric classification compared to adult X-rays.

*Full results table available in `assets/tables/Performance_Metrics.xlsx`.*

---

## 📂 Repository Structure

The repository contains representative notebooks for the top-performing models discussed in the thesis.

```text
CXR-Classification-ViT-vs-CNN/
│
├── assets/
│   ├── figures/
│   │   ├── architectures/   # Block diagrams of Swin, DaViT, CoAtNet, etc.
│   │   ├── statistics/      # Class distribution charts
│   │   └── preprocessing/   # Pipeline visualization
│   ├── samples/             # Sample X-rays from the datasets
│   └── tables/              # Raw result CSVs
│
├── docs/                    # Full Thesis PDF
│
├── notebooks/
│   ├── VinDr_CXR/           # Adult Dataset (Unbalanced Multi-label)
│   ├── VinDr_PCXR/          # Pediatric Dataset (Balanced & Unbalanced)
│
|    Model_Architectures.ipynb    # Contains all model definitions
|
└── README.md


```


## 📊 Dataset Overview
The study utilized two primary datasets with distinct label configurations tailored to the patient demographics.

### 1. Adult Dataset (VinDr-CXR)
**Configuration:** Unbalanced (Real-world distribution)
* **Target Labels (15 Classes):** 14 common thoracic abnormalities (including *Aortic enlargement, Cardiomegaly, Pleural effusion, Pulmonary fibrosis, etc.*) plus the 'No finding' class.

### 2. Pediatric Dataset (VinDr-PCXR)
**Configuration:** Balanced Subset
* To handle the extreme imbalance in pediatric data, we filtered the dataset to focus on the 6 most clinically significant classes:
    1.  **Bronchitis**
    2.  **Broncho-pneumonia**
    3.  **Bronchiolitis**
    4.  **Pneumonia**
    5.  **Other disease**
    6.  **No finding**

---

## 🧠 Model Architectures
We analyzed the internal mechanisms of both CNNs and ViTs. Click below to view the architectural details.

<details>
<summary><b>🔍 View Swin Transformer & DaViT (Vision Transformers)</b></summary>

| Swin Transformer (Shifted Windows) | DaViT (Dual-Attention Mechanism) |
| :---: | :---: |
| ![Swin](assets/figures/architectures/Swin_01_Overview.jpg) | ![DaViT](assets/figures/architectures/DaViT_01_Overview.jpg) |

</details>

<details>
<summary><b>🔍 View CoAtNet & ConvNeXt (Hybrid & Modern CNN)</b></summary>

| CoAtNet (Hybrid) | ConvNeXt (Pure CNN) |
| :---: | :---: |
| ![CoAtNet](assets/figures/architectures/CoAtNet_01_Overview.jpg) | ![ConvNeXt](assets/figures/architectures/ConvNeXt_01_Architecture.jpg) |

</details>

---

## 🖼️ Data Preprocessing Pipeline
We implemented a 3-stage preprocessing pipeline to enhance feature visibility in low-contrast X-rays:

| Step 1: Original | Step 2: CLAHE Enhancement | Step 3: Cropping & Resizing |
| :---: | :---: | :---: |
| ![Original](assets/figures/preprocessing/step1_original.jpg) | ![CLAHE](assets/figures/preprocessing/step2_clahe.jpg) | ![Final](assets/figures/preprocessing/step3_final.jpg) |

---

## 🛠️ Usage

To reproduce the experiments:

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/CellerCity/CXR-Classification-ViT-vs-CNN.git](https://github.com/CellerCity/CXR-Classification-ViT-vs-CNN.git)
    ```
2.  **Dataset Setup:**
    Ensure you have the VinDr-CXR or VinDr-PCXR datasets downloaded. Update the path in the notebook variables.
3.  **Run Experiment:**
    Open any notebook in `notebooks/` (e.g., `VinDr_CXR/Swin_CXR_Unbalanced_Multilabel.ipynb`). The training loop is self-contained.

---

## 👥 Contributors
* **Aman Nasim**
* Bobbili Sunny Rishy Vardhan
* Kalakonda Prudhvi Raj

*Supervised by Dr. Srilatha Chebrolu, NIT Andhra Pradesh (2024).*