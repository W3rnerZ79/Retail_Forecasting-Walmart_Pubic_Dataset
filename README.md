# Retail Forecasting (Walmart Public Dataset)
A hands-on project combining predictive modeling with business intelligence. I used Python to build a Weighted Moving Average forecasting script that prioritizes recent data trends, then integrated the data into Power BI to create an interactive dashboard for visualizing future demand and model accuracy.

## 📊Walmart Forecasting Dashboard (V2)

| Full Timeline View (All Data) | Memory-Active Phase (2011+ Focused) |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/bad197be-d94f-4b07-ae09-93731c629d01" width="100%"> | <img src="https://github.com/user-attachments/assets/5b93914b-0ebf-4820-8f74-f64088dc8c86" width="100%"> |

The V2 dashboard tracks the performance of the **Memory-Active Forecast** model, highlighting how the integration of historical seasonal multipliers drastically reduces error during high-volatility holiday periods.

---
#### 1. Full Timeline View (All Data)
* **What it shows:** Displays the entire time-series from 2010 through late 2012. It catches the transition where the model gains "memory" after the first 52 weeks.
* **Key Visual Trend:** In Jan 2011 (the first major peak), the baseline forecast significantly lags and flattens out behind actual sales. By Jan 2012, the dark blue **Memory-Active Forecast** accurately tracks and captures the massive seasonal spike.
* **Network-Wide Metrics:** Across the entire lifecycle, the network maintains a **5.78% MAPE** and a **$389.66M** gross variance.

#### 2. Memory-Active Phase View (2011+ Focused)
* **What it shows:** Filters the dashboard exclusively to the period where the 52-week seasonal multipliers are actively running.
* **Performance Leap:** Isolating the memory model demonstrates a massive drop in overall error. Individual store MAPEs drop significantly (e.g., Store 1 falls to **3.73%**, Store 4 drops to a highly accurate **3.38%**).
* **Optimized Metrics:** Network-wide **MAPE decreases to 4.27%**, MAE drops to **44.69K**, and the gross forecast variance is slashed nearly in half down to **182.99M**, validating the effectiveness of the V2 pipeline.

#### ⚠️ Performance Diagnostic & Next Steps

* **The Problem:** The V2 model captures fixed-date holidays perfectly but fails on **floating holidays** (like Easter and Thanksgiving). A strict 52-week shift creates a "Phase Shift Error," applying holiday multipliers to normal weeks when dates move across the retail calendar.
* **The Evidence:** The dashboard's volatility analysis shows that **60.53%** of the remaining model error is still concentrated entirely within holiday weeks.
* **The Fix:** Future iterations will replace the blind 52-week lag with an **Event-Aligned Holiday Dictionary** to explicitly map moving holidays to their exact historical counterparts.

---

## 🐍 Python Backend (V2)

<img width="1789" height="1541" alt="image" src="https://github.com/user-attachments/assets/40377c04-a289-4044-be49-d44cc4e883c8" />

The V2 script updates the pipeline to scale the moving average using historical multipliers, capturing major holiday spikes.

#### ⚙️ How it Works
* **52-Week Lag:** Pulls sales from the same week last year to establish a historical baseline.
* **Baseline Smoothing:** Takes a 4-week average of that lag to remove random anomalies.
* **Multiplier Calculation:** Divides last year's actual sales by the smoothed baseline to isolate the seasonal spike (e.g., a holiday yields a `2.0` multiplier).
* **Forecast Fusion:** Multiplies the 3-week WMA by the multiplier to blend current momentum with seasonal trends.
* **Clean & Export:** Calculates error metrics, drops null rows, and exports the clean data to `Walmart_Forecasted_V2.csv`.

---

## Walmart Forecasting Dashboard (V1)

<img width="2296" height="1293" alt="image" src="https://github.com/user-attachments/assets/eeed066c-7067-4dd9-b993-ea07c07c0bfc" />

A hands-on project combining predictive data modeling with business intelligence. This project uses Python to calculate a 3-week Weighted Moving Average (WMA) forecast on multi-store retail data, then integrates the outputs into Power BI to track performance and error metrics.

#### 🛠️ Tech Stack & Features
* **Backend:** Python (`pandas`, `numpy`) for data cleanup, WMA modeling, and error calculation.
* **Frontend:** Power BI dashboard featuring dynamic DAX KPIs, store-by-store performance tables, and trend lines comparing Actual Sales vs. Forecast.
* **Metrics Tracked:** Gross Revenue ($6.74B), Gross Forecast Variance ($518.41M), Mean Absolute Error (82.29K), and Network MAPE (7.69%).

#### ⚠️ Performance Diagnostic & Next Steps
* **The Problem:** The trend analysis revealed that the WMA model lags behind sharp seasonal spikes. Because it relies on a strict rolling window, it cannot anticipate sudden demand surges.
* **The Evidence:** The dashboard's volatility analysis proves that **77.1%** of the model's total forecasting error is concentrated entirely within holiday weeks.
* **The Fix:** Future iterations will upgrade the Python pipeline to include a holiday indicator multiplier

---

## 🐍 Python Backend (V1)

<img width="1024" height="887" alt="image" src="https://github.com/user-attachments/assets/2f61b003-7156-46c4-9e8d-9c03a5e43074" />

The Python script (`Walmart_Forecasting_V1.py`) handles the data preprocessing, core mathematical modeling, and error calculation before exporting the structured dataset to Power BI.

#### ⚙️ How it Works
1. **Data Sorting:** Ensures the timeline is sequential by sorting historical data chronologically by `Store` and `Date`.
2. **Custom WMA Calculation:** Utilizes a custom `weighted_moving_average` function. Using a rolling 3-week window, it applies optimized statistical weights `[0.15, 0.35, 0.50]` via a `lambda` dot product operation to prioritize recent trends.
3. **Store-Isolated Grouping:** Uses `.groupby('Store')` to ensure sales data from individual stores are forecasted independently without cross-contaminating historical data.
4. **Error Metrics Generation:** Programmatically calculates `Forecast_Error` and `Absolute_Error` for every individual data point to enable variance tracking on the dashboard.
5. **Automated Export:** Outputs the fully transformed time-series data into a streamlined CSV file (`Walmart_Forecasted.csv`) for seamless ingestion into Power BI.

---

## 📫 Connect with Me
LinkedIn: https://www.linkedin.com/in/zachary-werner-aaaa41310/
Email: zachcwerner@gmail.com
