# Phase 02 -- Core Machine Learning

> **Watch this FIRST (mandatory):** [Map of Artificial Intelligence -- Maxime Kawawa-Beaudan (Berkeley AI researcher, 14 min)](https://www.youtube.com/watch?v=hDWDtH1jnXg) -- builds the full AI map from scratch so nothing feels like it came from nowhere.

> **Rule:** Every concept row has a Quick Quiz. Answer it before moving to the next video. Every 3-4 concepts has a Mini Assignment in bold below the table.

---

## ML conceptual foundations

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.1 | What is ML? Full taxonomy | [CampusX -- What is ML?](https://www.youtube.com/watch?v=ZftI2fEv0Fw) | What is the difference between supervised, unsupervised, and reinforcement learning? Give one example of each. |
| 2.2 | Batch vs online machine learning | [CampusX -- Batch ML](https://www.youtube.com/watch?v=nPrhFxEuTYU) | What is the key difference between batch and online learning? When would you need online learning? |
| 2.3 | Instance-based vs model-based learning | [CampusX -- Instance vs model based](https://www.youtube.com/watch?v=ntAOq1ioTKo) | Is KNN instance-based or model-based? What about linear regression? Explain why. |
| 2.4 | Parametric vs non-parametric models | [StatQuest -- Parametric vs non-parametric](https://www.youtube.com/watch?v=68ABAU_V8qI) | Why does a non-parametric model need more data as the dataset grows? Give an example of each type. |

> **Mini Assignment 2.1:** For each of the following problems, classify: (a) supervised/unsupervised/RL, (b) regression/classification/clustering, (c) parametric/non-parametric. Problems: (1) predict stock price, (2) group customers by purchase behavior, (3) train a robot to walk, (4) detect fraudulent transactions, (5) translate English to French. Justify each answer in one sentence.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.5 | Challenges in ML: overfitting, bad data, irrelevant features | [CampusX -- Challenges in ML](https://www.youtube.com/watch?v=WGUNAJki2S4) | What is overfitting? What are three ways to fix it? |
| 2.6 | Prediction vs inference tradeoff | [StatQuest -- Prediction vs inference](https://www.youtube.com/watch?v=EkAQAi3a4js) | Why is a neural network bad for inference but good for prediction? When would you need inference over prediction? |
| 2.7 | Bias-variance tradeoff | [StatQuest -- Bias and Variance](https://www.youtube.com/watch?v=EuBBz3bI-aA) | A model with high bias and low variance -- is it overfitting or underfitting? What does the error vs model complexity curve look like? |
| 2.8 | What are tensors? | [CampusX -- What are Tensors?](https://www.youtube.com/watch?v=vVhD2EyS41Y) | What is the difference between a scalar, vector, matrix, and tensor? What shape is a batch of 32 RGB images (224x224)? |

> **Mini Assignment 2.2:** Build a bias-variance demonstration: (1) Generate noisy data from y=sin(x)+noise. (2) Fit polynomials of degree 1, 3, 10, 20 using numpy. (3) For each, compute training error and test error. (4) Plot the bias-variance tradeoff. Which degree underfits? Which overfits?

---

## EDA (Exploratory Data Analysis)

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| EDA.1 | Understanding your data: shape, dtypes, describe | [CampusX -- Understanding your data](https://www.youtube.com/watch?v=mJlRTUuVr04) | What does `df.describe()` not tell you that `df.info()` does? What does skewness tell you about a column? |
| EDA.2 | Univariate analysis: histograms, box plots | [CampusX -- Univariate Analysis](https://www.youtube.com/watch?v=4HyTlbHUKSw) | A feature has mean=10, median=3. Is it left-skewed or right-skewed? How does a box plot show this? |
| EDA.3 | Bivariate and multivariate analysis | [CampusX -- Bivariate Analysis](https://www.youtube.com/watch?v=6D3VtEfCw7w) | What does a correlation of 0.95 between two features mean for a linear model? Should you keep both features? |

> **Mini Assignment 2.3:** Full EDA on the Titanic dataset. Produce: (1) survival rate by sex and class (grouped bar chart), (2) age distribution by survival (overlapping histograms), (3) correlation heatmap, (4) 3 written insights from your EDA that could guide model building.

---

## Supervised learning: regression

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.9 | Linear regression: cost function, normal equation | [Andrew Ng -- ML free YouTube](https://www.youtube.com/playlist?list=PLkDaE6sCZn6FNC6YRfRQc_FbeQrF8BwGI) | What is the cost function for linear regression? Why is MSE preferred over MAE in optimization? |
| 2.10 | Gradient descent for linear regression | [CampusX -- Linear Regression playlist](https://www.youtube.com/watch?v=UZPfbG0jNec&list=PLKnIA16_Rmva-wY_HBh1gTH32ocu2SoTr) | Derive the gradient of MSE with respect to weights w. In one line of matrix math. |
| 2.11 | Ridge regression (L2) | [StatQuest -- Ridge regression](https://www.youtube.com/watch?v=Q81RR3yKn30) | What does L2 regularization add to the loss function? Why does it shrink coefficients but not zero them out? |
| 2.12 | Lasso regression (L1) | [StatQuest -- Lasso regression](https://www.youtube.com/watch?v=NGf0voTMlcs) | Why does L1 regularization produce exact zero coefficients? What geometric property causes this? |

> **Mini Assignment 2.4:** From scratch (numpy only, no sklearn): (1) Implement linear regression with gradient descent. (2) Implement Ridge regression by adding L2 penalty. (3) Train on Boston Housing dataset. (4) Plot coefficient values vs regularization strength (regularization path). (5) Verify your implementation against sklearn's LinearRegression and Ridge.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.13 | Elastic net: combining L1 and L2 | [StatQuest -- Elastic net](https://www.youtube.com/watch?v=1dKRdX9bfIo) | When would you choose elastic net over pure Lasso? What hyperparameters does it have? |
| 2.14 | Polynomial regression | [StatQuest -- Polynomial regression](https://www.youtube.com/watch?v=Vd2nMLP6-XQ) | How is polynomial regression still a "linear" model? What risk increases as degree increases? |
| 2.15 | GLMs with link functions | [StatQuest -- GLMs](https://www.youtube.com/watch?v=ANMuuq502rE) | What link function does logistic regression use? What link function does Poisson regression use and when is it appropriate? |
| 2.16 | Gaussian process regression | [Mutual Information -- Gaussian Processes visually](https://www.youtube.com/watch?v=92-98SYOdlY) | What does a Gaussian process return that linear regression doesn't? Why is this useful for small datasets? |

---

## Supervised learning: classification

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.17 | Logistic regression | [StatQuest -- Logistic Regression](https://www.youtube.com/watch?v=yIYKR4sgzI8) | Why can't you use linear regression for classification? What does the sigmoid function output? |
| 2.18 | KNN: algorithm, distance metrics, choosing k | [StatQuest -- KNN](https://www.youtube.com/watch?v=HVXime0nQeI) | What happens to KNN with k=1 vs k=100? Which is more likely to overfit? Why is scaling critical for KNN? |
| 2.19 | Naive Bayes classifier | [StatQuest -- Naive Bayes](https://www.youtube.com/watch?v=O2L2Uv9pdDA) | What "naive" assumption does Naive Bayes make? When is this assumption likely to be violated? |
| 2.20 | Support Vector Machines: max margin | [StatQuest -- SVM](https://www.youtube.com/watch?v=efR1C6CvhmE) | What is the margin in an SVM? What are support vectors? What is the kernel trick? |

> **Mini Assignment 2.5:** Implement KNN from scratch (numpy only): (1) Euclidean distance function, (2) find k nearest neighbors for a query point, (3) predict by majority vote (classification) or mean (regression). Test on Iris dataset. Compare accuracy with k=1, 3, 5, 10, 20. Plot the decision boundary for k=1 and k=15.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.21 | Decision trees: splitting, Gini, information gain | [StatQuest -- Decision Trees](https://www.youtube.com/watch?v=7VeUPuFGJHk) | What is Gini impurity? Compute it for a node with 3 class A and 1 class B samples. |
| 2.22 | CART: Classification and Regression Trees | [StatQuest -- Decision Trees](https://www.youtube.com/watch?v=7VeUPuFGJHk) | How is CART for regression different from classification? What does it minimize at each split? |
| 2.23 | Random forest: bagging + feature randomness | [StatQuest -- Random Forests](https://www.youtube.com/watch?v=J4Wdy0Wc_xQ) | What two sources of randomness does random forest introduce vs a single decision tree? Why does this reduce variance? |
| 2.24 | Gradient boosting: XGBoost, LightGBM | [StatQuest -- Gradient Boosting](https://www.youtube.com/watch?v=3CC4N4z3GJc) | How is boosting different from bagging? What does each new tree in gradient boosting predict? |

> **Mini Assignment 2.6:** Full classification comparison on a dataset of your choice: (1) Train KNN, Naive Bayes, Logistic Regression, Decision Tree, Random Forest, XGBoost. (2) Compare accuracy, precision, recall, F1, and ROC-AUC for each. (3) Plot the ROC curves for all models on the same figure. (4) Which model wins? Is it always the most complex one? Use 5-fold cross-validation for all comparisons.

---

## Unsupervised learning: clustering

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.25 | K-means: algorithm, convergence, choosing k | [StatQuest -- K-means](https://www.youtube.com/watch?v=4b5d3muPQmA) | Walk through one full iteration of k-means with 2 clusters on points: (1,1),(1,2),(5,5),(5,6). |
| 2.26 | k-Medians and Fuzzy C-Means | [StatQuest -- k-medians](https://www.youtube.com/watch?v=4b5d3muPQmA) | How does k-Medians differ from k-Means? In Fuzzy C-Means, what does a membership value of 0.7 for cluster 1 mean? |
| 2.27 | DBSCAN: density-based clustering | [StatQuest -- DBSCAN](https://www.youtube.com/watch?v=RDZUdRSDOok) | What are core points, border points, and noise points in DBSCAN? What two hyperparameters does it use? |
| 2.28 | Hierarchical clustering and dendrograms | [StatQuest -- Hierarchical clustering](https://www.youtube.com/watch?v=7xHsRkOdVwo) | What does the height of a merge in a dendrogram represent? How do you choose the number of clusters from a dendrogram? |

> **Mini Assignment 2.7:** On the Iris dataset (without labels): (1) Apply k-means with k=3. Compare clusters to true labels using confusion matrix. (2) Apply DBSCAN -- tune epsilon and min_samples. (3) Apply hierarchical clustering and plot the dendrogram. (4) Compute Silhouette score for k-means and DBSCAN. Which clusters better? (5) Visualize all clustering results in 2D using PCA.

---

## Model evaluation

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.29 | Confusion matrix: TP, TN, FP, FN | [StatQuest -- Confusion matrix](https://www.youtube.com/watch?v=Kdsp6soqA7o) | Draw a confusion matrix for 3 true positives, 2 false positives, 1 false negative, 4 true negatives. |
| 2.30 | Precision, Recall, F1 | [StatQuest -- Precision and Recall](https://www.youtube.com/watch?v=vP06aMoz4v8) | A spam filter has precision=0.99 and recall=0.5. What does this mean in plain English? Is this good? |
| 2.31 | ROC curve and AUC | [StatQuest -- ROC and AUC](https://www.youtube.com/watch?v=4jRBRDbJemM) | What does AUC=0.5 mean? What about AUC=1.0? What does a point in the top-left of the ROC curve represent? |
| 2.32 | R-squared and regression metrics | [StatQuest -- R-squared](https://www.youtube.com/watch?v=2AQKmw14mHM) | What does R²=0.85 mean? Can R² be negative? If so, what would that mean? |

> **Mini Assignment 2.8:** (1) Train a logistic regression on an imbalanced dataset (95% class 0, 5% class 1). (2) Report accuracy, precision, recall, F1, and AUC. (3) A model that always predicts class 0 -- what are its precision, recall, and F1? (4) Tune the classification threshold from 0.5 to 0.1. How do precision and recall change? Plot the precision-recall curve.

---

## Hyperparameter tuning

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.33 | Grid search: exhaustive search | [StatQuest -- GridSearchCV](https://www.youtube.com/watch?v=Gol_qOgRqfA) | If you have 3 hyperparameters with 5, 4, and 3 values respectively, how many models does grid search train with 5-fold CV? |
| 2.34 | Random search: sample randomly | [StatQuest -- RandomizedSearchCV](https://www.youtube.com/watch?v=Gol_qOgRqfA) | Why does random search often find better solutions than grid search with the same number of trials? |
| 2.35 | Bayesian optimization with Optuna | [Optuna official tutorial](https://optuna.readthedocs.io) | What makes Bayesian optimization smarter than random search? What probabilistic model does it use internally? |
| 2.36 | Learning curves and validation curves | [StatQuest -- Learning curves](https://www.youtube.com/watch?v=ISBGFY-Ab70) | If training accuracy is 99% and validation accuracy is 70%, what is the problem? What does the learning curve look like? |

> **Mini Assignment 2.9:** Tune a Random Forest on a dataset of your choice: (1) Define a search space for n_estimators, max_depth, min_samples_split. (2) Run GridSearchCV. Record best params and score. (3) Run RandomizedSearchCV with same budget. (4) Run Optuna for 50 trials. (5) Compare: which found the best score? Which was fastest? Plot Optuna's optimization history.

---

## Model selection guide (quick reference)

| Problem | First try | If that fails | Best case |
|---------|----------|--------------|----------|
| Tabular regression | Ridge regression | Random forest | XGBoost |
| Tabular classification | Logistic regression | Random forest | XGBoost |
| Clustering, unknown k | K-means with elbow method | DBSCAN | Hierarchical |
| High dimensional, sparse | Lasso | Linear SVM | -- |
| Small dataset (<500 rows) | Logistic/Linear regression | KNN | Gaussian process |
| Imbalanced classes | Logistic + class_weight='balanced' | XGBoost + scale_pos_weight | Tune threshold |

> **Key rule:** Always try logistic/linear regression first. It trains in seconds, is interpretable, and often beats complex models on tabular data. Only move to XGBoost or neural networks if simple models clearly underfit.
