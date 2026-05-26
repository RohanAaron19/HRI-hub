# Phase 01B -- Assignment: Complete Data Processing Pipeline

> Build a full data preprocessing pipeline from raw data to model-ready features. This is what every real ML project starts with.

---

## Setup

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.preprocessing import StandardScaler, MinMaxScaler, LabelEncoder
from sklearn.impute import KNNImputer, SimpleImputer
from sklearn.pipeline import Pipeline
from sklearn.compose import ColumnTransformer
from sklearn.model_selection import train_test_split
```

---

## Part 1 -- Create a messy dataset

```python
np.random.seed(42)
n = 500

data = pd.DataFrame({
    'age':        np.random.normal(35, 10, n),
    'income':     np.random.exponential(50000, n),  # right-skewed
    'education':  np.random.choice(['High School','Bachelor','Master','PhD'], n),
    'city':       np.random.choice(['NYC','LA','Chicago','Houston','Phoenix'], n),
    'score':      np.random.normal(70, 15, n),
    'target':     np.random.randint(0, 2, n)
})

# Introduce problems
data.loc[np.random.choice(n, 50), 'age'] = np.nan       # missing values
data.loc[np.random.choice(n, 30), 'income'] = np.nan    # missing values
data.loc[np.random.choice(n, 5), 'age'] = -5            # impossible values
data.loc[np.random.choice(n, 5), 'income'] = 5000000    # extreme outliers

print(data.head())
print(data.info())
print(data.describe())
```

---

## Part 2 -- EDA

```python
# Univariate: continuous
fig, axes = plt.subplots(1, 3, figsize=(15, 4))
for ax, col in zip(axes, ['age', 'income', 'score']):
    data[col].hist(bins=30, ax=ax)
    ax.set_title(col)
plt.tight_layout()
plt.savefig('univariate_continuous.png')

# Univariate: categorical
data['education'].value_counts().plot(kind='bar')
plt.title('Education distribution')
plt.savefig('univariate_categorical.png')

# Bivariate: correlation heatmap
plt.figure(figsize=(6, 5))
sns.heatmap(data[['age','income','score','target']].corr(), annot=True, fmt='.2f')
plt.title('Correlation heatmap')
plt.savefig('correlation_heatmap.png')
```

Write 2 sentences: What do you observe? Which features look most correlated with the target?

---

## Part 3 -- Data cleaning

```python
# Detect impossible values
print("Ages below 0:", (data['age'] < 0).sum())
data.loc[data['age'] < 0, 'age'] = np.nan  # treat as missing

# Detect outliers using IQR
Q1 = data['income'].quantile(0.25)
Q3 = data['income'].quantile(0.75)
IQR = Q3 - Q1
upper_bound = Q3 + 1.5 * IQR
print(f"Income outliers above {upper_bound:.0f}: {(data['income'] > upper_bound).sum()}")
data.loc[data['income'] > upper_bound, 'income'] = upper_bound  # cap outliers

# Handle special values
data = data.replace([np.inf, -np.inf], np.nan)
print("Missing values per column:")
print(data.isnull().sum())
```

---

## Part 4 -- Imputation

```python
# Mean imputation for age
data['age'].fillna(data['age'].mean(), inplace=True)

# KNN imputation for income (uses other features)
imputer = KNNImputer(n_neighbors=5)
data[['income']] = imputer.fit_transform(data[['income']])

print("Missing values after imputation:")
print(data.isnull().sum())
```

---

## Part 5 -- Encoding and scaling

```python
# Ordinal encoding for education (order matters)
edu_order = ['High School', 'Bachelor', 'Master', 'PhD']
data['education_encoded'] = data['education'].map({v: i for i, v in enumerate(edu_order)})

# One-hot encoding for city
data = pd.get_dummies(data, columns=['city'], drop_first=True)

# Log transform for income (right-skewed)
data['income_log'] = np.log1p(data['income'])

# Standardize continuous features
scaler = StandardScaler()
data[['age', 'score', 'income_log']] = scaler.fit_transform(
    data[['age', 'score', 'income_log']]
)

print(data.head())
print(data.shape)
```

---

## Part 6 -- Sklearn Pipeline (the proper way)

```python
from sklearn.preprocessing import OrdinalEncoder, OneHotEncoder

X = data.drop(['target', 'education', 'income', 'income_log', 'education_encoded'], axis=1, errors='ignore')
y = data['target']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

print(f"Training set: {X_train.shape}")
print(f"Test set: {X_test.shape}")
print("Data processing pipeline complete. Ready for model training.")
```

---

## Checklist

- [ ] Messy dataset created with missing values, outliers, impossible values
- [ ] EDA: univariate histograms, bivariate correlation heatmap
- [ ] Impossible values detected and corrected
- [ ] Outliers detected using IQR and capped
- [ ] Special values (Inf, NaN) handled
- [ ] Mean and KNN imputation applied
- [ ] Ordinal encoding for education, one-hot for city
- [ ] Log transform applied to skewed income
- [ ] StandardScaler applied to continuous features
- [ ] Written observations from EDA

## What to commit

```bash
git add phases/phase-01b-data-processing/
git commit -m "Phase 01B assignment: complete data processing pipeline"
git push
```
