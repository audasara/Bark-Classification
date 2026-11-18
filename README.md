# Bark Classification

A deep learning research project for classifying tree bark images into **15 tree species** using image classification models. This repository documents the dataset setup, experimental workflow, model comparison, and statistical evaluation.

## Project Overview

The project investigates how different deep learning architectures recognize visual patterns and textures in tree bark images. Experiments are repeated with three random seeds (42, 123, and 2026) to assess performance and consistency.

### Key Information

| Item | Description |
|---|---|
| Task | 15-class tree bark image classification |
| Total images | 6,090 |
| Training | 3,705 images |
| Validation | 795 images |
| Final test | 795 images |
| Random seeds | 42, 123, 2026 |
| Main models | ResNet-E20, ConvNeXt-Tiny E20, Swin-T-E20 |

## Repository Structure

```text
Bark-Classification/
├── README.md
├── notebooks/
│   └── README.md              # Add training and evaluation notebooks here
├── src/
│   └── README.md              # Add reusable source code here
├── results/
│   └── README.md              # Add metric tables, CSV/XLSX, and statistical tests
├── figures/
│   └── README.md              # Add plots, confusion matrices, and prediction examples
└── requirements.txt           # Add the exact project dependencies
```

Large datasets and model checkpoints are kept outside this repository and linked separately.

## Dataset

The dataset is hosted on Google Drive.

| Dataset folder | Purpose | Images |
|---|---|---:|
| Bark\_runModel | Training and validation source | 4,500 |
| Bark\_Test\_53\_Final | Final test set | 795 |
| **Total** | | **5,295 source images** |

The 4,500 images in `Bark_runModel` are split into:
- Training: 247 images per class (3,705 images)
- Validation: 53 images per class (795 images)

The final test set contains 53 images per class (795 images).

### Google Drive

- [Bark Archive All](https://drive.google.com/drive/folders/1_F09BhlVYArv5J5o7Uc8iMxIQ7c-Hwz8?usp=sharing)
- [Bark RunModel](https://drive.google.com/drive/folders/1cdW8pJVxBrAp2VENX00sF0DRfs4DCD5h?usp=drive_link)
- [Bark Test 53 Final](https://drive.google.com/drive/folders/1skTNxEqCtxcTLbO9pNuYtL0GmbD2osdd?usp=drive_link)

### Classes

The dataset contains the following 15 species:

1. Alstonia scholaris
2. Cassia fistula
3. Delonix regia
4. Dipterocarpus alatus Roxb
5. Lagerstroemia duperreana
6. Lagerstroemia loudonii
7. Lagerstroemia macrocarpa
8. Peltophorum dasyrhachis
9. Peltophorum pterocarpum
10. Pterocarpus indicus
11. Pterocarpus macrocarpus
12. Streblus asper
13. Swietenia macrophylla
14. Tectona grandis
15. Triplaris cumingiana Fisch

## Models

The experiments compare three main architectures:

| Model | Architecture family | Role |
|---|---|---|
| ResNet-E20 | Residual CNN | CNN baseline |
| ConvNeXt-Tiny E20 | Modern CNN | CNN comparison |
| Swin-T-E20 | Hierarchical Vision Transformer | Transformer comparison |

**EfficientNetV2-S** is also used as a comparator in the paired McNemar statistical analysis.

### Short model descriptions

- **ResNet (Residual Network):** Uses residual/skip connections to help train deeper convolutional networks. It serves as a CNN baseline.
- **ConvNeXt-Tiny:** A modernized convolutional architecture that adopts design ideas from Vision Transformers while retaining convolution-based feature extraction.
- **Swin Transformer (Swin-T):** Uses shifted-window self-attention to learn local and broader visual relationships efficiently. Its hierarchical representation is useful for image recognition.
- **EfficientNetV2-S:** An efficient convolutional architecture included as the comparison model in the McNemar test.

## Experimental Setup

- Evaluation uses a held-out test set of **795 images**.
- Each main model is evaluated with random seeds **42, 123, and 2026**.
- The reported summary is the mean and standard deviation across the three seed runs.
- Each listed E20 experiment ran for 20 epochs.

## Results

### Main model comparison

**Test set: 795 images · Mean ± standard deviation across 3 seeds**

| Model | Macro-F1 (%) | Accuracy (%) |
|---|---:|---:|
| ResNet-E20 | 86.67 ± 1.39 | 87.00 ± 1.28 |
| ConvNeXt-Tiny E20 | 88.79 ± 1.18 | 89.56 ± 0.83 |
| **Swin-T-E20** | **93.00 ± 0.58** | **93.17 ± 0.48** |

Based on these experiments, **Swin-T-E20 achieved the highest mean Macro-F1 and Accuracy**, and showed the smallest standard deviation across the three seeds among the three main models.

### Detailed results by seed

| Model | Seed | Macro-F1 (%) | Accuracy (%) | Macro-Precision (%) | Macro-Recall (%) | AUC OvR macro (%) | MCC (%) | Training time (min) |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| ResNet-E20 | 42 | 87.84 | 87.92 | 90.33 | 87.92 | 99.54 | 87.25 | 2.48 |
| ResNet-E20 | 123 | 85.14 | 85.53 | 89.54 | 85.53 | 99.48 | 84.82 | 2.48 |
| ResNet-E20 | 2026 | 87.04 | 87.55 | 90.50 | 87.55 | 99.51 | 86.91 | 2.47 |
| ConvNeXt-Tiny E20 | 42 | 87.93 | 88.81 | 91.64 | 88.81 | 99.39 | 88.31 | 8.22 |
| ConvNeXt-Tiny E20 | 123 | 88.19 | 89.06 | 91.84 | 89.06 | 99.77 | 88.57 | 8.21 |
| ConvNeXt-Tiny E20 | 2026 | 90.26 | 90.82 | 93.36 | 90.82 | 99.38 | 90.41 | 8.21 |
| Swin-T-E20 | 42 | 92.83 | 92.96 | 94.41 | 92.96 | 99.95 | 92.58 | 8.89 |
| Swin-T-E20 | 123 | 93.65 | 93.71 | 95.01 | 93.71 | 99.97 | 93.37 | 8.91 |
| Swin-T-E20 | 2026 | 92.53 | 92.83 | 94.67 | 92.83 | 99.93 | 92.49 | 8.90 |

### Statistical comparison: McNemar's test

The latest Swin-T-E20 model was compared with EfficientNetV2-S using paired predictions on the same 795 test images for each seed. Holm adjustment was applied across the three seed-specific comparisons for this model pair.

| Seed | b (EfficientNet correct) | c (Swin-T correct) | Raw p-value | Holm-adjusted p-value | Conclusion |
|---:|---:|---:|---:|---:|---|
| 42 | 21 | 47 | 0.0024 | 0.0049 | Swin-T better |
| 123 | 19 | 53 | 0.0001 | 0.0003 | Swin-T better |
| 2026 | 25 | 44 | 0.0302 | 0.0302 | Swin-T better |

All three Holm-adjusted p-values are below 0.05. In these paired test comparisons, Swin-T-E20 made significantly better predictions than EfficientNetV2-S for each seed.

| Seed | EfficientNetV2-S Accuracy (%) | Swin-T-E20 Accuracy (%) | χ² (continuity corrected) |
|---:|---:|---:|---:|
| 42 | 89.6855 | 92.9560 | 9.1912 |
| 123 | 89.4340 | 93.7107 | 15.1250 |
| 2026 | 90.4403 | 92.8302 | 4.6957 |

## Evaluation Metrics

- **Accuracy:** Overall proportion of correctly classified test images.
- **Macro-Precision:** Precision averaged equally across the 15 classes.
- **Macro-Recall:** Recall averaged equally across the 15 classes.
- **Macro-F1:** F1-score averaged equally across the 15 classes.
- **Weighted-F1:** F1-score averaged by class support.
- **AUC OvR macro:** Macro-averaged one-vs-rest area under the ROC curve.
- **MCC:** Matthews correlation coefficient.
- **Confusion Matrix:** Shows correct and incorrect predictions by class.
- **McNemar's test:** Compares paired classification outcomes from two models on the same test samples.

## Run in Google Colab

The project notebook is available in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1QEju6fyMV0oWNzuMhuUpEWMIqM5UZDtF)

The notebook searches Google Drive for the dataset, validates the expected class folders and image counts, and supports nested ZIP folder structures. It stops at the dataset validation step if required folders or image counts do not match.

### Environment

- Google Colab GPU (NVIDIA T4 or higher recommended)
- Approximately 10 GB of available `/content` storage
- Internet access to download pretrained weights from Hugging Face
- Python libraries: `torch`, `timm`, `scikit-learn`, `scipy`, `pandas`, `matplotlib`, and `openpyxl`

The first notebook cell installs `timm` if it is not already available.

### Optional split verification

If available, place `split_manifest.csv` at:

`MyDrive/Bark_results/split_manifest.csv`

The notebook uses MD5 hashes to check whether the image split matches the previous experiment.

## Results and Outputs

The notebook writes results to:

`/content/Bark_results_multiseed/`

It can create a ZIP archive for download and copy the results to:

`MyDrive/Bark_results_multiseed/`

Model checkpoint files (`.pth`) are excluded from the default Google Drive export because of storage limitations. The notebook includes an option to export them.

## Project Status

Research and model evaluation. Notebook, source code, detailed result files, and figures will be added to their respective folders in this repository.

---

**Bark Classification · Deep Learning · Computer Vision · Multi-class Image Classification**
