# Rainfall Prediction Classifier (Australia) 🌧️

## Project Overview
This machine learning project predicts whether it will rain in Australia based on daily weather observations. Using the **Rainfall in Australia** dataset, the project builds a binary classification model to predict the target variable `RainToday`.

The project compares two algorithms—**Random Forest Classifier** and **Logistic Regression**—optimized using `GridSearchCV` to determine the best model for deployment.

## 📂 Dataset
The dataset (`weatherAUS.csv`) contains daily weather observations from numerous Australian weather stations.
* **Source:** Australian Bureau of Meteorology (BOM).
* **Target Variable:** `RainToday` (Did it rain? Yes/No).
* **Key Features:** MinTemp, MaxTemp, Humidity, WindSpeed, Pressure, and Seasonality.

## 🛠️ Technologies Used
* **Language:** Python 3.x
* **Data Manipulation:** Pandas, NumPy
* **Machine Learning:** Scikit-Learn (sklearn)
* **Visualization:** Matplotlib

## ⚙️ Project Workflow

### 1. Data Preprocessing
* **Data Cleaning:** Removed features with excessive missing values (`Evaporation`, `Sunshine`, `Cloud9am`, `Cloud3pm`).
* **Feature Engineering:** * Converted `Date` column into a categorical `Season` feature (Summer, Autumn, Winter, Spring).
    * Renamed `RainTomorrow` to `RainToday` to set the prediction target.
* **Handling Missing Data:**
    * Numerical columns: Imputed with **Mean**.
    * Categorical columns: Imputed with **Mode** (Most Frequent).
* **Encoding:**
    * Binary columns converted to 0/1.
    * Categorical columns (Wind Direction, Season) transformed using **One-Hot Encoding**.

### 2. Model Training
* **Split:** Data was split 80/20 into training and testing sets.
* **Stratification:** Used `StratifiedKFold` to handle the class imbalance (There are significantly more "No Rain" days than "Rain" days).
* **Pipeline:** Constructed a Scikit-Learn `Pipeline` combining the `ColumnTransformer` and the Classifier.

### 3. Model Optimization
Used `GridSearchCV` to tune hyperparameters:
* **Random Forest:** Tuned `n_estimators`, `max_depth`, and `min_samples_split`.
* **Logistic Regression:** Tuned `solver`, `penalty`, and `class_weight`.

## 📊 Results
The models were evaluated using **Accuracy**, **F1-Score**, and the **Confusion Matrix**.

| Model | Best Parameters | Accuracy Score |
| :--- | :--- | :--- |
| **Random Forest** | `max_depth`: 20, `n_estimators`: 100 | **~85%** |
| **Logistic Regression** | `solver`: liblinear, `penalty`: l2 | *[Insert Your Score]* |

*Key Finding:* The Random Forest model generally outperformed Logistic Regression due to its ability to capture non-linear relationships between weather variables.

## 🚀 How to Run

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/rainfall-prediction.git](https://github.com/your-username/rainfall-prediction.git)
