# Phase 03 — Deep Learning + PyTorch + JAX Quiz

---

## Easy

**Q1.** What are weights in a neural network?

- A) Hyperparameters set before training
- B) Learnable scalar parameters on connections between neurons, optimized by backpropagation
- C) The learning rate values
- D) Controls that determine which neurons activate first

---

**Q2.** What does the ReLU activation function output for a negative input?

- A) The input unchanged (passes through)
- B) 0 (zero)
- C) The absolute value of the input
- D) -1

---

## Medium

**Q3.** What is a PyTorch tensor?

- A) A type of neural network layer
- B) A multi-dimensional array with GPU support and automatic differentiation (autograd)
- C) A loss function
- D) A type of optimizer

---

**Q4.** What does `loss.backward()` do in PyTorch?

- A) Runs the forward pass through the network
- B) Computes gradients of the loss with respect to all parameters via backpropagation
- C) Updates the model weights
- D) Resets all gradients to zero

---

## Hard

**Q5.** What is the key innovation of the attention mechanism in Transformers?

- A) Uses recurrence to process sequences one step at a time
- B) Each element can attend to (weight the importance of) every other element in the sequence based on learned similarity — enabling long-range dependencies in parallel
- C) Replaces learnable weights entirely with attention scores
- D) Processes sequences using 1D convolutions

---

**Q6.** Why does JAX's `jit` (just-in-time compilation) matter for RL research?

- A) It makes code easier to read
- B) It compiles Python functions to XLA, enabling thousands of environments to run in parallel on a single GPU — reducing RL training from days to minutes
- C) It automatically adds regularization
- D) It replaces the need for neural networks
