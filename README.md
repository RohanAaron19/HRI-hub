# HRI Learning Hub 🤖

> Complete self-study curriculum from Python and C++ fundamentals to Human-Robot Interaction mastery.  
> Aligned to **Virginia Tech ME/CS 4824 / 5824 / 5844** — Prof. Dylan Losey.

---

## Who this is for

A Mechanical Engineering graduate student with no prior ML or coding experience who wants to reach full working mastery of Human-Robot Interaction — able to read papers, implement algorithms, design experiments, and do research in the field.

---

## Curriculum at a glance

| # | Phase | Key skills | Est. time |
|---|-------|-----------|-----------|
| 00 | [Python & C++ Fundamentals](phases/phase-00-python-cpp/) | Python, NumPy, Matplotlib, C++ basics | 4–6 weeks |
| 01 | [Math for ML and AI](phases/phase-01-math/) | Tiers 1-7: linear algebra, calculus, probability, statistics, optimization, information theory, numerical methods, loss functions, regularization | 3-4 months |
| 01B | [Data Processing](phases/phase-01b-data-processing/) | Data types, EDA, cleaning, imputation (mean/KNN/MICE/Hot-Deck/Cold-Deck), encoding, scaling, transformation, feature engineering, feature selection, dataset construction | 3-4 weeks |
| 02 | [Core Machine Learning](phases/phase-02-core-ml/) | Regression, classification, GPs, overfitting | 4–6 weeks |
| 03 | [Deep Learning + PyTorch + JAX](phases/phase-03-deep-learning-pytorch-jax/) | Neural nets, backprop, PyTorch, JAX, Transformers | 6–8 weeks |
| 03B | [Computer Vision + OpenCV](phases/phase-03b-computer-vision-opencv/) | OpenCV, YOLO, SAM, segmentation, depth | 3–4 weeks |
| 04 | [Reinforcement Learning](phases/phase-04-reinforcement-learning/) | MDPs, DQN, PPO, SAC, TD3, MARL, offline RL | 4–6 weeks |
| 05 | [Imitation Learning](phases/phase-05-imitation-learning/) | BC, DAgger, IRL, ACT, Diffusion Policy | 3–4 weeks |
| 05B | [VLA Models + Foundation Models](phases/phase-05b-vla-models/) | RT-2, OpenVLA, CLIP, ACT in depth, Diffuser, 3D Diffusion Policy, world models, language-conditioned manipulation, Open X-Embodiment | 3–4 weeks |
| 06 | [ROS2 & Simulation](phases/phase-06-ros2-simulation/) | ROS2, Gazebo, MuJoCo, Isaac Sim, Nav2, MoveIt2 | 4–6 weeks |
| 06B | [Probabilistic Robotics](phases/phase-06b-probabilistic-robotics/) | Bayes filters, Kalman/particle filters, motion models, sensor models, occupancy grids, SLAM, AMCL, graph-based SLAM | 3–4 weeks |
| 07 | [HRI Core — VT Weeks 1–9](phases/phase-07-hri-core/) | Physical HRI, human models, shared autonomy, safety | 6–8 weeks |
| 08 | [Advanced HRI — VT Weeks 10–14](phases/phase-08-advanced-hri/) | Game theory, machine teaching, adaptation | 4–6 weeks |

**Total: 135 concepts · ~2,430 study hours · ~24 months at 2 hrs/day**

---

## How each phase is organized

Every phase folder contains:

```
phase-XX-name/
├── README.md       ← all concepts with YouTube links
├── quiz.md         ← 6 questions: 2 easy, 2 medium, 2 hard
├── solutions.md    ← full answers and explanations
└── assignment.md   ← hands-on coding or math task
```

---

## Recommended certifications

| Certificate | Provider | Phases covered | Cost |
|-------------|----------|---------------|------|
| Machine Learning Specialization | Andrew Ng / Coursera | 02 | ~$59/mo |
| Deep Learning Specialization | DeepLearning.AI / Coursera | 03 | ~$59/mo |
| PyTorch for Deep Learning | DeepLearning.AI / Coursera | 03 PyTorch | ~$59/mo |
| Deep RL Course | HuggingFace | 04 | Free |
| Robotics Course (LeRobot) | HuggingFace | 05 + VLA | Free |

> All Coursera courses can be **audited for free**. Apply for financial aid to get the certificate free.

See [certifications.md](certifications.md) for full details.

---

## How to use this repo

1. Start at Phase 00 and work in order
2. For each concept: watch the linked video → take notes → do the quiz → check solutions → complete the assignment
3. Track your progress in [PROGRESS.md](PROGRESS.md) and commit it — your git history becomes a timestamped record of your learning journey
4. Concepts tagged `[HRI]` appear directly in the VT course lectures

---

## VT course alignment

Phases 07 and 08 map directly to the 14-week lecture series, discussion materials, and homework assignments (HW0–HW14) from ME/CS 4824/5824/5844.

---

## License

MIT — use freely for personal learning.

---

*Aligned to VT ME/CS 4824/5824/5844 · Last updated May 2026*

---

## Key reference files

| File | What it contains |
|------|-----------------|
| [model-selection-guide.md](model-selection-guide.md) | **Which model to use for which problem** -- decision trees, comparison tables, rules of thumb for every data type |
| [resources.md](resources.md) | Every free resource organized by topic |
| [certifications.md](certifications.md) | Certification roadmap with links |
| [how-to-practice.md](how-to-practice.md) | Study strategies and daily rhythm |
| [PROGRESS.md](PROGRESS.md) | Your personal study log |
