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
