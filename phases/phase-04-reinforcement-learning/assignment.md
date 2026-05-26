# Phase 04 -- Assignment: PPO and SAC on Control Tasks

## Setup

```bash
pip install gymnasium stable-baselines3
```

## Part 1 -- PPO on CartPole

```python
import gymnasium as gym
from stable_baselines3 import PPO
import numpy as np

env = gym.make("CartPole-v1")
model = PPO("MlpPolicy", env, verbose=1)
model.learn(total_timesteps=100_000)
model.save("ppo_cartpole")

# Evaluate
eval_env = gym.make("CartPole-v1")
rewards = []
for _ in range(20):
    obs, _ = eval_env.reset()
    total_reward = 0
    done = False
    while not done:
        action, _ = model.predict(obs, deterministic=True)
        obs, reward, terminated, truncated, _ = eval_env.step(action)
        total_reward += reward
        done = terminated or truncated
    rewards.append(total_reward)

print(f"Average reward: {np.mean(rewards):.1f} (target: 400+)")
```

## Part 2 -- SAC on Pendulum (continuous actions)

```python
from stable_baselines3 import SAC

env = gym.make("Pendulum-v1")
model = SAC("MlpPolicy", env, verbose=1)
model.learn(total_timesteps=50_000)
model.save("sac_pendulum")
```

## Part 3 -- Questions to answer

1. Why is SAC better suited for Pendulum (continuous torque) than CartPole (discrete left/right)?
2. How does SAC entropy regularization relate to HRI? Why might a robot that explores more be better at learning human preferences?
3. What is the practical difference between on-policy (PPO) and off-policy (SAC) training?

## Checklist
- [ ] PPO trained on CartPole, average reward > 400
- [ ] SAC trained on Pendulum
- [ ] Three questions answered

## What to commit
```bash
git add phases/phase-04-reinforcement-learning/
git commit -m "Phase 04 assignment: PPO and SAC"
git push
```
