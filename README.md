# Solar Power Forecasting: Autoregressive Time-Series 

A Machine Learning project that forecasts the AC power output of a solar power plant using weather sensor logs. Designed to simulate a real-world energy trading desk environment. We transition from a static physical baseline to an advanced time-series framework capable of capturing short-term cloud volatility.

---

## Dataset

The open-source data used in this project is sourced from Kaggle:
**[Solar Power Generation Data on Kaggle]([https://www.kaggle.com/datasets/anikannal/solar-power-generation-data)]**

---

## Project Architecture & Core Insights

This project focuses on a crucial upgrade: moving from a basic model to a smart time-series approach. In the real world, this shift is essential for an energy trading desk to avoid expensive financial penalties caused by inaccurate power forecasts.

1. **The Physics Baseline (Step 5):** Using a randomized train-test split, we evaluate how perfectly the model maps static physical laws (Weather $\rightarrow$ Power). The Random Forest achieves an exceptional $R^2$ here, proving great data quality.
2. **Trading Simulation (Step 6):** We switch to a strict **Chronological Split (`shuffle=False`)** and introduce **Lag Features** (`AC_POWER_LAG_1` to `_3`). This eliminates data leakage and captures fast-moving cloud fronts, reflecting true forecasting conditions.

---

## Key Results

* **Baseline Performance:** Random Forest outclassed Linear Regression by capturing the highly non-linear time effects.
* **Volatility Optimization:** Transitioning to the Autoregressive setup reduced the Mean Absolute Error (MAE) by **3.65 kW**, making the model significantly more reliable for sudden drops in solar generation.

## Future Outlook & Model Improvement Strategies

To further push the performance of our forecasting pipeline, the following iterative steps should be explored next:

* **Cyclic Time Features:** Convert `HOUR` and `MINUTE` into Sine and Cosine components so the model mathematically understands that hour 23 and hour 0 are seamlessly connected.
* **Rolling Window Statistics:** Introduce rolling features (e.g., rolling means or standard deviations) to give the model a smoother representation of recent production trends rather than relying solely on single lag snapshots.
* **Advanced Algorithms:** Transition from Random Forest to Gradient Boosting architectures like **XGBoost** or **LightGBM**, which typically perform better at minimising MAE in volatile time-series datasets.
