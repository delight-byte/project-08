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
