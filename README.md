# data-cleaning-and-visualization-project
Data Cleaning &amp; Visualization Project using Python, Pandas, Matplotlib, and Seaborn. Learn data preprocessing, exploratory data analysis (EDA), visualization techniques, and data storytelling through real-world datasets.
# Data Cleaning & Visualization Project

## Overview

This project demonstrates how to clean, preprocess, analyze, and visualize a raw dataset using Python.

The workflow includes:

- Handling missing values
- Removing duplicates
- Detecting and treating outliers
- Exploratory Data Analysis (EDA)
- Data visualization
- Insight generation and reporting

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Project Workflow

1. Load Raw Dataset
2. Clean Data
3. Handle Missing Values
4. Remove Duplicates
5. Detect Outliers
6. Perform EDA
7. Create Visualizations
8. Generate Insights

## Installation

```bash
git clone https://github.com/yourusername/data-cleaning-visualization-project.git

cd data-cleaning-visualization-project

pip install -r requirements.txt
```

## Run Project

```bash
python src/data_cleaning.py
python src/visualization.py
```

## Example Visualizations

- Histogram
- Scatter Plot
- Correlation Heatmap
- Category Count Plot

## Learning Outcomes

- Data preprocessing
- Data visualization
- Exploratory data analysis
- Data storytelling

## requirements.txt
pandas
numpy
matplotlib
seaborn
jupyter
openpyxl

reports/project_report.md
# Project Report

src/data_cleaning.py
import pandas as pd

# Load dataset
df = pd.read_csv("data/raw/dataset.csv")

print("Original Shape:", df.shape)

# Remove duplicates
df.drop_duplicates(inplace=True)

# Fill missing numeric values
numeric_cols = df.select_dtypes(include="number").columns

for col in numeric_cols:
    df[col].fillna(df[col].mean(), inplace=True)

# Fill missing categorical values
categorical_cols = df.select_dtypes(include="object").columns

for col in categorical_cols:
    df[col].fillna(df[col].mode()[0], inplace=True)

print("Cleaned Shape:", df.shape)

# Save cleaned data
df.to_csv("data/processed/cleaned_data.csv", index=False)

print("Cleaned dataset saved.")
src/visualization.py
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("data/processed/cleaned_data.csv")

# Histogram
plt.figure(figsize=(8,5))
sns.histplot(df.select_dtypes(include="number").iloc[:,0], kde=True)
plt.title("Distribution Plot")
plt.savefig("reports/figures/distribution.png")

# Correlation Heatmap
plt.figure(figsize=(10,8))
sns.heatmap(
    df.corr(numeric_only=True),
    annot=True,
    cmap="coolwarm"
)
plt.title("Correlation Heatmap")
plt.savefig("reports/figures/correlation_heatmap.png")

plt.show()
src/utils.py
def print_separator():
    print("=" * 50)
## Dataset Overview

Provide information about:

- Number of rows
- Number of columns
- Data types

## Data Cleaning

### Missing Values

Describe how missing values were handled.

### Duplicates

Number of duplicate rows removed.

### Outliers

Methods used to detect and remove outliers.

## Visualizations

### Distribution Analysis

Key observations.

### Correlation Analysis

Important relationships found.

## Conclusions

Summarize the insights gained from the dataset.
