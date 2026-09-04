# Logistics Delivery Analysis and Delivery Time Prediction

## Project Overview

This project focuses on analyzing logistics delivery data to identify factors associated with delivery delays, understand delivery performance, and predict delivery time using Python and machine learning techniques.

The project follows a complete data-analysis workflow, starting from data loading and cleaning, followed by exploratory data analysis (EDA), KPI analysis, regression-based prediction, and clustering.

## Problem Statement

Logistics companies often face delivery delays caused by factors such as distance, traffic conditions, weather, vehicle type, and order quantity.

The main objectives of this project are:

* Analyze delivery performance.
* Identify factors associated with delivery delays.
* Calculate important logistics KPIs.
* Explore relationships between delivery variables.
* Predict delivery time using regression.
* Group similar deliveries using clustering.
* Generate insights that can support logistics decision-making.

## Dataset

The project uses a **120-row synthetic logistics dataset created for academic analysis**.

### Dataset Features

| Column             | Description                                 |
| ------------------ | ------------------------------------------- |
| `Order_ID`         | Unique identifier for each delivery         |
| `Distance_km`      | Delivery distance in kilometers             |
| `Traffic_Level`    | Traffic condition: Low, Medium, or High     |
| `Weather`          | Weather condition during delivery           |
| `Vehicle_Type`     | Type of vehicle used                        |
| `Order_Quantity`   | Number of items in the order                |
| `Delivery_Time_hr` | Actual delivery time in hours               |
| `Expected_Time_hr` | Expected delivery time in hours             |
| `Delivery_Status`  | Whether the delivery was On-Time or Delayed |
| `Delivery_Cost`    | Cost associated with the delivery           |

## Key Performance Indicators (KPIs)

The following KPIs are analyzed:

1. **Average Delivery Time**
   Measures the average time required to complete deliveries.

2. **On-Time Delivery Rate**
   Measures the percentage of deliveries completed within the expected time.

3. **Average Delivery Cost**
   Measures the average cost associated with deliveries.

4. **Delivery Delay Rate**
   Measures the percentage of deliveries that were delayed.

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Jupyter Notebook

## Project Workflow

```text
Problem Definition
        ↓
Data Collection
        ↓
Data Loading
        ↓
Data Understanding
        ↓
Data Cleaning
        ↓
Exploratory Data Analysis
        ↓
KPI Analysis
        ↓
Feature Engineering
        ↓
Regression
        ↓
Clustering
        ↓
Model Evaluation
        ↓
Business Insights
        ↓
Conclusion
```

## Exploratory Data Analysis

The project investigates questions such as:

* Does delivery distance affect delivery time?
* Does traffic level affect delivery delays?
* Does weather condition affect delivery delays?
* Does vehicle type affect delivery cost?
* Does order quantity have a relationship with delivery time?
* Which deliveries experience the highest delays?

### Example Finding

The analysis found a **strong positive correlation of 0.89** between delivery distance and delivery time in the dataset.

This indicates that longer delivery distances are generally associated with longer delivery times.

Traffic conditions are also analyzed by comparing delay rates across Low, Medium, and High traffic levels.

## Machine Learning

### 1. Regression

Linear Regression is used to predict:

```text
Delivery_Time_hr
```

### Target Variable

```text
Delivery_Time_hr
```

### Features

Potential input features include:

```text
Distance_km
Order_Quantity
Traffic_Level
Weather
Vehicle_Type
```

The categorical variables are converted into numerical representations before training the model.

### Model Evaluation

The regression model is evaluated using:

* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)
* R² Score

Lower MAE and RMSE indicate smaller prediction errors, while a higher R² score indicates that the model explains more of the variation in the target variable.

## 2. Clustering

K-Means clustering is used to group similar deliveries based on:

* Distance
* Order Quantity
* Delivery Cost

The resulting clusters can help identify different types of delivery patterns, such as short-distance, medium-distance, or higher-cost delivery groups.

## Business Applications

The analysis can help logistics managers:

* Identify conditions associated with delivery delays.
* Improve delivery-time estimation.
* Plan vehicle allocation.
* Analyze transportation costs.
* Identify different delivery patterns.
* Improve operational planning.
* Support data-driven decision-making.


## How to Run the Project

### 1. Clone the repository

```bash
git clone <your-repository-url>
```

### 2. Install the required libraries

```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

### 3. Open the notebook

```bash
jupyter notebook logistics_analysis_complete.ipynb
```

### 4. Run the notebook

Execute the cells from top to bottom to reproduce the analysis.

## Conclusion

This project demonstrates how data analysis and machine learning can be applied to logistics operations.

By analyzing delivery distance, traffic, weather, vehicle type, order quantity, delivery time, and delivery cost, the project identifies patterns related to delivery performance.

Linear Regression provides a method for predicting delivery time, while K-Means clustering helps group similar delivery records. These analytical techniques can support better planning, resource allocation, cost management, and delivery performance improvement.

## Future Improvements

Future versions of the project could include:

* Larger real-world logistics datasets.
* Route optimization algorithms.
* Time-series forecasting.
* Advanced regression models such as Random Forest and XGBoost.
* Real-time traffic and weather data.
* Interactive dashboards using Power BI or Streamlit.
* Real-time delivery-time prediction.
