# Phase 01B -- Quiz Solutions

---

## Q1 -- Answer: B (Ordinal)

Education level has a clear meaningful order: High School < Bachelor < Master < PhD. However, the differences between levels are NOT necessarily equal (the jump from High School to Bachelor is arguably larger than Bachelor to Master). This makes it ordinal, not interval. In practice, you can encode ordinal data with integers (1, 2, 3, 4) preserving the order, unlike nominal data which requires one-hot encoding.

---

## Q2 -- Answer: B

One-hot encoding a column with 500 unique cities creates 500 new binary columns. With a dataset of, say, 1000 rows, you now have more features than meaningful signal. This causes the curse of dimensionality -- models struggle, training slows down, and overfitting risk skyrockets. Solutions: feature hashing (map to a fixed-size vector), target encoding (replace category with mean of target), or embedding layers in neural networks.

---

## Q3 -- Answer: C (1.0)

Min-max formula: x_scaled = (x - x_min) / (x_max - x_min) = (100 - 1) / (100 - 1) = 99/99 = 1.0

The maximum value always maps to 1.0, the minimum to 0.0. Notice that the outlier 100 has disproportionate influence -- everyone else gets compressed into [0.0, 0.03]. This is why Robust Scaling (using median and IQR instead of min/max) is preferred when outliers are present.

---

## Q4 -- Answer: B

- **Hot-Deck**: finds the first missing value and uses the cell value immediately prior in the same dataset to impute. Stays within the same data distribution.
- **Cold-Deck**: selects donor values from an entirely different dataset -- useful when no prior value exists or when the external dataset better represents the true distribution.

Both are historical imputation methods. In modern practice, KNN Imputer or MICE are preferred because they use multivariate information rather than just proximity in the data file.

---

## Q5 -- Answer: B

Wrapper methods evaluate every candidate feature subset by actually training and testing the model. With 200 features and only 150 samples, exhaustive wrapper search will find a subset that performs well on training data purely by chance -- the model has more degrees of freedom than it has data to constrain them. This is a textbook recipe for overfitting.

Filter methods (correlation, chi-square) are computed independently of the model, so they cannot overfit in this way. Embedded methods (Lasso) use regularization which explicitly penalizes complexity.

---

## Q6 -- Answer: B

A right-skewed income distribution violates the assumption in linear regression that residuals are normally distributed. The log transform compresses large values: log(10,000,000) = 7 vs log(40,000) = 4.6 -- the extreme outliers are pulled back toward the bulk of the data. The resulting distribution is much more Gaussian, which makes linear regression assumptions hold much better. In code: `df['income_log'] = np.log1p(df['income'])` (log1p handles zeros safely).
