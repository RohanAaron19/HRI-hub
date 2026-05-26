# Phase 04 -- Reinforcement Learning

> **Time estimate:** 4-6 weeks  
> **Primary textbooks:** Sutton & Barto (free PDF): http://incompleteideas.net/book/RLbook2020.pdf  
> **Rule:** Every concept has a Quick Quiz inline. Every 3-4 concepts has a Mini Assignment. Do not move on until you can answer the quiz without looking.

---

## Section 1 -- RL foundations

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.1 | RL framework: agent, environment, reward, state, action | [David Silver -- RL Course Lecture 1](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What are the five components of an RL problem? What is the difference between a state and an observation? |
| 4.2 | Markov Decision Process (MDP): S, A, P, R, γ | [David Silver -- RL Course Lecture 2](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What does the Markov property mean? What does discount factor γ=0 vs γ=0.99 each prioritize? |
| 4.3 | Value function V(s) and Q-function Q(s,a) | [David Silver -- RL Course Lecture 2](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What does V(s) represent? What is the difference between V(s) and Q(s,a)? Which is more useful for choosing actions and why? |
| 4.4 | Bellman equations: recursive definition of value | [David Silver -- RL Course Lecture 2](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | Write the Bellman equation for V(s). What does the expectation E[] represent? |

> **Mini Assignment 4.1 -- Solve a small MDP by hand:** Define a 3-state, 2-action MDP with a reward matrix and transition probabilities. (1) Write out the Bellman equations for all states. (2) Solve for V(s) using value iteration: initialize V=0, iterate until convergence. (3) Extract the optimal policy from V. (4) Implement this in Python and verify. This is the foundation of everything in RL.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.5 | Dynamic programming: policy iteration and value iteration | [David Silver -- RL Course Lecture 3](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What is the difference between policy iteration and value iteration? Which converges faster in practice? |
| 4.6 | Policy vs value-based methods | [David Silver -- RL Course Lecture 5](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | Name one pure policy-based, one pure value-based, and one actor-critic method. What is the key advantage of policy-based methods for continuous actions? |
| 4.7 | Discount factor and reward shaping | [David Silver -- RL Course Lecture 2](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | Why is reward shaping dangerous? What is reward hacking and give one real example? |

---

## Section 2 -- Value-based methods

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.8 | Q-learning: off-policy TD control | [David Silver -- RL Course Lecture 5](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | Write the Q-learning update rule. What makes it "off-policy"? What is the target in the update? |
| 4.9 | SARSA: on-policy TD control | [David Silver -- RL Course Lecture 5](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | Write the SARSA update rule. How does it differ from Q-learning? When would SARSA be safer than Q-learning? |
| 4.10 | Deep Q-Network (DQN): neural network as Q-function | [DeepMind -- RL lecture series](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What two tricks does DQN use to stabilize training? What is a replay buffer and why is it needed? |
| 4.11 | Double DQN, Dueling DQN, Rainbow | [DeepMind -- RL lecture series](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What overestimation problem does Double DQN fix? What do the value and advantage streams in Dueling DQN each estimate? |

> **Mini Assignment 4.2 -- Implement Q-learning from scratch:** (1) Implement tabular Q-learning on FrozenLake (Gymnasium). No libraries -- just a Q-table and the update rule. (2) Plot cumulative reward over episodes. (3) Implement epsilon-greedy exploration and show how epsilon decay affects learning. (4) Compare Q-learning vs SARSA on the same environment. Which performs better? Why?

---

## Section 3 -- Policy gradient methods

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.12 | Policy gradient theorem | [David Silver -- RL Course Lecture 7](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | Write the policy gradient update: ∇J(θ) = ? What is the "score function" trick? Why can we not just backprop through the environment? |
| 4.13 | REINFORCE: Monte Carlo policy gradient | [David Silver -- RL Course Lecture 7](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What is the high variance problem in REINFORCE? What is a baseline and how does it help without introducing bias? |
| 4.14 | Actor-Critic: A2C and A3C | [DeepMind -- RL lecture series](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What does the critic estimate? What does the actor do with that estimate? What is the advantage function A(s,a)? |
| 4.15 | PPO: Proximal Policy Optimization | [Spinning Up -- PPO explanation](https://spinningup.openai.com/en/latest/algorithms/ppo.html) | What does the "clipped surrogate objective" in PPO prevent? Why is PPO more stable than vanilla policy gradients? |

> **Mini Assignment 4.3 -- Train PPO on a continuous control task:** Using CleanRL (https://github.com/vwxyzjn/cleanrl): (1) Run the single-file PPO implementation on CartPole. Read every line of code -- it's ~300 lines. (2) Train on HalfCheetah-v4 (MuJoCo). (3) Add wandb logging. (4) Tune learning rate and clip ratio. (5) Plot the learning curve. This single file teaches you more than most RL courses.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.16 | SAC: Soft Actor-Critic with entropy regularization | [Spinning Up -- SAC](https://spinningup.openai.com/en/latest/algorithms/sac.html) | What does the entropy term in SAC encourage? What is the temperature parameter α? Why is SAC more sample-efficient than PPO? |
| 4.17 | TD3: Twin Delayed DDPG | [Spinning Up -- TD3](https://spinningup.openai.com/en/latest/algorithms/td3.html) | What three tricks does TD3 add over DDPG? What is the "twin" in Twin Delayed? |
| 4.18 | DDPG: Deep Deterministic Policy Gradient | [Spinning Up -- DDPG](https://spinningup.openai.com/en/latest/algorithms/ddpg.html) | Why can't DQN handle continuous action spaces? What does DDPG use instead of argmax over actions? |

---

## Section 4 -- Advanced RL

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.19 | Monte Carlo methods in RL | [Sutton & Barto Chapter 5](http://incompleteideas.net/book/RLbook2020.pdf) | What is the difference between first-visit and every-visit Monte Carlo? When would you use MC over TD methods? |
| 4.20 | TD(λ) and eligibility traces | [David Silver -- RL Course Lecture 4](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What does λ=0 give you in TD(λ)? What does λ=1 give you? What is the bias-variance tradeoff as λ increases? |
| 4.21 | Model-based RL: Dyna-Q | [David Silver -- RL Course Lecture 8](https://www.youtube.com/playlist?list=PLqYmG7hTraZBKeNJ-JE_eyJHZ7XgBoAyb) | What does Dyna-Q add to Q-learning? Why does planning with a learned model improve sample efficiency? |
| 4.22 | Model-based RL: MuZero and DreamerV3 | [Two Minute Papers -- MuZero](https://www.youtube.com/watch?v=L0A86LmH7Yw) | What is the key difference between MuZero and AlphaZero? What does DreamerV3 learn that Dyna-Q doesn't? |

> **Mini Assignment 4.4 -- Compare model-free vs model-based:** (1) Implement Dyna-Q on a simple grid world. (2) Compare sample efficiency vs pure Q-learning: how many episodes to reach the same performance? (3) Intentionally break the learned model (add noise). How does this affect performance? (4) Plot reward vs environment steps (not episodes) for both.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.23 | Curiosity-driven exploration: ICM and RND | [Two Minute Papers -- curiosity driven learning](https://www.youtube.com/watch?v=l1FqtAHfJLI) | What does ICM predict to compute an intrinsic reward? When is curiosity most useful (dense vs sparse rewards)? |
| 4.24 | Hindsight Experience Replay (HER) | [OpenAI -- HER explanation](https://www.youtube.com/watch?v=Dz_HuzgMxzo) | What is the "hindsight" insight in HER? How does it solve the sparse reward problem for goal-conditioned tasks? |
| 4.25 | Safe RL: constrained MDP and Lagrangian methods | [Berkeley -- safe RL lecture](https://www.youtube.com/watch?v=woNQfhM3fks) | What is a constrained MDP? How does the Lagrangian method convert a constrained optimization into an unconstrained one? |
| 4.26 | RLHF: PPO with a reward model | [Yannic Kilcher -- InstructGPT and RLHF](https://www.youtube.com/watch?v=TqOeMYtOc1w) | What are the three stages of RLHF? What does the reward model learn to predict? Why is RLHF needed for language model alignment? |

> **Mini Assignment 4.5 -- HER on a goal-conditioned task:** (1) Set up a goal-conditioned environment in Gymnasium (e.g., FetchPush). (2) Train SAC without HER -- observe that it barely learns due to sparse rewards. (3) Add HER by relabeling failed trajectories with achieved goals. (4) Compare learning curves. (5) Visualize successful vs failed episodes.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 4.27 | Offline RL: IQL, CQL, TD3+BC | [Sergey Levine -- Offline RL lecture](https://www.youtube.com/watch?v=k08N5a0gG0A) | What is the distributional shift problem in offline RL? Why does a naively trained Q-function overestimate OOD actions? |
| 4.28 | Decision Transformer: RL as sequence modeling | [Yannic Kilcher -- Decision Transformer](https://www.youtube.com/watch?v=w4Bief2jM9Y) | How does Decision Transformer reframe RL as a supervised learning problem? What is the "return-to-go" conditioning? |
| 4.29 | Multi-agent RL: MADDPG, MAPPO | [DeepMind -- multi-agent RL](https://www.youtube.com/watch?v=V_UKDlsKBHU) | What is the non-stationarity problem in multi-agent RL? How does MADDPG's centralized training fix it? |
| 4.30 | Sim-to-real: domain randomization | [OpenAI -- domain randomization](https://www.youtube.com/watch?v=SAcKFYuHGKc) | What does domain randomization randomize? Why does training on many random environments help transfer to the real world? |

> **Mini Assignment 4.6 -- Read and run CleanRL source code:** (1) Clone CleanRL. Read the SAC implementation completely (ppo_continuous_action.py). (2) Identify: actor network, critic network, replay buffer, entropy term, temperature α. (3) Add a simple modification: log the entropy of the policy during training. (4) Run on Ant-v4 for 1M steps. This exercise is about reading real research code, not writing from scratch.
