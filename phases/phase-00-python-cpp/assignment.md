# Phase 00 — Assignment: Robot Joint Simulator

> Build a Python script that simulates a single robot joint moving toward a target angle, then port the core logic to C++. This directly connects your Mechanical Engineering background to code.

---

## Part 1 — Python

### Task

Write a Python script `joint_sim.py` that simulates a robot joint moving toward a target angle.

### Requirements

1. Create variables: `current_angle = 90`, `target_angle = 0`, `step_size = 5`
2. Use a `while` loop to move `current_angle` toward `target_angle` one step at a time
3. Print the angle at each step
4. Wrap the logic in a function: `move_joint(current, target, step) -> float`
5. Plot angle vs iteration number using Matplotlib (x-axis: step number, y-axis: angle)

### Extension (do this after the basics work)

Replace the fixed `step_size` with a **proportional controller**:

```python
step = kp * (target - current)
```

Try `kp = 0.1`, `kp = 0.5`, and `kp = 1.0`. How does the convergence behavior change? This is the foundation of PID control — something you already know from ME.

### Expected output

```
Step 0: angle = 90
Step 1: angle = 85
Step 2: angle = 80
...
Step 18: angle = 0
```

---

## Part 2 — C++

### Task

Implement the same `move_joint` function in C++.

### Requirements

1. Create `joint_sim.cpp`
2. Implement `float move_joint(float current, float target, float step)`
3. Use a `while` loop in `main()` to drive the joint to target
4. Print the angle at each step
5. Compile with: `g++ -o joint_sim joint_sim.cpp`
6. Run with: `./joint_sim` (Linux/Mac) or `joint_sim.exe` (Windows)

### Starter structure

```cpp
#include <iostream>
#include <cmath>

float move_joint(float current, float target, float step) {
    // your code here
}

int main() {
    float current = 90.0f;
    float target = 0.0f;
    float step = 5.0f;
    
    // your loop here
    
    return 0;
}
```

---

## Checklist

- [ ] Python: function `move_joint()` works correctly
- [ ] Python: while loop converges to target
- [ ] Python: Matplotlib plot shows convergence
- [ ] Python extension: proportional controller implemented
- [ ] C++: compiles without errors
- [ ] C++: produces same output as Python version

---

## What to commit

When done, add your files to the repo:

```bash
git add joint_sim.py joint_sim.cpp
git commit -m "Phase 00 assignment: robot joint simulator"
git push
```
