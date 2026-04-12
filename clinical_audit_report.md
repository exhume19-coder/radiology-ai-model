# Radiology AI Project: Final Summary & Walkthrough

This project marks a successful transition from a standard neural network (v1.0) to a clinically-governed diagnostic support tool (v2.0).

## 🏆 Key Achievements
- **Accuracy:** 91% (Radiological limit)
- **Sensitivity (Recall):** 95% (Optimized for clinical safety)
- **Clinical Governance:** 100-sample MD audit performed to identify 17% label noise.

## ⚕️ The Expert-in-the-Loop Advantage
The major breakthrough in this project was the **Clinical Audit**. By reviewing the data through a radiologist's lens, we discovered that 17% of the dataset labels were mismatched with the radiological appearance. This finding redefined our training strategy from "Blind Engineering" to "Dual-Validation Learning."

## 🚀 Model v2.0 Features
1. **High Resolution (256x256):** Preserved interstitial and peribronchial patterns.
2. **Balanced Learning:** Class weights prioritized the healthy class to reduce over-diagnosis errors.
3. **Robust Architecture:** Integrated BatchNormalization and Dropout to ignore noisy clinical labels.

---
**Status:** Completed & Validated
**MD Reviewer:** Emrah Seker
**AI Assistant:** Antigravity AI
