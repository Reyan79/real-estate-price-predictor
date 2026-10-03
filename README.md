# 🏠 Real Estate Price Predictor

A machine learning project that predicts residential property prices in Indian urban cities using property characteristics such as location, area, property type, age, and distance to metro/city center.

> **Dataset note:** The dataset used in this project is a synthetic Indian urban house-price dataset. The predictions should therefore be treated as machine-learning outputs for this dataset, not as real-world property valuations.

## 📌 Project Objective

The main objective is to build a machine learning model that predicts a property's price in **INR Lakhs** based on its characteristics.

The project covers:

**Data → Cleaning → EDA → Feature Engineering → Model Training → Evaluation → Prediction → Model Saving**

## 📂 Project Structure

```text
Real_Estate_Price_Predictor/
│
├── data/
│   └── raw/
│       └── train.csv
│
├── notebooks/
│   ├── real_estate_prediction.ipynb
│   └── random_forest_real_estate_model.pkl
│
└── README.md
```

## 📊 Dataset

The dataset contains **80,000 property records** and **18 original columns**.

Important features include:

* City
* Locality Type
* Property Type
* BHK
* Bathrooms
* Super Area
* Carpet Area
* Floor Number
* Total Floors
* Age of Property
* Furnishing Status
* Parking
* Lift Available
* Gated Community
* Distance to Metro
* Distance to City Center

### Target Variable

```text
Price_INR_Lakhs
```

## 🧹 Data Cleaning

The following checks were performed:

* Checked dataset shape and data types
* Checked missing values
* Checked duplicate rows
* Checked minimum and maximum values
* Checked area consistency
* Examined categorical values

### Cleaning Results

* Total records: **80,000**
* Missing values: **0**
* Duplicate rows: **0**
* Invalid area records: **0**

## 📈 Exploratory Data Analysis

The following relationships were explored:

* Price distribution
* Super Area vs Price
* City vs Average Price
* BHK vs Average Price
* Property Type vs Average Price
* Locality Type vs Average Price
* Furnishing Status vs Average Price
* Property Age vs Price
* Distance to City Center vs Price
* Distance to Metro vs Price
* Feature correlations

### Important Observations

`Super_Area_SqFt` showed a noticeable positive relationship with property price.

`Age_of_Property` and `Distance_to_City_Center_km` showed relatively weak negative relationships with price.

`City` and `Locality_Type` were important features in the Random Forest model.

## ⚙️ Feature Engineering

A `Price_per_SqFt` feature was created for analysis.

However, it was **not used as a model input** because it is calculated directly from the target price and would cause target leakage.

`Property_ID` was also excluded because it is an identifier.

## 🔀 Train/Test Split

The dataset was divided into:

```text
Training data: 64,000 rows
Testing data: 16,000 rows
```

A test size of 20% and `random_state=42` were used.

## 🤖 Models

Two regression models were trained:

### 1. Linear Regression

Used as the baseline model.

### 2. Random Forest Regressor

The Random Forest model used:

```text
n_estimators = 50
random_state = 42
n_jobs = -1
```

## 📊 Model Evaluation

The models were evaluated using:

* MAE — Mean Absolute Error
* RMSE — Root Mean Squared Error
* R² — Coefficient of Determination

### Results

| Model             |         MAE |        RMSE |     R² |
| ----------------- | ----------: | ----------: | -----: |
| Linear Regression | 47.94 Lakhs | 86.03 Lakhs | 0.6657 |
| Random Forest     | 33.93 Lakhs | 70.19 Lakhs | 0.7775 |

## ⭐ Feature Importance

Important features identified by the Random Forest model included:

1. `Super_Area_SqFt`
2. `City_Mumbai`
3. `Locality_Type_Premium`
4. `City_Delhi`
5. `Distance_to_City_Center_km`
6. `Age_of_Property`
7. `Carpet_Area_SqFt`
8. `Distance_to_Metro_km`

Feature importance shows how much
