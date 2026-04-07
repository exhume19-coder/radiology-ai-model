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

## 🧑‍⚕️ Clinical AI Evaluation (Grad-CAM Explainability)
To ensure the model is acting upon valid medical indicators rather than artifacts, **Explainable AI (Grad-CAM)** was integrated to generate heatmaps. A domain expert (MD) review of these heatmaps revealed several critical insights:
1. **Successful Cardiac Masking:** The model correctly learned to ignore the heart contour as an irrelevant structure for pneumonia classification, heavily down-weighting the cardiac silhouette without explicit masking.
2. **Image Resolution Confounders:** The original model was trained on `150x150` downscaled inputs. Clinical review confirmed this resolution causes significant pixellation, potentially destroying fine-grained infiltrate details and causing diffuse "confused" (zero-gradient) activations on certain images.
3. **Background Bias Diagnosis:** The AI occasionally highlighted out-of-body (empty background) areas, exposing a classic CNN bias.
4. **Focal Pathology Detection:** The model localized activations in the right peri-hilar and left peripheral zones, aligning with expected pneumonic distribution patterns.

## 🚀 Future Roadmap & Next Steps
As this project evolves into a production-ready application, the following milestones are planned:
1. **High-Resolution Architecture:** Re-architecting the model to accept `512x512` inputs to preserve critical radiological tissue details.
2. **Mitigating Bias:** Implementing Class Weights to balance the dataset and reduce over-prediction of Pneumonia.
3. **Clinical Metrics:** Shifting focus to true medical metrics: **Recall (Sensitivity), Precision, F1-Score**, and plotting a Confusion Matrix.
4. ~~**Explainable AI (XAI):**~~ **[COMPLETED]** Integrated Grad-CAM heatmaps and conducted Expert-in-the-Loop clinical evaluation.
5. **Deployment:** Wrapping the model in a **Gradio or Streamlit** web application for real-time edge inference.

## 👨‍💻 How to Run
The entire workflow is contained within a Jupyter Notebook.
1. Open the `case.ipynb` notebook in Google Colab or your local Jupyter environment.
2. Upload the respective dataset.
3. Run all cells sequentially to train and evaluate the model.
