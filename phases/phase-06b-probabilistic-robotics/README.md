# Phase 06B -- Probabilistic Robotics

> **Time estimate:** 3-4 weeks  
> **Primary textbook:** Thrun, Burgard & Fox -- Probabilistic Robotics (free PDF): https://docs.ufpr.br/~danielsantos/ProbabilisticRobotics.pdf  
> **Lecture series:** Cyrill Stachniss -- Mobile Sensing and Robotics: https://www.youtube.com/playlist?list=PLgnQpQtFTOGQrZ4O5QzbIHgl3b1JHimN_  
> **Rule:** Every concept has a Quick Quiz. Every 3-4 concepts has a Mini Assignment.

---

## Section 1 -- Bayes filters

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| PR.1 | The Bayes filter: recursive state estimation | [Cyrill Stachniss -- Bayes filter lecture](https://www.youtube.com/watch?v=0lKD1pi3BE8) | Write the two steps of the Bayes filter (prediction and update). What does bel(x_t) represent? |
| PR.2 | Belief distributions: representing uncertainty about robot state | [Cyrill Stachniss -- Bayes filter lecture](https://www.youtube.com/watch?v=0lKD1pi3BE8) | Why does a robot maintain a probability distribution over states rather than a single state estimate? Give a robot scenario where uncertainty is critical. |
| PR.3 | Prediction step: propagating belief through motion model | [Cyrill Stachniss -- Bayes filter lecture](https://www.youtube.com/watch?v=0lKD1pi3BE8) | What does the prediction step do to a Gaussian belief when you apply a noisy motion command? Does it make the distribution wider or narrower? Why? |
| PR.4 | Update step: sharpening belief with sensor measurement | [Cyrill Stachniss -- Bayes filter lecture](https://www.youtube.com/watch?v=0lKD1pi3BE8) | What happens to a Gaussian belief when a precise sensor measurement arrives? What determines how much the sensor narrows the distribution? |

> **Mini Assignment PR.1 -- Implement a 1D Bayes filter:** A robot moves along a hallway with 3 possible positions (A, B, C). (1) Initialize a uniform belief. (2) The robot moves right (noisy: 80% chance of moving right, 20% chance of staying). Update belief with the motion model. (3) The robot senses "door" (P(door|A)=0.9, P(door|B)=0.2, P(door|C)=0.4). Update belief with Bayes theorem. (4) Repeat for 5 steps. Plot belief at each step. This is the exact computation that runs inside every localization system.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| PR.5 | Kalman filter: Bayes filter for linear Gaussian systems | [Cyrill Stachniss -- Kalman filter lecture](https://www.youtube.com/watch?v=s_9InuQAx-g) | What two assumptions make the Kalman filter exact (optimal)? Write the 5 Kalman filter equations. |
| PR.6 | Extended Kalman Filter (EKF): linearization for nonlinear systems | [Cyrill Stachniss -- EKF lecture](https://www.youtube.com/watch?v=DE6Jn2cB4J4) | How does the EKF handle nonlinear motion models? What is the Jacobian used for in EKF? When does linearization fail? |
| PR.7 | Unscented Kalman Filter (UKF): sigma point approximation | [Thrun Chapter 3](https://docs.ufpr.br/~danielsantos/ProbabilisticRobotics.pdf) | What problem does UKF solve that EKF doesn't? What are sigma points and why are they better than a single linearization? |
| PR.8 | Particle filter: nonparametric Bayes via sampling | [Cyrill Stachniss -- Particle filter](https://www.youtube.com/watch?v=MsYlueVDLI0) | What is a particle? What are the three steps of a particle filter (sample, weight, resample)? When does a particle filter degenerate? |

> **Mini Assignment PR.2 -- Implement a Kalman filter for robot localization:** A robot moves in 1D with noisy odometry (σ_motion=0.5m). A GPS sensor gives noisy position measurements (σ_gps=1.0m). (1) Implement the full Kalman filter: predict step (use motion model), update step (use GPS measurement). (2) Simulate 100 timesteps. (3) Plot: true position, noisy odometry, GPS measurements, and Kalman filter estimate. (4) Compute RMSE of odometry alone vs Kalman filter. How much does the filter help?

---

## Section 2 -- Robot models

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| PR.9 | Velocity motion model: pose uncertainty from velocity commands | [Cyrill Stachniss -- motion models](https://www.youtube.com/watch?v=5VELtbV2pv0) | What 4 noise parameters does the velocity motion model have? If you command v=1m/s, w=0, why does the robot not end up exactly 1m forward? |
| PR.10 | Odometry motion model: wheel encoder noise | [Cyrill Stachniss -- motion models](https://www.youtube.com/watch?v=5VELtbV2pv0) | What causes odometry drift? If the robot drives in a circle, what shape does the uncertainty ellipse grow into over time? |
| PR.11 | Beam model for range sensors (LIDAR, sonar) | [Thrun Chapter 6](https://docs.ufpr.br/~danielsantos/ProbabilisticRobotics.pdf) | What are the 4 components of the beam sensor model? What causes an unexpected short reading in a LIDAR scan? |
| PR.12 | Likelihood field model: efficient sensor likelihood | [Thrun Chapter 6](https://docs.ufpr.br/~danielsantos/ProbabilisticRobotics.pdf) | Why is the likelihood field model computationally cheaper than the beam model? What preprocessing step does it require on the map? |

> **Mini Assignment PR.3 -- Particle filter localization:** (1) Load a 2D grid map. (2) Initialize 1000 particles uniformly across the map. (3) Simulate robot motion and LIDAR readings (you can use a fake robot). (4) At each step: propagate particles through the motion model, weight by LIDAR likelihood field, resample. (5) Track the particle cloud over 50 steps. Does it converge? What happens when you reduce to 100 particles?

---

## Section 3 -- Mapping and localization

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| PR.13 | Occupancy grid mapping: representing the environment | [Cyrill Stachniss -- occupancy grid mapping](https://www.youtube.com/watch?v=v-Rm9TUQ9LY) | What does each cell in an occupancy grid store? What does a value of 0.9 mean? What does 0.5 mean? |
| PR.14 | Log-odds representation: numerically stable updates | [Thrun Chapter 9](https://docs.ufpr.br/~danielsantos/ProbabilisticRobotics.pdf) | Why do we use log-odds instead of probabilities for occupancy updates? Write the log-odds update rule. |
| PR.15 | Monte Carlo Localization (AMCL) | [Cyrill Stachniss -- MCL lecture](https://www.youtube.com/watch?v=MsYlueVDLI0) | What does AMCL add to basic MCL? How does it adapt the number of particles based on uncertainty? |

> **Mini Assignment PR.4 -- Build an occupancy grid mapper:** (1) Simulate a robot with a LIDAR sensor in a simple 2D environment. (2) As the robot moves (using your motion model), update an occupancy grid using log-odds. (3) Plot the growing map as the robot explores. (4) Compare: what does the map look like after 100 steps vs 500 steps? (5) Add noise to the LIDAR readings. How does it affect the map quality?

---

## Section 4 -- SLAM

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| PR.16 | The SLAM problem: localization and mapping are coupled | [Cyrill Stachniss -- SLAM introduction](https://www.youtube.com/watch?v=wVsfCnHto2g) | Why can't you solve localization and mapping independently? What is the chicken-and-egg problem in SLAM? |
| PR.17 | Graph-based SLAM: pose graph optimization | [Cyrill Stachniss -- graph-based SLAM](https://www.youtube.com/watch?v=uHbRKvD8TWg) | What are the nodes and edges in a pose graph? What does loop closure detection add to the graph? |
| PR.18 | g2o and GTSAM: open-source graph optimization | [GTSAM -- official tutorial](https://gtsam.org/tutorials/intro.html) | What optimization algorithm does g2o use to solve the pose graph? What does GTSAM's factor graph represent? |
| PR.19 | LiDAR SLAM: Cartographer and LOAM | [Google Cartographer -- official docs](https://google-cartographer-ros.readthedocs.io) | What sensor does Cartographer primarily use? What does the submapping approach solve for large environments? |

> **Mini Assignment PR.5 -- Run SLAM on a real dataset:** (1) Download the KITTI or TUM dataset. (2) Run ORB-SLAM3 on the sequence. (3) Visualize the trajectory and 3D point cloud. (4) Compare the estimated trajectory to ground truth (if available). (5) What happens to the map when you remove loop closure? Run it with loop closure disabled and compare.
