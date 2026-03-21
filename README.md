# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** G. Bhagya Sri  
**Student ID    :** 2310040100  
**Date Submitted:** 20/3/2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
[ The count_clashes() function measures the number of scheduling conflicts where a student has more than one exam in the same time slot.

A value of 0 means a perfect timetable with no clashes.]
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
[ The generate_neighbor() function creates a new timetable by randomly selecting one exam and assigning it to a different time slot.

The new timetable differs from the current one by only a single change, making it a small variation used for exploration in the search process.]
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
[ This line decides whether to accept a new timetable. If the new solution is better (delta < 0), it is always accepted. If it is worse, it may still be accepted based on a probability.

Simulated Annealing accepts worse solutions to escape local minima and explore more possible solutions, especially at higher temperatures.]
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed | 1379|
| Clashes at iteration 1 |13 |
| Final best clashes | 3|
| Did SA reach 0 clashes? (Yes / No) |No |

**Copy the printed timetable output here:**
```
[ ================================================
  EXPERIMENT 1 - Baseline
================================================

  Final Timetable
------------------------------------------
  Slot 1:  Geography
  Slot 2:  Chemistry, English
  Slot 3:  History, Computer Science, Economics
  Slot 4:  Biology, Statistics
  Slot 5:  Mathematics, Physics
------------------------------------------
  Total clashes : 3

  Iterations     : 1379
  Start clashes  : 12
  Final clashes  : 3
  Saved -> plots/experiment_1.png ]
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
[ The number of clashes drops very quickly in the early iterations, showing a steep decline at the beginning. After that, the curve gradually flattens as the algorithm fine-tunes the solution.

This indicates that most improvements happen early, while later iterations focus on small refinements.]
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        | 8              |     8                 |      No              |
| 0.95        |      3         |        3              |   No                 |
| 0.995       |      3         |             3         |        No            |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
[ The cooling rate has a significant impact on the performance of Simulated Annealing. With a fast cooling rate (0.80), the temperature drops quickly, causing the algorithm to stop exploring early and often resulting in suboptimal solutions.

With a moderate cooling rate (0.95), the algorithm performs better, sometimes reaching near-optimal or optimal solutions, but still lacks consistency.

With a slow cooling rate (0.995), the algorithm explores the search space more thoroughly and consistently finds the optimal solution with zero clashes. However, it requires more iterations and time.]
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
[ The cooling rate of 0.995 gave the best result because it allows the algorithm to explore more solutions before settling. The slow decrease in temperature helps avoid getting stuck in local minima and increases the chance of finding the optimal timetable. ]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 |3 |Slow cooling improves solution quality but may not always reach zero clashes  |
| 2 — Cooling rate | cooling_rate = 0.80 |8 |Fast cooling leads to poor solutions due to insufficient exploration |

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
[ From these experiments, I learned that Simulated Annealing is an optimization algorithm that balances exploration and exploitation using temperature. The cooling rate plays a crucial role in determining how well the algorithm searches for solutions.

If the cooling rate is too fast, the algorithm stops exploring early and produces poor results. If the cooling is slow, it explores more thoroughly and finds better solutions, although it takes more time.

Overall, choosing the right cooling schedule is important for achieving good performance in optimization problems.]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
