👤 Author

Maiva Ndjiakou Kaptue
AI / Machine Learning Engineer
# Bearing Fault Severity Classification (Group-Aware ML System)

Advanced vibration-based bearing fault severity classification using 
windowed feature extraction and group-aware machine learning validation.

---

## 📌 Project Overview

This project implements a production-ready machine learning system for 
multi-class bearing fault severity classification using the 
Case Western Reserve University (CWRU) Bearing Dataset.

The system:

- Uses raw vibration signals (.mat files)
- Performs window-based segmentation
- Extracts statistical vibration features
- Applies group-aware splitting to prevent data leakage
- Trains and evaluates a multi-class Random Forest classifier
- Performs cross-validation using GroupKFold

The goal is to simulate a realistic predictive maintenance pipeline.

---

## 🎯 Objective

Classify bearing condition into severity levels:

| Label | Condition |
|-------|----------|
| 0 | Normal |
| 1 | Inner Race Fault – 0.007" |
| 2 | Inner Race Fault – 0.014" / 0.021" |
| 3 | Inner Race Fault – 0.028" |

All windows from the same file are kept together using group-aware splitting 
to avoid leakage across training and test sets.

---

## 🏗 System Architecture

1. Load MATLAB vibration files
2. Extract Drive-End accelerometer signal
3. Segment signal into fixed-size windows
4. Compute statistical features per window:
   - Mean
   - Standard Deviation
   - RMS
   - Peak-to-Peak
   - Signal Energy
5. Build labeled dataset
6. Perform group-aware train/test split
7. Cross-validate using GroupKFold
8. Train Random Forest classifier
9. Evaluate performance

---

## 🔬 Dataset

Case Western Reserve University Bearing Data Center

- Sampling frequency: 12 kHz
- Seeded inner race faults
- Controlled laboratory environment
- Window size: 2048 samples

---

## 🧠 Model

Random Forest Classifier

Parameters:
- n_estimators = 300
- max_depth = 6
- class_weight = "balanced"
- random_state = 42

Cross-validation:
- GroupKFold (3 folds)
- Scoring metric: F1-macro

---

## 📊 Results

Group-Based Cross Validation:
Mean F1 Score: ~0.9986

Test Set Performance:
Accuracy: 1.00
Macro F1: 1.00

Confusion Matrix: Perfect diagonal separation across severity classes.

Feature Importance:

1. Energy
2. RMS
3. Standard Deviation
4. Peak-to-Peak
5. Mean

The strong performance reflects the controlled laboratory nature of the dataset,
where fault diameter strongly correlates with vibration energy.

---

## 🚀 How to Run

The raw dataset is not included in this repository.

To reproduce results:

1. Download data from:
   https://engineering.case.edu/bearingdatacenter

2. Place files into:

Dataset/
    Normal/
    Faulty/


3. Run:

```bash
python main.py

''````


