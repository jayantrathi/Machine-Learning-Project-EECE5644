# Machine-Learning-Project
This project predicts flight delays (>15 minutes) by combining BTS flight data with weather data, using machine learning models to identify key factors influencing delays. A Random Forest model achieved strong performance (F1 ≈ 0.76, ROC-AUC ≈ 0.85), showing that time, route, and weather conditions are significant predictors.


# Flight Delay Prediction using Machine Learning

## Overview
This project predicts flight delays (>15 minutes) by combining U.S. Bureau of Transportation Statistics (BTS) flight data with real-world weather data.  
The goal is to understand how scheduling and environmental factors contribute to delays and build a reliable predictive model.

---

## Dataset

- **Flight Data:** BTS On-Time Performance Data (2019 Q1)  
- **Weather Data:** Iowa State Environmental Mesonet (around top 20 airports)
- Datasets not included in this github (too large to do so)
- **Integration:** Data merged using airport location and timestamp (converted to UTC)

---

## Methodology

### Data Processing
- Cleaned and filtered flight records  
- Removed data leakage features (e.g., `DEP_DELAY`)  
- Aggregated weather data into 30-minute intervals  
- Merged datasets on airport and time  

### Feature Engineering
- Temporal features: departure hour, weekend flag, peak hour  
- Weather features: temperature, wind speed, precipitation, pressure  
- Route-based and categorical encoding  

### Handling Class Imbalance
- Applied **Random OverSampling** to balance delayed vs non-delayed flights  

---

## Models Evaluated

- Logistic Regression  
- Decision Tree  
- Random Forest  
- Gradient Boosting  
- AdaBoost  
- Linear SVM  

---
## Model Comparison

| Model                | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---------------------|----------|-----------|--------|----------|---------|
| **Random Forest**   | 0.7636   | 0.7973    | 0.7069 | **0.7494** | **0.8515** |
| Decision Tree       | 0.7377   | 0.7459    | 0.7209 | 0.7332   | 0.8214  |
| Extra Trees         | 0.7313   | 0.7695    | 0.6604 | 0.7108   | 0.8170  |
| Gradient Boosting   | 0.6528   | 0.6597    | 0.6310 | 0.6450   | 0.7116  |
| Logistic Regression | 0.6322   | 0.6379    | 0.6114 | 0.6244   | 0.6822  |
| Linear SVM          | 0.6323   | 0.6388    | 0.6089 | 0.6235   | N/A     |
| AdaBoost            | 0.6216   | 0.6292    | 0.5921 | 0.6101   | 0.6739  |

## Final Model Performance for the Best Model = Random Forest

| Metric        | Value |
|--------------|------|
| **F1 Score** | 0.76 |
| **ROC-AUC**  | 0.85 |
| **Model**    | Random Forest |

The Random Forest model provided the best balance between precision and recall, effectively capturing delay patterns.

---

## Key Insights

### Delay Patterns Throughout the Day
![Delay vs Time](delay_vs_time.png)

- Delay probability increases during peak travel hours  
- Congestion plays a major role in delays  

---

### Weather Impact on Delays

#### Wind Speed
![Wind vs Delay](wind_vs_delay.png)

#### Temperature
![Temperature vs Delay](temp_vs_delay.png)


#### Dew Point
![Dewpoint vs Delay](dewpoint_vs_delay.png)

#### Wind Gusts
![Gust vs Delay](gust_vs_delay.png)

- Strong correlation between adverse weather conditions and delays  
- Wind and precipitation-related features significantly influence outcomes  

---

### Airport-Specific Rain Impact
![Airport Rain Heatmap](airport_rain_heatmap.png)

- Certain airports are more sensitive to weather disruptions  
- Rain amplifies delay probability across major hubs  

---

---

## How to Run

1. Install dependencies:

pip install -r requirements.txt

2. Launch Notebook 

jupyter notebook Project.ipynb

---

## Notes

- Raw datasets are not included due to size constraints  
- Data paths may need adjustment depending on local setup  

---

## Key Takeaways

- Flight delays are strongly influenced by **time-of-day and weather conditions**  
- Tree-based models outperform linear models due to nonlinear relationships  
- Handling class imbalance is critical for realistic performance  

---

## Future Work

- Incorporate real-time flight tracking data  
- Include air traffic congestion metrics  
- Explore deep learning or sequence-based models  

---

## Author
Jayant Rathi  
MS Robotics – Northeastern University
- Project done for EECE 5644 - Spring 2026
