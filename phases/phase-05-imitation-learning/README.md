# Phase 05 -- Imitation Learning

> **Time estimate:** 3-4 weeks  
> **Why this matters:** This is the bridge between RL theory and real robot learning. Lectures 8-9 of your VT course are entirely this topic.  
> **Rule:** Every concept has a Quick Quiz. Every 3-4 concepts has a Mini Assignment.

---

## Section 1 -- Core IL algorithms

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 5.1 | What is imitation learning and why not just use RL? | [Pieter Abbeel -- IL lecture (Berkeley)](https://www.youtube.com/watch?v=WjFrmric-Bs) | When would you choose imitation learning over RL? What does IL assume that RL does not? |
| 5.2 | Behavior Cloning (BC): supervised learning on demonstrations | [Pieter Abbeel -- IL lecture](https://www.youtube.com/watch?v=WjFrmric-Bs) | Write the BC objective function. Why is BC essentially a supervised classification/regression problem? |
| 5.3 | Covariate shift: why BC fails at test time | [Pieter Abbeel -- IL lecture](https://www.youtube.com/watch?v=WjFrmric-Bs) | What is covariate shift? Give a concrete robot example where BC works during training but catastrophically fails during deployment. |
| 5.4 | Compounding errors in BC | [Pieter Abbeel -- IL lecture](https://www.youtube.com/watch?v=WjFrmric-Bs) | If each BC step has 1% error probability, what is the error probability after 100 steps? Why does this get exponentially worse? |

> **Mini Assignment 5.1 -- Implement BC from scratch:** (1) Collect 100 expert demonstrations on CartPole using a scripted expert. (2) Train a neural network policy using BC (supervised learning on state-action pairs). (3) Evaluate on 50 test episodes. (4) Now start from random states NOT in the training distribution. How quickly does performance degrade? This is covariate shift -- you must observe it empirically.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 5.5 | DAgger: Dataset Aggregation fixing covariate shift | [Pieter Abbeel -- DAgger paper walkthrough](https://www.youtube.com/watch?v=WjFrmric-Bs) | What does DAgger do that BC doesn't? What is the role of the human/expert in DAgger's training loop? |
| 5.6 | DAgger limitations: human in the loop cost | [Pieter Abbeel -- IL lecture](https://www.youtube.com/watch?v=WjFrmric-Bs) | Why is DAgger expensive in practice for physical robots? What safety risk does it introduce? |
| 5.7 | Inverse Reinforcement Learning (IRL): learn the reward | [Pieter Abbeel -- IRL paper](https://www.youtube.com/watch?v=h7uGyBcIeII) | What does IRL recover that BC does not? Why is a learned reward function more general than a learned policy? |
| 5.8 | MaxEnt IRL: maximum entropy formulation | [Chelsea Finn -- IRL and Meta-Learning](https://www.youtube.com/watch?v=h7uGyBcIeII) | What does the maximum entropy principle add to IRL? What distribution over trajectories does MaxEnt IRL produce? |

> **Mini Assignment 5.2 -- Implement DAgger:** (1) Start with your BC implementation from Mini Assignment 5.1. (2) Add one DAgger iteration: run the current policy, query the expert for correct actions at visited states, add to dataset. (3) Retrain on the augmented dataset. (4) Compare performance vs pure BC after 3 DAgger rounds. Plot the improvement. (5) How many expert queries did DAgger require vs BC?

---

## Section 2 -- Modern IL architectures

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 5.9 | GAIL: Generative Adversarial Imitation Learning | [Yannic Kilcher -- GAIL paper](https://www.youtube.com/watch?v=eyxmSmjmNS0) | What plays the role of generator and discriminator in GAIL? What does the discriminator learn to distinguish? |
| 5.10 | AIRL: Adversarial Inverse RL | [Chelsea Finn -- AIRL](https://www.youtube.com/watch?v=h7uGyBcIeII) | How does AIRL improve on GAIL? What does AIRL recover that GAIL cannot? |
| 5.11 | ACT: Action Chunking with Transformers | [Tony Zhao -- ACT paper walkthrough (author)](https://www.youtube.com/watch?v=zMdVfWFMDQs) | What is "action chunking"? Why does predicting k future actions reduce the compounding error problem vs single-step BC? |
| 5.12 | CVAE in ACT: handling multimodal demonstrations | [Tony Zhao -- ACT paper](https://www.youtube.com/watch?v=zMdVfWFMDQs) | What does the CVAE in ACT model? Why is a multimodal distribution important when learning from multiple human demonstrators? |

> **Mini Assignment 5.3 -- Run the official ACT code:** (1) Clone the ACT repository: https://github.com/tonyzhaozh/act. (2) Run the simulation environment. (3) Collect 50 demonstrations using the teleoperation interface. (4) Train ACT on your demonstrations. (5) Evaluate: how many successes out of 20 rollouts? (6) Try temporal ensemble -- does it improve success rate? Read every line of the training script.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 5.13 | Diffusion Policy: robot actions as denoising | [HuggingFace Robotics Course](https://huggingface.co/learn/robotics-course) | What does the diffusion model learn in Diffusion Policy? Why is it better than BC for multimodal action distributions? |
| 5.14 | BC for robot assistance (HRI context) | [Losey VT lectures -- 08imitationlearning1.pdf](lectures/) | How does BC for assistive robotics differ from BC for autonomous robots? What additional signal does the human provide? |

> **Mini Assignment 5.4 -- Compare BC vs Diffusion Policy:** Using the HuggingFace LeRobot library (https://github.com/huggingface/lerobot): (1) Train a BC policy on a manipulation task from the dataset. (2) Train a Diffusion Policy on the same data. (3) Compare success rates across 50 rollouts. (4) Visualize the action distributions -- does Diffusion Policy capture multimodality that BC misses?
