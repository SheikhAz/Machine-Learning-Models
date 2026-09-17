# ⚔️ Clash of Clans Upgrade Cost Predictor

A Machine Learning regression project that predicts the **Elixir cost required for a Clash of Clans upgrade** based on the building type, Town Hall level, and current building level.

The project compares multiple regression algorithms and selects the model with the lowest Mean Absolute Error (MAE).

## 🎯 Project Overview

The dataset contains **1,000 Clash of Clans upgrade records**.

Each record contains information such as:

| Feature | Description |
|---|---|
| `upgrade_id` | Unique upgrade identifier |
| `building_type` | Type of building being upgraded |
| `town_hall_level` | Required/current Town Hall level |
| `current_level` | Current level of the building |
| `builder_boost_percent` | Builder boost percentage |
| `builder_count` | Number of builders |
| `upgrade_cost_elixir` | Elixir cost of the upgrade |
| `upgrade_time_hours` | Upgrade duration in hours |

The current notebook trains the model to predict:

```text
upgrade_cost_elixir
```

using:

```text
town_hall_level
current_level
building_type
```

> **Important:** `builder_boost_percent`, `builder_count`, and `upgrade_time_hours` are present in the dataset, but they are not used as input features in the current trained model.

## 🤖 Machine Learning Models

Three regression approaches were implemented and compared.

### 1. Linear Regression

A Linear Regression model is used with:

- `town_hall_level`
- `current_level`
- `building_type`

The categorical `building_type` feature is converted using `OneHotEncoder`.

**Mean Absolute Error:**

```text
135,983.85 Elixir
```

### 2. Polynomial Regression

Polynomial Regression uses **degree-3 polynomial features** for the numerical variables.

This allows the model to capture more complex relationships between:

- Town Hall level
- Current building level
- Upgrade cost

**Mean Absolute Error:**

```text
117,162.95 Elixir
```

### 3. Random Forest Regressor

The Random Forest Regressor is trained using the same preprocessing pipeline as Linear Regression.

```python
RandomForestRegressor(random_state=43)
```

**Mean Absolute Error:**

```text
43,242.18 Elixir
```

The Random Forest model produced the lowest MAE among the three models tested and was saved for deployment.

## 📊 Model Comparison

| Model | Mean Absolute Error |
|---|---:|
| Linear Regression | 135,983.85 Elixir |
| Polynomial Regression | 117,162.95 Elixir |
| Random Forest Regressor | **43,242.18 Elixir** |

### What does MAE mean?

Mean Absolute Error represents the average absolute difference between the actual upgrade cost and the model's predicted upgrade cost.

For the Random Forest model:

```text
MAE ≈ 43,242 Elixir
```

This means that, on the test set, predictions differed from the actual upgrade cost by approximately **43,242 Elixir on average**.

## 🔄 Machine Learning Pipeline

```text
Clash of Clans Upgrade Dataset
             ↓
       Data Inspection
             ↓
       Feature Selection
             ↓
      Train / Test Split
             ↓
      800 Training Rows
      200 Testing Rows
             ↓
      Data Preprocessing
       ┌───────────────┐
       │ Numerical     │
       │ Passthrough   │
       └───────────────┘
              +
       ┌───────────────┐
       │ Building Type │
       │ One-Hot Encode│
       └───────────────┘
             ↓
   ┌─────────────────────────┐
   │ Linear Regression       │
   │ Polynomial Regression   │
   │ Random Forest Regressor │
   └─────────────────────────┘
             ↓
        Model Evaluation
             ↓
       Random Forest
             ↓
    Save with Joblib
```

## 🧪 Train / Test Split

The dataset is divided using:

```python
train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=43
)
```

This results in:

- **800 training records**
- **200 testing records**

## 💾 Saved Model

The final Random Forest pipeline is saved using Joblib:

```python
joblib.dump(
    pipe_rfr,
    "coc_elixir_model.joblib"
)
```

The saved pipeline contains both:

1. Feature preprocessing
2. Random Forest regression model

This makes it possible to load the complete pipeline and make predictions on new input data.

Example:

```python
import joblib

model = joblib.load("coc_elixir_model.joblib")

prediction = model.predict([
    {
        "town_hall_level": 12,
        "current_level": 10,
        "building_type": "Cannon"
    }
])
```

## ⚔️ Example Use Case

A user can provide:

```text
Building Type: Cannon
Town Hall Level: 12
Current Level: 10
```

The trained model can then estimate:

```text
Predicted Elixir Cost: XXXXX Elixir
```

This can be integrated into a web application to provide an interactive upgrade-cost calculator.

## ⏱️ Upgrade Time & Builder Boost

The dataset also contains:

```text
builder_boost_percent
builder_count
upgrade_time_hours
```

The notebook includes an alternative commented target for predicting:

```python
# y = df['upgrade_time_hours']
```

However, the current trained model predicts **Elixir cost**, not upgrade time.

Therefore, the current ML model should be described as an **Upgrade Cost Predictor**.

A future version can extend the application to calculate or predict:

- Upgrade duration
- Builder Boost effect
- Number of builders required
- Total upgrade resources
- Combined resource + time planning

## 🛠️ Tech Stack

- **Python**
- **Pandas**
- **Matplotlib**
- **Scikit-learn**
- **Linear Regression**
- **Polynomial Regression**
- **Random Forest Regressor**
- **OneHotEncoder**
- **ColumnTransformer**
- **Pipeline**
- **Joblib**
- **Jupyter Notebook**

## 📂 Project Structure

```text
Clash-of-Clans-Upgrade/
│
├── data/
│   └── clash_of_clans_upgrades.csv
│
├── clashofclanupgrade.ipynb
├── coc_elixir_model.joblib
└── README.md
```

## ☁️ Deployment

The Machine Learning platform is deployed on **Render**.

### Live Platform

https://machine-learning-models-3d5a.onrender.com/

> If this model has a dedicated Django route, replace the platform URL above with the specific Clash of Clans model URL.

## 📌 Key Learning Outcomes

This project demonstrates:

- Regression Machine Learning
- Categorical feature encoding
- Feature preprocessing with `ColumnTransformer`
- Scikit-learn Pipelines
- Linear Regression
- Polynomial Regression
- Random Forest Regression
- Train-test splitting
- Mean Absolute Error evaluation
- Model comparison
- Model serialization with Joblib
- Preparing an ML model for web deployment

## 👨‍💻 Author

**Sheikh Azmatulla**

Python | Django | Machine Learning | Backend Development