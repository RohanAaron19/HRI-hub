# Phase 01 -- Assignment: Linear Algebra and Optimization by Hand, then Python

> Work every problem with pencil and paper first. Then verify in Python. This is the only way to build genuine mathematical intuition.

---

## Section 1 -- Linear algebra (pencil and paper + NumPy)

### Problem 1
Compute the dot product of [2, 3, 1] and [4, -1, 2] by hand. Then verify:
```python
import numpy as np
result = np.dot([2, 3, 1], [4, -1, 2])
print(result)
```

### Problem 2
Multiply these matrices by hand:
```
A = [[1, 2], [3, 4]]    B = [[5, 6], [7, 8]]
```
Show all intermediate calculations. Then verify: np.matmul(A, B)

### Problem 3
For matrix A = [[4, 1], [2, 3]], find the eigenvalues by solving det(A - lambda*I) = 0.
1. Write out A - lambda*I
2. Compute the determinant (a quadratic in lambda)
3. Solve for lambda using the quadratic formula

Then verify:
```python
A = np.array([[4,1],[2,3]])
eigenvalues, eigenvectors = np.linalg.eig(A)
print("Eigenvalues:", eigenvalues)
```

### Problem 4 -- SVD exploration
```python
import numpy as np
import matplotlib.pyplot as plt

A = np.array([[3, 2, 2], [2, 3, -2]], dtype=float)
U, S, Vt = np.linalg.svd(A)
print("U:", U)
print("Singular values:", S)
print("Vt:", Vt)

# Reconstruct A
A_reconstructed = U @ np.diag(S) @ Vt
print("Reconstruction error:", np.linalg.norm(A - A_reconstructed))
```

Write 2 sentences: what do the singular values S tell you about the matrix A?

---

## Section 2 -- Probability and Bayes (the HRI one)

### Problem 5 -- Bayesian update
A robot sees a human reaching. The human could be reaching for a cup or a plate.

Given:
- P(observation | cup) = 0.8
- P(observation | plate) = 0.2
- P(cup) = P(plate) = 0.5 (uniform prior)

Compute P(cup | observation) using Bayes theorem. Show every step.

Then verify in Python:
```python
p_obs_given_cup = 0.8
p_obs_given_plate = 0.2
p_cup = 0.5
p_plate = 0.5

p_obs = p_obs_given_cup * p_cup + p_obs_given_plate * p_plate
p_cup_given_obs = (p_obs_given_cup * p_cup) / p_obs
print(f"P(cup | obs) = {p_cup_given_obs:.3f}")
```

### Problem 6 -- KL divergence computation
Compute the KL divergence D_KL(P||Q) for:
- P = [0.4, 0.4, 0.2] (robot's belief about human goals)
- Q = [1/3, 1/3, 1/3] (uniform prior)

Formula: D_KL(P||Q) = sum over i of P[i] * log(P[i] / Q[i])

Compute by hand, then verify:
```python
import numpy as np
P = np.array([0.4, 0.4, 0.2])
Q = np.array([1/3, 1/3, 1/3])
kl = np.sum(P * np.log(P / Q))
print(f"KL divergence: {kl:.4f} nats")
```

Write 1 sentence: what does this KL divergence value tell you?

---

## Section 3 -- Optimization

### Problem 7 -- Gradient descent from scratch
Minimize f(x) = (x - 3)^2 using gradient descent.

1. Compute df/dx analytically
2. Implement gradient descent manually:
```python
x = 0.0
lr = 0.1

for i in range(50):
    grad = 2 * (x - 3)
    x = x - lr * grad
    if i % 10 == 0:
        print(f"Step {i}: x = {x:.4f}, f(x) = {(x-3)**2:.6f}")

print(f"Final x = {x:.4f} (true minimum at x = 3)")
```

3. Try learning rates lr = 0.01, 0.1, 0.5, 1.1. What happens at lr = 1.1? Why?

### Problem 8 -- Constrained optimization (Lagrange multipliers)
Minimize f(x, y) = x^2 + y^2 subject to the constraint g(x, y) = x + y - 1 = 0.

1. Write the Lagrangian: L(x, y, lambda) = f(x, y) + lambda * g(x, y)
2. Set partial derivatives to zero: dL/dx = 0, dL/dy = 0, dL/dlambda = 0
3. Solve the system of equations
4. What is the minimum value of f subject to the constraint?

This type of problem appears in SVMs and in the robot safety constraints in HRI Lecture 5.

---

## Section 4 -- Visualization

### Problem 9 -- Plot the 2D Gaussian
```python
import numpy as np
import matplotlib.pyplot as plt

mu = np.array([1.0, 2.0])
sigma2 = 1.0

x1 = np.linspace(-2, 4, 100)
x2 = np.linspace(-1, 5, 100)
X1, X2 = np.meshgrid(x1, x2)

diff = np.stack([X1 - mu[0], X2 - mu[1]], axis=-1)
Z = np.exp(-np.sum(diff**2, axis=-1) / (2 * sigma2))
Z = Z / (2 * np.pi * sigma2)

plt.figure(figsize=(7, 5))
plt.contourf(X1, X2, Z, levels=20, cmap='viridis')
plt.colorbar(label='Probability density')
plt.scatter(*mu, color='red', s=100, label='Mean mu (robot goal estimate)')
plt.xlabel('x1')
plt.ylabel('x2')
plt.title('2D Gaussian: robot belief about human goal position')
plt.legend()
plt.savefig('gaussian_belief.png')
plt.show()
```

---

## Checklist

- [ ] Problem 1: dot product computed by hand, verified in NumPy
- [ ] Problem 2: matrix multiply done by hand, verified in NumPy
- [ ] Problem 3: eigenvalues found analytically, verified in NumPy
- [ ] Problem 4: SVD explored, singular values explained
- [ ] Problem 5: Bayesian update computed step by step
- [ ] Problem 6: KL divergence computed and interpreted
- [ ] Problem 7: gradient descent implemented, learning rate experiments done
- [ ] Problem 8: constrained optimization solved with Lagrange multipliers
- [ ] Problem 9: Gaussian plot generated and saved

## What to commit
```bash
git add phases/phase-01-math/
git commit -m "Phase 01 assignment: complete math foundations"
git push
```
