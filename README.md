
# 📘 Dataset for “Rapid Health Estimation of In-service Battery Packs Based on Limited Labels and Domain Adaptation”

**Authors:** Zhongwei Deng, Le Xu*, Hongao Liu, Xiaosong Hu, Bing Wang, Jingjing Zhou
**Published in:** *Journal of Energy Chemistry*, Vol. 89, 2024, pp. 345–354
**DOI:** [10.1016/j.jechem.2023.10.056](https://doi.org/10.1016/j.jechem.2023.10.056)

---

## 🧩 Overview

This repository contains the **charging test data of 10 electric vehicles (EVs)** used in the above publication.
The dataset supports research on **rapid state-of-health (SOH) estimation** of in-service lithium-ion battery packs using **short-time charging data** and **domain adaptation-based transfer learning**.

The dataset can be used to:

* Reproduce the experiments and figures presented in the paper;
* Train and validate deep learning or machine learning models for SOH estimation;
* Develop and benchmark domain adaptation and transfer learning strategies for battery data.

---

## ⚙️ Data Description

### 1. Dataset Structure

```
Charging-test-data-of-in-service-electric-vehicles/
│
├── vehicle_01.csv
├── vehicle_02.csv
├── ...
├── vehicle_10.csv
└── README.md
```

Each file corresponds to one EV battery pack tested in the study.

| File name      | Rated Capacity (Ah) | Cell Count | Real SOH (%) |
| -------------- | ------------------- | ---------- | ------------ |
| vehicle_01.csv | 234                 | 96         | 94.30        |
| vehicle_02.csv | 174                 | 104        | 93.85        |
| vehicle_03.csv | 100                 | 84         | 78.91        |
| vehicle_04.csv | 115                 | 100        | 87.77        |
| vehicle_05.csv | 174                 | 96         | 82.21        |
| vehicle_06.csv | 100                 | 88         | 92.87        |
| vehicle_07.csv | 110                 | 90         | 96.98        |
| vehicle_08.csv | 152                 | 108        | 90.81        |
| vehicle_09.csv | 150                 | 84         | 101.71       |
| vehicle_10.csv | 100                 | 90         | 99.08        |

---

### 2. Data Columns

Each CSV file contains synchronized measurements collected during a **constant-current–constant-voltage (CC–CV) charging test**.

| Column                | Unit | Description                          |
| --------------------- | ---- | ------------------------------------ |
| `Time(s)`             | s    | Time stamp                           |
| `Current(A)`          | A    | Charging current                     |
| `Voltage(V)`          | V    | Pack voltage                         |
| `Cell_max(V)`         | V    | Maximum cell voltage within the pack |
| `Cell_mean(V)`        | V    | Mean cell voltage within the pack    |
| `Temperature(°C)`     | °C   | Measured pack temperature            |
| `Charge_Capacity(Ah)` | Ah   | Cumulative charge capacity           |
| `SOC(%)`              | %    | State of charge estimated by BMS     |

---

## 🧠 How to Use

1. **Feature Extraction**

   * Extract short voltage–capacity segments (ΔV = 100 mV recommended) from the charging data.
   * Compute **incremental capacity sequences (ΔQ)** for both maximum and mean cell voltages.

2. **Model Training**

   * Use synthetic data (from digital twin simulation) for pre-training a deep convolutional neural network (DCNN).
   * Apply **transfer learning** or **domain adaptation** with these real vehicle datasets for fine-tuning.

3. **Evaluation**

   * Metrics: Mean Absolute Error (MAE) and Root Mean Square Error (RMSE) between estimated and measured SOH.
   * Typical result: MAE ≈ 3.2%, RMSE ≈ 3.9% using DCNN with domain adaptation.

---

## 🔍 Experimental Setup Summary

* **Battery Chemistry:** Ternary Li-ion (NCM-based)
* **Voltage range:** 3.6 V – 4.2 V
* **Charging rate:** 0.3 C
* **Test environment:** Constant ambient temperature (25 °C)
* **Sampling rate:** 1 Hz
* **Model reference:** 1st-order RC (Thevenin) equivalent circuit model for parameter identification and digital twin simulation.

---

## 📊 Citation

If you use this dataset, please cite the following paper:

> **Zhongwei Deng**, Le Xu*, Hongao Liu, Xiaosong Hu, Bing Wang, Jingjing Zhou.
> *Rapid health estimation of in-service battery packs based on limited labels and domain adaptation.*
> *Journal of Energy Chemistry*, 89 (2024): 345–354.
> DOI: [10.1016/j.jechem.2023.10.056](https://doi.org/10.1016/j.jechem.2023.10.056)

---

## 🧾 License

This dataset is shared for **academic and non-commercial research purposes only**.
Please contact the first author (*Prof. Zhongwei Deng*) for data use beyond research applications.
