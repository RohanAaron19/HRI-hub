# Phase 03 — Quiz Solutions

---

## Q1 — Answer: B

Each connection between neurons has a **weight** — a scalar that scales the signal passing through it. During training, backpropagation adjusts all weights simultaneously to minimize the loss. A network with 1 million parameters has 1 million such weights, all being optimized together via gradient descent.

---

## Q2 — Answer: B

**ReLU: f(x) = max(0, x)**

Any negative input gives output 0. Positive inputs pass through unchanged. ReLU is preferred over sigmoid/tanh in deep networks because it avoids the vanishing gradient problem — its derivative is exactly 1 for positive inputs, not 0.25 or less like sigmoid.

---

## Q3 — Answer: B

A PyTorch tensor is like a NumPy array with two superpowers:
1. **GPU computation** — matrix operations run ~100× faster on GPU
2. **Autograd** — PyTorch tracks every operation on tensors, building a computation graph. Calling `.backward()` on any scalar automatically computes all gradients via the chain rule.

---

## Q4 — Answer: B

`loss.backward()` triggers **backpropagation** — PyTorch traverses the computation graph backward from the loss, computing the gradient of the loss with respect to every parameter using the chain rule. After calling this, each parameter's `.grad` attribute contains its gradient. Note: `optimizer.step()` then uses those gradients to update the weights.

Standard training loop order:
```python
optimizer.zero_grad()   # clear old gradients
output = model(input)   # forward pass
loss = criterion(output, target)
loss.backward()         # compute gradients
optimizer.step()        # update weights
```

---

## Q5 — Answer: B

Attention computes for each token a **weighted sum of all other tokens** based on query-key dot product similarity:

```
Attention(Q, K, V) = softmax(QKᵀ / √d_k) × V
```

Unlike RNNs which process sequentially and struggle with long-range dependencies, attention handles arbitrary dependencies in parallel. In HRI, Transformers process robot joint states as sequences — the **ACT (Action Chunking with Transformers)** algorithm used in LeRobot is built on this.

---

## Q6 — Answer: B

JAX's `@jax.jit` compiles Python functions to **XLA (Accelerated Linear Algebra)**, enabling full GPU/TPU acceleration including control flow. Combined with `jax.vmap` for automatic vectorization, you can run 1000+ environment instances in parallel on a single GPU. RL tasks that take 12 hours with PyTorch + CPU environments take 5–10 minutes with JAX + Gymnax. This is why Google DeepMind uses JAX for most modern RL research.
