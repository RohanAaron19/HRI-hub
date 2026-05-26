# Phase 01 -- Math for ML and AI

> **Time estimate:** 3-4 months  
> **Rule:** Every concept has a quiz question inline. Answer it before moving on. Every 3-4 concepts has a mini assignment. These are not optional -- they ARE the learning.  
> **Free textbooks:** MML book (https://mml-book.github.io) · Boyd Convex Opt (https://web.stanford.edu/~boyd/cvxbook) · D2L appendix (https://d2l.ai)

---

## Tier 1 -- Linear algebra

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 1.1 | Vectors: magnitude, direction, addition, dot product | [3Blue1Brown -- Essence of Linear Algebra Ch 1-2](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) | What is the dot product of [1,2,3] and [4,5,6]? What does a dot product of 0 tell you about two vectors? |
| 1.2 | Matrices as linear transformations | [3Blue1Brown -- Essence of Linear Algebra Ch 3-5](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) | What does a 2x2 matrix do geometrically to a 2D vector? What does the identity matrix do? |
| 1.3 | Matrix multiplication, transpose, inverse | [3Blue1Brown -- Essence of Linear Algebra Ch 4,7,9](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) | If A is (3x4) and B is (4x2), what is the shape of AB? What is A^T if A is (3x4)? |
| 1.4 | Determinants | [3Blue1Brown -- Essence of Linear Algebra Ch 6](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) | What does a determinant of 0 tell you about a matrix? What does det=2 mean geometrically? |

> **Mini Assignment 1.1:** By hand: (1) Multiply [[1,2],[3,4]] by [[5,6],[7,8]]. Show every multiplication step. (2) Find the determinant of [[4,3],[2,1]]. (3) Verify your matrix multiply using `np.matmul`. (4) Compute the inverse of [[2,1],[1,1]] by hand using the 2x2 inverse formula, verify with `np.linalg.inv`.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 1.5 | Systems of linear equations: Ax=b | [MIT OCW 18.06 -- Gilbert Strang -- Systems of equations](https://www.youtube.com/watch?v=ZK3O402wf1c) | What does it mean geometrically when Ax=b has no solution? Exactly one solution? Infinite solutions? |
| 1.6 | Row echelon form, Gaussian elimination | [MIT OCW 18.06 -- Gilbert Strang -- Row reduction](https://www.youtube.com/watch?v=QVKj3LADCnA) | Walk through Gaussian elimination on: x+2y=5, 2x+3y=8. What is the solution? |
| 1.7 | Rank, linear independence, null space | [3Blue1Brown -- Essence of Linear Algebra Ch 7](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) | What does it mean for two vectors to be linearly dependent? If a matrix has rank 2, what can you say about its columns? |
| 1.8 | Eigenvalues and eigenvectors | [3Blue1Brown -- Essence of Linear Algebra Ch 14](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) | What does Av = λv mean geometrically? If λ=1, what happens to v when A is applied? |

> **Mini Assignment 1.2:** For matrix A = [[4,1],[2,3]]: (1) Find eigenvalues by solving det(A - λI) = 0 by hand. (2) Find eigenvectors for each eigenvalue. (3) Verify with `np.linalg.eig(A)`. (4) Reconstruct A from eigenvalues and eigenvectors (A = PDP^-1). (5) Use `np.linalg.solve` to solve Ax=b for b=[5,6].

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 1.9 | Change of basis | [3Blue1Brown -- Essence of Linear Algebra Ch 13](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) | Why does changing the coordinate basis matter for robot arm kinematics? What does "expressing a vector in a new basis" mean? |

---

## Tier 1 -- Multivariable calculus

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 1.10 | Derivatives and the chain rule | [3Blue1Brown -- Essence of Calculus full playlist](https://www.youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr) | If f(x) = x³ + 2x, what is f'(x)? If h(x) = sin(x²), what is h'(x) using the chain rule? |
| 1.11 | Partial derivatives | [Khan Academy -- Multivariable calculus](https://www.khanacademy.org/math/multivariable-calculus) | If f(x,y) = x²y + 3xy², what is ∂f/∂x? What is ∂f/∂y? |
| 1.12 | Gradient vectors | [3Blue1Brown -- Gradient descent visual](https://www.youtube.com/watch?v=IHZwWFHWa-w) | What direction does the gradient point? Why do we subtract the gradient in gradient descent instead of adding it? |
| 1.13 | The Jacobian matrix | [Khan Academy -- Jacobian matrix](https://www.youtube.com/watch?v=bohL918kXQk) | If a function maps R³ → R², what is the shape of its Jacobian? What does each entry represent? |

> **Mini Assignment 1.3:** (1) Compute the gradient of f(x,y) = x²+y² at point (1,2). Which direction is steepest ascent? (2) Take one step of gradient descent on f with learning rate 0.1 starting at (1,2). Where do you end up? (3) Code this in Python: implement gradient descent on f(x)=(x-3)² from x=0. Plot the loss curve. (4) Try learning rates 0.01, 0.1, 0.9, 1.1. What happens at 1.1?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 1.14 | The Hessian matrix | [MIT OCW 18.065 -- Hessian matrix](https://www.youtube.com/watch?v=LbBcuZukCAw) | What does a positive definite Hessian tell you about a critical point? What about indefinite? |
| 1.15 | Taylor series expansion | [3Blue1Brown -- Taylor series](https://www.youtube.com/watch?v=3d6DsjIBzJ4) | What does the Taylor series approximate? Why does Newton's method use a second-order Taylor approximation? |

---

## Tier 1 -- Probability theory

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 1.16 | Sample spaces, events, probability axioms | [StatQuest -- Statistics Fundamentals](https://www.youtube.com/playlist?list=PL1328115D3D8A2566) | What are the three probability axioms? If P(A)=0.3, what is P(not A)? |
| 1.17 | Conditional probability and independence | [3Blue1Brown -- Bayes theorem visual](https://www.youtube.com/watch?v=HZGCoVF3YvM) | If P(A)=0.4, P(B)=0.3, P(A∩B)=0.12, are A and B independent? Show your calculation. |
| 1.18 | Bayes theorem: posterior from prior and likelihood | [3Blue1Brown -- Bayes theorem](https://www.youtube.com/watch?v=HZGCoVF3YvM) | A robot sees a human reaching. P(cup goal) = P(plate goal) = 0.5. P(obs\|cup) = 0.8, P(obs\|plate) = 0.2. What is P(cup\|obs)? |
| 1.19 | Discrete distributions: Bernoulli, Binomial, Poisson | [StatQuest -- Probability distributions](https://www.youtube.com/playlist?list=PL1328115D3D8A2566) | If I flip a fair coin 10 times, what distribution models the number of heads? What are its parameters? |

> **Mini Assignment 1.4:** (1) A robot classifies objects as "cup" or "plate". The prior is 70% cup. Likelihood of the observation given cup is 0.6, given plate is 0.9. Compute the posterior for cup. (2) Code a Bayesian update function that takes a prior, likelihood, and returns a posterior. Run it 5 times as you get 5 observations. Plot how the posterior evolves.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 1.20 | Gaussian / Normal distribution | [StatQuest -- Normal Distribution](https://www.youtube.com/watch?v=qBigTkBLU6g) | What do μ and σ² mean? If X~N(0,1), what fraction of values fall within ±2 standard deviations? |
| 1.21 | Multivariate Gaussian distribution | [StatQuest -- Multivariate Gaussian](https://www.youtube.com/watch?v=az3j4Vr8B7g) | What does the covariance matrix in a multivariate Gaussian encode? What does a diagonal covariance mean? |
| 1.22 | Expectation, variance, covariance | [StatQuest -- Expectation and variance](https://www.youtube.com/playlist?list=PL1328115D3D8A2566) | If E[X]=5 and E[X²]=30, what is Var[X]? What does Cov(X,Y)=0 mean about X and Y? |
| 1.23 | Central limit theorem | [StatQuest -- Central Limit Theorem](https://www.youtube.com/watch?v=YAlJCEDH2uY) | What does the CLT say? Why does it justify using Gaussian noise in ML models? |

---

## Tier 1 -- Statistics

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 1.24 | Maximum Likelihood Estimation (MLE) | [StatQuest -- Maximum Likelihood](https://www.youtube.com/watch?v=XepXtl9YKwc) | What does MLE find? Show why minimizing cross-entropy is equivalent to maximizing log-likelihood for classification. |
| 1.25 | Maximum a posteriori (MAP) estimation | [StatQuest -- MAP](https://www.youtube.com/watch?v=85yx-V4Mq7I) | How is MAP different from MLE? Show that MAP with a Gaussian prior is equivalent to L2 regularization. |
| 1.26 | Confidence intervals | [StatQuest -- Confidence Intervals](https://www.youtube.com/watch?v=TqOeMYtOc1w) | What does a 95% confidence interval actually mean? Common misconception: does it mean there's a 95% chance the true value is inside? |
| 1.27 | Hypothesis testing: t-tests, p-values | [StatQuest -- Hypothesis testing](https://www.youtube.com/playlist?list=PL1328115D3D8A2566) | What is a null hypothesis? If p=0.03 and α=0.05, what do you conclude? |

> **Mini Assignment 1.5:** (1) Generate 100 samples from N(3, 4). Estimate the mean and variance using MLE. How close are they to the true values? (2) Add a Gaussian prior N(0, 1) on the mean and compute the MAP estimate. How does regularization pull the estimate toward zero? (3) Compute a 95% confidence interval for the mean. Does it contain 3?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 1.28 | Effect sizes and statistical power | [StatQuest -- Effect sizes](https://www.youtube.com/watch?v=VX_M3tIyiYk) | Why can a result be statistically significant but practically meaningless? What does Cohen's d measure? |
| 1.29 | A/B testing and experimental design | [StatQuest -- Experimental design](https://www.youtube.com/watch?v=VX_M3tIyiYk) | In an HRI experiment comparing two robot policies, what is your null hypothesis? How do you determine sample size? |

---

## Tier 2 -- Optimization

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.1 | Gradient descent: batch, mini-batch, SGD | [3Blue1Brown -- Gradient descent visual](https://www.youtube.com/watch?v=IHZwWFHWa-w) | What is the difference between batch and stochastic gradient descent? Why does SGD sometimes escape local minima better? |
| 2.2 | Momentum and Nesterov acceleration | [Distill -- Why momentum works](https://distill.pub/2017/momentum/) | What does momentum add to gradient descent? If momentum=0.9, how much of the previous update is kept? |
| 2.3 | Adam optimizer: adaptive learning rates | [Andrej Karpathy -- optimizers from scratch](https://www.youtube.com/watch?v=mdKjMPmcWjY) | What are the two moment estimates that Adam maintains? Why does Adam work better than vanilla SGD on sparse gradients? |
| 2.4 | Learning rate schedules | [fast.ai -- learning rate finder](https://www.youtube.com/watch?v=hVEJHJmkEhI) | What is a learning rate warm-up? Why does using a very high LR at the start of training often cause divergence? |

> **Mini Assignment 2.1:** Implement gradient descent, SGD, and Adam from scratch in Python (no PyTorch). Test all three on minimizing f(x,y) = x² + 10y² from (5, 5). Plot all three trajectories on the same contour plot. Which converges fastest? Why does SGD bounce more?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.5 | Newton's method: second-order optimization | [MIT 18.065 -- Newton's method](https://www.youtube.com/watch?v=U0xlKuFqCuI) | Why does Newton's method converge faster than gradient descent? What is the computational cost of computing the Hessian? |
| 2.6 | L-BFGS: approximating the Hessian cheaply | [Boyd Convex Optimization Ch 9](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf) | Why is L-BFGS preferred over full Newton's method in practice? What does "limited memory" mean here? |
| 2.7 | Line search: Armijo and Wolfe conditions | [Boyd Convex Optimization Ch 9](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf) | What problem does line search solve? What does the Armijo condition ensure? |
| 2.8 | Convex vs non-convex optimization | [Boyd Convex Optimization Ch 1-3](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf) | Why is convex optimization "easy" (guaranteed global solution)? Why are neural networks non-convex? |

> **Mini Assignment 2.2:** (1) Implement Newton's method from scratch for f(x) = x³ - 2x - 5. Find the root. (2) Compare convergence to bisection method. (3) Use scipy.optimize.minimize with method='BFGS' and method='Nelder-Mead' on a 2D non-convex function. Plot both trajectories. Which finds a better solution?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 2.9 | Lagrange multipliers for equality constraints | [Khan Academy -- Lagrange multipliers](https://www.khanacademy.org/math/multivariable-calculus/applications-of-multivariable-derivatives/lagrange-multipliers-and-constrained-optimization/a/lagrange-multipliers-single-constraint) | Minimize x²+y² subject to x+y=1. Set up the Lagrangian and solve for x, y, and λ. |
| 2.10 | KKT conditions for inequality constraints | [Boyd Convex Optimization Ch 5](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf) | What are the 4 KKT conditions? Why does complementary slackness (λg(x)=0) make sense intuitively? |
| 2.11 | Convex optimization: LP and QP | [Boyd Convex Optimization Ch 4](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf) | What makes a quadratic program (QP) different from a linear program (LP)? Where does QP appear in robot motion planning? |
| 2.12 | Saddle points in neural network loss landscapes | [Rong Ge -- Saddle points in DL](https://www.youtube.com/watch?v=gkH5_YOIxBk) | Why do most critical points in high-dimensional neural networks turn out to be saddle points rather than local minima? |

---

## Tier 3 -- Deep linear algebra

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.1 | SVD: Singular Value Decomposition | [MIT 18.065 -- SVD lecture Gilbert Strang](https://www.youtube.com/watch?v=rYz83XPxiZo) | If A = UΣV^T, what do U, Σ, and V each represent? How do you use SVD for low-rank approximation? |
| 3.2 | PCA from scratch via SVD | [StatQuest -- PCA clearly explained](https://www.youtube.com/watch?v=FgakZw6K1QQ) | What are the principal components? What does the explained variance ratio tell you? |
| 3.3 | Matrix calculus: ∂(Wx)/∂W | [Matrix cookbook reference](https://www.math.uwaterloo.ca/~hwolkowi/matrixcookbook.pdf) | If L = ||Wx - y||², what is ∂L/∂W? Write it out. This is the gradient used in linear regression. |
| 3.4 | Positive definite matrices | [MIT 18.065 -- Positive definite matrices](https://www.youtube.com/watch?v=xsP-S7yKaRA) | What does positive definite mean for the Hessian at a critical point? How does this relate to it being a minimum? |

> **Mini Assignment 3.1:** (1) Implement PCA from scratch using SVD on a dataset of your choice. (2) Plot the explained variance ratio vs number of components. (3) Reduce a 50-dimensional dataset to 2D and plot it. (4) Compare your scratch implementation to sklearn's PCA. Do they give the same result?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.5 | Norms: L1, L2, Frobenius | [Boyd Convex Optimization Ch 1](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf) | Compute the L1, L2, and Frobenius norm of [[1,-2],[3,4]]. Which norm is used for Lasso? Which for Ridge? |
| 3.6 | Tensor algebra | [eigenchris -- Tensors for ML](https://www.youtube.com/playlist?list=PLJHszsWbB6hrkmmq57lX8BV-o-YIOFsiG) | What is the difference between a rank-1, rank-2, and rank-3 tensor? How does a 3D image (H×W×C) fit this? |
| 3.7 | Low-rank matrix approximation | [MIT 18.065 -- Low rank](https://www.youtube.com/watch?v=rYz83XPxiZo) | If you keep only the top k singular values, how do you reconstruct an approximation of A? What determines the quality of this approximation? |

---

## Tier 4 -- Information theory and probabilistic depth

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.1 | Shannon entropy | [Aurélien Géron -- Information theory](https://www.youtube.com/watch?v=ErfnhcEV1O8) | What is the entropy of a fair coin flip? Of a biased coin with P(H)=0.99? Which is higher and why? |
| 4.2 | KL divergence | [Mutual Information -- KL divergence](https://www.youtube.com/watch?v=SxGYPqCgJWM) | Is KL divergence symmetric? What does D_KL(P||Q)=0 mean? Where does it appear in VAEs? |
| 4.3 | Mutual information | [Aurélien Géron -- Mutual information](https://www.youtube.com/watch?v=ErfnhcEV1O8) | What does I(X;Y)=0 mean about X and Y? How is mutual information used in feature selection? |
| 4.4 | Joint and Conditional Entropy | [Aurélien Géron -- Information theory](https://www.youtube.com/watch?v=ErfnhcEV1O8) | What is the chain rule of entropy: H(X,Y) = ? How does this connect to the chain rule of probability? |

> **Mini Assignment 4.1:** In Python: (1) Implement Shannon entropy from scratch for a probability distribution. (2) Plot entropy vs p for a Bernoulli(p) distribution. Where is it maximized? (3) Compute KL divergence between N(0,1) and N(1,1) by sampling. (4) Verify: the cross-entropy loss for a binary classifier IS the KL divergence from the true distribution. Show this mathematically.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.5 | MLE and MAP in depth | [StatQuest -- Maximum Likelihood](https://www.youtube.com/watch?v=XepXtl9YKwc) | Derive: why does maximizing log P(data\|θ) for a Gaussian give you the sample mean as the MLE estimate? |
| 4.6 | Bayesian inference and conjugate priors | [Ben Lambert -- Bayesian statistics](https://www.youtube.com/watch?v=9TDjifpGj-k) | What is a conjugate prior? If the likelihood is Binomial, what is the conjugate prior? Why is conjugacy useful? |
| 4.7 | Kernel Density Estimation (KDE) | [StatQuest -- KDE clearly explained](https://www.youtube.com/watch?v=x5zLaWT5KPs) | What does the bandwidth parameter h control in KDE? What happens with h very small vs very large? |
| 4.8 | Fisher information matrix | [Information geometry -- natural gradient](https://www.youtube.com/watch?v=WnuZO5TZ7xw) | What does the Fisher information measure? How is it used in natural gradient descent (TRPO)? |

---

## Tier 5 -- Discrete math and game theory

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 5.1 | Graph theory: nodes, edges, paths, adjacency | [MIT OCW -- Algorithms graph section](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/) | What is the difference between a directed and undirected graph? What is the adjacency matrix of a triangle graph? |
| 5.2 | BFS, DFS, Dijkstra for robot path planning | [MIT OCW -- Algorithms](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/) | When would you use Dijkstra over BFS? What assumption does Dijkstra make that BFS does not? |
| 5.3 | Graph Neural Networks: mathematical foundations | [Petar Velickovic -- GNN lecture](https://www.youtube.com/watch?v=uF53xsT7mjc) | What is message passing in a GNN? What does the aggregation step compute? |
| 5.4 | Game theory: Nash equilibria | [Yale Game Theory -- Ben Polak free lectures](https://www.youtube.com/playlist?list=PL6EF60E1027E1A10B) | What is a Nash equilibrium? In the prisoner's dilemma, what is the Nash equilibrium? Is it Pareto optimal? |

> **Mini Assignment 5.1:** (1) Implement Dijkstra's algorithm from scratch. Test it on a 5-node weighted graph. (2) Implement BFS for path planning on a 10x10 grid with obstacles. Visualize the path with matplotlib. (3) Find the Nash equilibrium of the payoff matrix: [[3,0],[5,1]] for a 2-player game. Is it unique?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 5.5 | Stackelberg equilibria for HRI | [Yale Game Theory -- Ben Polak lectures](https://www.youtube.com/playlist?list=PL6EF60E1027E1A10B) | In a Stackelberg game between a robot (leader) and human (follower), what advantage does the leader have? How does this model HRI? |

---

## Tier 6 -- Numerical methods

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 6.1 | Floating point arithmetic and numerical precision | [MIT 18.335 -- Numerical methods](https://www.youtube.com/watch?v=1LoN5_VegOU) | Why does `0.1 + 0.2 != 0.3` in Python? What is the log-sum-exp trick and why is it needed? |
| 6.2 | Numerical differentiation: finite differences | [MIT 18.335 -- Numerical differentiation](https://www.youtube.com/watch?v=1LoN5_VegOU) | What is the forward difference formula for a derivative? What is the truncation error? |
| 6.3 | Automatic differentiation: forward and reverse mode | [Andrej Karpathy -- micrograd from scratch](https://www.youtube.com/watch?v=VMj-3S1tku0) | What is the difference between forward mode and reverse mode autodiff? Why does PyTorch use reverse mode (backprop)? |
| 6.4 | LU and Cholesky decomposition | [MIT 18.065 -- Gilbert Strang](https://www.youtube.com/playlist?list=PLUl4u3cNGP63oMNUHXqIUcrkS2PivhN3k) | When is Cholesky decomposition preferred over LU? What property must a matrix have for Cholesky to work? |

> **Mini Assignment 6.1:** (1) Build a minimal autograd engine following Karpathy's micrograd tutorial. Implement Value class with +, *, and backward(). (2) Use it to compute the gradient of f(x,y) = x²+y². Verify against analytical gradient. (3) Implement a 2-layer neural network using only your autograd engine. This is the most important implementation exercise in the entire math phase.

---

## Loss functions (complete reference)

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| LF.1 | Log-likelihood and MLE connection | [StatQuest -- Maximum Likelihood](https://www.youtube.com/watch?v=XepXtl9YKwc) | Why is it easier to maximize log-likelihood than likelihood? Do they have the same optimum? |
| LF.2 | Logistic loss (log loss / binary cross-entropy) | [StatQuest -- Log Loss](https://www.youtube.com/watch?v=MztgenIfGgM) | Write the logistic loss for one sample. What happens to loss when true label=1 and prediction=0.001? |
| LF.3 | 0-1 loss: correct=0, wrong=1 | [StatQuest -- Loss functions](https://www.youtube.com/watch?v=Skc8nqJirJg) | Why can't you use gradient descent to minimize 0-1 loss? What makes it theoretically important but practically unused? |
| LF.4 | Hinge loss for SVMs | [StatQuest -- SVM and hinge loss](https://www.youtube.com/watch?v=efR1C6CvhmE) | Write the hinge loss formula. What happens to loss when a correctly classified point is far from the margin? |

> **Mini Assignment LF.1:** Implement logistic loss, hinge loss, and MSE loss from scratch. For each: (1) Plot loss vs prediction for true label = 1. (2) Compute and plot the gradient. (3) Run a gradient descent step. Which loss has the sharpest gradient near the boundary?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| LF.5 | Exponential loss (AdaBoost) | [StatQuest -- AdaBoost](https://www.youtube.com/watch?v=LsK-xG1cLYA) | Why does exponential loss penalize misclassified samples much more harshly than logistic loss? |
| LF.6 | Hellinger Distance | [Mutual Information -- probability distances](https://www.youtube.com/watch?v=SxGYPqCgJWM) | How is Hellinger distance different from KL divergence? Is it symmetric? Bounded? |
| LF.7 | KL divergence as a loss | [Mutual Information -- KL divergence](https://www.youtube.com/watch?v=SxGYPqCgJWM) | Where does KL divergence appear in the VAE loss function (ELBO)? What does minimizing it encourage? |

---

## Statistics depth

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| ST.1 | Mean, Median, Mode, Quantile | [StatQuest -- Descriptive statistics](https://www.youtube.com/watch?v=tPhzDKjQBpo) | For income data with outliers like Elon Musk, why is median more representative than mean? |
| ST.2 | Variance, Standard Deviation, Z-score | [StatQuest -- Variance and std](https://www.youtube.com/watch?v=SzZ6GpcfoUA) | A data point has a Z-score of -2.5. Is it above or below the mean? How many standard deviations away is it? |
| ST.3 | Range, IQR, MAD | [StatQuest -- Dispersion measures](https://www.youtube.com/watch?v=hVEJHJmkEhI) | Why is IQR more robust to outliers than the range? When would you report MAD instead of standard deviation? |
| ST.4 | Pearson, Spearman, Kendall correlations | [StatQuest -- Correlation](https://www.youtube.com/watch?v=XV1bKgFEcA4) | When would you use Spearman instead of Pearson correlation? What does Kendall's τ measure? |

> **Mini Assignment ST.1:** On a dataset of your choice: (1) Compute mean, median, mode, and IQR. (2) Compute Z-scores for all data points and identify outliers (|Z|>3). (3) Compute Pearson and Spearman correlation between two features. How different are they? Why? (4) Test p-hacking: run 20 t-tests on random subsets. How many yield p<0.05 by chance?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| ST.5 | Frequentist vs Bayesian probability | [3Blue1Brown -- Bayes theorem](https://www.youtube.com/watch?v=HZGCoVF3YvM) | What is the key philosophical difference between frequentist and Bayesian interpretations of probability? |
| ST.6 | p-hacking and multiple comparisons | [StatQuest -- p-hacking](https://www.youtube.com/watch?v=UFhJefdVCjE) | If you run 20 hypothesis tests with α=0.05, how many false positives do you expect by chance? What is the Bonferroni correction? |
| ST.7 | Curse of Dimensionality | [StatQuest -- Curse of Dimensionality](https://www.youtube.com/watch?v=9ry2HHDRMQo) | Why does KNN fail in high dimensions? What fraction of a hypercube's volume is within 10% of its edge in 100 dimensions? |
| ST.8 | CDF and probability distributions | [StatQuest -- CDF explained](https://www.youtube.com/watch?v=eMEFSBJrRws) | What does F(x) = 0.8 mean for a CDF? How do you compute P(a < X < b) from a CDF? |
