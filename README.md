# ImageCHD: Exploratory Data Analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Wajeeh18/imagechd-exploratory-data-analysis-eda/blob/main/ImageCHD.ipynb)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Exploratory Data Analysis of the **ImageCHD** dataset, a CT-based whole-heart dataset for children with Congenital Heart Disease (CHD).

This repository contains a structured, step-by-step exploration of the dataset's images, segmentation labels, and diagnosis metadata, aimed at understanding the data before any modeling is attempted.

---

## 📌 About the Dataset

**ImageCHD** consists of 3D cardiac CT scans (`.nii.gz`) paired with voxel-level segmentation masks covering 7 core cardiac structures, along with a spreadsheet of diagnosis labels for various types of congenital heart disease.

**Segmented structures:**

| Label | Structure |
|-------|-----------|
| 1 | Left Ventricle (LV) |
| 2 | Right Ventricle (RV) |
| 3 | Left Atrium (LA) |
| 4 | Right Atrium (RA) |
| 5 | Myocardium (MYO) |
| 6 | Aorta (AO) |
| 7 | Pulmonary Artery (PA) |

**Diagnosis categories** in the metadata include conditions such as:
- ASD: Atrial Septal Defect
- VSD: Ventricular Septal Defect
- AVSD: Atrioventricular Septal Defect
- ToF: Tetralogy of Fallot
- TGA: Transposition of Great Arteries
- DORV: Double Outlet Right Ventricle
- CAT: Common Arterial Trunk
- CA: Coronary Anomaly

---

## 🔍 What This Notebook Covers

The analysis is organized into clear stages:

### 1. Setup & Data Loading
- Mounting Google Drive
- Locating and extracting the dataset archive
- Verifying folder structure and file counts

### 2. Quick Visual Sanity Check
- Loading a sample CT scan and its label mask
- Visualizing a single slice (image / label / overlay)
- Scrolling through multiple slices of one scan

### 3. Core Exploratory Data Analysis
- Pairing image and label files, checking for mismatches
- Loading and summarizing the diagnosis metadata
- Image shape and voxel spacing analysis across all scans
- Per-scan intensity statistics (min, max, mean, std, median)
- Voxel-level class distribution across all structures
- Detecting unexpected/unknown label classes
- Corrupt file and empty-volume checks
- Intensity histograms across scans
- Diagnosis co-occurrence heatmap (which CHD conditions appear together)
- Heart extent (slice range) per case
- Structure presence/absence per patient

### 4. Detailed Structural Analysis
- In-plane vs. through-plane voxel spacing comparison
- Multi-planar visualization (axial, sagittal, coronal) for smallest/median/largest volume cases
- Segmentation overlays across all planes
- Full-cohort slice grids (with and without segmentation overlay)
- Class imbalance analysis (voxel proportion per structure)
- Structure presence/absence heatmap across all patients
- Physical volume distribution (cm³) per cardiac structure
- Stacked voxel contribution across patients
- Focused analysis on individual structures (e.g., Right Ventricle presence and volume)

---

## 🛠️ Tools & Libraries

- `nibabel`: reading `.nii.gz` medical imaging files
- `numpy`, `pandas`: numerical and tabular analysis
- `matplotlib`, `seaborn`: visualization
- Google Colab + Google Drive for storage and execution

---

## 🚀 How to Run

1. Open the notebook in Google Colab.
2. Mount your Google Drive and update `dataset_path` to point to your local copy of the ImageCHD dataset.
3. Run cells sequentially from top to bottom, each section builds on variables defined earlier (e.g., file lists, label maps).

> **Note:** The ImageCHD dataset is not included in this repository due to its size and licensing. You will need to obtain it separately and place it in your own Drive/storage before running the notebook.

---

## 📊 Sample Output

**CT Image, Segmentation Label, and Overlay**
A single mid-slice comparison showing the raw CT scan, its corresponding label mask, and the two combined.
![CT image, label, and overlay](sample-outputs/middleSlice.png)

**Multiple Slices of a Single Scan**
Sampling across the full depth of one CT volume to see how the heart's cross-section changes from top to bottom.
![Multiple CT slices](sample-outputs/multipleSlices.png)

**3-Plane View (Axial, Sagittal, Coronal)**
The same scan viewed from all three anatomical planes, with and without the segmentation overlay.
![3-plane view](sample-outputs/3PlaneView.png)

**Raw CT with Segmentation Overlay Across Patients**
Axial, coronal, and sagittal overlays compared across three different patients, highlighting how heart structure and orientation vary case to case.
![Raw CT with segmentation overlay](sample-outputs/rawCTwithOverlay.png)

**Middle Axial Slice with Overlay — All Patients**
A full-cohort grid of the middle axial slice for every scan, with segmentation overlaid, giving a quick visual sense of dataset-wide variation.
![Middle slices for all patients](sample-outputs/middleSlicesMany.png)

**Voxel Class Distribution**
Voxel counts per cardiac structure shown on log scale, linear scale, and as a percentage share — highlighting the class imbalance across structures (e.g., Myocardium and Right Atrium dominate compared to LV/RV).
![Voxel class distribution](sample-outputs/ClassDistribution.png)

---

## 📁 Repository Structure

```
ImageCHD-EDA/
│
├── ImageCHD.ipynb     # Main notebook (this analysis)
└── README.md              # This file
```

---

## 📖 Citation

If you use the ImageCHD dataset, please cite the original paper:

> Xu, X., et al. "ImageCHD: A 3D Computed Tomography Image Dataset for Classification of Congenital Heart Disease." MICCAI 2020.

---

## 🤝 Contributing

Suggestions and improvements to the analysis are welcome, feel free to open an issue or submit a pull request.
