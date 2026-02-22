# 🦠 COVID-19 Early Case Trend Analysis & Recovery Insights

## 📌 Project Overview

This project was developed for **HealthGuard Analytics Pvt. Ltd.**, a healthcare data analytics firm collaborating with a national public health authority.

The objective is to analyze early-stage infectious disease (COVID-19) case data to uncover patterns in:

- Patient demographics  
- Infection spread  
- Recovery timelines  
- Regional impact  
- Factors influencing recovery duration  

The insights generated from this analysis support data-driven public health decisions, screening optimization, and isolation planning.


## 🏢 Business Context

During the early phase of an outbreak, rapid analytical insights are critical.  
This project leverages patient-level COVID-19 case data to:

- Identify high-risk demographic groups  
- Understand infection transmission patterns  
- Evaluate recovery trends  
- Compare regional outbreak severity  
- Explore predictors of recovery duration  


## 🎯 Problem Statement

The public health authority requested answers to the following:

### 1️⃣ Who is getting infected?
- Age distribution  
- Gender distribution  
- Country & region analysis  

### 2️⃣ How are infections spreading?
- Primary infection reasons  
- Infection order (primary vs secondary cases)  
- Contact exposure levels  

### 3️⃣ What are the recovery trends?
- Recovery duration (confirmed → released)  
- Average recovery time  

### 4️⃣ Which regions are most impacted?
- Confirmed cases by region  
- Released cases comparison  

### 5️⃣ What factors influence recovery time?
- Age  
- Contact number  
- Infection order  


## 🛠️ Tech Stack

### Programming Language
- Python 🐍

### Libraries Used
- NumPy  
- Pandas  
- Matplotlib  
- Seaborn  
- Scikit-learn  

### Statistical Methods
- Descriptive Statistics  
- Correlation Analysis  
- Linear Regression (optional predictive modeling)  


## 📂 Dataset Information

**Source:** Public health COVID-19 patient-level dataset  

### Attributes Included:

#### 👤 Demographics
- `sex`
- `birth_year`
- `country`
- `region`

#### 🦠 Infection Details
- `infection_reason`
- `infection_order`
- `infected_by`

#### 📊 Exposure Metrics
- `contact_number`

#### 📅 Timeline Data
- `confirmed_date`
- `released_date`
- `deceased_date`

#### 📌 Case Outcome
- `state` (released, isolated, deceased)

Dataset Link:  
https://drive.google.com/file/d/1TXoqikmE0S3LGem8Ig-GktaJJyZPGMgN/view


## 🔎 Exploratory Data Analysis (EDA)

The project includes:

- Data cleaning & missing value treatment  
- Date parsing and feature engineering  
- Creation of recovery duration variable  
- Outlier detection  
- Summary statistics  
- Distribution visualizations  
- Regional comparisons  


## 📐 Feature Engineering

A new feature was created to calculate recovery duration:

```python
df["confirmed_date"] = pd.to_datetime(df["confirmed_date"])
df["released_date"] = pd.to_datetime(df["released_date"])

df["recovery_days"] = (df["released_date"] - df["confirmed_date"]).dt.days
```

This enables quantitative analysis of recovery duration.


## 📊 Statistical Analysis

### Descriptive Statistics
- Mean, median recovery time  
- Average age by outcome  
- Contact exposure averages  
- Gender-wise case distribution  

### Correlation Analysis
- Age vs recovery time  
- Contact number vs recovery time  
- Infection order vs recovery time  

Example:

```python
df[["age", "contact_number", "infection_order", "recovery_days"]].corr()


## 📈 Linear Regression Model (Optional)

Model Objective: Predict Recovery Duration (days)

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score
from sklearn.model_selection import train_test_split

# Feature Engineering
df["age"] = 2020 - df["birth_year"]

X = df[["age", "contact_number", "infection_order"]]
y = df["recovery_days"]

# Handle missing values
X = X.fillna(0)
y = y.fillna(0)

# Train-Test Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model Training
model = LinearRegression()
model.fit(X_train, y_train)

# Prediction
predictions = model.predict(X_test)

# Evaluation
print("R2 Score:", r2_score(y_test, predictions))
print("Coefficients:", model.coef_)
```

Model evaluation includes:
- R² Score  
- Coefficient interpretation  
- Residual analysis  


## 📁 Project Structure


COVID19-Early-Case-Analysis/
│
├── data/
│   └── patient_data.csv
│
├── notebooks/
│   └── EDA_and_Modeling.ipynb
│
├── src/
│   └── analysis.py
│
├── visuals/
│   └── charts/
│
├── requirements.txt
└── README.md



## ▶️ How to Run the Project

### 1️⃣ Clone the repository
```bash
git clone https://github.com/your-username/covid19-early-case-analysis.git


### 2️⃣ Navigate into the directory
```bash
cd covid19-early-case-analysis
```

### 3️⃣ Install dependencies
```bash
pip install -r requirements.txt
```

### 4️⃣ Run Jupyter Notebook
```bash
jupyter notebook
```

---

## 📊 Expected Outcomes

✔ Clear understanding of early outbreak infection patterns  
✔ Identification of high-risk demographic groups  
✔ Evidence-based recovery insights  
✔ Statistical support for healthcare policy decisions  
✔ Identification of statistically significant recovery predictors  

---

## 🚀 Optional Extensions

- Advanced Feature Engineering  
- Cross-validation  
- Residual distribution plots  
- Feature importance analysis  
- Deploy as Streamlit Dashboard  
- Convert analysis into Power BI dashboard  


## 📜 License

This project is for educational and analytical purposes only.  
Data belongs to the respective public health authority.


## 👨‍💻 Author

HealthGuard Analytics Pvt. Ltd.  
Healthcare Data Science & Public Health Intelligence
