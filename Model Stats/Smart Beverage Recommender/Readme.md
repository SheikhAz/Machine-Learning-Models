# 🥤 Smart Beverage Recommender

A Machine Learning classification project that recommends the **perfect beverage order** based on environmental and time-related conditions.

The model uses **temperature, humidity, and time of day** as input features and predicts the most suitable beverage category.

## 🎯 Project Overview

The Smart Beverage Recommender is trained on a dataset containing **1,000 records**.

The model predicts one of these beverage categories:

- Elaichi chai
- Ginger tea
- Kiwi tea
- Masala chai
- Plain chai

### Input Features

| Feature | Description |
|---|---|
| `temperature_c` | Temperature in Celsius |
| `humidity_percent` | Humidity percentage |
| `time_of_day_hours` | Time of day represented in hours |

### Target

```text
perfect_order
```

The target represents the recommended beverage for the given conditions.

## 🤖 Machine Learning Models

Three classification algorithms were implemented and compared:

### 1. Random Forest Classifier

A Random Forest classifier with **100 decision trees** was trained on the dataset.

```python
RandomForestClassifier(
    n_estimators=100,
    random_state=42
)
```

**Test accuracy: 99%**

The Random Forest model achieved the strongest performance in the notebook and was selected as the final model.

### 2. Logistic Regression

Logistic Regression was implemented with feature standardization using a Scikit-learn Pipeline.

```python
Pipeline([
    ("scaler", StandardScaler()),
    ("model", LogisticRegression(max_iter=1000, random_state=42))
])
```

**Test accuracy: 71%**

### 3. K-Nearest Neighbors

KNN was also implemented using feature standardization.

```python
Pipeline([
    ("scaler", StandardScaler()),
    ("model", KNeighborsClassifier(n_neighbors=6))
])
```

The notebook compares KNN with the other classifiers using accuracy and confusion matrices.

## 📊 Model Evaluation

The dataset was divided using an **80/20 train-test split**:

- Training samples: **800**
- Testing samples: **200**
- Random state: `42`

Evaluation techniques used:

- Accuracy Score
- Confusion Matrix
- Classification Report
- Model Accuracy Comparison

### Random Forest Classification Report

| Class | Precision | Recall | F1-Score |
|---|---:|---:|---:|
| Elaichi chai | 1.00 | 1.00 | 1.00 |
| Ginger tea | 1.00 | 0.92 | 0.96 |
| Kiwi tea | 1.00 | 1.00 | 1.00 |
| Masala chai | 0.98 | 1.00 | 0.99 |
| Plain chai | 1.00 | 1.00 | 1.00 |
| **Overall Accuracy** | | | **0.99** |

## 💾 Trained Model

The final Random Forest model is saved using `joblib`:

```python
import joblib

joblib.dump(classifier_rf, "chai_model.joblib")
```

The saved model can be loaded later for prediction without retraining:

```python
model = joblib.load("chai_model.joblib")

prediction = model.predict([
    [temperature, humidity, time_of_day]
])
```

## 🛠️ Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Joblib
- Jupyter Notebook

## 📂 Project Structure

```text
Smart-Beverage-Recommender/
│
├── data/
│   └── smart_beverage_recommender.csv
│
├── SmartBeverageRecommender.ipynb
│
├── chai_model.joblib
│
└── README.md
```

## 🔄 Machine Learning Workflow

```text
Dataset
   ↓
Data Loading
   ↓
Data Quality Check
   ↓
Feature Selection
   ↓
Train / Test Split
   ↓
Model Training
   ├── Random Forest
   ├── Logistic Regression
   └── KNN
   ↓
Model Evaluation
   ├── Accuracy
   ├── Confusion Matrix
   └── Classification Report
   ↓
Select Random Forest
   ↓
Save Model with Joblib
```

## 🚀 Future Deployment

The trained model can be integrated into a Django web application where users provide:

```text
Temperature
Humidity
Time of Day
```

and receive a beverage recommendation such as:

```text
Recommended Beverage: Masala chai
```

## ☁️ Live Deployment

The model is deployed as part of the ML platform on Render.

**Live platform:**

`https://machine-learning-models-3d5a.onrender.com/`

> If Smart Beverage Recommender has its own Django route, replace the URL above with the specific model endpoint.

## 📌 Key Learning Outcomes

This project demonstrates:

- Classification using Scikit-learn
- Comparing multiple ML algorithms
- Feature selection
- Train-test splitting
- Feature scaling
- Model evaluation
- Confusion matrix analysis
- Classification reports
- Model serialization using Joblib
- Preparing an ML model for web deployment

## 👨‍💻 Author

**Sheikh Azmatulla**

Python | Django | Machine Learning | Backend Development