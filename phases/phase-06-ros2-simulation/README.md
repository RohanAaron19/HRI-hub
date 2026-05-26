# Phase 06 -- ROS2 and Simulation

> **Time estimate:** 4-6 weeks  
> **Rule:** Every concept has a Quick Quiz. Every 3-4 concepts has a Mini Assignment.

---

## Section 1 -- ROS2 fundamentals

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| ROS.1 | What is ROS2 and why it exists | [Articulated Robotics -- ROS2 full series](https://www.youtube.com/@ArticulatedRobotics) | What problem does ROS2 solve that writing robot software from scratch would require? What is a node? |
| ROS.2 | Nodes, topics, publishers, subscribers | [Articulated Robotics -- ROS2 full series](https://www.youtube.com/@ArticulatedRobotics) | What is the difference between a publisher and a subscriber? What is a topic? Is communication synchronous or asynchronous? |
| ROS.3 | Services and actions: synchronous vs long-running | [Articulated Robotics -- ROS2 full series](https://www.youtube.com/@ArticulatedRobotics) | When would you use a service instead of a topic? When would you use an action instead of a service? Give robot examples of each. |
| ROS.4 | ROS2 message types: std_msgs, geometry_msgs, sensor_msgs | [Articulated Robotics -- ROS2 full series](https://www.youtube.com/@ArticulatedRobotics) | What message type would you use to publish a robot's velocity command? What about a camera image? What about a joint state? |

> **Mini Assignment ROS.1 -- Your first ROS2 node:** (1) Install ROS2 Humble or Iron. (2) Write a Python publisher node that publishes "Hello from Rohan" to a topic every 1 second. (3) Write a subscriber node that receives it and prints it with a timestamp. (4) Run both nodes simultaneously. (5) Use `ros2 topic echo` to inspect the topic from the command line. This is the ROS2 hello world.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| ROS.5 | TF2 transforms and coordinate frames | [Articulated Robotics -- TF2 tutorial](https://www.youtube.com/@ArticulatedRobotics) | What does a TF transform represent? Why does a robot arm need a tree of coordinate frames from base to end-effector? |
| ROS.6 | URDF: robot description format | [Articulated Robotics -- URDF tutorial](https://www.youtube.com/@ArticulatedRobotics) | What two things does a URDF define? What is the difference between a joint and a link? |
| ROS.7 | Launch files and parameters | [Articulated Robotics -- launch files](https://www.youtube.com/@ArticulatedRobotics) | What does a ROS2 launch file let you do that running each node manually doesn't? What is a parameter server? |
| ROS.8 | Colcon build system and package structure | [Articulated Robotics -- ROS2 packages](https://www.youtube.com/@ArticulatedRobotics) | What files are required in every ROS2 Python package? What does `colcon build --symlink-install` do? |

> **Mini Assignment ROS.2 -- Turtlebot controller:** (1) Install the turtlesim package. (2) Write a ROS2 node that makes the turtle drive in a square: 4 sides, 4 turns. (3) Use the TF2 listener to track the turtle's pose as it moves. (4) Add a service that resets the turtle to the origin when called. (5) Visualize the trajectory in rviz2.

---

## Section 2 -- Simulation environments

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| ROS.9 | Gazebo: ROS-integrated physics simulation | [Articulated Robotics -- Gazebo tutorial](https://www.youtube.com/@ArticulatedRobotics) | What does Gazebo simulate that a pure kinematic model doesn't? What file format describes the simulation world? |
| ROS.10 | MuJoCo: accurate physics for robot RL | [MuJoCo -- official documentation](https://mujoco.readthedocs.io) | What makes MuJoCo's contact dynamics more accurate than Gazebo? What file format does MuJoCo use for robot models? |
| ROS.11 | Isaac Sim / Isaac Lab: GPU-accelerated RL training | [NVIDIA Isaac Lab -- official docs](https://isaac-sim.github.io/IsaacLab/) | Why does GPU-based simulation enable 1000x faster RL training? What is "headless" simulation and why is it used for training? |
| ROS.12 | Gymnasium environments: standard RL interface | [Farama -- Gymnasium docs](https://gymnasium.farama.org) | What does the step() function return? What is the reset() function for? Write the standard RL loop structure. |

> **Mini Assignment ROS.3 -- Train RL in simulation:** (1) Load the Ant-v4 environment in MuJoCo via Gymnasium. (2) Run a random policy for 1000 steps -- what is the average reward? (3) Train SAC using Stable-Baselines3 for 500k steps. (4) Render a video of the trained policy. (5) Save and reload the trained model. This is the sim-to-real starting point.

---

## Section 3 -- Navigation and planning

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| ROS.13 | Nav2: autonomous navigation stack | [Nav2 -- official documentation](https://nav2.ros.org) | What are the four main components of Nav2? What is the difference between the global planner and local planner? |
| ROS.14 | MoveIt2: robot arm motion planning | [MoveIt2 -- official tutorials](https://moveit.picknik.ai) | What does a motion planner like RRT do that inverse kinematics alone cannot? What is a planning scene? |

> **Mini Assignment ROS.4 -- Full robot pipeline in ROS2:** (1) Spawn a differential drive robot in Gazebo. (2) Add a lidar sensor. (3) Use Nav2 to navigate from point A to point B autonomously using lidar data. (4) Publish a goal pose via the command line. (5) Record the entire run as a rosbag. This integrates ROS2, simulation, sensors, and autonomous navigation in one pipeline.
