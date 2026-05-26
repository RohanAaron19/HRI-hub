# Phase 03 — Assignment: Neural Network in PyTorch

> Build, train, and evaluate a neural network from scratch. The most important coding skill for HRI research.

---

## The task

Train a neural network to approximate **f(x) = sin(x)** over [-π, π].

---

## Part 1 — Build the network

```python
import torch
import torch.nn as nn
import numpy as np
import matplotlib.pyplot as plt

class Net(nn.Module):
    def __init__(self, input_dim, hidden_dim, output_dim):
        super().__init__()
        self.fc1 = nn.Linear(input_dim, hidden_dim)
        self.fc2 = nn.Linear(hidden_dim, hidden_dim)
        self.fc3 = nn.Linear(hidden_dim, output_dim)
        self.relu = nn.ReLU()
    
    def forward(self, x):
        x = self.relu(self.fc1(x))
        x = self.relu(self.fc2(x))
        return self.fc3(x)

model = Net(input_dim=1, hidden_dim=64, output_dim=1)
print(model)
print(f"Parameters: {sum(p.numel() for p in model.parameters())}")
```

---

## Part 2 — Train it

```python
# Data
x = torch.linspace(-torch.pi, torch.pi, 1000).unsqueeze(1)
y = torch.sin(x)

# Training setup
criterion = nn.MSELoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.01)

losses = []

for epoch in range(3000):
    optimizer.zero_grad()
    y_pred = model(x)
    loss = criterion(y_pred, y)
    loss.backward()
    optimizer.step()
    losses.append(loss.item())
    
    if (epoch + 1) % 300 == 0:
        print(f"Epoch {epoch+1}/3000 — Loss: {loss.item():.6f}")
```

Loss should drop below 0.001 by epoch 3000.

---

## Part 3 — Evaluate and plot

```python
model.eval()
with torch.no_grad():
    y_pred = model(x)

plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.plot(losses)
plt.xlabel("Epoch")
plt.ylabel("MSE Loss")
plt.title("Training loss")
plt.yscale('log')

plt.subplot(1, 2, 2)
plt.plot(x.numpy(), y.numpy(), label='True sin(x)', linewidth=2)
plt.plot(x.numpy(), y_pred.numpy(), '--', label='Network prediction')
plt.legend()
plt.title("sin(x) approximation")

plt.tight_layout()
plt.savefig('sinx_approximation.png')
plt.show()
```

---

## Extension — try these experiments

1. Change hidden_dim from 64 to 8. Does the network still fit sin(x)? Why?
2. Add a 4th hidden layer. Does it converge faster or slower?
3. Change the learning rate from 0.01 to 0.1. What happens?
4. Replace Adam with SGD. What changes?

Write 2 sentences per experiment describing what you observed and why.

---

## Checklist

- [ ] Network trains without errors
- [ ] Final loss below 0.001
- [ ] Loss curve and prediction plot saved
- [ ] At least 2 extension experiments completed with written observations

## What to commit

```bash
git add phases/phase-03-deep-learning-pytorch-jax/
git commit -m "Phase 03 assignment: neural network in PyTorch"
git push
```
