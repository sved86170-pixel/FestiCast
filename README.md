# 📈 FestiCast — Store Item Demand Time Series Analysis & Forecasting

[![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue.svg?logo=python&logoColor=white)](#)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange.svg?logo=jupyter&logoColor=white)](#)
[![Statsmodels](https://img.shields.io/badge/Statsmodels-TSA-green.svg)](#)
[![Dataset](https://img.shields.io/badge/Dataset-Kaggle%20Store%20Item%20Demand-informational.svg?logo=kaggle)](#)
[![Status](https://img.shields.io/badge/Project%20Status-Active-brightgreen.svg)](#)

> **FestiCast** is a time series analysis and forecasting project aimed at understanding, decomposing, and predicting retail demand across multiple stores and items. The project investigates multi-scale seasonality (weekly patterns and seasonal/festival spikes), long-term trends, and data integrity to build accurate forecasting models.

---

## 📌 Project Overview

Accurate demand forecasting is vital for inventory management, supply chain optimization, and mitigating under-stocking or over-stocking costs. **FestiCast** leverages 5 years of daily store-item transaction data from the [Kaggle Store Item Demand Forecasting Challenge](https://www.kaggle.com/c/demand-forecasting-kernels-only/data).

### Key Objectives:
- **Comprehensive Exploratory Data Analysis (EDA)**: Investigate sales behavior, distributions, and outliers.
- **Seasonality & Trend Extraction**: Apply STL (Seasonal-Trend decomposition using LOESS) and MSTL to decouple weekly rhythms and annual macro-cycles.
- **Temporal Integrity Verification**: Confirm full data continuity across all store-item combinations without gaps or duplicates.
- **Forecasting Readiness**: Lay the groundwork for statistical (ARIMA/SARIMAX) and machine learning (LightGBM/XGBoost) forecasting pipelines.

---

## 📊 Dataset Profile

The dataset comprises daily sales transactions recorded across 10 distinct store locations and 50 unique items:

| Metric | Detail / Value |
| :--- | :--- |
| **Total Observations** | `913,000` store-item-day records |
| **Time Horizon** | `2013-01-01` to `2017-12-31` (5 full calendar years) |
| **Granularity** | Daily (`1,826` daily timestamps per series) |
| **Entities** | `10` Stores $\times$ `50` Items = `500` distinct time series |
| **Target Variable** | `sales` (units sold per item per store per day) |
| **Data Completeness** | `100%` (0 missing dates, 0 duplicate records, 0 nulls) |
| **Sales Distribution** | Min: `0` \| Median: `47.0` \| Mean: `52.3` \| Max: `231` |

---

## 🔍 Key Insights & Analysis Pipeline

### 1. Trend & Moving Dynamics
- Tracks daily aggregate sales across all stores and items alongside a **30-day rolling average**.
- Uncovers consistent year-over-year growth across the 5-year observation window.

### 2. Multi-Level Seasonality
- **Day-of-Week Effect**: Sales build up over weekdays, reaching pronounced peaks on Friday through Sunday.
- **Annual / Month-of-Year Seasonality**: Annual surge throughout late spring and summer months (June–August), followed by seasonal adjustments toward year-end.

### 3. STL / MSTL Decomposition
- Utilizes LOESS-based smoothing to separate the underlying sales signal into:
  - **Trend**: Long-term upward growth.
  - **Seasonal Components**: Weekly cycles and annual periodicity.
  - **Residuals / Remainder**: Random noise and localized shock anomalies.

### 4. Data Quality & Gap Analysis
- Exhaustive validation confirms all $10 \times 50 = 500$ time series are contiguous with zero missing timestamps.

---

## 🗂️ Project Structure

```text
FestiCast/
├── README.md                  # Project documentation & overview
├── time_series_project.ipynb  # Primary interactive analysis notebook
└── figs/                      # Generated figures and EDA plots (optional output)
    ├── fig1_line.png          # Daily aggregate sales + rolling mean
    ├── fig2_missing.png       # Missing data & completeness confirmation
    ├── fig3_decomp.png        # STL / MSTL seasonal decomposition
    └── fig4_seasonal.png      # Weekday & monthly seasonality charts
```

---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3.8+ installed. Install the required libraries:

```bash
pip install numpy pandas matplotlib statsmodels jupyter
```

### Dataset Setup

1. Download `train.csv` from the [Kaggle Store Item Demand Forecasting Challenge](https://www.kaggle.com/c/demand-forecasting-kernels-only/data).
2. Place `train.csv` in the root of the project directory:
   ```text
   FestiCast/
   ├── train.csv
   ├── time_series_project.ipynb
   └── ...
   ```

### Running the Analysis

#### Option A: Jupyter Notebook
Launch the interactive notebook:
```bash
jupyter notebook time_series_project.ipynb
```

#### Option B: VS Code / IDE
Open the folder in VS Code or your preferred IDE and run `time_series_project.ipynb` with the selected Python kernel.

---

## 🗺️ Roadmap & Planned Milestones

- [x] **Phase 1: Synopsis & Exploratory Data Analysis (EDA)**
  - Dataset profiling & completeness verification
  - Multi-seasonality identification and STL decomposition
  - Synopsis visualizations and reporting figures
- [ ] **Phase 2: Feature Engineering & Preprocessing**
  - Lag features & rolling window aggregations
  - Holiday/calendar encoding and festival indicators
  - Stationarity tests (ADF, KPSS) & differencing
- [ ] **Phase 3: Model Development & Experimentation**
  - Baseline models (Naive, Exponential Smoothing)
  - Statistical methods (ARIMA, SARIMAX)
  - Machine Learning & Gradient Boosting (LightGBM, CatBoost)
- [ ] **Phase 4: Evaluation & Deployment**
  - Backtesting with Expanding / Rolling Window Cross-Validation
  - Error metrics assessment (SMAPE, MAE, RMSE)
  - Forecasting dashboard / reporting pipeline

---

## 👥 Authors

Developed as part of the **Time Series Analysis (TSA) Lab** project.
