# project-08
f1-predictive-telemetry-analytics: An end-to-end XGBoost &amp; Power BI solution for Formula 1 race strategy optimization.

# 🏎️ Predictive Telemetry Analytics & Race Strategy Optimization 

An end-to-end Machine Learning and Business Intelligence solution designed to process high-frequency Formula 1 race telemetry, balance highly skewed time-series datasets, and deliver real-time lap-time predictions through an enterprise-grade Power BI dashboard.

---

## 📈 Executive Project Performance

Before diving into the architecture, here is the direct business and technical impact of the optimization pipeline:

| Performance Metric | Baseline Model | Optimized Production Model | Impact / Improvement |
| :--- | :---: | :---: | :---: |
| **Model Fidelity (RMSE)** | 1.52 | **1.18** | **~22.3% Error Reduction** |
| **Data Volume Balanced** | 18,450 Laps | **24,600 Laps** | **SMOTE Variance Control** |
| **Prediction Latency** | -- | **< 45ms** | **Real-Time UI Responsiveness** |

---

## 🧠 Core Architecture & ML Blueprint

The system is split into three core layers: raw machine learning execution, synthetic telemetry data engineering, and interactive context-aware validation.

### 1. ML Core Architecture
* **Algorithm:** Gradient Boosted Decision Trees (`XGBoost Regressor`) — *The Predictive Brain driving high-speed lap estimations.*
* **Objective Function:** Mean Squared Error (`reg:squarederror`) — *Mathematical target used to force prediction errors down toward zero.*
* **Aero-Calibration:** `500 Trees | Learning Rate: 0.05 | Depth: 8` — *The hyperparameter sweet-spot discovered via extensive Grid Search.*

### 2. Data & Validation Pipeline
* **Feature Optimization:** `SMOTE Balance` — *Synthetic Minority Over-sampling Technique used to eliminate dataset variance, ensuring the AI learns all track conditions equally.*
* **Testing Split:** `80:20 Train-Test Ratio` — *Rigorous data segmentation ensuring zero data leakage and a rock-solid validation standard.*

### 3. BI Integration & Diagnostics
* **Engine Connection:** `Context-Aware DAX` — *High-fidelity backend formulas linking Power BI’s dynamic UI filters with the model's prediction matrix synchronously.*
* **Telemetry Map:** `Loss Convergence Tracker` — *A visual telemetry log mapping exactly how the AI steadily minimized its error metrics over 500 iterations.*
