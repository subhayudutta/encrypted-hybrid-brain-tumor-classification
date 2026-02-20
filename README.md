# WT-HE Net: Privacy-Preserving Hybrid Brain Tumor Classification

## Description
This repository contains the implementation of **WT-HE Net**, a privacy-preserving hybrid deep learning framework for brain tumor classification using MRI images. The framework integrates block-based geometric texture feature extraction, deep learning image embeddings, and Homomorphic Encryption (HE) to enable secure and explainable medical image analysis.

The complete pipeline is implemented in a single Jupyter Notebook to ensure ease of use and full reproducibility.

---

## Repository Contents
- `BrainTumorClassification.ipynb`  
  This notebook includes:
  - Dataset loading and preprocessing  
  - Block-based image partitioning using geometric triangle division  
  - Statistical and texture feature extraction (GLCM, LBP, histogram features)  
  - CSV generation and dimensionality reduction using PCA  
  - Training of traditional ML models  
  - Transfer learning models on MRI images  
  - Hybrid deep learning model combining image and CSV features  
  - Homomorphic Encryption–based inference  
  - Explainability analysis using SHAP  

---

## Dataset Information
This study uses the **Brain Tumor MRI Dataset** curated by **Msoud Nickparvar (2021)** and publicly available on Kaggle.

- Dataset URL:  
  https://www.kaggle.com/dsv/2645886

- Classes:
  - No Tumor
  - Glioma
  - Meningioma
  - Pituitary

- Dataset Characteristics:
  - Fully anonymized MRI images
  - Released for research and educational purposes
  - No personally identifiable patient information is included

---

## Requirements
The notebook was developed and tested using the following environment:

- Python 3.9+
- numpy
- pandas
- opencv-python
- scikit-learn
- tensorflow / keras
- pywavelets
- shap
- tenseal
- matplotlib
- seaborn

Install dependencies using:

```bash
pip install numpy pandas opencv-python scikit-learn tensorflow pywavelets shap tenseal matplotlib seaborn
```

## Usage Instructions

1. Download the Brain Tumor MRI Dataset from Kaggle.
 
2. Organize the dataset into class-wise folders as follows:

dataset/
 
 ├── glioma/
 
 ├── meningioma/

 ├── notumor/

 └── pituitary/

3. Open BrainTumorClassification.ipynb.

4. Update the dataset directory path inside the notebook.

5. Run all notebook cells sequentially to reproduce:

    - Feature extraction

    - Model training

    - Evaluation

    - Encrypted inference

    - Explainability analysis


## Methodology Overview

- MRI images are padded to square dimensions.

- Images are partitioned into multiple triangular blocks using a geometric block division strategy.

- Statistical and texture features such as GLCM, LBP, entropy, and intensity statistics are extracted and stored in CSV format.

- PCA is applied to reduce feature dimensionality.

- A hybrid deep learning model fuses CNN-based image features with statistical CSV features.

- Homomorphic Encryption using the CKKS scheme is applied during inference.

- SHAP is used to explain model predictions and feature contributions.

## Encrypted Inference Configuration

The homomorphic encryption experiments use the CKKS scheme implemented via the TenSEAL library. Configuration parameters used in the manuscript are provided within the notebook to ensure reproducibility.

### CKKS Parameters
- Polynomial modulus degree: 8192
- Coefficient modulus: [60, 40, 40, 60]
- Security level: ~128-bit
- Polynomial activation approximation: Degree-2
- Encrypted feature vector size: 112 dimensions

### Reproducing Encrypted Inference

Encrypted inference experiments can be reproduced by executing the following sections in the notebook:

1. CKKS context initialization
2. Key generation (public and secret keys)
3. Feature encryption
4. Encrypted linear inference
5. Decryption and prediction

All encryption parameters and inference configurations are defined within the notebook cells to ensure transparent and reproducible experimentation.

## Reproducibility Statement

All experiments and results reported in the associated manuscript can be reproduced using the provided Jupyter Notebook and the publicly available dataset referenced above.

## License
This project is licensed under the Apache License 2.0.
