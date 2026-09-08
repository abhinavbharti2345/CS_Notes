---
topic: Classical Machine Learning
type: concept
tags:
  - ml
  - paradigm
  - model
date: 2026-09-05
---

# Introduction to Machine Learning

## 🔄 Traditional Programming vs. Machine Learning

To understand Machine Learning (ML), forget complex formulas for a moment and look at how problem-solving is fundamentally flipped.

### 1. Traditional Programming (Rule-Based)
In standard software development, a human programmer explicitly writes down **rules** (if/else logic, algorithms) and feeds them along with **data** into the computer to produce an **output**:

```text
  Rules (Code / Logic) ──┐
                         ├──> [ Computer Program ] ──> Output (Result)
  Data (Inputs)        ──┘
```

```python
# Traditional logic: The developer invents the rules
if marks >= 40:
    result = "Pass"
else:
    result = "Fail"
```

---

### 2. Machine Learning (Data-Driven Learning)
Machine Learning flips this paradigm. Instead of hand-coding rules, you feed the computer **historical Data** and the **Correct Answers (Labels)**. The machine algorithm analyzes the data and **learns the underlying mathematical rules (the Model)** automatically:

```text
  Data (Inputs)            ──┐
                             ├──> [ ML Algorithm ] ──> Rules (Learned Model)
  Correct Answers (Labels) ──┘
```

```text
Example: Study Hours vs. Exam Marks Data

  Hours Studied (Data)  ──>  Exam Marks (Answers)
           1            ──>         35
           2            ──>         42
           3            ──>         51
           4            ──>         61
           5            ──>         70

The ML algorithm learns the mathematical relationship:
             Hours Studied ──> [ Learned Model ] ──> Predicted Marks

Now, when given a new, unseen input:
             6 Hours ──> [ Learned Model ] ──> ~80 Marks
```

---

## 📐 What is a "Model"?

> [!important] Definition
> A **Model** is a **learned mathematical pattern (function)** that approximates the relationship between input features and output targets.

A model does **not** memorize exact pairs like `(6, 80)`. Instead, it extracts the general mathematical rule from the training data:

```text
Historical Data:
Hours (X)    Marks (y)
   1            35
   2            43
   3            52
   4            60
   5            71
```

From this data, the model might learn the linear equation:

$$\text{Marks} \approx 9 \times \text{Hours} + 26$$

When you test it with a brand new input ($\text{Hours} = 6$):

$$\text{Marks} \approx 9 \times 6 + 26 = 54 + 26 = 80$$

```text
Input: Hours = 6 ──> [ Model: y ≈ 9x + 26 ] ──> Output: Predicted Marks ≈ 80
```

---

## 🔑 Core Takeaways
1. Traditional programming requires humans to design the logic; Machine Learning extracts the logic from historical data.
2. A machine learning model is a function that maps inputs to outputs based on statistical patterns.
3. The true test of an ML model is not how well it remembers past examples, but how accurately it predicts on **new, unseen data**.

---

## 🔗 Prerequisites & Next Steps

### Next Step
- [[Supervised vs Unsupervised Learning]] — Understanding the two main branches of classical machine learning.

## 🔗 Related Notes
- [[Classical ML/README|📁 Classical ML Foundations MOC]]
- [[Supervised vs Unsupervised Learning]]
- [[Features, Targets, and Datasets]]
- [[Train-Test Split and Generalization]]
- [[End-to-End ML Pipeline]]
