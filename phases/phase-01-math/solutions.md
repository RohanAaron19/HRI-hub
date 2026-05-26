# Phase 01 -- Quiz Solutions

---

## Q1 -- Answer: B (5)

Magnitude = sqrt(3^2 + 4^2) = sqrt(9 + 16) = sqrt(25) = 5.

This is the Pythagorean theorem applied to vector components. In HRI, robot arm positions are vectors -- magnitude gives the Euclidean distance to a target object. NumPy: np.linalg.norm([3, 4]) returns 5.0.

---

## Q2 -- Answer: B

P(H|E) = P(E|H) x P(H) / P(E)

Your posterior probability of hypothesis H given evidence E equals the likelihood of seeing E if H were true, times your prior belief in H, divided by the total probability of E.

This is the exact formula Prof. Losey's Lecture 3 uses for human goal inference. The robot maintains P(theta|obs) -- a distribution over human goals -- and updates it every timestep as it observes human motion. The prior P(theta) starts uniform (all goals equally likely). The likelihood P(obs|theta) measures how probable the observed motion is if the goal were theta. The posterior is the updated belief.

---

## Q3 -- Answer: B (3x2)

Rule: (m x n)(n x p) = (m x p). The inner dimensions must match -- both are 4, so the multiplication is valid. The result takes the outer dimensions: 3 x 2.

This arises constantly in neural network layer size calculations. If your input batch is (batch_size x input_features) and your weight matrix is (input_features x output_features), the result is (batch_size x output_features).

---

## Q4 -- Answer: B

KL divergence D_KL(P||Q) = sum over x of P(x) * log(P(x)/Q(x)).

It measures how much information is lost (in bits or nats) when Q approximates P. Note it is asymmetric: D_KL(P||Q) is not equal to D_KL(Q||P).

This appears directly in:
- SAC (Soft Actor-Critic): entropy regularization minimizes KL divergence from a uniform policy
- VAEs: the loss has a KL divergence term regularizing the latent space
- RLHF and reward learning: comparing policy distributions
- HRI Lecture 11 (state representation): learning compressed latent spaces

---

## Q5 -- Answer: B

When matrix A acts on its eigenvector v, the vector stays on the same line -- it only stretches or shrinks by the scalar factor lambda (the eigenvalue). Lambda > 1: stretches. 0 < lambda < 1: shrinks. Lambda < 0: flips direction. Lambda = 1: unchanged. Lambda = 0: collapses to zero.

This is critical for:
- PCA: eigenvalues of the covariance matrix tell you which directions have the most variance
- Stability analysis: eigenvalues of a system matrix determine whether a controller is stable (all eigenvalues must have negative real parts for stability)
- Understanding why certain weight initializations in neural networks cause exploding or vanishing gradients

---

## Q6 -- Answer: B

Lagrange multipliers handle equality constraints: minimize f(x) subject to g(x) = 0.

KKT (Karush-Kuhn-Tucker) conditions extend this to inequality constraints: minimize f(x) subject to g(x) <= 0 and h(x) = 0. The KKT conditions are:
1. Stationarity: gradient of Lagrangian = 0
2. Primal feasibility: g(x) <= 0
3. Dual feasibility: lambda >= 0
4. Complementary slackness: lambda * g(x) = 0

In HRI, KKT conditions are the foundation of:
- Support Vector Machines (SVMs) in classical ML
- Control barrier functions in safe robot control (HRI Lecture 5)
- Constrained RL where the robot must stay within safe operating regions
