# Seizure Onset Prediction Using Classical Machine Learning
This repository contains the full pipeline for a seizure onset prediction project using EEG data from the CHB-MIT Scalp EEG Database. The project implements preprocessing, feature extraction, and training of classical machine learning models to distinguish seizure from non-seizure EEG segments.

# 📚 Project Description
Seizure detection is critical for improving clinical care and automated monitoring of patients with epilepsy. This project focuses on predicting seizure onset using 2-second EEG signal windows. We use a classical machine learning pipeline, based on the method in Shoeb & Guttag (2010), extracting spectral energy features from band-specific EEG signals. The final models are trained on a balanced dataset with extreme class imbalance mitigation.

This project was completed as a final assignment for the workshop course on Data Science in Neuroscience.

# Project Structure

# 🧠 Dataset
Source: CHB-MIT Scalp EEG Database
Sampling Rate: 256 Hz
Channels: 18 common EEG channels selected from available signals

Preprocessing:

    Bandpass filter: 0.5–25 Hz

    Windowing: 2-second windows with 50% overlap

    Spectral energy features extracted using an 8-band filterbank

# 🛠️ Pipeline Overview
1. Data Conversion

    Converts .edf files to .h5 format

    Extracts seizure start/end times from summary files

2. Preprocessing

    Applies bandpass filtering (0.5–25 Hz)

    Selects 18 common EEG channels

    Normalizes data per channel

3. Segmentation

    Segments data into overlapping 2-second windows

    Labels each window as seizure or non-seizure

4. Feature Extraction

    Applies filterbank of 8 frequency bands

    Computes spectral energy per band per channel

    Final feature vector: 8 bands × 18 channels = 144 features

5. Class Imbalance Handling

    Downsamples the majority (non-seizure) class to 1000 examples

    Retains all minority (seizure) class examples

6. Model Training

    Logistic Regression, Random Forest, SVM (classical models)

    Cross-validation (5-fold) and evaluation on val/test splits

    Evaluation metrics: Accuracy, Precision, Recall, F1, Specificity
    
# Model Performance Summary

| Model                  | Set        | Accuracy | Precision | Recall | Specificity | F1 Score |
| ---------------------- | ---------- | -------- | --------- | ------ | ----------- | -------- |
| **LogisticRegression** | CV         | 0.5694   | 0.6971    | 0.4063 | —           | 0.5129   |
|                        | Validation | 0.5912   | 0.7107    | 0.4526 | 0.7667      | 0.5531   |
|                        | Test       | 0.5206   | 0.6080    | 0.4000 | 0.6733      | 0.4825   |
| **RandomForest**       | CV         | 0.8165   | 0.7879    | 0.9199 | —           | 0.8486   |
|                        | Validation | 0.8147   | 0.7926    | 0.9053 | 0.7000      | 0.8452   |
|                        | Test       | 0.8176   | 0.7735    | 0.9526 | 0.6467      | 0.8538   |
| **SVM**                | CV         | 0.8007   | 0.8554    | 0.7754 | —           | 0.8128   |
|                        | Validation | 0.7735   | 0.8383    | 0.7368 | 0.8200      | 0.7843   |
|                        | Test       | 0.7676   | 0.8101    | 0.7632 | 0.7733      | 0.7859   |

