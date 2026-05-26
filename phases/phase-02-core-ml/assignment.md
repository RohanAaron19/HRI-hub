# Phase 02 — Assignment: Train Your First ML Model

> Implement linear regression from scratch with gradient descent, then reproduce it with scikit-learn. Understanding both levels is critical for HRI research.

---

## Part 1 — From scratch

```python
import numpy as np
import matplotlib.pyplot as plt

# Generate synthetic data
np.random.seed(42)
x = np.linspace(0, 10, 100)
y = 2 * x + 1 + np.random.randn(100) * 0.5

# Initialize parameters
w = 0.0
b = 0.0
lr = 0.01
epochs = 1000
losses = []

# Gradient descent
for epoch in range(epochs):
    y_pred = w * x + b
    loss = np.mean((y_pred - y) ** 2)
    losses.append(loss)
    
    # Compute gradients
    dL_dw = 2 * np.mean((y_pred - y) * x)
    dL_db = 2 * np.mean(y_pred - y)
    
    # Update parameters
    w -= lr * dL_dw
    b -= lr * dL_db

print(f"Learned: w = {w:.3f}, b = {b:.3f}")
print(f"True:    w = 2.000, b = 1.000")
```

Plot the loss curve. It should decrease smoothly.

---

## Part 2 — scikit-learn

```python
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split

x_2d = x.reshape(-1, 1)
X_train, X_test, y_train, y_test = train_test_split(x_2d, y, test_size=0.2, random_state=42)

model = LinearRegression()
model.fit(X_train, y_train)

print(f"sklearn: w = {model.coef_[0]:.3f}, b = {model.intercept_:.3f}")
train_loss = np.mean((model.predict(X_train) - y_train) ** 2)
test_loss  = np.mean((model.predict(X_test)  - y_test)  ** 2)
print(f"Train MSE: {train_loss:.4f}")
print(f"Test MSE:  {test_loss:.4f}")
```

Are the coefficients similar to your manual implementation?

---

## Part 3 — Overfitting demonstration

```python
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import Pipeline

degrees = [1, 3, 5, 9]
fig, axes = plt.subplots(1, 4, figsize=(16, 4))

for ax, deg in zip(axes, degrees):
    model = Pipeline([
        ('poly', PolynomialFeatures(degree=deg)),
        ('lr', LinearRegression())
    ])
    model.fit(X_train, y_train)
    x_plot = np.linspace(0, 10, 200).reshape(-1, 1)
    ax.scatter(X_train, y_train, alpha=0.4, s=10)
    ax.plot(x_plot, model.predict(x_plot), color='red')
    ax.set_title(f'Degree {deg}')
    ax.set_ylim(-5, 25)

plt.tight_layout()
plt.savefig('overfitting_demo.png')
plt.show()
```

Write 3 sentences describing what you observe as degree increases.

---

## Checklist

- [ ] Gradient descent converges (loss decreases)
- [ ] Manual w and b are close to sklearn's values
- [ ] Train/test MSE are similar (not overfit)
- [ ] Overfitting plot generated and explained

## What to commit

```bash
git add phases/phase-02-core-ml/
git commit -m "Phase 02 assignment: linear regression from scratch"
git push
```
