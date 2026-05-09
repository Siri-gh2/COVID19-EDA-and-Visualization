# 🌍 COVID-19 EDA and Visualization

A Python-based Exploratory Data Analysis (EDA) and Data Visualization project focused on analyzing global COVID-19 data using Pandas, NumPy, Matplotlib, and Seaborn.

This project involves data cleaning, preprocessing, statistical analysis, feature engineering, and visualization techniques to uncover meaningful insights about confirmed cases, deaths, recoveries, active cases, and country-wise pandemic trends.

---

# 📌 Project Objectives

* Perform data cleaning and preprocessing
* Handle missing values
* Analyze global COVID-19 trends
* Compare confirmed, recovered, active, and death cases
* Identify highly affected regions
* Perform statistical and correlation analysis
* Apply feature engineering techniques
* Create meaningful visualizations for better insights

---

# 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook / Google Colab

---

# 📂 Dataset Features

The dataset contains information related to:

* Province / State
* Country / Region
* Confirmed Cases
* Death Cases
* Recovered Cases
* Active Cases

---

# ⚙️ Project Workflow

## 1️⃣ Importing Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 2️⃣ Loading Dataset

```python
df = pd.read_csv('Covid19Data.csv')
```

---

## 3️⃣ Data Cleaning

* Checked dataset shape and information
* Handled missing values
* Filled null values in Province/State column

```python
df['Province/State'].fillna('Unknown', inplace=True)
```

---

## 4️⃣ Data Analysis

### ✅ Region-wise COVID Analysis

```python
df.groupby('Country/Region')[['Confirmed', 'Deaths', 'Recovered', 'Active']].sum()
```

### ✅ Most Affected Regions

```python
df.groupby('Country/Region').Confirmed.sum().sort_values(ascending=False).head(10)
```

### ✅ Minimum Death Cases Analysis

```python
df.groupby('Country/Region').Deaths.sum().sort_values(ascending=True)
```

### ✅ India COVID Analysis

```python
df[df['Country/Region'] == "India"]
```

---

# 📈 Visualizations Included

## ✅ Missing Values Heatmap

```python
sns.heatmap(df.isnull())
plt.show()
```

---

## ✅ Top 10 Countries by Confirmed Cases

```python
top_confirmed = df.groupby('Country/Region')['Confirmed'].sum().sort_values(ascending=False).head(10)

top_confirmed.plot(kind='bar', figsize=(10,5))
plt.show()
```

---

## ✅ Deaths vs Recovered Comparison

```python
country_data = df.groupby('Country/Region')[['Deaths','Recovered']].sum().head(10)

country_data.plot(kind='bar', figsize=(10,5))
plt.show()
```

---

## ✅ Active Cases Distribution

```python
sns.histplot(df['Active'], bins=30)
plt.show()
```

---

## ✅ Correlation Heatmap

```python
sns.heatmap(df[['Confirmed','Deaths','Recovered','Active']].corr(),
            annot=True,
            cmap='coolwarm')

plt.show()
```

---

# 🧠 Feature Engineering

## ✅ Recovery Rate

```python
df['Recovery Rate'] = (df['Recovered'] / df['Confirmed']) * 100
```

---

## ✅ Death Rate

```python
df['Death Rate'] = (df['Deaths'] / df['Confirmed']) * 100
```

These engineered features help in deeper analytical understanding of recovery and fatality patterns across different regions.

---

# 📊 Key Insights

* Certain countries recorded significantly higher confirmed cases than others.
* Strong positive correlation exists between confirmed and recovered cases.
* Recovery and death rates vary across regions.
* Active case distributions highlighted differences in outbreak severity.
* Visualization techniques helped identify important pandemic trends and relationships.

---

# 🚀 Future Improvements

* Build an interactive Streamlit dashboard
* Add real-time COVID API integration
* Perform predictive analytics using Machine Learning
* Create geographical visualizations using Plotly
* Deploy the project online

---

# 📁 Project Structure

```bash
COVID19-EDA-and-Visualization/
│
├── Covid19Data.csv
├── covid_19.py
├── README.md
```

---

# 👩‍💻 Author

**Korupolu Siri**
