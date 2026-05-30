# Salmon Fish Disease Classification

This repository contains a Google Colab-based deep learning workflow for salmon fish disease classification using the SalmonScan dataset.

## Dataset Used

This work uses the following public dataset:

Ahmed, Md Shoaib (2024), “SalmonScan: A Novel Image Dataset for Machine Learning and Deep Learning Analysis in Fish Disease Detection in Aquaculture”, Mendeley Data, V3.  
DOI: `10.17632/x3fz2nfm4w.3`  
Dataset URL: https://data.mendeley.com/datasets/x3fz2nfm4w/3

## Dataset Description

The SalmonScan dataset contains salmon fish images categorized into two classes:

- Fresh Salmon
- Infected Salmon

The dataset is suitable for machine learning and deep learning-based fish disease detection in aquaculture systems.

## Repository Workflow

The complete workflow is implemented in a Google Colab notebook and follows these steps:

## Step 1: Install Required Libraries

The notebook installs the required Python libraries, including:

- PyTorch
- Torchvision
- timm
- Transformers
- Ultralytics
- scikit-learn
- pandas
- matplotlib
- seaborn
- statsmodels

## Step 2: Import Libraries and Set Random Seed

All required libraries are imported, and a fixed random seed is used to improve reproducibility.

The notebook automatically detects whether GPU acceleration is available.

## Step 3: Download the SalmonScan Dataset

The dataset is downloaded directly from Mendeley Data Version 3 using:

```text
https://data.mendeley.com/public-api/zip/x3fz2nfm4w/download/3
````

## Step 4: Extract the Dataset

The downloaded archive contains a nested `SalmonScan.zip` file.

The workflow first extracts the main archive and then extracts the nested dataset archive to access the image folders.

## Step 5: Discover Images and Infer Labels

The notebook scans all image files and assigns labels based on folder or filename patterns.

The two target classes are:

```text
FreshFish
InfectedFish
```

## Step 6: Train/Validation/Test Split

The dataset is divided into:

* Training set
* Validation set
* Test set

A stratified split is used so that class proportions are preserved across all partitions.

## Step 7: Visualize Dataset Distribution

The class distribution across training, validation, and testing subsets is plotted using bar charts.

This helps verify whether the split is balanced and suitable for model training.

## Step 8: Define Image Preprocessing

Images are resized to a fixed input size and normalized using ImageNet statistics.

Training augmentation includes:

* Horizontal flipping
* Vertical flipping
* Rotation
* Color jittering
* Normalization

Validation and test images are only resized and normalized.

## Step 9: Build Data Loaders

PyTorch `ImageFolder` and `DataLoader` are used to create efficient loaders for:

* Training data
* Validation data
* Test data

## Step 10: Define Model Architectures

The notebook supports multiple deep learning models, including classical CNNs, efficient CNNs, transformer-based models, and transfer-learning baselines.

Models included:

* AlexNet
* VGG16
* VGG19
* ResNet18
* ResNet50
* DenseNet121
* EfficientNet-B0
* MobileNetV3-Small LAMB using `timm`
* ViT-Base
* Falconsai NSFW ViT transfer baseline
* YOLO26n-cls

## Step 11: Train Models

Each selected model is trained using transfer learning.

The final classification layer is replaced with a binary classifier for salmon disease classification.

The training loop stores:

* Training loss
* Validation loss
* Training accuracy
* Validation accuracy
* Training F1-score
* Validation F1-score

## Step 12: Plot Training Curves

For each model, the notebook plots:

* Training vs validation loss
* Training vs validation accuracy

These plots help analyze convergence and overfitting behavior.

## Step 13: Evaluate on Test Set

Each trained model is evaluated on the independent test set.

The workflow computes several publication-oriented evaluation metrics, including:

* Accuracy
* Precision
* Recall / Sensitivity
* Specificity
* F1-score
* Balanced accuracy
* Matthews correlation coefficient
* Cohen’s kappa
* ROC-AUC
* PR-AUC
* Brier score
* True positives
* True negatives
* False positives
* False negatives

## Step 14: Generate Confusion Matrices

Confusion matrices are generated for each trained model to visualize correct and incorrect predictions.

## Step 15: Generate ROC and Precision-Recall Curves

The notebook plots:

* ROC curves
* Precision-recall curves

These plots are useful for publication-grade model comparison.

## Step 16: Generate Classification Reports

For each model, the notebook prints a copy-paste-ready classification report containing class-wise precision, recall, F1-score, and support.

## Step 17: Hybrid Ensemble

A probability-averaging ensemble is created using the top-performing models.

The ensemble combines predicted probabilities and produces a final binary prediction.

## Step 18: Statistical Comparison

The notebook applies McNemar’s test to compare the top two models statistically.

This helps determine whether their prediction differences are statistically meaningful.

## Step 19: Inference Speed Benchmarking

The notebook measures inference efficiency for each trained model using:

* Total inference time
* Images per second
* Milliseconds per image

This is useful for practical deployment discussion.

## Step 20: YOLO26 Classification

The workflow also trains a YOLO26 classification model using Ultralytics.

YOLO26 is used as a modern image-level classification baseline.

## Step 21: Export Publication Tables

The notebook exports important tables to Excel files, including:

* Dataset distribution
* Model test metrics
* Inference benchmark results

These files can be directly used for manuscript preparation and further analysis.

## Suggested Repository Structure

```text
Salmon_fish_disease_classification/
│
├── Salmon_Fish_Disease.ipynb
├── README.md
├── results/
│   ├── salmon_model_test_metrics.csv
│   ├── salmon_inference_benchmark.csv
│   └── salmon_publication_results_full.xlsx
└── figures/
    ├── class_distribution.png
    ├── training_curves/
    ├── confusion_matrices/
    └── roc_pr_curves/
```

## Main Objective

The objective of this repository is to provide a reproducible deep learning workflow for classifying salmon fish images into healthy and infected categories using modern computer vision models.


## Revision of Code

The **Salmon_Fish_Disease_New.ipynb** file contains newly revised codes.



## Citation

If you use the dataset, please cite:

```bibtex
@dataset{ahmed2024salmonscan,
  author    = {Ahmed, Md Shoaib},
  title     = {SalmonScan: A Novel Image Dataset for Machine Learning and Deep Learning Analysis in Fish Disease Detection in Aquaculture},
  year      = {2024},
  publisher = {Mendeley Data},
  version   = {V3},
  doi       = {10.17632/x3fz2nfm4w.3},
  url       = {https://data.mendeley.com/datasets/x3fz2nfm4w/3}
}
```

## Author

Partha Pratim Ray, Sikkim University, India, May 24, 2026, parthapratimray1986@gmail.com, ppray@cus.ac.in
GitHub: [https://github.com/ParthaPRay](https://github.com/ParthaPRay)

```
```
