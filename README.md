# Code Smell Detection

This repository focuses on detecting code smells in software projects using machine learning and pretrained code embeddings. The project leverages the **MLCQ dataset** to identify and classify code smells, specifically "Data Class" and "Feature Envy."

## Dataset
The dataset used in this project is the **MLCQ dataset**:  
Madeyski, L. and Lewowski, T., 2020. *MLCQ: Industry-relevant code smell dataset*.  
Available at: [Zenodo](https://zenodo.org/record/3666840#.YnOJ1ehBwuU).

---
## Project Workflow
### 1. Dataset Setup
- The MLCQ dataset was downloaded as an Excel sheet.  
- Dataset preparation was performed separately for the following code smells:  
  - **Data Class:** [Setting up dataset notebook](https://github.com/rohansood98/code_smell_detection/blob/main/data_class/setting_up_dataset.ipynb)  
  - **Feature Envy:** [Setting up dataset notebook](https://github.com/rohansood98/code_smell_detection/blob/main/feature_envy/setting_up_dataset.ipynb)  

### 2. Code Embeddings Extraction
Pretrained models were utilized to extract embeddings for the dataset. Code embeddings were computed line by line for both code smells, followed by aggregation (average and sum) and padding.  
The following models were used:  
- `plbart_base`  
- `cubert`  
- `codeT5_base`  
- `codeT5_small`
- `codebert-base`

### 3. Code Metrics Extraction
- For Data Class, code metrics were extracted using the CK tool and further processed.  
- For Feature Envy, multiple tools were tried; however, no metrics were generated due to the short lines of code in the dataset for this smell.

### 4. Modeling and Evaluation
Random Forest,Bagging,XGBoost and SVM machine learning models were applied to analyze and classify code smells.

---

## Repository Structure

.

├── ├── dataset/
│   ├── data_class/
│   │   ├── embeddings/
│   │   │   ├── codeT5/                         # CodeT5 embeddings
│   │   │   ├── codebert/                       # CodeBERT embeddings
│   │   │   ├── cubert/                         # CuBERT embeddings
│   │   │   ├── plbart/                         # PLBART embeddings
│   │   ├── metrics/
│   │   │   └── ck_metrics_dataset_setup.ipynb  # CK metrics setup 
│   │   ├── results/
│   │   │   ├── codeT5/                         # CodeT5 results
│   │   │   ├── codebert/                       # CodeBERT results
│   │   │   ├── cubert/                         # CuBERT results
│   │   │   └── plbart/                         # PLBART results
│   │   │   └── metrics/                        # CK Metrics results
│   │   ├── training_evaluation/
│   │   │   ├── metrics/                        # Training on metrics
│   │   │   └── training_on_embeddings/         # Training on embeddings
│   │   └── setting_up_dataset.ipynb            # Data Class dataset setup 
│   ├── feature_envy/
│   │   ├── embeddings/
│   │   │   ├── codeT5/                         # CodeT5 embeddings
│   │   │   ├── codebert/                       # CodeBERT embeddings
│   │   │   ├── cubert/                         # CuBERT embeddings
│   │   │   ├── plbart/                         # PLBART embeddings
│   │   ├── metrics/
│   │   │   └── ck_metrics_dataset_setup.ipynb  # CK metrics setup 
│   │   ├── results/
│   │   │   ├── codeT5/                         # CodeT5 results
│   │   │   ├── codebert/                       # CodeBERT results
│   │   │   ├── cubert/                         # CuBERT results
│   │   │   └── plbart/                         # PLBART results
│   │   ├── training_evaluation/
│   │   │   ├── metrics/                        # Training on metrics
│   │   │   └── training_on_embeddings/         # Training on embeddings
│   │   └── setting_up_dataset.ipynb            # Feature Envy dataset setup 