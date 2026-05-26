# Phase 08 -- Advanced HRI (VT Lectures 10-14)

> **This is the advanced half of your VT course.**  
> All lecture slides are in the [`lectures/`](lectures/) folder.  
> **Rule:** Every concept has a Quick Quiz. Discussion problems ARE the mini assignments.

---

## VT Course Lecture PDFs (Prof. Dylan Losey, Spring 2026)

All lecture slides and discussion sets are in the [`lectures/`](lectures/) folder.

| Week | Lecture PDF | Discussion PDF | Topic |
|------|------------|---------------|-------|
| 10 | [10 Reward Learning](lectures/10rewardlearning.pdf) | [Discussion 10](lectures/discussion_10.pdf) | Learning reward functions from human feedback |
| 11 | [11 State Representation](lectures/11staterepresentation.pdf) | [Discussion 11](lectures/discussion_11.pdf) | Latent spaces, state compression, learned embeddings |
| 12 | [12 Game Theory](lectures/12gametheory.pdf) | [Discussion 12](lectures/discussion_12.pdf) | Nash equilibria, Stackelberg games, multi-agent HRI |
| 13 | [13 Machine Teaching](lectures/13machineteaching.pdf) | [Discussion 13](lectures/discussion_13.pdf) | Teaching dimension, optimal demonstration selection |
| 14 | [14 Adaptation](lectures/14adaptation.pdf) | [Discussion 14](lectures/discussion_14.pdf) | Robot adaptation, online learning from human feedback |

---

---

## Week 10 -- Reward Learning

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| A.1 | Learning reward functions from human feedback | [10 Reward Learning](lectures/10rewardlearning.pdf) | Why is specifying a reward function by hand insufficient for complex HRI tasks? Give an example where hand-coded reward causes unexpected behavior. |
| A.2 | Pairwise preference queries: which trajectory is better? | [10 Reward Learning](lectures/10rewardlearning.pdf) | In preference-based reward learning, the human compares two robot trajectories. Write the Bradley-Terry model: P(τ_1 ≻ τ_2) = ? |
| A.3 | Bayesian reward learning: posterior over reward functions | [10 Reward Learning](lectures/10rewardlearning.pdf) | How does the robot update P(R\|preferences) after each human comparison? What is the prior over reward functions? |
| A.4 | Active learning for efficient query selection | [10 Reward Learning](lectures/10rewardlearning.pdf) | Why should the robot choose queries that maximize information gain rather than randomly? What makes a query maximally informative? |

> **Discussion 10:** Open [discussion_10.pdf](lectures/discussion_10.pdf) and work through all problems.

> **Mini Assignment A.1 -- Implement preference-based reward learning:** (1) Define a 2D feature space (speed, smoothness) for robot trajectories. (2) Generate 20 random trajectory pairs. (3) Simulate a human who prefers trajectories with high smoothness and low speed (their hidden reward function). (4) Use logistic regression on pairwise labels to learn the reward function. (5) After 20 queries, how close is the learned reward to the true reward? Plot the learning curve.

---

## Week 11 -- State Representation

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| A.5 | State representation learning: why raw states are bad | [11 State Representation](lectures/11staterepresentation.pdf) | Why is a raw pixel image a bad state representation for a robot policy? What properties should a good state representation have? |
| A.6 | Latent spaces and learned embeddings | [11 State Representation](lectures/11staterepresentation.pdf) | What is a latent space? How does an autoencoder learn a compressed state representation? |
| A.7 | Learning as representation: humans interfacing with robot representations | [11 State Representation](lectures/11staterepresentation.pdf) | In Prof. Losey's framework, how can a human directly interface with a robot's learned latent space? What does "learning as representation" mean? |
| A.8 | State compression for HRI: what information does the robot need? | [11 State Representation](lectures/11staterepresentation.pdf) | For a robot assisting a human with picking up objects, what features of the state are essential? What can be discarded? |

> **Discussion 11:** Open [discussion_11.pdf](lectures/discussion_11.pdf) and work through all problems.

> **Mini Assignment A.2 -- Learn a state representation for manipulation:** (1) Collect 1000 images of a robot workspace with objects in different positions. (2) Train a convolutional autoencoder. (3) Visualize the 2D latent space -- do images with similar object positions cluster together? (4) Train a linear regression from the latent representation to object position. How accurate is it? (5) Compare with using raw pixels as state. How much smaller is the latent representation?

---

## Week 12 -- Game Theory

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| A.9 | Normal-form games: payoff matrices | [12 Game Theory](lectures/12gametheory.pdf) | What is a payoff matrix? Write the payoff matrix for Prisoner's Dilemma. What is the dominant strategy? |
| A.10 | Nash equilibria: no player benefits from deviating | [12 Game Theory](lectures/12gametheory.pdf) | What is a Nash equilibrium? Is the Prisoner's Dilemma Nash equilibrium Pareto optimal? Why does this matter for HRI? |
| A.11 | Stackelberg equilibria: leader-follower games | [12 Game Theory](lectures/12gametheory.pdf) | What is the difference between a Nash equilibrium and a Stackelberg equilibrium? In a human-robot team, who is typically the leader? |
| A.12 | Multi-agent HRI: modeling human as a game-theoretic agent | [12 Game Theory](lectures/12gametheory.pdf) | How does modeling the human as a rational game-theoretic agent improve robot decision-making vs treating the human as an obstacle? |

> **Discussion 12:** Open [discussion_12.pdf](lectures/discussion_12.pdf) and work through all problems.

> **Mini Assignment A.3 -- Game theory in shared autonomy:** (1) Model a simple driving merge scenario as a 2-player game (robot car + human car). (2) Compute the Nash equilibrium of the payoff matrix. (3) Now model it as a Stackelberg game where the robot is the leader. (4) Compare the outcomes: which model leads to safer, more efficient merging? (5) Implement the Stackelberg solution and simulate 20 merges.

---

## Week 13 -- Machine Teaching

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| A.13 | Machine teaching: optimal demonstration selection | [13 Machine Teaching](lectures/13machineteaching.pdf) | What is the teaching dimension of a hypothesis class? How does it differ from the VC dimension (sample complexity for learning)? |
| A.14 | Teaching dimension: Goldman and Kearns | [13 Machine Teaching](lectures/13machineteaching.pdf) | For a linear classifier in 2D, what is the minimum number of examples needed to uniquely identify it (teaching dimension)? |
| A.15 | Bayesian teaching: teacher models the learner | [13 Machine Teaching](lectures/13machineteaching.pdf) | In Bayesian teaching, the teacher selects examples that maximize P(h*\|examples) for the learner. Write this optimization problem. |
| A.16 | POMDP for teaching under uncertainty | [13 Machine Teaching](lectures/13machineteaching.pdf) | Why is the teaching problem a POMDP when the teacher is uncertain about the learner's current hypothesis? What is the state space? |

> **Discussion 13:** Open [discussion_13.pdf](lectures/discussion_13.pdf) and work through all problems.

> **Mini Assignment A.4 -- Implement optimal teaching:** (1) Define a 1D threshold concept class (the target is "x > θ" for unknown θ). (2) Implement a random teacher that gives examples uniformly. (3) Implement an optimal teacher that selects the two boundary examples (just above and just below θ). (4) Compare how quickly a Bayesian learner converges to the correct θ with each teacher. (5) How many examples does the optimal teacher need vs random?

---

## Week 14 -- Adaptation

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| A.17 | Robot adaptation: learning from ongoing human feedback | [14 Adaptation](lectures/14adaptation.pdf) | What is the plasticity-stability tradeoff in online learning? What happens if the robot adapts too fast vs too slow? |
| A.18 | Bayesian online learning for robot adaptation | [14 Adaptation](lectures/14adaptation.pdf) | How does maintaining a posterior over the human's preferences enable principled adaptation? What is the update rule? |
| A.19 | HRI experiment design: within vs between subjects | [14 Adaptation](lectures/14adaptation.pdf) | What is the difference between within-subjects and between-subjects experimental design? When is each appropriate for HRI? |
| A.20 | NASA-TLX, Schaefer trust scale, statistical tests for HRI | [14 Adaptation](lectures/14adaptation.pdf) | What does NASA-TLX measure? What are its 6 subscales? What statistical test do you use to compare two robot policies in a within-subjects study? |

> **Discussion 14:** Open [discussion_14.pdf](lectures/discussion_14.pdf) and work through all problems.

> **Mini Assignment A.5 -- Design a complete HRI experiment:** Design (do not necessarily run) a full user study comparing two robot policies: (1) State your hypothesis in formal statistical terms (null and alternative). (2) Choose within-subjects or between-subjects. Justify why. (3) Determine sample size using power analysis (α=0.05, power=0.8, estimated effect size). (4) List all dependent variables (task time, NASA-TLX, trust score, success rate). (5) Specify counterbalancing scheme. (6) Write the exact statistical test you will use and what result would let you reject the null hypothesis. This is how you write your thesis methods section.
