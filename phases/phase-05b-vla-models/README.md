# Phase 05B -- VLA Models and Foundation Models for Robotics

> **Time estimate:** 3-4 weeks  
> **Rule:** Every concept has a Quick Quiz. Every 3-4 concepts has a Mini Assignment.

---

## Section 1 -- Vision-Language-Action models

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| VLA.1 | What is a VLA model and why does it matter? | [Two Minute Papers -- RT-2](https://www.youtube.com/watch?v=GNlODFTKSy4) | What three modalities does a VLA model connect? What enables VLA models to generalize to new tasks without retraining? |
| VLA.2 | RT-1: Robotic Transformer architecture | [Brohan et al. -- RT-1 paper](https://arxiv.org/abs/2212.06817) | How does RT-1 tokenize robot actions? What is the input and output of RT-1? |
| VLA.3 | RT-2: VLM fine-tuned on robot data | [DeepMind -- RT-2 blog](https://www.deeplearning.ai/the-batch/rt-2-a-vision-language-action-model/) | What pretrained model is RT-2 built on? What does co-fine-tuning on robot data and web data each contribute? |
| VLA.4 | OpenVLA: open-source 7B parameter VLA | [OpenVLA -- official repository](https://github.com/openvla/openvla) | What base model is OpenVLA built on? How do you fine-tune OpenVLA for a new robot task? |

> **Mini Assignment VLA.1 -- Run OpenVLA inference:** (1) Clone the OpenVLA repository. (2) Load the pretrained model. (3) Give it a language instruction and a camera image. (4) Decode the output action token. (5) Visualize what action it predicts. (6) Try 5 different language instructions on the same image. How does the output change?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| VLA.5 | CLIP: contrastive language-image pretraining | [Yannic Kilcher -- CLIP paper](https://www.youtube.com/watch?v=T9XSU0pKX2E) | What does CLIP learn to align? What is the contrastive objective and what are positive/negative pairs? |
| VLA.6 | SayCan: LLM plans grounded in robot affordances | [SayCan -- official site](https://say-can.github.io) | What problem does SayCan solve that a pure LLM cannot? What is an "affordance" in this context? |
| VLA.7 | Code as Policies: LLMs writing robot control code | [Code as Policies -- site](https://code-as-policies.github.io) | What is the advantage of generating code vs generating actions directly? What can code express that token-level actions cannot? |

> **Mini Assignment VLA.2 -- Build a CLIP-based object picker:** (1) Load a pretrained CLIP model from HuggingFace. (2) Given an image of a table with several objects and a text instruction ("pick up the red cup"), use CLIP to score which object best matches. (3) Draw a bounding box around the top-scoring object. (4) Test with 5 different instructions on the same image. This is the core of many language-conditioned manipulation systems.

---

## Section 2 -- Diffusion models for robotics

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| VLA.8 | Diffuser: offline RL and planning with diffusion | [Janner et al. -- Diffuser paper](https://arxiv.org/abs/2205.09991) | How does Diffuser formulate trajectory planning as denoising? What replaces the Q-function as a guide? |
| VLA.9 | 3D Diffusion Policy: diffusion on point clouds | [Two Minute Papers -- 3D robot policies](https://www.youtube.com/watch?v=fbLgFrlTnGU) | What advantage does using 3D point cloud observations give over 2D images for manipulation? |
| VLA.10 | Consistency models for faster inference | [OpenAI -- Consistency Models paper](https://arxiv.org/abs/2303.01469) | Why are diffusion models slow at inference time? What does a consistency model do differently to enable single-step generation? |

---

## Section 3 -- World models for robotics

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| VLA.11 | World models: learning a simulator of the environment | [Two Minute Papers -- world models](https://www.youtube.com/watch?v=wzV1yDNGgLY) | What does a world model learn to predict? How does it enable planning without interacting with the real environment? |
| VLA.12 | DreamerV3: world models for model-based RL | [Two Minute Papers -- DreamerV3](https://www.youtube.com/watch?v=vfh2E9UEZiA) | What does DreamerV3 learn inside its latent space? How does it train a policy without environment rollouts? |
| VLA.13 | UniSim: neural sensor simulator | [UniSim paper](https://arxiv.org/abs/2308.01545) | What does UniSim simulate? How does having a photorealistic neural simulator help with data collection for robot learning? |

> **Mini Assignment VLA.3 -- Explore the Open X-Embodiment dataset:** (1) Access the dataset: https://robotics-transformer-x.github.io. (2) Load 10 episodes from different robot platforms. (3) Visualize the trajectories (images + actions). (4) What is the most common task type? (5) What differences do you notice between episodes from different robot embodiments? (6) Write a data loader in PyTorch that reads episodes from this dataset.

---

## Section 4 -- ACT in depth

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| VLA.14 | ACT full architecture walkthrough | [Tony Zhao -- ACT author walkthrough](https://www.youtube.com/watch?v=zMdVfWFMDQs) | Draw the ACT architecture: what are the inputs to the encoder? What does the decoder generate? |
| VLA.15 | Action chunking theory: why k steps beats 1 | [Tony Zhao -- ACT paper](https://www.youtube.com/watch?v=zMdVfWFMDQs) | If you predict 100 future actions and execute all of them, what risk do you run? How does temporal ensemble address this? |
| VLA.16 | Temporal ensemble: averaging overlapping chunks | [Tony Zhao -- ACT implementation](https://github.com/tonyzhaozh/act) | Explain the temporal ensemble algorithm in one paragraph. What weighting scheme does ACT use and why? |
| VLA.17 | Diffusion Policy vs ACT: when to use each | [HuggingFace LeRobot benchmark](https://huggingface.co/lerobot) | What task types favor Diffusion Policy? What task types favor ACT? What is the main computational difference? |

> **Mini Assignment VLA.4 -- Implement ACT from scratch:** Following the ACT paper and Tony Zhao's code: (1) Implement the CVAE encoder in PyTorch. (2) Implement the Transformer decoder that generates an action chunk. (3) Implement the temporal ensemble at inference time. (4) Train on a simple simulated task. This is the single most important implementation exercise in the VLA phase.
