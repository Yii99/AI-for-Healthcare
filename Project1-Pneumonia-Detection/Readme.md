# Pneumonia Detection from Chest X-Rays

## Project Overview

In this project, we need to analyze data from the NIH Chest X-ray Dataset and train a CNN to classify a given chest x-ray for the presence or absence of pneumonia.

The project will include access to a GPU for fast training of deep learning architecture, as well as access to 112,000 chest x-rays with disease labels  acquired from 30,000 patients.

## Dataset

The data can be download from the [kaggle website](https://www.kaggle.com/nih-chest-xrays/data). 

There are 112,120 X-ray images with disease labels from 30,805 unique patients in this dataset. The disease labels were created using Natural Language Processing (NLP) to mine the associated radiological reports. The labels include 14 common thoracic pathologies: 
- Atelectasis 
- Consolidation
- Infiltration
- Pneumothorax
- Edema
- Emphysema
- Fibrosis
- Effusion
- Pneumonia
- Pleural thickening
- Cardiomegaly
- Nodule
- Mass
- Hernia 

The biggest limitation of this dataset is that image labels were NLP-extracted so there could be some erroneous labels but the NLP labeling accuracy is estimated to be >90%.

The original radiology reports are not publicly available but you can find more details on the labeling process [here.](https://arxiv.org/abs/1705.02315) 


### Dataset Contents: 

1. 112,120 frontal-view chest X-ray PNG images in 1024*1024 resolution (under images folder)
2. Meta data for all images (Data_Entry_2017.csv): Image Index, Finding Labels, Follow-up #,
Patient ID, Patient Age, Patient Gender, View Position, Original Image Size and Original Image
Pixel Spacing.


## Project Steps

### 1. Exploratory Data Analysis

The first part of this project will involve exploratory data analysis (EDA) to understand and describe the content and nature of the data.

* The patient demographic data such as gender, age, patient position,etc. 
* The x-ray views taken (i.e. view position)
* The number of cases including: 
    * number of pneumonia cases,
    * number of non-pneumonia cases
* The distribution of other diseases that are comorbid with pneumonia
* Number of disease per patient 
* Pixel-level assessments of the imaging data for healthy & disease states of interest (e.g. histograms of intensity values) and compare distributions across diseases.

### 2. Building and Training the Model

**Training and validating Datasets**

Curate the appropriate training and validation sets for classifying pneumonia by taking the following into consideration: 

* Distribution of diseases other than pneumonia that are present in both datasets
* Demographic information, image view positions, and number of images per patient in each set
* Distribution of pneumonia-positive and pneumonia-negative cases in each dataset

**Model Architecture**

VGG16 architecture with weights trained on the ImageNet dataset. Fine-tuning by combining with selectively freezing and training some layers of the pre-trained network. 


**Performance Assessment**

Metrics: Precision and Recall, F1 score, ROC


## Project Structure
---
- **[EDA.ipynb](./EDA.ipynb):** Jupyter notebook containing the exploratory data analysis for dataset
- **[Inference.ipynb](./Inference.ipynb):** Jupyter notebook containing the helper functions
- **[Build_and_train_model.ipynb](./Build_and_train_model.ipynb):** Jupyter notebook containing the whole pipeline to train the model
- **[FDA_Submission_Template.pdf](./FDA_Submission_Template.pdf):** The FDA submission