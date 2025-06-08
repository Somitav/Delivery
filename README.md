# 🚚 Delivery Analytics & Time Prediction

This project focuses on analyzing and predicting **actual delivery time** using real-world logistics trip data. The goal is to clean and transform the data, generate insights, perform hypothesis testing, and finally build a machine learning model to forecast delivery time accurately.

---

## 📁 Dataset Overview

The dataset contains trip-level and segment-level logistics information such as:

- `trip_creation_time`, `od_start_time`, `od_end_time`
- `source_center`, `destination_center`, `source_name`, `destination_name`
- `route_type` (e.g., FTL, Carting)
- Actual and predicted delivery times and distances
- Segment-level routing (OSRM) and actual time breakdowns

---

## 🧹 Data Cleaning & Feature Engineering

- Handled missing values and corrected date formats
- Extracted new features:
  - `delivery_minutes` from `od_start_time` and `od_end_time`
  - `source_state`, `destination_state` from location names
- Grouped data by `trip_uuid`, `source_center`, and `destination_center` to create segment-level aggregations
- Further aggregated per `trip_uuid` to analyze full-trip metrics

---

## 📊 Exploratory Data Analysis (EDA)

- Visualized route types and corridor frequencies
- Examined distribution of delivery times and distances
- Identified outliers using **boxplots** and handled them with the **IQR method**
- Generated **correlation heatmaps** to understand variable relationships
- Compared delivery speeds between **Carting** and **FTL**

---

## 📈 Statistical Testing

Performed Z-tests and hypothesis testing to compare:
- `actual_total_time` vs `osrm_total_time`
- `actual_total_time` vs `segment_actual_total_time`
- Differences in performance between delivery route types

---

## 🤖 Machine Learning Modeling

- **Target Variable**: `actual_total_time`
- **Train-Test-Validation Split**
- Models Used:
  - **Linear Regression**
  - **Random Forest Regressor** (final choice)

### 🔍 Model Evaluation Metrics (Validation Set):

| Metric         | Linear Regression | Random Forest |
|----------------|-------------------|----------------|
| MAE            | 83.49             | 75.49          |
| RMSE           | 25,158.24         | 18,882.70      |
| R² Score       | 0.926             | 0.936          |

✅ **Random Forest Regressor** performed better and was chosen as the final model.

---

## 📊 Feature Importance

Plotted feature importance from the Random Forest to understand key drivers behind delivery times.

---

## 📌 Technologies Used

- Python (Pandas, NumPy, Scikit-learn, Seaborn, Matplotlib)
- Jupyter / Google Colab
- Statistical testing (Scipy)
- Visualization (Seaborn, Matplotlib)

---

## 📎 Project Structure

