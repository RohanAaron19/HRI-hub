# Phase 00 — Quiz Solutions

> Only open this after attempting all questions in [quiz.md](quiz.md).

---

## Q1 — Answer: B

`print()` writes its argument to standard output — your terminal or Jupyter cell. It is the most basic debugging tool in Python. Every experienced programmer uses `print()` constantly to inspect variables, robot states, and reward values during development.

---

## Q2 — Answer: B

Python uses **0-based indexing**. The first element is at index `0`, the second at index `1`, and so on. This is the opposite of MATLAB which uses 1-based indexing. A useful shortcut: `x[-1]` gives you the last element of any list or array.

---

## Q3 — Answer: B (2)

`x[1]` accesses the element at index 1. With 0-based indexing, index 1 is the **second** element, which is `2`. Index `0` would give `1`, index `2` would give `3`.

---

## Q4 — Answer: B

`np.zeros((3,3))` creates a 3×3 array filled with floating-point zeros. The argument is a **shape tuple**. This is equivalent to `zeros(3,3)` in MATLAB. It is one of the most frequently used NumPy calls in robotics and ML code.

---

## Q5 — Answer: B

`self` refers to the **specific object instance** on which the method is being called. It allows the method to access and modify that instance's own attributes. Without `self`, a method cannot distinguish between different instances of the same class. In HRI code, `Robot`, `Environment`, and `Policy` classes all use `self` extensively.

---

## Q6 — Answer: B

The key distinction:
- **Pointer** (`int* p`): can be `null`, can be reassigned to point to different objects, must be dereferenced with `*p`
- **Reference** (`int& r`): must be initialized at declaration, always refers to the same object, used like a regular variable

In robotics C++ code, references are used for safe guaranteed-valid handles to objects. Pointers are used for optional or dynamically allocated objects. This distinction matters a lot in ROS2 node code.
