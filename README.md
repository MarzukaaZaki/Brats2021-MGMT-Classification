# Brain Tumor Classification from MRI Scans (RSNA-MICCAI 2021)
This project focuses on classifying the MGMT promoter methylation status in glioblastoma patients using the RSNA-MICCAI Brain Tumor Radiogenomic Classification dataset. It includes detailed exploratory data analysis (EDA) and CNN-based classification using multimodal MRI scans.

## Dataset Description
Dataset Description
The project utilizes the RSNA-MICCAI Brain Tumor Radiogenomic Classification dataset, released as part of a Kaggle competition. The dataset contains multi-modal MRI scans of glioblastoma patients, with a corresponding label indicating the MGMT promoter methylation status — a key biomarker in treatment planning.

**Key Characteristics:**
Number of Patients: 585

Total DICOM Images: ~348,000

MRI Modalities per patient:

FLAIR (Fluid Attenuated Inversion Recovery)

T1w (T1-weighted)

T1wCE (T1-weighted with contrast enhancement)

T2w (T2-weighted)

Each patient folder contains four subfolders (one per modality), each storing multiple DICOM slices.

Directory Structure
mathematica
Copy
Edit
Dataset/
│
├── 00000/
│   ├── FLAIR/
│   │   ├── Image-1.dcm
│   │   ├── Image-2.dcm
│   │   └── ...
│   ├── T1w/
│   │   ├── Image-1.dcm
│   │   └── ...
│   ├── T1wCE/
│   │   ├── Image-1.dcm
│   │   └── ...
│   └── T2w/
│       ├── Image-1.dcm
│       └── ...
│
├── 00001/
│   └── ...
│
└── 00002/
    └── ...
Each patient ID (00000, 00001, etc.) maps to a unique case, and each modality folder contains individual .dcm image slices of the brain.

## Exploratory Data Analysis
The goal of the EDA was to validate dataset structure, verify imaging completeness, and extract critical metadata for downstream modeling.

Key Steps:
**Dataset Structure Exploration**

- Parsed the folder hierarchy of the dataset (585 patients, ~348,000 DICOM images).
- Verified that each patient case included all four required MRI modalities: FLAIR, T1w, T1wCE, and T2w.

**Metadata Inspection**

- Extracted and reviewed DICOM metadata such as ImageOrientationPatient and SeriesInstanceUID to assess image alignment and organization.
- Grouped image slices by SeriesInstanceUID to determine how each modality was structured per patient.

**Quantitative Summaries**
Calculated slice counts per modality and total slices per patient to understand variability in data volume.

**Class Distribution Check**
Verified that the MGMT_value target variable was relatively balanced across methylated and unmethylated classes.

