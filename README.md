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

### Dataset Structure Exploration**

- Parsed the folder hierarchy of the dataset (585 patients, ~348,000 DICOM images).
- Verified that each patient case included all four required MRI modalities: FLAIR, T1w, T1wCE, and T2w.

![Class Distribution of MGMT](/Visualizations/Slices_from_MRI_modalities_for_each_MGMT_label.png)

### Class Distribution Check

Verified that the MGMT_value target variable was relatively balanced across methylated and unmethylated classes.

![Class Distribution of MGMT](/Visualizations/MGMT_Class_Distribution.png)


### Metadata Inspection

- Extracted and reviewed DICOM metadata such as ImageOrientationPatient and SeriesInstanceUID to assess image alignment and organization.
- Grouped image slices by SeriesInstanceUID to determine how each modality was structured per patient.

![Image Slice Count Per SeriesInstanceUID](/Visualizations/Slice_Count_Per_SeriesID.png)

### Quantitative Summaries

Calculated slice counts per modality and total slices per patient to understand variability in data volume.

![Image Slice Count Per Modality](/Visualizations/Slice_Distribution_Per_Modality.png)


## MGMT Classification

Two convolutional neural networks were trained to classify the MGMT promoter methylation status using individual DICOM slices.

**Models:**
For this classification task, two different models were explored:

DenseNet121: A deep convolutional neural network that is known for its efficiency in handling images with its dense connectivity pattern.

EfficientNetB0: A lightweight model known for its efficient use of resources, achieving high accuracy while maintaining fewer parameters.

Both models were trained and evaluated to predict management values, and the training process was conducted using standard deep learning techniques such as early stopping and regularization.

Preprocessing & Features
Data was preprocessed by normalizing images to ensure consistency in input.

Various augmentation techniques were employed to enhance the diversity of training samples and help the models generalize better.

## Tools and Technologies
- Python
- Pytorch