# How to Practice

> The strategies that researchers, engineers, and ML practitioners actually use to build lasting skill. Watching videos is not learning -- doing is learning.

---

## Math

**Pencil and paper only.** Never just watch. Pause, rederive every formula yourself, cover the solution, attempt the problem, then compare. If you cannot do it without looking, you do not know it.

- [MIT OCW 18.06 Linear Algebra](https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/) -- free problem sets with solutions
- [MIT OCW Single Variable Calculus](https://ocw.mit.edu/courses/18-01sc-single-variable-calculus-fall-2010/) -- free problem sets
- [Khan Academy Linear Algebra](https://www.khanacademy.org/math/linear-algebra) -- auto-graded exercises for self-checking
- [Anki](https://apps.ankiweb.net/) -- flashcards for key formulas (spaced repetition)

**Daily habit:** 3-5 problems per day. Return to earlier topics weekly.

---

## Python and C++

**Type every line yourself.** Never copy-paste code. Mistakes you make while typing are where the learning happens.

**The four-step method:**
1. Run the tutorial code as-is
2. Change one thing and see what breaks
3. Break it intentionally, then fix it
4. Rebuild from scratch without looking

- [LeetCode Explore (Python)](https://leetcode.com/explore/learn/card/python/) -- Easy level, 10 minutes each
- [Google Colab](https://colab.research.google.com) -- free GPU, pre-installed libraries, no setup
- For C++: compile and run your code, do not just read it

---

## Computer Vision and OpenCV

- [Roboflow](https://roboflow.com/) -- free datasets and labeling tools; train your own YOLO model
- [Segment Anything playground](https://segment-anything.com/) -- build intuition before coding
- **Goal:** run YOLO on your webcam, detect objects in real time, publish detections to a ROS2 topic. That is a complete real HRI perception pipeline.

---

## Machine Learning and Deep Learning

- [Kaggle Learn](https://www.kaggle.com/learn) -- free micro-courses with auto-graded notebooks
- [fast.ai](https://course.fast.ai/) -- best hands-on DL course; you build real models in Week 1
- [Google Colab](https://colab.research.google.com) -- run all experiments here

**The reimplement-a-paper rule:** At the end of each phase, pick one classic paper and reimplement its main result from scratch. This is what separates practitioners from people who just watched videos.

---

## Reinforcement Learning

- [Gymnasium](https://gymnasium.farama.org/) + [Stable-Baselines3](https://stable-baselines3.readthedocs.io/) -- train PPO and SAC in under 20 lines of code
- [HuggingFace Deep RL Course](https://huggingface.co/learn/deep-rl-course) -- free, certificate-earning, hands-on
- [Gymnax](https://github.com/RobertTLange/gymnax) -- JAX-native environments for 1000x faster training (after you learn JAX)

---

## Imitation Learning and HRI

- **Your HW0-HW14 assignments** -- these are the primary HRI practice. They are research-grade problems.
- [HuggingFace LeRobot](https://github.com/huggingface/lerobot) -- run ACT and Diffusion Policy on real robot datasets
- [D4RL](https://github.com/Farama-Foundation/d4rl) -- offline RL and IL benchmark datasets

---

## ROS2 and Simulation

- [The Construct](https://www.theconstructsim.com/) -- browser-based ROS2 with real robots, no local install needed
- [MuJoCo Menagerie](https://github.com/deepmind/mujoco_menagerie) -- ready-to-use robot models (Franka, UR5, Spot)
- [Isaac Lab](https://isaac-sim.github.io/IsaacLab/) -- NVIDIA GPU-accelerated robot RL for sim-to-real transfer

---

## Daily study rhythm (the five-day cycle)

| Day | Activity |
|-----|----------|
| Day 1 | Watch the linked video, take notes on paper |
| Day 2 | Quiz yourself (attempt before checking solutions), do math problems |
| Day 3 | Write and run the code from the assignment |
| Day 4 | Explain the concept out loud as if teaching someone (Feynman technique) |
| Day 5 | Rest, or review a concept from two weeks ago |

**The Feynman technique:** After each concept, explain it out loud as if teaching a friend with no background. If you cannot explain it simply, you do not understand it yet. Go back and rewatch.

---

## Keep a learning log

After each session, add a brief entry to [PROGRESS.md](PROGRESS.md):
- What concept you covered
- What confused you
- What connects to your HRI course
- Any code that was hard to get working

Reviewing this log weekly prevents knowledge decay. Committing it to git gives you a permanent timestamped record of your learning journey.

---

## Connect everything to HRI constantly

After every foundation topic, ask: where does this appear in my HRI course?

- Gradient descent (Phase 02) -- used in every neural network trained for HRI
- Bayesian inference (Phase 01) -- is literally Lecture 3 of your VT course
- PPO/SAC (Phase 04) -- appears in Lecture 9 slides by name
- Behavior cloning (Phase 05) -- is Lecture 8 of your VT course
- YOLO object detection (Phase 03B) -- used in real robot perception pipelines

The "used in HRI" tags in each phase README are your guide.
