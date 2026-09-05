# Logistics Delivery Analysis and Delivery Time Prediction

## Overview

This project analyzes a logistics delivery dataset to understand what drives delivery delays, measure delivery performance through KPIs, and predict delivery time using machine learning. The workflow covers data cleaning, exploratory data analysis, KPI calculation, regression modeling, and clustering, and is documented through weekly reports alongside a single end-to-end Jupyter notebook.

## Repository Structure

```
Logistic_Data_Analysis/
|-- dataset/
|   `-- logistics_delivery.csv
|-- notebook/
|   `-- logistics_analysis.ipynb
|-- reports/
|   |-- Week1_Strategic_Planning_Report.docx
|   |-- Week2_Data_Cleaning_Report.docx
|   |-- Week3_EDA_Visualization_Report.docx
|   `-- Week4_Predictive_Modeling_Final_Report.docx
|-- visualization/
|   |-- 01_distance_vs_delivery_time.png
|   |-- 02_traffic_vs_delay.png
|   |-- 03_vehicle_cost.png
|   |-- 04_weather_vs_delay.png
|   `-- 05_actual_vs_predicted.png
`-- Readme.md
```

## Dataset

The dataset (`dataset/logistics_delivery.csv`) contains 120 synthetic delivery records built for academic analysis.

| Column             | Description                                 |
| ------------------ | -------------------------------------------- |
| `Order_ID`         | Unique identifier for each delivery          |
| `Distance_km`      | Delivery distance in kilometers              |
| `Traffic_Level`    | Traffic condition: Low, Medium, or High      |
| `Weather`          | Weather condition during delivery            |
| `Vehicle_Type`     | Type of vehicle used                         |
| `Order_Quantity`   | Number of items in the order                 |
| `Delivery_Time_hr` | Actual delivery time in hours                |
| `Expected_Time_hr` | Expected delivery time in hours              |
| `Delivery_Status`  | Whether the delivery was On-Time or Delayed  |
| `Delivery_Cost`    | Cost associated with the delivery            |

The notebook confirms the dataset has no missing values or duplicate rows.

## Workflow

The analysis in `notebook/logistics_analysis.ipynb` follows this sequence:

1. Load the dataset and inspect its shape, data types, and summary statistics.
2. Check for missing values, duplicates, and unique values per column.
3. Review value counts for the categorical columns (Traffic_Level, Weather, Vehicle_Type).
4. Calculate core KPIs (average delivery time, average delivery cost, on-time rate, delay rate).
5. Explore relationships between delivery variables, including distance vs. delivery time, traffic vs. delay rate, vehicle type vs. cost, weather vs. delay rate, and order quantity vs. delivery time.
6. Calculate delay in hours per order and identify the most delayed deliveries.
7. Encode categorical variables and train a Linear Regression model to predict delivery time.
8. Evaluate the regression model using MAE, RMSE, and R².
9. Scale the numeric features and apply K-Means clustering to group similar deliveries.
10. Summarize what each resulting cluster represents.

## Key Performance Indicators

Based on the current dataset, the notebook reports:

| KPI                     | Value        |
| ------------------------ | ------------ |
| Average Delivery Time    | 3.99 hours   |
| Average Delivery Cost    | 183.41       |
| On-Time Delivery Rate    | 27.5%        |
| Delay Rate               | 72.5%        |

## Exploratory Findings

- Delivery distance and delivery time show a strong positive correlation of 0.89, meaning longer distances are generally associated with longer delivery times.
- Delay rate increases with traffic level: deliveries under High traffic were delayed in every recorded case in this dataset, while Low traffic deliveries were delayed roughly half the time.
- Weather conditions and vehicle type also show measurable relationships with delay rate and delivery cost respectively (see `visualization/02_traffic_vs_delay.png`, `03_vehicle_cost.png`, and `04_weather_vs_delay.png`).
- The most delayed orders were identified by computing `Delay_Hours` (Delivery_Time_hr minus Expected_Time_hr) and sorting in descending order.

## Machine Learning

### Regression

A Linear Regression model predicts `Delivery_Time_hr` using `Distance_km`, `Order_Quantity`, `Traffic_Level`, `Weather`, and `Vehicle_Type` (categorical variables one-hot encoded). Data was split 80/20 into training and test sets.

Model performance on the test set:

| Metric | Value        |
| ------ | ------------ |
| MAE    | 0.264 hours  |
| RMSE   | 0.335 hours  |
| R²     | 0.954        |

A low MAE and RMSE combined with an R² close to 1 indicate the model explains most of the variation in delivery time for this dataset. The fit between actual and predicted values is visualized in `visualization/05_actual_vs_predicted.png`.

### Clustering

K-Means clustering (3 clusters, features scaled with StandardScaler) groups deliveries by Distance_km, Order_Quantity, and Delivery_Cost. The resulting cluster profiles are:

| Cluster | Avg Distance (km) | Avg Order Quantity | Avg Delivery Time (hr) | Avg Delivery Cost |
| ------- | ------------------ | -------------------- | ------------------------ | -------------------- |
| 0       | 15.31               | 2.80                  | 2.59                      | 136.74                |
| 1       | 39.04               | 5.31                  | 5.25                      | 239.84                |
| 2       | 14.87               | 8.16                  | 3.35                      | 137.79                |

These clusters roughly correspond to short-distance/low-cost deliveries, long-distance/high-cost deliveries, and short-distance/high-quantity deliveries.

## Reports

The `reports/` folder contains four weekly `.docx` reports documenting the project as it progressed:

- **Week 1** - Strategic Planning
- **Week 2** - Data Cleaning
- **Week 3** - EDA and Visualization
- **Week 4** - Predictive Modeling (Final Report)

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## How to Run

1. Clone the repository:
   ```bash
   git clone <your-repository-url>
   ```
2. Install the required libraries:
   ```bash
   pip install pandas numpy matplotlib scikit-learn jupyter
   ```
3. Open the notebook:
   ```bash
   jupyter notebook notebook/logistics_analysis.ipynb
   ```
4. Run all cells from top to bottom to reproduce the analysis.

## Business Applications

This analysis can support logistics decision-making in areas such as:

- Identifying conditions most associated with delivery delays
- Improving delivery-time estimation for customers
- Planning vehicle allocation based on cost and route profiles
- Analyzing transportation cost drivers
- Segmenting delivery types for operational planning

## Future Improvements

- Test on a larger, real-world logistics dataset
- Add route optimization
- Incorporate time-series forecasting for demand and delay trends
- Try more advanced models such as Random Forest or XGBoost
- Integrate real-time traffic and weather data
- Build an interactive dashboard using Power BI or Streamlit
