# Phase 00 -- Python and C++

> **Time estimate:** 4-6 weeks  
> **Goal:** Get fluent in Python for ML. Every concept has a quiz question right beside it. Every 3-4 concepts has a mini assignment. Do not skip these -- they are the whole point.

---

## How to read this phase

Each row has 4 columns:
- **#** -- concept number
- **Concept** -- what you are learning
- **Video** -- the free resource
- **Quick quiz** -- answer this before moving to the next concept. If you cannot answer it, rewatch.

Every few concepts there is a **Mini Assignment** -- a small coding task that takes 20-60 minutes.

---

## Section 1 -- Python basics

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.1 | Variables, data types, print, input | [Corey Schafer -- Python Basics](https://www.youtube.com/watch?v=YYXdXT2l-Gg) | What is the difference between `int`, `float`, and `str`? What does `type(3.0)` return? |
| 0.2 | Lists, tuples, dictionaries, sets | [Corey Schafer -- Lists](https://www.youtube.com/watch?v=W8KRzm-HUcc) | When would you use a tuple instead of a list? What makes a dictionary different from a list? |
| 0.3 | If/else, for loops, while loops | [Corey Schafer -- Conditionals](https://www.youtube.com/watch?v=DZwmZ8Usvnk) | Write a for loop that prints every even number from 0 to 20. |
| 0.4 | Functions: def, return, arguments, default values | [Corey Schafer -- Functions](https://www.youtube.com/watch?v=9Os0o3wzS_I) | What is the difference between a parameter and an argument? What does `return` do vs `print`? |

> **Mini Assignment 1:** Write a function `describe_list(lst)` that takes a list of numbers and prints: the length, the sum, the min, the max, and whether it contains any duplicates. Test it on `[3, 1, 4, 1, 5, 9, 2, 6]`.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.5 | String methods, f-strings, formatting | [Corey Schafer -- Strings](https://www.youtube.com/watch?v=k9TUPpGqYTo) | What does `"hello".upper()` return? How do you embed a variable `x=42` inside a string using f-strings? |
| 0.6 | File I/O: reading and writing files | [Corey Schafer -- File objects](https://www.youtube.com/watch?v=Uh2ebFW8OYM) | What does `open('file.txt', 'r')` do? What is the difference between `read()` and `readlines()`? |
| 0.7 | List comprehensions, lambda, map, filter | [Corey Schafer -- Comprehensions](https://www.youtube.com/watch?v=3dt4OGnU5sM) | Rewrite `[x*2 for x in range(10) if x%2==0]` using a regular for loop. What does it produce? |
| 0.8 | Classes and OOP: `__init__`, methods, inheritance | [Corey Schafer -- OOP](https://www.youtube.com/watch?v=ZDa-Z5JzLYM) | What is `self`? What does `__init__` do? Write a class `Dog` with a `name` attribute and a `bark()` method. |

> **Mini Assignment 2:** Build a `Matrix` class with: `__init__(rows, cols)`, a `fill(value)` method, a `get(i,j)` method, a `set(i,j,value)` method, and a `__str__` method that prints it nicely. Test it with a 3x3 matrix filled with zeros, then set `[1][1] = 99`.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.9 | Iterators, generators, yield | [Corey Schafer -- Generators](https://www.youtube.com/watch?v=bD05uGo_sVI) | What is the difference between a list and a generator? Why would you use `yield` instead of `return`? |
| 0.10 | Decorators and functools | [Corey Schafer -- Decorators](https://www.youtube.com/watch?v=FsAPt_9Bf3U) | What does a decorator do? Write a decorator that prints "calling function" before any function runs. |
| 0.11 | Regular expressions (regex) | [Corey Schafer -- Regex](https://www.youtube.com/watch?v=K8L6KVGG-7o) | What does `re.findall(r'\d+', 'age: 25, score: 98')` return? What does `\d+` mean? |

> **Mini Assignment 3:** Write a function that takes a string of messy data like `"name: Rohan, age: 25, gpa: 3.4"` and uses regex to extract all numbers. Then write a second function that checks if a string is a valid email address using regex.

---

## Section 2 -- Python for ML (the tools you use every day)

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.12 | Virtual environments, pip, conda, requirements.txt | [Corey Schafer -- Virtual Environments](https://www.youtube.com/watch?v=Kg1Yvry_Ydk) | Why use a virtual environment? What does `pip freeze > requirements.txt` do? |
| 0.13 | argparse: CLI arguments for ML scripts | [Python argparse tutorial](https://docs.python.org/3/howto/argparse.html) | Why would you use `argparse` instead of hardcoding values? Write a script that accepts `--lr` and `--epochs` as arguments. |
| 0.14 | Logging instead of print | [Corey Schafer -- Logging](https://www.youtube.com/watch?v=-ARI4Cz-awo) | What is the difference between `logging.info()` and `logging.debug()`? Why is logging better than print for ML training? |
| 0.15 | Git and version control | [Corey Schafer -- Git tutorial](https://www.youtube.com/playlist?list=PL-osiE80TeTuRUfjRe54Eea17-YfnOOAx) | What does `git add`, `git commit`, and `git push` each do? What is a branch? |

> **Mini Assignment 4:** Create a small Python project: `train.py` that accepts `--epochs`, `--lr`, and `--output` via argparse. It should log training progress using the `logging` module (not print). Initialize it as a git repo, make 3 commits as you add features, and write a `requirements.txt`.

---

## Section 3 -- NumPy

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.16 | Arrays: creation, shape, dtype | [freeCodeCamp -- NumPy full course](https://www.youtube.com/watch?v=QUT1VHiLmmI) | What is the difference between `np.zeros((3,4))` and `np.zeros(3,4)`? What does `.shape` return for a 3x4 matrix? |
| 0.17 | Indexing, slicing, boolean masks | [freeCodeCamp -- NumPy full course](https://www.youtube.com/watch?v=QUT1VHiLmmI) | Given `a = np.array([1,2,3,4,5])`, what does `a[a > 3]` return? What about `a[1:4]`? |
| 0.18 | Vectorized operations: no for loops | [freeCodeCamp -- NumPy full course](https://www.youtube.com/watch?v=QUT1VHiLmmI) | Why is `a * 2` faster than `[x*2 for x in a]`? What is broadcasting? |
| 0.19 | Matrix operations: dot, matmul, transpose, inverse | [freeCodeCamp -- NumPy full course](https://www.youtube.com/watch?v=QUT1VHiLmmI) | What is the difference between `np.dot(A,B)` and `A*B` for matrices? When does `np.linalg.inv(A)` fail? |

> **Mini Assignment 5:** Using only NumPy (no sklearn): (1) Generate a random 100x5 dataset. (2) Compute the mean and std of each column. (3) Standardize it (zero mean, unit variance). (4) Compute the covariance matrix. (5) Implement matrix multiplication from scratch using `np.dot` and verify it matches `@`. Do the numpy-100 problems 1-25: https://github.com/rougier/numpy-100

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.20 | np.random: seeds, distributions, sampling | [freeCodeCamp -- NumPy full course](https://www.youtube.com/watch?v=QUT1VHiLmmI) | Why do you set a random seed? What is the difference between `np.random.rand()` and `np.random.randn()`? |
| 0.21 | Reshaping, stacking, splitting arrays | [freeCodeCamp -- NumPy full course](https://www.youtube.com/watch?v=QUT1VHiLmmI) | What does `np.reshape(a, (4,3))` require about the total number of elements? What does `np.hstack` vs `np.vstack` do? |

---

## Section 4 -- Pandas

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.22 | DataFrame creation, loading CSV, basic inspection | [Keith Galli -- Pandas](https://www.youtube.com/watch?v=vmEHCJofslg) | What does `df.head()`, `df.info()`, and `df.describe()` each show you? |
| 0.23 | Selecting columns and rows: `[]`, `.loc`, `.iloc` | [Keith Galli -- Pandas](https://www.youtube.com/watch?v=vmEHCJofslg) | What is the difference between `.loc` and `.iloc`? How do you select rows where `age > 30`? |
| 0.24 | Filtering, sorting, groupby, aggregation | [Keith Galli -- Pandas](https://www.youtube.com/watch?v=vmEHCJofslg) | What does `df.groupby('city')['salary'].mean()` compute? What does `df.sort_values('age', ascending=False)` do? |
| 0.25 | Handling missing values: `isna`, `fillna`, `dropna` | [Keith Galli -- Pandas](https://www.youtube.com/watch?v=vmEHCJofslg) | What is the difference between `dropna()` and `fillna(0)`? When would each be appropriate? |

> **Mini Assignment 6:** Load the Titanic dataset from `sns.load_dataset('titanic')`. (1) How many passengers survived? (2) What was the survival rate by class? (3) What was the average age by sex? (4) Fill missing `age` values with the median age of that passenger's class. (5) Create a new column `family_size = sibsp + parch + 1`. Do the Pandas-100 puzzles 1-30: https://github.com/ajcr/100-pandas-puzzles

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.26 | Merging, joining, concatenating DataFrames | [Keith Galli -- Pandas](https://www.youtube.com/watch?v=vmEHCJofslg) | What is the difference between `pd.merge(df1, df2, on='id', how='inner')` and `how='left'`? |
| 0.27 | Apply, map, applymap for transformations | [Keith Galli -- Pandas](https://www.youtube.com/watch?v=vmEHCJofslg) | What does `df['age'].apply(lambda x: x*2)` do? When would you use `apply` vs vectorized operations? |

---

## Section 5 -- Matplotlib and Seaborn

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.28 | Line plots, scatter plots, histograms | [Corey Schafer -- Matplotlib](https://www.youtube.com/watch?v=3Xc3CA655Y4) | What does `plt.subplot(1,2,1)` do? How do you add a title, x-label, and y-label? |
| 0.29 | Heatmaps, boxplots, pairplots with Seaborn | [Corey Schafer -- Matplotlib](https://www.youtube.com/watch?v=3Xc3CA655Y4) | What does `sns.heatmap(df.corr(), annot=True)` show you? When is a boxplot better than a histogram? |
| 0.30 | Saving figures, subplots, styling | [Corey Schafer -- Matplotlib](https://www.youtube.com/watch?v=3Xc3CA655Y4) | What does `plt.savefig('plot.png', dpi=150, bbox_inches='tight')` do? What does `fig, ax = plt.subplots()` give you? |

> **Mini Assignment 7:** Using the Titanic dataset: (1) Plot a histogram of ages. (2) Plot survival rate by class as a bar chart. (3) Plot a correlation heatmap of all numeric columns. (4) Plot a boxplot of age grouped by survival. Save all four as PNG files. Each plot must have a title, axis labels, and a legend where applicable.

---

## Section 6 -- Flask and Streamlit

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.31 | Flask basics: routes, request, response, serving a function as API | [CampusX -- Flask basics](https://www.youtube.com/watch?v=swHI1H7DVsQ) | What does `@app.route('/predict', methods=['POST'])` do? How does a client send data to this endpoint? |
| 0.32 | Streamlit: build an ML demo app in pure Python | [Streamlit -- official tutorial](https://docs.streamlit.io/get-started) | What does `st.slider('Learning rate', 0.0, 1.0, 0.01)` create? How do you display a pandas DataFrame in Streamlit? |

> **Mini Assignment 8 (capstone for Phase 00):** Train a simple scikit-learn model (logistic regression on Iris dataset). Build a Flask API endpoint that accepts JSON input features and returns a prediction. Then build a Streamlit app that lets a user input feature values with sliders and shows the prediction. Push everything to GitHub with a clean README explaining how to run it.

---

## Practice problem sets (required, not optional)

| Resource | Link | Do this many |
|---------|-----|-------------|
| NumPy 100 problems | https://github.com/rougier/numpy-100 | All 100 |
| 100 Pandas puzzles | https://github.com/ajcr/100-pandas-puzzles | All 100 |
| Kaggle Python microcourse | https://www.kaggle.com/learn/python | All exercises |
| Kaggle Pandas microcourse | https://www.kaggle.com/learn/pandas | All exercises |

---

## C++ basics (needed for ROS2 and real-time robot code)

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 0.33 | Variables, types, pointers, references | [freeCodeCamp -- C++ full course](https://www.youtube.com/watch?v=vLnPwxZdW4Y) | What is the difference between a pointer and a reference? What does `int* p = &x` do? |
| 0.34 | Classes, OOP, constructors, destructors | [freeCodeCamp -- C++ full course](https://www.youtube.com/watch?v=vLnPwxZdW4Y) | What is a destructor? Why does C++ need destructors but Python does not? |
| 0.35 | Templates and the STL (vector, map, queue) | [freeCodeCamp -- C++ full course](https://www.youtube.com/watch?v=vLnPwxZdW4Y) | What is `std::vector<int>`? How is it different from a C-style array? |
| 0.36 | Memory management: heap vs stack, new/delete | [freeCodeCamp -- C++ full course](https://www.youtube.com/watch?v=vLnPwxZdW4Y) | What is a memory leak? What causes it and how do you prevent it? |
| 0.37 | Real-time constraints: why C++ for robots | [Articulated Robotics -- ROS2 and C++](https://www.youtube.com/watch?v=8MlmMOzITHI) | Why can't Python be used for real-time robot control at 1kHz? What is a deterministic execution time? |

> **Mini Assignment 9:** Write a C++ class `RingBuffer` with a fixed-size circular buffer. It should have `push(value)`, `pop()`, `is_full()`, `is_empty()` methods. This pattern is used everywhere in robot sensor data pipelines. Compile with `g++ -o ring ring_buffer.cpp` and test it.
