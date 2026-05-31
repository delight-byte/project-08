# project-08
f1-predictive-telemetry-analytics: An end-to-end XGBoost &amp; Power BI solution for Formula 1 race strategy optimization.

# 🏎️ Predictive Telemetry Analytics & Race Strategy Optimization 

An end-to-end Machine Learning and Business Intelligence solution designed to process high-frequency Formula 1 race telemetry, balance highly skewed time-series datasets, and deliver real-time lap-time predictions through an enterprise-grade Power BI dashboard.

---

## Executive Project Performance

Before diving into the architecture, here is the direct business and technical impact of the optimization pipeline:

| Performance Metric | Baseline Model | Optimized Production Model | Impact / Improvement |
| :--- | :---: | :---: | :---: |
| **Model Fidelity (RMSE)** | 1.52 | **1.18** | **~22.3% Error Reduction** |
| **Data Volume Balanced** | 18,450 Laps | **24,600 Laps** | **SMOTE Variance Control** |
| **Prediction Latency** | -- | **< 45ms** | **Real-Time UI Responsiveness** |

---

## Core Architecture & ML Blueprint

The system is split into three core layers: raw machine learning execution, synthetic telemetry data engineering, and interactive context-aware validation.

### 1. ML Core Architecture
* **Algorithm:** Gradient Boosted Decision Trees (`XGBoost Regressor`) — The Predictive Brain driving high-speed lap estimations.
* **Objective Function:** Mean Squared Error (`reg:squarederror`) — Mathematical target used to force prediction errors down toward zero.
* **Aero-Calibration:** `500 Trees | Learning Rate: 0.05 | Depth: 8` — The hyperparameter sweet-spot discovered via extensive Grid Search.

### 2. Data & Validation Pipeline
* **Feature Optimization:** `SMOTE Balance` — Synthetic Minority Over-sampling Technique used to eliminate dataset variance, ensuring the AI learns all track conditions equally.
* **Testing Split:** `80:20 Train-Test Ratio` — Rigorous data segmentation ensuring zero data leakage and a rock-solid validation standard.

### 3. BI Integration & Diagnostics
* **Engine Connection:** `Context-Aware DAX` — High-fidelity backend formulas linking Power BI’s dynamic UI filters with the model's prediction matrix synchronously.
* **Telemetry Map:** `Loss Convergence Tracker` — A visual telemetry log mapping exactly how the AI steadily minimized its error metrics over 500 iterations.

* ---

## 🎯 The Core Problem & Racing Domain Context

In Formula 1, race strategy is dictated by high-frequency, non-linear telemetry data. Predicting lap times accurately is a notorious data science challenge due to two massive real-world constraints:

1. **Severe Dataset Imbalance:** Optimal racing conditions (dry tracks, fresh soft tyres, clear air) yield thousands of data points. Conversely, critical high-variance scenarios—such as extreme tyre degradation spikes, sudden track temperature shifts, and irregular out-lap telemetry—are highly underrepresented. A standard model trained on this data becomes heavily biased toward average laps and fails completely during critical race pit-window decisions.
2. **Multi-Dimensional Telemetry Shifts:** Features like tyre age do not degrade linearly. The interaction between track temperature, engine RPM, and physical tyre wear creates complex, stochastic variance that traditional regression models cannot reliably capture.

### The Solution
This project tackles dataset skewness head-on by implementing a **SMOTE (Synthetic Minority Over-sampling Technique) Balance Pipeline** to synthetically simulate underrepresented high-variance racing laps. By expanding our baseline from **18,450 to 24,600 balanced laps**, the predictive backend safely handles edge-case race telemetry without memorizing or overfitting.

---

## ⚙️ Data Engineering & Feature Architecture

To feed the predictive brain (`XGBoost`), raw telemetry parameters were transformed into highly predictive, engineered features. The top operational drivers built into this model include:

* **`Tyre_Age_Delta` (Critical Driver):** Tracks the cumulative degradation coefficient per lap. This serves as the primary non-linear feature for calculating grip-loss curves.
* **`Engine_RPM`:** Captures raw powertrain stress and mechanical efficiency across different sectors of the circuit.
* **`Track_Temp_Celsius`:** Monitors real-time ambient track conditions, which directly influence tyre thermal degradation and optimal brake-cooling windows.
* **Relative Distance & Sector Splits:** Standardized features mapping spatial positioning to eliminate structural noise across different track layouts.

---

## 📊 Performance Results & Model Fidelity Convergence

The deployment of the hyperparameter-tuned `XGBoost Regressor` alongside the `SMOTE` data pipeline yielded massive predictive upgrades. 

* **Error Minimization:** The baseline model started with a high variance **RMSE of 1.52**. Through structural fine-tuning and loss convergence optimization over 500 decision trees, the production-ready model achieved an **RMSE of 1.18**. This represents a **~22.3% boost** in absolute accuracy.
* **Loss Tracking:** The model's learning journey follows a stable gradient descent path, proving that the algorithm successfully captured the non-linear degradation curves of the telemetry features without overfitting.

---

## 🖥️ Interactive Power BI Dashboard Showcase

The frontend layer is built as an elite, dark-themed **Strategy Analytics & ML Model Fidelity Console** designed to mimic real-world pit-wall telemetry systems.

### 🚨 How to Insert Your Screenshot
> 💡 *To display your stunning dashboard image here, name your screenshot file as `dashboard_screenshot.jpg`, upload it directly to your GitHub repository root, and it will automatically render below!*

![Formula 1 Telemetry Dashboard Console](dashboard_screenshot.jpg)

### Key Dashboard Control Panels:
1. **Model Fidelity Console (Top Left):** Houses the structured ML blueprint and live architecture documentation, giving instant clarity to technical stakeholders.
2. **Hyperparameter Sensitivity Matrix (Top Middle):** A dynamic heat-grid mapping out the exact sweet spot where Tree Depth and Learning Rates yield the lowest error margins.
3. **Actual vs. Predicted Lap Time (Middle Left):** A synchronized line chart tracking real-time convergence between the AI’s estimations and the actual performance on the circuit.
4. **Driver Performance Analytics (Bottom Half):** Features custom multi-gauge telemetry parameters tracking `Full_Throttle_Pct` (60.66%) and `Braking_Distance_Pct` (15.82%), linked directly to a dynamic, spatial Speed Heatmap of the racing circuit.

---

## 🛠️ Tech Stack & Tooling
* **Language:** Python 3.x (Pandas, NumPy, Scikit-Learn, XGBoost, SMOTE)
* **Business Intelligence:** Microsoft Power BI (Advanced DAX Engine)
* **Environment:** Jupyter Notebook / Production Scripts

---

## 📂 How to Explore this Repository
* `/code` — Contains the Jupyter notebooks used for data preparation, SMOTE balancing, and model training.
* `/dashboard` — Houses the template file for the Power BI dynamic UI.
* `/data` — Sample baseline race telemetry data configuration.
