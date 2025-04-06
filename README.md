# ACW-Data-Cleaning-Analysis

Here’s a clean and **extensive README** for your project, covering both **Section A: Data Preprocessing** and **Section B: Data Visualization**, written in a clear and professional tone:

---

# 📊 Customer Data Processing & Visualization Pipeline

## 📁 Project Overview

This project provides a **modular Python pipeline** for transforming, cleaning, and visualizing a customer dataset (`acw_user_data.csv`). The code is structured for **clarity**, **modularity**, and **reusability**. The process includes:

- **Data Cleaning**: Handling missing and inconsistent entries.
- **Data Transformation**: Converting flat CSV data into structured JSON with nested fields.
- **Feature Engineering**: Adding computed metrics like Salary-Commute Ratio.
- **Filtering**: Separating Retired vs Employed individuals and flagging invalid credit cards.
- **Visualization**: Univariate and multivariate analysis using `matplotlib` and `seaborn`.

> ⚠️ **Note**: All tasks are implemented in a modular (not sequential) fashion. You’ll find the corresponding task number as a comment above each function.

---

## 🧩 Section A: Data Preprocessing

### 🔌 Libraries Used

```python
import csv
import json
from datetime import datetime
```

### 🗂️ Modular Tasks and Implementation

#### ✅ Task 1: Load and Parse CSV

- Load data using `csv.DictReader`.
- Count and report rows with missing or invalid `Dependants` values.

#### ✅ Task 2 & 3: Transform CSV Rows to Nested JSON Format

- Restructures flat CSV rows into **nested dictionaries** for fields like `Address`, `CreditCard`, and `Vehicle`.
- Safely casts values using custom functions like `safe_int`, `safe_float`, `safe_bool`.

#### ✅ Task 4: Save Transformed Data to JSON

- Writes output to:  
  - `processed.json` (all customers)  
  - `retired.json` (only retired users)  
  - `employed.json` (only employed users)  

#### ✅ Task 5: Retired and Employed Data Split

- Based on the boolean `Retired` field.

#### ✅ Task 6: Flag Customers with Invalid Credit Card

- Flags cards where the difference between expiry and start date is **greater than 10 years**.
- Saved to `remove_ccard.json`.

#### ✅ Task 7: Compute Salary-to-Commute Ratio

- New field `Salary-Commute` = `Salary ÷ Distance Commuted`.
- Sorted output is saved in `commute.json`.

---

## 🛠️ Type Casting Utility Functions

To ensure clean data conversion:

```python
def safe_int(value): ...
def safe_bool(value): ...
def safe_float(value): ...
```

A mapping dictionary (`TYPE_CASTS`) assigns each relevant column a corresponding cast function.

---

## 🧠 Execution

To run the preprocessing pipeline:

```bash
python your_script_name.py
```

Upon successful execution, you'll see messages like:

```
⚠️ Problematic Dependant Rows: [22, 110, 180, ...]
✅ Data saved to processed.json successfully!
✅ Data saved to retired.json successfully!
✅ Data saved to employed.json successfully!
✅ Data saved to remove_ccard.json successfully!
✅ Data saved to commute.json successfully!
```

---

## 📈 Section B: Data Visualization

### 📚 Libraries Used

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import os
```

### 📦 Data Loading and Cleaning

- Input: `acw_user_data.csv`
- Converts relevant columns to numeric using `pd.to_numeric(..., errors='coerce')`
- Handles missing `Dependants` by filling with 0.

---

## 📊 Tasks and Plots

### 📍 Task 1: Mean and Median Visualizations

- **Salary Histogram** with Mean Line  
- **Age Boxplot** with Median Line  

### 📍 Task 2: Univariate Visualizations

- **Age Histogram** (Bin width = 5)
- **Dependents Countplot**
- **Age Distribution by Marital Status** (stacked histogram)

### 📍 Task 3: Multivariate Visualizations

- **Scatterplot**: Distance Commuted vs. Salary
- **Regression Plot**: Age vs. Salary (with best-fit line)

### 🖼️ Output

All plots are saved to a directory named `/plots`:

```
/plots
├── salary_distribution.png
├── age_boxplot.png
├── age_histogram.png
├── dependents_count.png
├── distance_vs_salary.png
...
```

---

## 📌 Folder Structure

```
project-root/
├── acw_user_data.csv
├── main_script.py
├── processed.json
├── retired.json
├── employed.json
├── remove_ccard.json
├── commute.json
└── plots/
    ├── salary_distribution.png
    ├── age_boxplot.png
    ...
```

---

## ✅ Features Summary

| Feature                       | Description |
|------------------------------|-------------|
| **Data Nesting**             | Flattens CSV → Nested JSON |
| **Type Safety**              | Custom functions ensure error-free conversion |
| **Error Detection**          | Logs rows with missing `Dependants` |
| **Credit Card Checker**      | Flags unrealistic validity periods |
| **Salary Commute Metric**    | Adds a derived metric for economic insight |
| **Plotting**                 | High-quality visualizations for analysis |

---

## 📌 Requirements

- Python 3.x
- Libraries: `pandas`, `matplotlib`, `seaborn`, `numpy`

Install all dependencies:

```bash
pip install pandas matplotlib seaborn numpy
```

---

## 🚀 Run Instructions

```bash
python main_script.py
```

---

## ✨ Authors

- *Muhammad Amaz Majid*
  
