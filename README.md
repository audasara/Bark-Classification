# Bark Classification

A Deep Learning project for classifying tree bark images into 15 different species using computer vision models.

## Overview

Tree bark contains visual characteristics such as texture, patterns, and surface structures that can help distinguish between different tree species.

This project explores the use of deep learning techniques to automatically classify tree bark images. Several convolutional and transformer-based architectures are evaluated to compare their classification performance.

## Objectives

- Develop an image classification system for identifying tree bark species.
- Compare the performance of different deep learning architectures.
- Evaluate model performance using multiple random seeds.
- Analyze classification performance using quantitative evaluation metrics.

## Dataset

The dataset consists of images from **15 tree bark classes**.

| Dataset | Number of Images |
|---|---:|
| Training | 3,705 |
| Testing | 795 |
| **Total** | **4,500** |

- Number of classes: 15
- Test samples per class: 53

## Models

The project investigates different deep learning architectures:

| Model | Architecture Type |
|---|---|
| ResNet50 | Convolutional Neural Network (CNN) |
| Swin Transformer (Swin-T) | Vision Transformer |
| ConvNeXt | Modern Convolutional Neural Network |

These models are compared to investigate their ability to learn bark texture features and distinguish between tree species.

## Experimental Setup

To improve the reliability of the experimental results, multiple random seeds are used:

- Seed 42
- Seed 123
- Seed 2026

Each model is evaluated across multiple runs to examine performance consistency.

## Evaluation Metrics

The following metrics are used to evaluate classification performance:

- **Accuracy:** Measures the proportion of correctly classified images.
- **Precision:** Measures how many predicted positive samples are correct.
- **Recall:** Measures how many actual positive samples are correctly identified.
- **Macro-F1 Score:** Calculates the average F1-score across all classes, treating each class equally.
- **Confusion Matrix:** Visualizes correct and incorrect predictions across classes.
- **McNemar's Test:** Compares the classification errors of two models statistically.

## Technologies

- Python
- PyTorch
- Google Colab
- NumPy
- Pandas
- Matplotlib
- Scikit-learn

## Project Structure

```text
Bark-Classification/
│
├── dataset/
│   ├── train/
│   └── test/
│
├── notebooks/
│   ├── resnet50.ipynb
│   ├── swin_transformer.ipynb
│   └── convnext.ipynb
│
├── results/
│   ├── metrics/
│   ├── confusion_matrices/
│   └── model_comparison/
│
└── README.md
```

*Note: The project structure above is a suggested organization.*

## Research Focus

This project focuses on comparing CNN-based and Transformer-based architectures for tree bark image classification, with particular attention to:

1. Classification performance across 15 classes.
2. The ability to recognize complex bark textures.
3. Model consistency across different random seeds.
4. Statistical comparison of model performance.

## Project Status

<em>Research and model evaluation in progress.</em>

---

**Bark Classification | Deep Learning | Computer Vision**
