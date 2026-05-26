# Phase 04 -- Quiz Solutions

## Q1 -- Answer: B
The agent is the learner and decision-maker. In HRI, the robot is the agent. It observes state, selects action, receives reward, updates policy. The human and physical world form the environment.

## Q2 -- Answer: B
P(s_{t+1} | s_t, s_{t-1},...) = P(s_{t+1} | s_t). Only the current state matters -- not all past history. In HRI, we design the state to include robot config + human position + inferred intent so the Markov property holds.

## Q3 -- Answer: B
V(s): how good is this state? Q(s,a): how good is this specific action in this state? Q-functions enable direct action selection: best_action = argmax_a Q(s,a). Actor-Critic methods use both.

## Q4 -- Answer: B
PPO clips the ratio r_t = pi_new(a|s)/pi_old(a|s) within [1-epsilon, 1+epsilon]. This prevents catastrophically large policy updates. Before PPO, policy gradient training was notoriously unstable. PPO made deep RL practical for robotics.

## Q5 -- Answer: B
SAC is off-policy (uses a replay buffer, reuses old data) and adds entropy bonus to encourage exploration. PPO is on-policy (uses only fresh data), simpler, more stable. In HRI robotics: SAC is preferred for continuous control (robot arm movements). SAC appears in your Lecture 9 slides.

## Q6 -- Answer: B
JAX's @jax.jit compiles Python functions to XLA, enabling full GPU acceleration. With jax.vmap over 1024 environments: potentially 1,000,000+ steps/second vs ~1,000 with standard PyTorch RL. Tasks that take 12 hours in PyTorch take 5 minutes in JAX. This is why Google DeepMind uses JAX for RL research.
