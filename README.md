# Machine Learning Models

A collection of practical Machine Learning projects built with **Python, Django, Pandas, NumPy, and Scikit-learn** and deployed as web applications on **Render**.

The project currently includes three interactive ML-based applications:

## 🚀 Live Models

| Model | Description | Live Demo |
|---|---|---|
| 🥤 **Smart Beverage Recommender** | Recommends suitable beverages based on user preferences and input features. | [Open Model](https://machine-learning-models-3d5a.onrender.com/) |
| 🛍️ **Mall Segmentation Persona** | Segments mall customers into different personas based on characteristics such as income and spending behavior, helping identify customer groups. | [Open Model](https://machine-learning-models-3d5a.onrender.com/) |
| ⚔️ **Clash of Clans Upgrade Calculator** | Estimates upgrade resources and time requirements for Clash of Clans, including the effect of Builder Boost on upgrade duration. | [Open Model](https://machine-learning-models-3d5a.onrender.com/) |

> **Note:** The three links above currently point to the deployed Render application. If each model has a separate route, replace the links with the corresponding model URLs.

## 📌 Models Overview

### 🥤 Smart Beverage Recommender

A recommendation system that suggests beverages based on user-provided preferences and relevant input features.

**Key concepts:**
- Recommendation system
- Data preprocessing
- Feature-based prediction
- Machine Learning inference
- Django web interface

### 🛍️ Mall Segmentation Persona

A customer segmentation model that groups mall customers into meaningful personas using customer attributes such as annual income and spending behavior.

The goal is to identify customer segments that can be used for targeted analysis and marketing strategies.

**Key concepts:**
- Customer segmentation
- K-Means clustering
- Feature scaling
- Data visualization
- Persona generation

### ⚔️ Clash of Clans Upgrade Resources & Time

A utility-based ML/data application for estimating the resources and time required to upgrade Clash of Clans buildings and units.

It also considers **Builder Boost** to calculate the adjusted upgrade duration.

**Key concepts:**
- Resource calculation
- Upgrade-time calculation
- Builder Boost adjustment
- Structured game data
- Interactive web interface

## 🛠️ Tech Stack

- **Python**
- **Django**
- **Scikit-learn**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **HTML / CSS**
- **Git & GitHub**
- **Render**

## 📂 Project Structure

```text
Machine-Learning-Models/
│
├── Trained_Data/
│   └── Saved / trained model data
│
├── Training/
│   └── Model training and experimentation
│
├── apps/
│   ├── Smart Beverage Recommender
│   ├── Mall Segmentation Persona
│   └── Clash of Clans
│
├── manage.py
├── requirements.txt
└── README.md
```

> The exact application folders may differ depending on the current project structure.

## ⚙️ Running Locally

Clone the repository:

```bash
git clone https://github.com/SheikhAz/Machine-Learning-Models.git
cd Machine-Learning-Models
```

Create and activate a virtual environment:

```bash
python -m venv .model
```

Windows:

```bash
.model\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run migrations:

```bash
python manage.py migrate
```

Start the Django development server:

```bash
python manage.py runserver
```

Open:

```text
http://127.0.0.1:8000/
```

## ☁️ Deployment

The applications are deployed using **Render**. Render supports deploying Python/Django web services from a connected Git repository and provides a public `onrender.com` URL for each web service. citeturn0search0turn0search1

Live deployment:

**https://machine-learning-models-3d5a.onrender.com/**

## 🎯 Project Goals

This repository demonstrates practical implementation of Machine Learning concepts from **data preprocessing and model training to web-based inference and deployment**.

The main focus is on building small, usable ML applications rather than only training models in notebooks.

## 👨‍💻 Author

**Sheikh Azmatulla**

Backend Developer | Python | Django | Machine Learning

---

⭐ If you find this project useful, consider giving the repository a star.
