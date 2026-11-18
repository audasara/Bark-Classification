# Bark Classification

A Deep Learning project for classifying tree bark images into 15 different species using Computer Vision.

## Dataset

The dataset is hosted on Google Drive and organized into separate folders for training, validation, and testing.

### Google Drive

| Dataset | Description | Link |
|---|---|---|
| Bark Archive All | Main dataset archive | [Open Drive](https://drive.google.com/drive/folders/1_F09BhlVYArv5J5o7Uc8iMxIQ7c-Hwz8?usp=sharing) |
| Bark RunModel | Dataset for training and validation | [Open Drive](https://drive.google.com/drive/folders/1cdW8pJVxBrAp2VENX00sF0DRfs4DCD5h?usp=drive_link) |
| Bark Test 53 Final | Final testing dataset | [Open Drive](https://drive.google.com/drive/folders/1skTNxEqCtxcTLbO9pNuYtL0GmbD2osdd?usp=drive_link) |

### Dataset Statistics

The dataset contains 15 tree bark species with a total of 6,090 images.

| Dataset Split | Images per Class | Total Images |
|---|---:|---:|
| Training | 247 | 3,705 |
| Validation | 53 | 795 |
| Testing | 53 | 795 |
| **Total** | **406** | **6,090** |

The original `Bark_runModel` folder contains 300 images per class (4,500 images), which are divided into training and validation sets.

### Class Names

The dataset consists of the following 15 tree species:

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

## Google Colab

The project uses Google Colab for model training and evaluation.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1QEju6fyMV0oWNzuMhuUpEWMIqM5UZDtF)

### Dataset Preparation

The notebook automatically searches for dataset folders in Google Drive.

- Primary location: `MyDrive/Bark_Archive_All/`
- Fallback location: `MyDrive/`
- Folder matching is case-insensitive.
- Nested ZIP extraction structures are supported.
- ZIP files that have not been extracted are also supported.

The notebook validates the folder names and image counts at STEP 1. If the dataset structure does not match the requirements, execution stops and reports the missing or incorrect files.

### Optional Split Verification

An optional `split_manifest.csv` can be placed at:

`MyDrive/Bark_results/split_manifest.csv`

This file is used to verify consistency with previous experiments by comparing MD5 hashes of the images.

## Requirements

### Hardware
- Google Colab GPU (NVIDIA T4 or higher recommended)
- Approximately 10 GB of available `/content` storage

### Libraries
- PyTorch
- timm
- scikit-learn
- SciPy
- Pandas
- Matplotlib
- openpyxl

The first notebook cell installs `timm` if necessary. An internet connection is required to download pretrained weights from Hugging Face.

## Models

The project investigates and compares different deep learning architectures:

- ResNet50
- Swin Transformer (Swin-T)
- ConvNeXt

## Experimental Setup

Experiments are conducted using three random seeds:

- 42
- 123
- 2026

Multiple runs are performed to evaluate model performance and consistency.

## Evaluation Metrics

- Accuracy
- Precision
- Recall
- Macro-F1 Score
- Confusion Matrix
- McNemar's Test

## Results and Outputs

Results are initially saved to:

`/content/Bark_results_multiseed/`

The notebook supports:
- Exporting results as a ZIP file for download.
- Copying results to Google Drive at `MyDrive/Bark_results_multiseed/`.

Model checkpoint files (`.pth`) are excluded from the default Google Drive export due to storage limitations. An option is available in the notebook to include them if needed.

## Notes

The following notebooks are not required for the current workflow:

- `bark_dataset_prep.ipynb` – Previously used to generate image patches, which are already included in `Bark_runModel`.
- `Bark_Extract_new.ipynb` – Replaced by the current notebook.

---

**Bark Classification | Deep Learning | Computer Vision | Multi-class Image Classification**
