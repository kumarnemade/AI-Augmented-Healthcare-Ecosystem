# Integrated Healthcare Intelligence: Fusing CNN Diagnostics and Comorbidity Metadata for Optimized Hospital Resource Management 🏥🤖

This repository hosts an end-to-end **AI-Augmented Healthcare Ecosystem** developed as a Capstone Project for the **Microsoft Elevate Internship**. The system automates the diagnostic path from raw chest X-ray images to real-time hospital bed allocation using Deep Learning and Business Intelligence.

## 🚀 Project Overview
In modern healthcare, diagnostic reports and patient medical histories often exist in silos. This project solves that fragmentation by creating a modular pipeline that:
1.  **Detects Pneumonia** using a Convolutional Neural Network (CNN).
2.  **Fuses AI results** with clinical metadata (Hypertension, Diabetes).
3.  **Automates Triage** to prioritize critical patients and manage ICU resources.[1, 1]

## 🔄 Data Pipeline & Workflow
The project follows a modular 3-step workflow as illustrated by the notebooks in this repository:

### Step 1: Diagnostic AI Engine
**File:** `AI-Augmented_Healthcare_Ecosystem_Main.ipynb`
- **Input:** 5,000+ Chest X-ray images retrieved via the **Kaggle API**.
- **Process:** Trains a 5-layer CNN model (`gtu_pneumonia_model.h5`) with optimized convolutional and pooling layers.
- **Output:** Generates `Integrated_Hospital_Report.csv`, a bridge file containing binary pneumonia predictions.

### Step 2: Intelligent Triage Logic
**File:** `Hospital Resource Management & Intelligent Triage.ipynb`
- **Input:** `Integrated_Hospital_Report.csv` (AI output) + `diabetes_012_health_indicators_BRFSS2015.csv` (Patient history).
- **Logic:** Applies a heuristic decision engine to categorize patients based on comorbid risk factors [1]:
    - **CRITICAL:** Pneumonia detected + High BP or Diabetes $\rightarrow$ Immediate ICU Admission.
    - **HIGH:** Pneumonia detected (No comorbidities) $\rightarrow$ General Ward Monitoring.
    - **STABLE:** Normal scan $\rightarrow$ Outpatient/Home Care.
- **Output:** Final 50-patient operational dataset: `hospital_operations_data.csv`.

### Step 3: Operational Dashboard
**File:** `Healthcare_Ecosystem.pbix`
- A 2-page Power BI dashboard for hospital administrators.
- **Page 1:** Diagnostic accuracy and total case distribution.
- **Page 2:** Real-time ICU occupancy gauges, emergency alert cards, and ward allocation bar charts.

## 🛠 Tech Stack
- **Deep Learning:** Python, TensorFlow, Keras, CNN.
- **Data Engineering:** Pandas, NumPy.
- **Visualization:** Power BI Desktop.
- **Version Control:** Git LFS (for large model weights).
- **Environment:** Google Colab.

## 📂 Repository Structure
├── notebooks/
│   ├── AI-Augmented_Healthcare_Ecosystem_Main.ipynb      # CNN Training Pipeline
│   └── Hospital_Resource_Management_Triage.ipynb        # Data Fusion & Logic
├── models/
│   └── gtu_pneumonia_model.h5                            # Trained Weights (Git LFS)
├── data/
│   ├── diabetes_012_health_indicators_BRFSS2015.csv     # Source Health Data
│   ├── Integrated_Hospital_Report.csv                   # Diagnostic Bridge File
│   └── hospital_operations_data.csv                      # Final Operational Data
├── visuals/
│   └── Healthcare_Ecosystem.pbix                        # Power BI Dashboard
└── README.md

## ⚠️ Requirements for Model Usage
The `.h5` model file is stored using **Git Large File Storage (LFS)**. To clone this repository with the model intact, please install Git LFS before cloning:
```bash
git lfs install
git clone https://github.com/kumarnemade/AI-Augmented-Healthcare-Ecosystem.git
```

## 👨‍💻 Author
**Kumar Nemade**  
Computer Science and Engineering  
Gujarat Technological University  

---
*Developed for MS Elevate Internship Program 2026.*
