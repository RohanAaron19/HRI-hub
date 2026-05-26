# Phase 02 — Quiz Solutions

---

## Q1 — Answer: B

Supervised learning trains on **(input X, correct output Y)** pairs. The model learns f: X → Y by minimizing error on training labels. In behavior cloning (HRI Lecture 8), the labels are expert robot actions — this is why BC is called supervised imitation learning.

---

## Q2 — Answer: B

Loss quantifies the gap between predictions and truth. **MSE = mean((pred - true)²)** for regression. **Cross-entropy** for classification. Minimizing loss is the entire goal of training. In behavior cloning, the loss measures how different the robot's predicted action is from the expert's action.

---

## Q3 — Answer: B

**θ = θ - α × ∇L**

We go in the **negative gradient direction** because the gradient points toward steepest increase in loss — going opposite moves toward lower loss. Think of water flowing downhill in a loss landscape. α is the learning rate controlling step size.

---

## Q4 — Answer: B

An overfit model learned the noise in training data rather than the underlying pattern. It achieves high training accuracy but poor test accuracy. In HRI, an overfit behavior cloning model works perfectly on the demonstration states but fails when the robot encounters situations slightly different from training.

---

## Q5 — Answer: B

A Gaussian process predicts a **full distribution** — mean AND confidence interval. A neural network gives one number by default. In HRI, uncertainty is critical: a GP-powered robot can say "I am 90% confident the human wants the cup" rather than just outputting a number with no uncertainty. This is why Lecture 3 uses Gaussian-based human models.

---

## Q6 — Answer: C

More complexity:
- Fits training data better → **bias decreases** (less systematic error)
- Becomes more sensitive to specific training examples → **variance increases**

Underfit model: high bias, low variance. Overfit model: low bias, high variance. Cross-validation finds the sweet spot. Regularization (L1/L2) adds a penalty that prevents the model from becoming too complex.
