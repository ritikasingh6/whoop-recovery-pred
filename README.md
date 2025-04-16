# whoop-recovery-pred
# Predicting Recovery Scores from WHOOP Data

This project uses personal WHOOP data to build a machine learning model that predicts daily recovery scores based on physiological, behavioral, and workout metrics. The model was developed using Python and trained in a Jupyter environment.

---

## Overview

**Goal:** Predict daily WHOOP recovery scores using both same-day and previous-day data, such as heart rate variability, sleep metrics, workout strain, and journal entries.

**Model used:** Random Forest Regressor

---

## Data Sources

The dataset was created by exporting and merging four personal WHOOP CSV files:
- `physiological_cycles.csv`: HRV, resting HR, respiratory rate, recovery score, strain
- `sleeps.csv`: sleep performance, sleep efficiency, sleep consistency
- `workouts.csv`: total workout time, strain, calories, HR zones
- `journal_entries.csv`: self-reported behavioral data (e.g., caffeine, alcohol, stress)

All data was merged and aligned by date. Lag features were created to include information from the previous day.

---

## Features Used

| Feature | Description |
|--------|-------------|
| Heart rate variability (HRV) | Primary indicator of recovery |
| Resting heart rate (RHR) | Strong inverse relationship with recovery |
| Sleep performance & efficiency | Quality and quantity of rest |
| Day strain | Training load from previous day |
| Respiratory rate, skin temp | Signals of illness or fatigue |
| Behavioral factors | e.g., caffeine intake, supplement use |
| Lag features | Prior-day HRV, RHR, strain, and sleep quality |

---

## Results

After testing different configurations, the **best model** used **same-day and 1-day lag features**:

| Metric | Value |
|--------|-------|
| **MAE** (Mean Absolute Error) | **7.29** |
| **R² Score** | **0.79** |

This means the model predicts daily recovery scores within ±7.3% on average, and explains 79% of the variance in recovery.

---

## Key Insights

- **Heart rate variability** is by far the strongest predictor of recovery.
- **Resting heart rate**, **sleep performance**, and **previous day strain** also contribute significantly.
- **Lag features** (especially from the day before) dramatically improved performance.
- Additional multi-day lags (2-day, 3-day) actually reduced accuracy, showing that recovery is most influenced by the **previous 24 hours**.

---

## Visualization Samples

- **Feature Importance Plot**  
- **Correlation Heatmap**  
- **Actual vs. Predicted Recovery Scatter Plot**

---

## Tech Stack

- Python (pandas, numpy, scikit-learn, seaborn, matplotlib)
- Jupyter Notebook / VS Code
- WHOOP export data

---

## Future Improvements

- Try time-aware models (XGBoost with time features, or RNNs)
- Build a dashboard for daily recovery forecasting
- Integrate with live WHOOP or Strava data via API (if accessible)

---

## About Me

This project was built by Ritika Singh, a student-athlete and data-driven product thinker passionate about wellness, performance, and applied machine learning.

> Predictive wellness is the future — this project explores how consumer wearables can guide smarter training and recovery.