# Zomato EDA Project 🍽️📊

## Project Overview
This project is based on **Exploratory Data Analysis (EDA)** using the Zomato Restaurant Dataset.

The main objective of this project is to analyze restaurant data from different countries and gain useful business insights related to:

- Restaurant ratings
- Online delivery services
- Table booking availability
- Country-wise restaurant distribution
- City-wise analysis
- Popular cuisines
- Customer voting patterns

The project is performed using **Python**, **Pandas**, **NumPy**, **Matplotlib**, and **Seaborn**.

---

# Problem Statement
Zomato contains restaurant information from multiple countries.

The dataset includes details such as:

- Restaurant names
- Locations
- Ratings
- Cuisines
- Online delivery options
- Price range
- Votes

The goal of this project is to clean the data, handle missing values, and perform detailed exploratory data analysis to extract meaningful insights and patterns.

---

# Technologies Used 🛠️

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Google Colab

---

# Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

# Dataset Information

The project uses two datasets:

1. **Zomato Dataset**
   - Contains restaurant information

2. **Country Code Dataset**
   - Contains mapping of country codes with country names

---

# Data Loading

The dataset generated a `UnicodeDecodeError` while loading because of encoding issues.

To solve this problem, the dataset was loaded using `latin-1` encoding.

```python
df = pd.read_csv('zomato.csv', encoding='latin-1')
```

---

# Steps Performed in EDA 📌

## 1. Data Understanding

- Checked dataset shape
- Viewed columns
- Inspected data types
- Generated statistical summary

Functions used:

```python
df.shape
df.columns
df.info()
df.describe()
```

---

## 2. Missing Value Analysis

The dataset was checked for missing values using:

```python
df.isnull().sum()
```

### Observation
- Only the `Cuisines` column contained missing values.

### Heatmap Visualization

```python
sns.heatmap(df.isnull(), yticklabels=False, cbar=False, cmap='viridis')
```

Purpose:
- Visualize missing values in the dataset

---

## 3. Data Merging

The Zomato dataset was merged with the Country Code dataset using:

```python
df3 = pd.merge(df, df2, on='Country Code', how='left')
```

Purpose:
- To map country codes with actual country names

---

## 4. Country-wise Analysis 🌍

### Findings
- India has the highest number of Zomato restaurants.
- After India, the United States and United Kingdom have the highest records.

### Pie Chart Visualization

```python
plt.pie(country_val[:3], labels=country_name[:3], autopct='%1.2f%%')
```

---

## 5. Rating Analysis ⭐

Ratings were grouped using:

```python
df3.groupby(['Aggregate rating', 'Rating color', 'Rating text']).size()
```

### Rating Categories

| Rating Range | Category |
|---|---|
| 4.5 - 4.9 | Excellent |
| 4.0 - 4.4 | Very Good |
| 3.5 - 3.9 | Good |
| 2.5 - 3.4 | Average |
| 1.8 - 2.4 | Poor |

### Observations
- Most restaurants are rated between **2.5 and 3.9**
- A large number of restaurants are **not rated**
- Very few restaurants have ratings above **4.5**

---

## 6. Rating Visualization 📈

### Bar Plot

```python
sns.barplot(x='Aggregate rating', y='Rating Count', data=ratings)
```

### Count Plot

```python
sns.countplot(x='Rating color', data=ratings)
```

Purpose:
- Understand distribution of ratings visually

---

## 7. Zero Rating Analysis

Countries having restaurants with zero ratings were identified.

### Observation
- India has the highest number of unrated restaurants.

---

## 8. Currency Analysis 💰

Analyzed which currency is used in different countries.

```python
df3.groupby(['Country', 'Currency']).size()
```

Purpose:
- Understand country-specific currency usage

---

## 9. Online Delivery Analysis 🚚

Checked which countries support online delivery.

### Observation
- Online delivery services are mainly available in:
  - India
  - UAE

---

## 10. City-wise Analysis 🏙️

Top cities with maximum restaurants were analyzed.

### Observation
- New Delhi has the highest number of restaurants.
- Gurgaon and Noida also contribute significantly.

### Pie Chart

```python
plt.pie(city_val[:5], labels=city_name[:5], autopct='%1.2f%%')
```

---

## 11. Cuisine Analysis 🍜

Most popular cuisines were identified.

### Top Cuisines
- North Indian
- Chinese
- Fast Food
- Mughlai
- Cafe
- Bakery

### Code

```python
df3['Cuisines'].value_counts().head(10)
```

---

# Key Insights 📊

- India dominates the Zomato dataset.
- Most restaurants fall under average to good ratings.
- Online delivery services are mostly concentrated in India.
- North Indian cuisine is the most popular cuisine.
- Many restaurants are still unrated.
- New Delhi contains the maximum number of listed restaurants.

---

# Data Visualization Used 📉

The following visualizations were used:

- Heatmaps
- Pie Charts
- Bar Plots
- Count Plots

These visualizations helped in better understanding patterns and trends in the dataset.

---

# Conclusion ✅

This project successfully performed Exploratory Data Analysis on the Zomato dataset and extracted valuable insights related to restaurant distribution, ratings, cuisines, and online delivery services.

The analysis helps understand customer preferences, restaurant trends, and country-wise business distribution.

---

# Future Improvements 🚀

- Build a Restaurant Recommendation System
- Perform Sentiment Analysis on reviews
- Create Interactive Dashboards using Power BI or Tableau
- Apply Machine Learning models for rating prediction

---

# How to Run the Project ▶️

## 1. Clone the repository

```bash
git clone <https://github.com/aot-abhishekyadav/zomato_EDA1/>
```

## 2. Install required libraries

```bash
pip install pandas numpy matplotlib seaborn
```

## 3. Run the notebook

Open the notebook in:
- Jupyter Notebook
- Google Colab

---

# Author 👨‍💻

**Abhishek Yadav**

Machine Learning & Data Analysis Enthusiast
