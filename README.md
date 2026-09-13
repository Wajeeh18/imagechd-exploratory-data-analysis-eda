# ImageCHD: Exploratory Data Analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Wajeeh18/imagechd-exploratory-data-analysis-eda/blob/main/ImageCHD.ipynb)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Exploratory data analysis of the **ImageCHD** congenital heart disease CT dataset, diagnosis label distribution, segmentation-label completeness, image shape/intensity profiling, and data-quality checks.

## About the dataset

ImageCHD (Xu et al., MICCAI 2020) is a public 3D CT dataset of 110 scans for congenital heart disease research, with per-voxel segmentation labels for seven cardiac structures (LV, RV, LA, RA, myocardium, aorta, pulmonary artery) and per-scan diagnostic metadata covering defect types such as ASD, VSD, PDA, and Tetralogy of Fallot.

The dataset itself is **not included in this repository**. It must be requested from the original authors/source, see the [ImageCHD paper](https://doi.org/10.1007/978-3-030-59719-1_60) for access details.

## What this notebook covers

- **Diagnosis distribution**: case counts per CHD subtype (ASD, VSD, PDA, ToF, etc.) and co-occurrence patterns
- **Label completeness check**: scans with missing or incomplete structure labels (e.g. myocardium missing in a subset of cases)
- **Label consistency check**: files containing unexpected/stray label classes
- **Image geometry profiling**: voxel spacing and in-plane shape variation across scans
- **Intensity (Hounsfield Unit) distribution**: per-scan and dataset-wide intensity profiling
- **Summary of data-quality flags** relevant to downstream modelling decisions

## Why this matters

Before any segmentation or classification work, it's worth knowing exactly what the dataset does and doesn't give you cleanly, which scans are usable as-is, which need cleanup, and which structures are reliable enough to build features on. This EDA is the basis for the scoping decisions used in the follow-up work (four-chamber segmentation instead of whole-heart, exclusion of PDA from initial modelling due to low case count, etc.).

## How to run

Click the **Open in Colab** badge above, or open manually via Colab's *File → Open notebook → GitHub* and point it at this repository. You'll need your own copy of the ImageCHD dataset mounted (e.g. via Google Drive), update the data path at the top of the notebook accordingly. And if that fails then you should download the file manually and open it manually in the colab.

## Requirements

```
numpy
pandas
matplotlib
seaborn
nibabel          # or SimpleITK, depending on how volumes are loaded
```

Colab has most of these pre-installed; any missing packages are installed in the notebook's first cell.

## Repository structure

```
.
├── imagechd.ipynb   # main EDA notebook
├── LICENSE
├── .gitignore
└── README.md
```

## Citation

If you use this analysis or the ImageCHD dataset, please cite the original dataset paper:

> Xu, X., Wang, T., Yuan, H., et al. (2020). *ImageCHD: A 3D Computed Tomography Image Dataset for Classification of Congenital Heart Disease.* In: Medical Image Computing and Computer Assisted Intervention (MICCAI 2020), LNCS vol. 12264. Springer, Cham.

## License

This repository is released under the [MIT License](LICENSE). The ImageCHD dataset itself is governed by its own separate license/usage terms, refer to the original dataset source.
