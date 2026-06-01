# Walmart_Forecasting_Dashboard
A hands-on project combining predictive modeling with business intelligence. I used Python to build a Weighted Moving Average forecasting script that prioritizes recent data trends, then integrated the data into Power BI to create an interactive dashboard for visualizing future demand and model accuracy.




## 🐍 Python Backend: Data Pipeline & Forecasting Logic

<img width="1024" height="887" alt="image" src="https://github.com/user-attachments/assets/2f61b003-7156-46c4-9e8d-9c03a5e43074" />

The Python script (`Walmart_Forecasting_V1.py`) handles the data preprocessing, core mathematical modeling, and error calculation before exporting the structured dataset to Power BI.

### ⚙️ How it Works
1. **Data Sorting:** Ensures the timeline is sequential by sorting historical data chronologically by `Store` and `Date`.
2. **Custom WMA Calculation:** Utilizes a custom `weighted_moving_average` function. Using a rolling 3-week window, it applies optimized statistical weights `[0.15, 0.35, 0.50]` via a `lambda` dot product operation to prioritize recent trends.
3. **Store-Isolated Grouping:** Uses `.groupby('Store')` to ensure sales data from individual stores are forecasted independently without cross-contaminating historical data.
4. **Error Metrics Generation:** Programmatically calculates `Forecast_Error` and `Absolute_Error` for every individual data point to enable variance tracking on the dashboard.
5. **Automated Export:** Outputs the fully transformed time-series data into a streamlined CSV file (`Walmart_Forecasted.csv`) for seamless ingestion into Power BI.

## Walmart Forecasting Dashboard V1

<img width="2296" height="1293" alt="image" src="https://github.com/user-attachments/assets/eeed066c-7067-4dd9-b993-ea07c07c0bfc" />

A hands-on project combining predictive data modeling with business intelligence. This project uses Python to calculate a 3-week Weighted Moving Average (WMA) forecast on multi-store retail data, then integrates the outputs into Power BI to track performance and error metrics.

## 🛠️ Tech Stack & Features
* **Backend:** Python (`pandas`, `numpy`) for data cleanup, WMA modeling, and error calculation.
* **Frontend:** Power BI dashboard featuring dynamic DAX KPIs, store-by-store performance tables, and trend lines comparing Actual Sales vs. Forecast.
* **Metrics Tracked:** Gross Revenue ($6.74B), Gross Forecast Variance ($518.41M), Mean Absolute Error (82.29K), and Network MAPE (7.69%).

## ⚠️ Performance Diagnostic & Next Steps
* **The Problem:** The trend analysis revealed that the WMA model lags behind sharp seasonal spikes. Because it relies on a strict rolling window, it cannot anticipate sudden demand surges.
* **The Evidence:** The dashboard's volatility analysis proves that **77.1%** of the model's total forecasting error is concentrated entirely within holiday weeks.
* **The Fix:** Future iterations will upgrade the Python pipeline to include a holiday indicator multiplier

# 📫 Connect with Me
LinkedIn: https://www.linkedin.com/in/zachary-werner-aaaa41310/
Email: zachcwerner@gmail.com
