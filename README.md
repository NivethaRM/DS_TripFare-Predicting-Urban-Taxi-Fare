🚖 TripFare: Predicting Urban Taxi Fare with Machine Learning

📌 Overview

The TripFare project aims to predict the total fare for New York City taxi rides using machine learning models. The goal is to enhance fare transparency, help users estimate trip costs in real-time, and support ride-sharing and urban mobility systems with predictive analytics. We used a real-world dataset and built a complete pipeline — from data preprocessing to model deployment using Streamlit.


🧠 Problem Statement
As a Data Analyst at an urban mobility analytics firm, your mission is to unlock insights from NYC taxi trip data to build a fare estimation system. This system helps:

* Users estimate fares before booking rides.

* Platforms offer price transparency.

* Cities understand urban travel trends.

* Tourists plan trip budgets more effectively.

🎯 Real-World Use Cases
  * 🛺 Ride-Hailing Platforms – Live fare estimates for better user trust.
  
  * 🚖 Driver Incentive Systems – Help drivers know when and where to drive.
  
  * 🌆 Urban Mobility Analytics – Analyze trip trends for policy planning.
  
  * 🧳 Travel Budgeting – Help travelers plan and manage trip costs.
  
  * 👥 Taxi Pooling & Sharing – Enable smarter dynamic pricing.

📂 Dataset

The dataset includes historical NYC taxi trip records with fields like pickup and dropoff timestamps, coordinates, passenger count, rate code, payment type, and fare components.
👉 Target variable: total_amount

| Column Name                                | Description                                        |
| ------------------------------------------ | -------------------------------------------------- |
| VendorID                                   | Taxi vendor/provider ID                            |
| tpep\_pickup\_datetime                     | Trip start datetime                                |
| tpep\_dropoff\_datetime                    | Trip end datetime                                  |
| passenger\_count                           | Number of passengers                               |
| pickup\_latitude/longitude                 | Pickup coordinates                                 |
| dropoff\_latitude/longitude                | Dropoff coordinates                                |
| RatecodeID                                 | Type of rate applied (e.g., JFK, Newark, Standard) |
| payment\_type                              | Type of payment (e.g., Card, Cash)                 |
| fare\_amount, tip, taxes, tolls, surcharge | Fare components                                    |
| total\_amount                              | Final total amount paid (target variable)          |

🛠️ Skills & Tools Used

Python, Pandas, NumPy

* EDA & Visualization: Matplotlib, Seaborn

* Preprocessing: Outlier Handling, Encoding, Transformation

* Feature Engineering: Derived features like trip_distance, trip_duration, is_night, pickup_hour

* Regression Models: Linear, Ridge, Lasso, Random Forest, Gradient Boosting, XGBoost

* Model Tuning: RandomizedSearchCV

* Model Deployment: Streamlit

* Model Saving: Pickle

🔍 Workflow & Tasks

1️⃣ Data Understanding & Cleaning
  * Loaded and explored dataset using pandas
  
  * Checked data types, missing values, duplicates

2️⃣ Feature Engineering
  * trip_distance using Haversine Formula
  
  * trip_duration_minutes from pickup and dropoff datetime

  * pickup_hour, is_night, pickup_dayofweek extracted from timestamp

3️⃣ Exploratory Data Analysis
  * Distribution plots for fare, distance, duration
  
  * Correlation heatmap

  * Fare vs. distance, passenger count, time-of-day analysis

4️⃣ Data Transformation
  * Outlier removal (Z-score & IQR)
  
  * Skewness treatment

Categorical encoding (One-hot)

5️⃣ Feature Selection
  * Tree-based feature importance using Random Forest
  
  * Selected top features based on importance

6️⃣ Model Building
Built 6 regression models:
| Model             | R² Score | MAE  | RMSE |
| ----------------- | -------- | ---- | ---- |
| Linear Regression | 0.926    | 1.12 | 2.02 |
| Ridge             | 0.926    | 1.12 | 2.02 |
| Lasso             | 0.898    | 1.37 | 2.38 |
| Random Forest     | 0.954    | 0.82 | 1.59 |
| Gradient Boosting | 0.958    | 0.83 | 1.53 |
| ✅ XGBoost (Best)  | 0.960    | 0.77 | 1.49 |

7️⃣ Hyperparameter Tuning
  * Tuned XGBoost using RandomizedSearchCV
  
  * Achieved R² ~ 0.960 on test set

8️⃣ Model Deployment
  * Saved the best model (xgb_fare_model.pkl) using pickle
  
  * Built an interactive Streamlit app where users enter trip details
  
  * App predicts the estimated total fare

🚀 Streamlit App Demo
User can input:

  * Trip distance (km)
  
  * Trip duration (minutes)
  
  * Pickup hour
  
  * Is night ride?
  
  * Passenger count
  
  * Rate Code (one-hot encoded)
  
  * Payment Type

On submission, the app returns the predicted total fare instantly.

