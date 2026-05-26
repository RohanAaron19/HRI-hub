# Phase 07 -- HRI Core (VT Lectures 1-9)

> **This is your actual VT course (ME/CS 4824/5824/5844, Prof. Dylan Losey).**  
> All lecture slides and discussion sets are in the [`lectures/`](lectures/) folder.  
> **Rule:** Every concept has a Quick Quiz tied directly to the lecture content. Mini Assignments are based on the discussion problems.

---

## VT Course Lecture PDFs (Prof. Dylan Losey, Spring 2026)

All lecture slides and discussion sets are in the [`lectures/`](lectures/) folder.

| Week | Lecture PDF | Discussion PDF | Topic |
|------|------------|---------------|-------|
| 1 | [01 Introduction](lectures/01introduction.pdf) | [Discussion 01](lectures/discussion_01.pdf) | What is HRI? Robot policies, learning paradigms |
| 2 | [02 Physical Interaction](lectures/02physicalinteraction.pdf) | [Discussion 02](lectures/discussion_02.pdf) | Impedance control, physical HRI, compliance |
| 3 | [03 Human Models](lectures/03humanmodels.pdf) | [Discussion 03](lectures/discussion_03.pdf) | Boltzmann rationality, Bayesian goal inference |
| 4 | [04 Shared Autonomy](lectures/04sharedautonomy.pdf) | [Discussion 04](lectures/discussion_04.pdf) | Blending human and robot control |
| 5 | [05 Safety](lectures/05safety.pdf) | [Discussion 05](lectures/discussion_05.pdf) | Control Barrier Functions, safe robot control |
| 6 | [06 Assistive Robotics](lectures/06assistiverobotics.pdf) | [Discussion 06](lectures/discussion_06.pdf) | Assistive devices, human-in-the-loop |
| 7 | [07 Communication](lectures/07communication.pdf) | [Discussion 07](lectures/discussion_07.pdf) | Robot legibility, predictability, expressive motion |
| 8 | [08 Imitation Learning I](lectures/08imitationlearning1.pdf) | [Discussion 08](lectures/discussion_08.pdf) | Behavior Cloning, covariate shift, DAgger |
| 9 | [09 Imitation Learning II](lectures/09imitationlearning2.pdf) | [Discussion 09](lectures/discussion_09.pdf) | IRL, GAIL, reward learning from demonstrations |

**Course syllabus:** [syllabus_HRI.pdf](syllabus_HRI.pdf)

---

---

## Week 1 -- Introduction to HRI

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| H.1 | What is HRI? Robot policies as mappings S→A | [01 Introduction](lectures/01introduction.pdf) | What is a robot policy π? Write it as a mathematical function. What is the difference between a deterministic and stochastic policy? |
| H.2 | Learning paradigms: RL, IL, reward learning | [01 Introduction](lectures/01introduction.pdf) | In your own words, what is the key difference between RL and imitation learning? Which requires a reward function? |
| H.3 | The HRI problem: robots working with humans | [01 Introduction](lectures/01introduction.pdf) | Why does the presence of a human fundamentally change the robot planning problem compared to standard RL? |

> **Discussion 1:** Open [discussion_01.pdf](lectures/discussion_01.pdf) and work through all problems in writing before checking with classmates.

---

## Week 2 -- Physical Interaction

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| H.4 | Impedance control: force-position tradeoff | [02 Physical Interaction](lectures/02physicalinteraction.pdf) | What does impedance control regulate? Write the impedance relationship F = K(x_d - x) + D(ẋ_d - ẋ). What does high K mean physically? |
| H.5 | Admittance control: inverse of impedance | [02 Physical Interaction](lectures/02physicalinteraction.pdf) | What is the difference between impedance and admittance control? Which is better when the robot interacts with a stiff environment? |
| H.6 | Physical compliance and safety in HRI | [02 Physical Interaction](lectures/02physicalinteraction.pdf) | Why is a compliant robot safer near humans than a stiff position-controlled robot? Give a concrete injury scenario that compliance prevents. |

> **Discussion 2:** Open [discussion_02.pdf](lectures/discussion_02.pdf) and work through all problems.

---

## Week 3 -- Human Models

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| H.7 | Boltzmann rationality: humans as noisy optimal agents | [03 Human Models](lectures/03humanmodels.pdf) | Write the Boltzmann distribution over actions: P(a\|s,θ) = ? What does the temperature parameter β control? What does β→∞ give you? |
| H.8 | Bayesian goal inference: posterior over human goals | [03 Human Models](lectures/03humanmodels.pdf) | Write the Bayes update for P(θ\|obs). What is the prior P(θ)? What is the likelihood P(obs\|θ)? |
| H.9 | Recursive belief update over multiple observations | [03 Human Models](lectures/03humanmodels.pdf) | If a robot receives 5 observations, how do you recursively update the goal belief? Does the order of observations matter? Why not? |

> **Discussion 3:** Open [discussion_03.pdf](lectures/discussion_03.pdf) and work through all problems. **Key problem:** Compute the posterior P(goal\|obs) for a specific scenario using Bayes theorem.

> **Mini Assignment H.1 -- Implement Bayesian goal inference:** (1) Define 3 possible human goals in a 2D workspace (pick up cup, pick up plate, pick up bottle). (2) For each goal, define a Gaussian likelihood over 2D human hand positions. (3) Start with a uniform prior. (4) As you observe 10 sequential hand positions, update the belief using Bayes theorem at each step. (5) Plot how the belief evolves. (6) At what observation does the robot become 90% confident about the goal?

---

## Week 4 -- Shared Autonomy

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| H.10 | Shared autonomy: blending human and robot control | [04 Shared Autonomy](lectures/04sharedautonomy.pdf) | What is the blending parameter α in shared autonomy? When α=0, who controls? When α=1? |
| H.11 | Javdani et al. framework: assistance as goal inference | [04 Shared Autonomy](lectures/04sharedautonomy.pdf) | How does the robot use the inferred goal distribution to decide how much to assist? What happens when goal uncertainty is high? |
| H.12 | Preserving human control authority | [04 Shared Autonomy](lectures/04sharedautonomy.pdf) | Why is it important for the robot NOT to take over completely even when it's confident about the goal? What is the risk of full robot authority? |

> **Discussion 4:** Open [discussion_04.pdf](lectures/discussion_04.pdf) and work through all problems.

> **Mini Assignment H.2 -- Shared autonomy simulation:** (1) Build a 2D simulation where a human controls a cursor to reach one of 3 goals. (2) Implement Bayesian goal inference updating at each timestep. (3) Implement assistance: blend the human input with a robot action toward the most likely goal, weighted by confidence. (4) Compare task completion time: human alone vs shared autonomy. (5) What happens when the robot incorrectly infers the goal?

---

## Week 5 -- Safety

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| H.13 | Control Barrier Functions (CBFs): formal safety guarantees | [05 Safety](lectures/05safety.pdf) | What does a CBF h(x)≥0 define? Write the CBF condition: ḣ(x,u) ≥ ? What does this guarantee? |
| H.14 | Safe robot control with CBF-QP | [05 Safety](lectures/05safety.pdf) | How does the CBF-QP formulation modify a nominal control input to make it safe? What is the optimization problem you solve? |
| H.15 | Safety in physical HRI: avoiding human harm | [05 Safety](lectures/05safety.pdf) | What are the key safety constraints in physical HRI? Give 3 concrete safety constraints you would enforce with CBFs for a robot arm near a human. |

> **Discussion 5:** Open [discussion_05.pdf](lectures/discussion_05.pdf) and work through all problems.

---

## Week 6 -- Assistive Robotics

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| H.16 | Assistive devices: wheelchairs, prosthetics, exoskeletons | [06 Assistive Robotics](lectures/06assistiverobotics.pdf) | What makes assistive robotics different from industrial robotics? What are the unique HRI challenges for assistive devices? |
| H.17 | Human-in-the-loop control for assistive devices | [06 Assistive Robotics](lectures/06assistiverobotics.pdf) | What interface modalities (EMG, EEG, joystick, eye gaze) can a paralyzed user use to control a robot arm? What are the tradeoffs? |

> **Discussion 6:** Open [discussion_06.pdf](lectures/discussion_06.pdf) and work through all problems.

---

## Week 7 -- Communication

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| H.18 | Robot legibility (Dragan et al.): predictable motion | [07 Communication](lectures/07communication.pdf) | What is the difference between a predictable robot and a legible robot? Which requires knowing the observer's inference model? |
| H.19 | Expressive robot motion: communicating intent | [07 Communication](lectures/07communication.pdf) | How can a robot communicate its intention through motion without speech? Give 2 concrete examples. |
| H.20 | Predictability vs legibility tradeoff | [07 Communication](lectures/07communication.pdf) | Why can a maximally legible trajectory NOT be the most predictable one? What is the fundamental tension? |

> **Discussion 7:** Open [discussion_07.pdf](lectures/discussion_07.pdf) and work through all problems.

---

## Week 8 -- Imitation Learning I

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| H.21 | Behavior Cloning for robot assistance | [08 Imitation Learning I](lectures/08imitationlearning1.pdf) | How does BC for a robot assistant differ from BC for an autonomous robot? What additional context does the human provide? |
| H.22 | Covariate shift in HRI contexts | [08 Imitation Learning I](lectures/08imitationlearning1.pdf) | Give a concrete example of covariate shift in a robot arm assistance task. What states does the BC policy fail at? |
| H.23 | Human corrections as learning signal | [08 Imitation Learning I](lectures/08imitationlearning1.pdf) | When a human physically corrects a robot's motion, what information does that correction encode? How can the robot learn from it? |

> **Discussion 8:** Open [discussion_08.pdf](lectures/discussion_08.pdf) and work through all problems.

> **Mini Assignment H.3 -- Implement BC for robot assistance:** (1) Set up a simulated assistive task where a human (scripted) tries to move an object to a goal. (2) Collect 50 demonstrations. (3) Train a BC policy that assists the human (predicts helpful robot actions given the human's current action). (4) Evaluate: does the assisted human reach the goal faster? (5) Intentionally start the human in a state not seen in training. Does the BC policy help or hinder?

---

## Week 9 -- Imitation Learning II

| # | Concept | Lecture | Quick quiz |
|---|---------|---------|-----------|
| H.24 | IRL for inferring human preferences | [09 Imitation Learning II](lectures/09imitationlearning2.pdf) | What does IRL recover that BC does not? Why is a recovered reward function more useful than a recovered policy? |
| H.25 | GAIL in the HRI context | [09 Imitation Learning II](lectures/09imitationlearning2.pdf) | How does GAIL avoid explicitly defining a reward function? What does the discriminator learn to distinguish in an HRI GAIL setup? |
| H.26 | Reward learning from pairwise preferences | [09 Imitation Learning II](lectures/09imitationlearning2.pdf) | Describe the preference-based reward learning loop. What does the human provide? What does the model learn to predict? |

> **Discussion 9:** Open [discussion_09.pdf](lectures/discussion_09.pdf) and work through all problems.
