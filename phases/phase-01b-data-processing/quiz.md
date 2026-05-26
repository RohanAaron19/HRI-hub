# Phase 01B -- Data Processing Quiz

> Attempt all questions before checking [solutions.md](solutions.md).

---

## Easy

**Q1.** A dataset has a column "Education Level" with values: High School, Bachelor, Master, PhD. What data type is this?

- A) Nominal -- categories with no order
- B) Ordinal -- categories with a meaningful order
- C) Interval -- ordered with equal spacing
- D) Ratio -- ordered with a true zero

---

**Q2.** You have a feature "City" with 500 unique values. Why is standard One-Hot Encoding a problem here?

- A) One-hot encoding only works for numerical data
- B) It creates 500 new binary columns, massively expanding dimensionality (the curse of dimensionality)
- C) One-hot encoding always causes overfitting
- D) It cannot handle string values

---

## Medium

**Q3.** A feature has values: [1, 2, 3, 4, 100]. You apply min-max scaling. What is the scaled value of 100?

- A) 0.0
- B) 0.5
- C) 1.0
- D) 100.0

---

**Q4.** What is the key difference between Hot-Deck and Cold-Deck imputation?

- A) Hot-Deck uses the mean; Cold-Deck uses the median
- B) Hot-Deck uses values from the same dataset; Cold-Deck uses donor values from a completely separate dataset
- C) Hot-Deck works for numerical data; Cold-Deck works for categorical
- D) They are the same method with different names

---

## Hard

**Q5.** You are doing feature selection. Your dataset has 200 features and only 150 samples. Which approach carries the highest overfitting risk?

- A) Filter methods using correlation
- B) Wrapper methods (forward/backward selection) -- they evaluate subsets on the actual model and can overfit to the training data
- C) Embedded methods using Lasso
- D) Removing features with near-zero variance

---

**Q6.** A column "Income" has a strong right skew (most people earn $40k but a few earn $10M). Which transformation is most appropriate before feeding this to a linear regression model?

- A) Min-max scaling to [0,1]
- B) Log transform -- compresses the long right tail, making distribution more Gaussian
- C) One-hot encoding
- D) Backward elimination
