# 🫁 Radiology AI: Chest X-Ray Pneumonia Classification

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow/Keras](https://img.shields.io/badge/TensorFlow-CNN-orange)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Environment-yellow)
![Status](https://img.shields.io/badge/Status-In%20Progress-brightgreen)

## 📌 Project Overview
This project focuses on building a Convolutional Neural Network (CNN) to classify Chest X-Ray images into two categories: **Normal** and **Pneumonia**. 

The goal of this project is not just to train a model, but to understand the end-to-end pipeline of medical imagery classification, identify real-world clinical biases, and iteratively improve a "Proof of Concept" into a clinically robust tool.

## 📊 Dataset
- **Source:** Pediatric Chest X-Ray image dataset.
- **Classes:** Normal vs. Pneumonia.
- **Preprocessing:** Images resized, normalized, and split into training and validation sets.

## 🧠 Model & Methodology
- Built from scratch using a Convolutional Neural Network (CNN) in Google Colab.
- Analyzed both Training and Validation Accuracy/Loss curves to monitor for overfitting.
- Extracted and visualized sample predictions to understand model behavior qualitatively.

## 🔬 Critical Findings & Known Limitations
In the medical field, recognizing model limitations is as crucial as the model itself. During validation, **a bias towards predicting "Pneumonia" (False Positives) was detected.** 

In clinical terms, a False Positive (calling a healthy patient sick) is generally preferred over a False Negative (missing a pneumonia diagnosis), but this bias still requires adjusting. The bias is likely due to class imbalance in the training data, which will be addressed in future iterations.

## 🧑‍⚕️ Clinical AI Evaluation (The Final Audit Verdict)
A rigorous clinical audit of 100 random samples (MD-led) has established the **"Ground Truth Paradox"** of this dataset:

1. **Statistical Noise:** A consistent **15-17% mismatch** was detected between file labels and radiological findings.
2. **The "Non-Specific" Trap:** Images labeled "Normal" (e.g., Cases 1, 4, 10, 27, 86) often showed subtle bilateral interstitial patterns, while 20% of "Pneumonia" labels (e.g., Cases 14, 15, 18, 19, 38, 39, 51, 56, 59, 60, 94, 100) were radiologically clean.
3. **Ground Truth Dual-Validation:** (CRITICAL FINDING) For a robust medical AI, training data must not be selected from clinical diagnosis alone, nor from images alone. Instead, **the ground truth must be derived from images that are both supported by visual positive findings and confirmed by clinical diagnosis.** This dual-validation protocol minimizes "Label Noise" and ensures the model learns true pathological features.
4. **Impact on AI:** This noise is the primary driver of the high False Positive rate. The model expects "Pneumonia" findings in radiologically normal images, leading to "over-sensitive" but clinically inaccurate predictions.

## 🚀 Model Upgrade v2.0 Strategy
Having debunked the data quality, we are now building a robust model designed to handle this noise:
1. **Resolution Leap:** Scaling inputs from `150x150` to `256x256` to preserve critical radiological tissue details.
2. **Label Bias Mitigation:** Implementing `Class Weights` to force the model to prioritize the under-represented "Normal" class.
3. **Advanced Evaluation:** Moving beyond "Accuracy" to **Precision-Recall curves** and **Confusion Matrices** to measure performance against our discovered 17% noise floor.

## 👨‍💻 How to Run
The entire workflow is contained within a Jupyter Notebook.
1. Open the `case.ipynb` notebook in Google Colab or your local Jupyter environment.
2. Upload the respective dataset.
3. Run all cells sequentially to train and evaluate the model.
