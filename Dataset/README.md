# Dataset Description

This project uses the Case Western Reserve University (CWRU) Bearing Data Center dataset for vibration-based fault severity classification.

---

## 📌 Source

Case Western Reserve University  
Bearing Data Center  

Official Website:
https://engineering.case.edu/bearingdatacenter

---

## ⚙ Experimental Setup

The test rig consists of:

- 2 HP motor
- Torque transducer / encoder
- Dynamometer
- Accelerometers mounted at 12 o’clock position

Vibration signals were collected from:

- Drive End (DE)
- Fan End (FE)
- Base (BA)

Sampling rates:
- 12,000 samples/second
- 48,000 samples/second (drive-end only)

---

## 🧪 Fault Types Used in This Project

This project uses:

- Normal baseline data
- Inner race faults (Drive End)
  - 0.007 inch defect
  - 0.014 inch defect
  - 0.021 inch defect
  - 0.028 inch defect

Faults were introduced using electro-discharge machining.

---

## 📊 File Format

All data files are MATLAB (.mat) format.

Each file contains:

- *_DE_time → Drive-end vibration signal
- *_FE_time → Fan-end vibration signal
- *_BA_time → Base vibration signal
- *RPM → Rotational speed

This project extracts only the Drive-End signal for modeling.

---

## 📁 Folder Structure

Dataset/
    Normal/
    Faulty/

---

## ⚠️ Note

The raw dataset is not redistributed in this repository.

To reproduce results:

1. Download data from the official CWRU website
2. Place Normal files in:
   Dataset/Normal/
3. Place Faulty files in:
   Dataset/Faulty/

---

## 🎯 Usage in This Project

- Signals are segmented into 2048-sample windows
- Statistical features are extracted per window
- Multi-class severity classification is performed
- Group-aware ML validation is applied to prevent data leakage
