## Dataset

The Bark Classification dataset is stored on Google Drive and organized into two main directories.

**Google Drive Location:** `MyDrive/Bark_Archive_All/`

### Dataset Structure

```text
MyDrive/
│
├── Bark_Archive_All/
│   │
│   ├── Bark_runModel/
│   │   └── [15 Class Folders]
│   │
│   └── Bark_Test_53_Final/
│       └── [15 Class Folders]
│
└── Bark_results/
    └── split_manifest.csv  (Optional)
```

### Dataset Description

| Dataset | Images per Class | Total Images | Purpose |
|---|---:|---:|---|
| Bark_runModel | 300 | 4,500 | Training and Validation |
| Bark_Test_53_Final | 53 | 795 | Final Testing |

The training and validation sets are divided as follows:

- Training: 247 images per class (3,705 images)
- Validation: 53 images per class (795 images)
- Testing: 53 images per class (795 images)

**Total Dataset: 6,090 images across 15 classes.**

### Class Names

The dataset contains 15 tree bark species:

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

Folder names must match the class names used in `CLASS_NAMES`.

## Google Drive Setup

The notebook automatically searches for the dataset folders in Google Drive.

- Primary location: `MyDrive/Bark_Archive_All/`
- Fallback location: `MyDrive/`

Folder matching is case-insensitive.

The notebook also supports:
- Nested ZIP extraction structures, such as `Bark_runModel/Bark_runModel/[class folders]`.
- ZIP files that have not yet been extracted.
- Automatic dataset folder discovery and validation.

If any class folder or expected image count is missing, the notebook stops at **STEP 1** and reports the detected dataset issues.

### Optional Split Verification

An optional file can be provided at:

```text
MyDrive/Bark_results/split_manifest.csv
```

This file is used to verify consistency with previous experiments by comparing image MD5 hashes.

## Requirements

### Hardware

- Google Colab
- GPU: NVIDIA T4 or higher recommended
- Approximately 10 GB of available `/content` storage

### Software and Libraries

- Python
- PyTorch
- timm
- scikit-learn
- SciPy
- Pandas
- Matplotlib
- openpyxl

Most libraries are already available in Google Colab. The first notebook cell installs `timm` if necessary.

An internet connection is required to download pretrained model weights from Hugging Face.

## How to Run

1. Open the project notebook in Google Colab.
2. Select a GPU runtime (T4 or higher recommended).
3. Mount Google Drive when prompted.
4. Make sure the dataset folders follow the required structure.
5. Run the notebook cells sequentially, starting from STEP 1.
6. The notebook automatically locates and validates the dataset.
7. Continue with model training, evaluation, and result generation.

## Notebooks

The main notebook handles dataset discovery, validation, model training, and evaluation.

The following notebooks are not required for the current workflow:

- `bark_dataset_prep.ipynb` – Previously used to generate image patches, which are already included in `Bark_runModel`.
- `Bark_Extract_new.ipynb` – Replaced by the current notebook workflow.

## Results and Outputs

Experimental results are initially saved to:

```text
/content/Bark_results_multiseed/
```

The notebook provides options to:

- Generate a ZIP archive for downloading results.
- Copy the results to Google Drive at:

```text
MyDrive/Bark_results_multiseed/
```

Model checkpoint files (`.pth`) are excluded from the default Drive export because of storage limitations. An option is available in the notebook to include checkpoints if needed.

## Reproducibility

To improve experimental reproducibility, the project uses multiple random seeds:

- 42
- 123
- 2026

The experiments evaluate model performance across repeated runs using consistent dataset splits and evaluation procedures.

An optional `split_manifest.csv` can be used to verify dataset consistency through MD5 image hashes.

---

**Bark Classification | Deep Learning | Computer Vision | Multi-class Image Classification**
