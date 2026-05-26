# Phase 01B -- Data Processing

> **Time estimate:** 3-4 weeks  
> **Rule:** Every row has a quiz question. Answer it before moving on. Every 3-4 concepts has a mini assignment -- code it, don't skip it.

---

## Section 1 -- Data types

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.1 | Nominal data: mutually exclusive categories, no order | [StatQuest -- Types of Data](https://www.youtube.com/watch?v=dwFsRZv4oHA) | Is "blood type" nominal, ordinal, interval, or ratio? Why? |
| DP.2 | Ordinal data: ordered categories, differences not meaningful | [StatQuest -- Types of Data](https://www.youtube.com/watch?v=dwFsRZv4oHA) | Is "satisfaction rating 1-5" ordinal or interval? Does the gap between 1 and 2 equal the gap between 4 and 5? |
| DP.3 | Interval data: ordered, equal spacing, no true zero | [StatQuest -- Types of Data](https://www.youtube.com/watch?v=dwFsRZv4oHA) | Why is Celsius temperature interval and not ratio? What does "no true zero" mean? |
| DP.4 | Ratio data: all interval properties plus a true zero | [StatQuest -- Types of Data](https://www.youtube.com/watch?v=dwFsRZv4oHA) | Is income ratio or interval? Can you say someone earning $100k earns "twice as much" as someone earning $50k? |

> **Mini Assignment DP-1:** Open a dataset (use Titanic from seaborn). For each column, classify it as Nominal, Ordinal, Interval, or Ratio. Write your answers with a justification for each. Which columns would need one-hot encoding? Which would need ordinal encoding?

---

## Section 2 -- Exploratory Data Analysis (EDA)

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.5 | Variable identification: predictor vs target | [CampusX -- Understanding your data](https://www.youtube.com/watch?v=mJlRTUuVr04) | In a house price prediction problem, which columns are predictors and which is the target? |
| DP.6 | Univariate analysis: continuous features | [CampusX -- Univariate Analysis](https://www.youtube.com/watch?v=4HyTlbHUKSw) | What does a right-skewed histogram look like? What does it tell you about the data? |
| DP.7 | Univariate analysis: categorical features | [CampusX -- Univariate Analysis](https://www.youtube.com/watch?v=4HyTlbHUKSw) | How does a frequency table differ from a histogram? When would you use each? |

> **Mini Assignment DP-2:** Load the House Prices dataset from Kaggle. (1) Plot histograms for `SalePrice`, `LotArea`, and `YearBuilt`. (2) Make a bar chart of `Neighborhood` frequency. (3) Which numeric feature has the most skew? (4) What is the most common neighborhood?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.8 | Bivariate analysis: scatter plot and correlation heatmap | [CampusX -- Bivariate Analysis](https://www.youtube.com/watch?v=6D3VtEfCw7w) | What does a Pearson correlation of -0.8 between two features mean? Is that good or bad for a model? |
| DP.9 | Bivariate analysis: two-way table and stacked column chart | [CampusX -- Bivariate Analysis](https://www.youtube.com/watch?v=6D3VtEfCw7w) | In a two-way table of Survived vs Pclass, what does the cell (Survived=1, Pclass=1) represent? |
| DP.10 | Chi-square test for categorical variable relationships | [StatQuest -- Chi-square test](https://www.youtube.com/watch?v=2QeDRsxSF9M) | What is the null hypothesis in a chi-square test? What does a p-value of 0.001 tell you? |
| DP.11 | T-test for comparing means between two groups | [StatQuest -- t-tests](https://www.youtube.com/watch?v=0Pd3dc1GcHc) | When do you use a t-test vs a chi-square test? What assumptions does a t-test make? |
| DP.12 | ANOVA for comparing means across 3 or more groups | [StatQuest -- ANOVA](https://www.youtube.com/watch?v=0Pd3dc1GcHc) | Why can't you just run multiple t-tests instead of ANOVA? What problem does that cause? |

> **Mini Assignment DP-3:** Using the Titanic dataset: (1) Make a correlation heatmap of all numeric columns. (2) Run a chi-square test between `Survived` and `Pclass`. Is the relationship significant? (3) Run a t-test comparing ages of survivors vs non-survivors. (4) Run ANOVA on fare prices across the three passenger classes. Interpret each result in one sentence.

---

## Section 3 -- Feature cleaning

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.13 | Detecting missing values: `isna()`, `isnull()`, heatmap | [CampusX -- Missing values overview](https://www.youtube.com/watch?v=aUnNWZorGmk) | What does `df.isnull().sum()` tell you? If 40% of a column is missing, what are your options? |
| DP.14 | Special values: Inf, -Inf, NA, NaN in numeric data | [Corey Schafer -- Python data cleaning](https://www.youtube.com/watch?v=iYie42M1ZyU) | What does `1/0` produce in Python vs NumPy? How do you replace `np.inf` with `np.nan`? |
| DP.15 | Outlier detection: Z-score method | [CampusX -- Outlier detection Z-score](https://www.youtube.com/watch?v=OnPE-Z8jtqM) | If a data point has a Z-score of 4.5, is it likely an outlier? What threshold is commonly used? |
| DP.16 | Outlier detection: IQR method | [CampusX -- Outlier detection IQR](https://www.youtube.com/watch?v=Ccv1-W5ilak) | What is the IQR? What is the formula for the upper and lower fence for outlier detection? |

> **Mini Assignment DP-4:** On the House Prices dataset: (1) Find all columns with more than 20% missing. (2) Detect outliers in `SalePrice` using both Z-score and IQR method. How many outliers does each method find? (3) Replace all `np.inf` values with `np.nan`. (4) Cap outliers at the 99th percentile instead of removing them. Why might capping be better than removal?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.17 | Outlier detection: Percentile method | [CampusX -- Percentile method](https://www.youtube.com/watch?v=bcXA4CqRXvM) | What is the difference between capping outliers and removing them? When would you choose capping? |
| DP.18 | Obvious inconsistencies: impossible values in data | [Towards Data Science -- Data validation](https://www.youtube.com/watch?v=iYie42M1ZyU) | A person's age is -5. A transaction amount is 999999999. How do you detect and handle these? |

---

## Section 4 -- Feature imputation

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.19 | Complete Case Analysis: drop rows with any missing value | [CampusX -- Complete Case Analysis](https://www.youtube.com/watch?v=aUnNWZorGmk) | If you have 1000 rows and 10 columns each with 5% missing values, how many rows survive `dropna()`? Why is this dangerous? |
| DP.20 | Mean / median / mode substitution | [CampusX -- Mean imputation](https://www.youtube.com/watch?v=mCL2xLBDw8M) | When would you use median instead of mean for imputation? Give a concrete example. |
| DP.21 | Hot-Deck imputation: use the value from the prior row | [StatQuest -- Imputation strategies](https://www.youtube.com/watch?v=sKFnJ-3bTKE) | What assumption does Hot-Deck imputation make about the data? When would this assumption be wrong? |
| DP.22 | Cold-Deck imputation: use donor values from another dataset | [StatQuest -- Imputation strategies](https://www.youtube.com/watch?v=sKFnJ-3bTKE) | What is the key difference between Hot-Deck and Cold-Deck? When would Cold-Deck be better? |

> **Mini Assignment DP-5:** Using the Titanic dataset: (1) Impute missing `age` with mean, then with median. Plot both distributions -- how different are they? (2) Impute missing `embarked` with mode. (3) Use `KNNImputer` on `age` with k=5. Compare the distribution to mean imputation. Which preserves the shape better?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.23 | Regression imputation: predict missing values with a model | [CampusX -- Advanced imputation](https://www.youtube.com/watch?v=a38ehxv3kyk) | How is regression imputation different from mean imputation? What is the risk of using it? |
| DP.24 | KNN Imputer: use nearest neighbors to fill missing values | [CampusX -- KNN Imputer](https://www.youtube.com/watch?v=-fK-xEev2I8) | What does k=5 mean in KNN imputation? What distance metric does sklearn's KNNImputer use by default? |
| DP.25 | MICE: Multivariate Imputation by Chained Equations | [CampusX -- MICE](https://www.youtube.com/watch?v=a38ehxv3kyk) | Why is MICE more powerful than single-column imputation? What does "chained equations" mean? |
| DP.26 | Missing indicator: add a binary flag column for missingness | [CampusX -- Missing indicator](https://www.youtube.com/watch?v=Ratcir3p03w) | Why would the fact that a value is missing itself be informative? Give a real-world example. |

---

## Section 5 -- Feature encoding

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.27 | Label encoding: integer per category | [CampusX -- Label encoding](https://www.youtube.com/watch?v=w2GglmYHfmM) | Why is label encoding dangerous for nominal data like city names? What false assumption does it create? |
| DP.28 | One-hot encoding: binary column per category | [CampusX -- One Hot Encoding](https://www.youtube.com/watch?v=U5oCv3JKWKA) | What is the "dummy variable trap"? Why do you use `drop_first=True`? |
| DP.29 | Ordinal encoding: integers preserving order | [CampusX -- Ordinal encoding](https://www.youtube.com/watch?v=w2GglmYHfmM) | How is ordinal encoding different from label encoding? When is each appropriate? |
| DP.30 | Target encoding: replace category with target mean | [Kaggle -- Target encoding](https://www.youtube.com/watch?v=589nCGeWFze) | What is the risk of target encoding on the training set? How does cross-validation help? |

> **Mini Assignment DP-6:** On the Titanic dataset: (1) Apply one-hot encoding to `embarked` and `pclass`. (2) Apply ordinal encoding to a custom column where you define the order. (3) Apply target encoding to `cabin_letter` (first letter of cabin). (4) Compare the dimensionality of the resulting dataset for each method. Which creates the most columns?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.31 | Feature hashing for high-cardinality categoricals | [CampusX -- Feature hashing](https://datasciencestunt.com/dealing-with-categorical-features-with-high-cardinality-feature-hashing/) | If you have 10,000 unique cities, why is one-hot encoding impractical? What does feature hashing do instead? |

---

## Section 6 -- Normalisation and scaling

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.32 | Min-max rescaling: scale to [0,1] | [CampusX -- Normalization](https://www.youtube.com/watch?v=eBrGyuA2MIg) | If min=10 and max=100, what does the value 55 become after min-max scaling? Show the formula. |
| DP.33 | Standardization (z-score): zero mean, unit variance | [CampusX -- Standardization](https://www.youtube.com/watch?v=1Yw9sC0PNwY) | If mean=50 and std=10, what does the value 70 become after standardization? Why is this better than min-max for many algorithms? |
| DP.34 | Scaling to unit length: divide by L2 norm | [Scikit-learn -- Normalizer docs](https://scikit-learn.org/stable/modules/preprocessing.html#normalization) | What is the L2 norm of the vector [3, 4]? After unit length scaling, what does the vector become? |
| DP.35 | Robust scaling: use median and IQR | [Scikit-learn -- RobustScaler](https://scikit-learn.org/stable/modules/preprocessing.html#scaling-to-a-range) | Why is robust scaling better than standardization when your data has outliers? |

> **Mini Assignment DP-7:** On the House Prices dataset: (1) Apply min-max scaling to `LotArea` and `SalePrice`. (2) Apply standardization. (3) Apply robust scaling. (4) Intentionally add 5 extreme outliers to `LotArea` and rerun all three. Which scaling method is least affected? Plot all three scaled versions as histograms side by side.

---

## Section 7 -- Feature transformation

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.36 | Log transform for right-skewed data | [CampusX -- Log Transform](https://www.youtube.com/watch?v=cTjj3LE8E90) | Why use `np.log1p` instead of `np.log`? What happens to log(0)? |
| DP.37 | Box-Cox transform: optimal power for normality | [CampusX -- Box Cox Transform](https://www.youtube.com/watch?v=lV_Z4HbNAx0) | What constraint does Box-Cox have that Yeo-Johnson doesn't? What does lambda=1 mean in Box-Cox? |
| DP.38 | Yeo-Johnson: like Box-Cox but handles negatives | [CampusX -- Yeo Johnson](https://www.youtube.com/watch?v=lV_Z4HbNAx0) | When would you choose Yeo-Johnson over Box-Cox? Give a feature that Box-Cox cannot handle. |
| DP.39 | Discretization: continuous to bins | [CampusX -- Discretization](https://www.youtube.com/watch?v=kKWsJGKcMvo) | What is the difference between equal-width and equal-frequency binning? Which is better for skewed data? |
| DP.40 | Reframing numerical quantities | [Towards Data Science -- Feature reframing](https://towardsdatascience.com/feature-engineering-for-machine-learning-3a5e293a5114) | Converting income from dollars to thousands of dollars -- how does this help a linear model? |

---

## Section 8 -- Feature engineering

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.41 | Datetime decomposition: extract hour, day, month | [CampusX -- Time and date features](https://www.youtube.com/watch?v=J73mvgG9fFs) | Why is a raw timestamp useless as a model feature? What features would you extract from `2024-12-25 14:30:00`? |
| DP.42 | Feature crossing: combine existing features | [Google ML Crash Course -- Feature crosses](https://developers.google.com/machine-learning/crash-course/feature-crosses/video-lecture) | Why might `latitude * longitude` be a more useful feature than `latitude` and `longitude` separately for a property price model? |
| DP.43 | Feature construction: domain knowledge | [CampusX -- Feature Construction](https://www.youtube.com/watch?v=ma-h30PoFms) | In the Titanic dataset, why might `family_size = sibsp + parch + 1` be more useful than `sibsp` and `parch` separately? |

> **Mini Assignment DP-8:** On the House Prices dataset: (1) Apply log transform to `SalePrice` and `LotArea`. Plot before and after. (2) Create `house_age = 2024 - YearBuilt`. (3) Create `total_bath = FullBath + 0.5*HalfBath`. (4) Discretize `OverallQual` into 3 bins: Low/Medium/High. Which new feature correlates most strongly with `SalePrice`?

---

## Section 9 -- Feature selection

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.44 | Filter methods: select by statistical metrics | [CampusX -- Filter methods](https://www.youtube.com/watch?v=YaKMeAlHgqQ) | Why are filter methods computationally cheap? What is their main weakness compared to wrapper methods? |
| DP.45 | Correlation-based selection: remove correlated features | [CampusX -- Correlation feature selection](https://www.youtube.com/watch?v=YaKMeAlHgqQ) | If two features have correlation 0.95 with each other, why is keeping both a problem? |
| DP.46 | Forward Selection: add features one at a time | [StatQuest -- Forward selection](https://www.youtube.com/watch?v=YaKMeAlHgqQ) | What is the stopping criterion for forward selection? What computational problem does it have? |
| DP.47 | Backward Elimination: remove worst feature one at a time | [CampusX -- Backward elimination](https://www.youtube.com/watch?v=xlHk4okO8Ls) | Why might backward elimination give different results than forward selection? |

> **Mini Assignment DP-9:** On the House Prices dataset: (1) Remove all features with more than 0.9 pairwise correlation. How many features remain? (2) Use `SelectKBest` with `f_regression` to select top 10 features for predicting `SalePrice`. (3) Use Lasso (alpha=0.01) as embedded feature selection. Which features does it set to zero? (4) Compare the top features from all three methods. Do they agree?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.48 | RFE: Recursive Feature Elimination | [CampusX -- RFE](https://www.youtube.com/watch?v=xlHk4okO8Ls) | How does RFE decide which feature to remove at each step? What model does it use internally? |
| DP.49 | Genetic algorithms for feature selection | [StatQuest -- Genetic algorithms](https://www.youtube.com/watch?v=MacVqujSXWE) | What is a "chromosome" in the context of genetic algorithm feature selection? What does the fitness function measure? |
| DP.50 | Embedded: Lasso (L1) drives irrelevant features to zero | [StatQuest -- Lasso regression](https://www.youtube.com/watch?v=NGf0voTMlcs) | Why does L1 regularization produce sparse solutions (exact zeros) while L2 does not? |
| DP.51 | Chi-squared test for categorical feature selection | [CampusX -- Chi-squared selection](https://www.youtube.com/watch?v=fMIwIKLGke0) | Why can't you use chi-squared for continuous features? What do you use instead? |

---

## Section 10 -- Dataset construction

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.52 | Train / validation / test split: what each is for | [StatQuest -- Train/test split](https://www.youtube.com/watch?v=fSytzGwwBVw) | Why must you NEVER tune your model based on test set performance? What does that violate? |
| DP.53 | Cross-validation: k-fold, stratified, leave-one-out | [StatQuest -- Cross-validation](https://www.youtube.com/watch?v=fSytzGwwBVw) | What does stratified k-fold preserve that regular k-fold does not? When does this matter? |
| DP.54 | Sklearn Pipeline: chain preprocessors and model | [CampusX -- Sklearn Pipelines](https://www.youtube.com/watch?v=xOccYkgRV4Q) | Why must scaling happen INSIDE a pipeline and not before? What is data leakage? |
| DP.55 | Column Transformer: different preprocessing per column | [CampusX -- Column Transformer](https://www.youtube.com/watch?v=5TVj6iEBR4I) | How does `ColumnTransformer` let you apply different transformers to numeric vs categorical columns simultaneously? |

> **Mini Assignment DP-10 (Capstone):** Full preprocessing pipeline on House Prices dataset. Build a single sklearn `Pipeline` that: (1) Imputes numeric columns with median. (2) Imputes categorical with mode. (3) One-hot encodes categoricals. (4) Standardizes numerics. (5) Applies this pipeline inside a 5-fold cross-validation with a Ridge regression model. Report mean and std of RMSE across folds. This is a production-grade ML preprocessing pipeline.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| DP.56 | Imbalanced datasets: SMOTE, class weights, undersampling | [CampusX -- Imbalanced data](https://www.youtube.com/watch?v=GCVMhujuSkM) | If your dataset is 95% class 0 and 5% class 1, what accuracy does a model get by always predicting class 0? Why is this a problem? |
