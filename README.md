# Bike-Sharing Demand & Logistics Optimization

This project combines machine learning and operations research to improve the efficiency of a bike-sharing system. The goal is to predict hourly bike demand and use those predictions to optimize bike redistribution while minimizing operational costs.

The project follows a complete workflow, from data preprocessing and demand forecasting to mathematical optimization, demonstrating how predictive analytics can support real-world decision-making in urban mobility.



## Project Overview

Bike-sharing systems often struggle to keep bikes available where and when people need them. Demand changes throughout the day, making it difficult to balance supply across stations.

To address this challenge, the project is divided into two main parts:

* **Demand Forecasting:** Build a machine learning model to predict hourly bike demand using historical rental data and weather information.
* **Logistics Optimization:** Use the predicted demand as input to a Mixed-Integer Linear Programming (MILP) model that determines the most cost-effective bike redistribution strategy.



## Methodology

### 1. Machine Learning

The forecasting model is built using a **Random Forest Regressor**, with hyperparameters tuned through **Grid Search**.

Feature engineering includes:

* Cyclical encoding of time variables (hour, month, weekday)
* Weather-related features such as temperature and humidity
* Calendar information including working days and holidays

### Model Performance

* **Model:** Random Forest Regressor
* **R² Score:** 0.84
* Approximately **50% lower prediction error** than the linear regression baseline.

The model successfully captures the morning and evening commuting peaks, making it suitable for planning bike availability before demand increases.



### 2. Optimization

After forecasting demand, the project formulates a **Mixed-Integer Linear Programming (MILP)** model using **PuLP**.

The optimization minimizes the overall operating cost while ensuring bikes are distributed efficiently.

The objective function considers:

* Transportation costs
* Fixed dispatching costs
* Penalties for unmet demand

The model includes constraints for:

* Available bike supply
* Demand satisfaction
* Route activation using a Big-M formulation

---

## Repository Structure

```text
├── data/               # Input datasets
├── main.ipynb          # Complete implementation (forecasting + optimization)
├── requirements.txt    # Project dependencies
└── README.md           # Documentation
```



## Results

The forecasting model accurately identifies daily demand patterns, especially the sharp increases during commuting hours.

Using these predictions, the optimization model generates redistribution plans that reduce transportation costs while maintaining bike availability across stations.

Together, the forecasting and optimization stages provide a practical framework for supporting operational decisions in bike-sharing systems.



## Business Recommendations

Based on the analysis, the following operational improvements are recommended:

* **Pre-emptive bike rebalancing:** Redistribute bikes before morning and evening rush hours using demand forecasts.
* **Weather-aware operations:** Schedule maintenance and fleet servicing during periods of expected low demand caused by unfavorable weather.
* **Capacity planning:** Account for long-term growth by expanding station capacity in consistently high-demand locations.



## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* PuLP
* Matplotlib
* Jupyter Notebook



## Project Summary

This project demonstrates how predictive analytics and optimization can be combined to solve real operational problems.

A Random Forest model was developed to forecast hourly bike demand using historical usage patterns and environmental variables. The predicted demand was then incorporated into a Mixed-Integer Linear Programming model that determines the most efficient bike redistribution strategy while minimizing transportation, dispatching, and unmet demand costs.

The project illustrates the connection between machine learning and operations research, showing how accurate forecasting can directly improve operational planning and resource allocation in urban mobility systems.
