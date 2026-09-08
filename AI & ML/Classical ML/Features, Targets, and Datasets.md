---
topic: Classical Machine Learning
type: concept
tags:
  - ml
  - features
  - targets
  - dataset
date: 2026-09-05
---

# Features, Targets, and Datasets

## 📖 Core Machine Learning Vocabulary

To read ML literature, build models in Scikit-Learn, or understand algorithms, you must be comfortable with the standard vocabulary used to describe datasets.

---

## 1. The Key Components of a Dataset

Consider this student exam dataset:

| Sample (Row) | Study Hours | Sleep Hours | Attendance (%) | Exam Marks |
| :---: | :---: | :---: | :---: | :---: |
| **Row 1** | 2 | 7 | 65% | **45** |
| **Row 2** | 4 | 6 | 80% | **60** |
| **Row 3** | 6 | 8 | 90% | **78** |
| **Row 4** | 8 | 7 | 95% | **90** |

```text
┌──────────────────────────────────────────────┐ ┌────────────┐
│              Feature Matrix (X)              │ │ Target (y) │
│  Study Hours  │  Sleep Hours  │  Attendance  │ │ Exam Marks │
├───────────────┼───────────────┼──────────────┤ ├────────────┤
│       2       │       7       │      65      │ │     45     │ <-- Sample 1
│       4       │       6       │      80      │ │     60     │ <-- Sample 2
│       6       │       8       │      90      │ │     78     │ <-- Sample 3
│       8       │       7       │      95      │ │     90     │ <-- Sample 4
└──────────────────────────────────────────────┘ └────────────┘
```

---

## 2. Definitions & Mathematical Notation

### A. Features ($X$)
- **What they are**: The input attributes, independent variables, or characteristics used by the model to make a prediction.
- **Convention**: Denoted by a capitalized **$X$** (because it is typically a 2D table/matrix with multiple columns).
- In the table above: $\text{Features} = \{\text{Study Hours}, \text{Sleep Hours}, \text{Attendance}\}$.

### B. Target / Label ($y$)
- **What it is**: The ground-truth answer, dependent variable, or output attribute that the model is trying to predict.
- **Convention**: Denoted by a lowercase **$y$** (because it is typically a 1D list/vector of values).
- In the table above: $\text{Target } (y) = \text{Exam Marks}$.

### C. Samples (Rows)
- **What they are**: Individual instances, observations, or data points in the dataset.
- In the table above, there are **4 samples** and **3 input features**.

---

## 3. The Core Machine Learning Equation

Every supervised machine learning workflow follows the mathematical transformation:

$$X \xrightarrow{\text{Model}} \hat{y}$$

Where:
- $X$ = Input feature values
- $\text{Model}$ = Learned mathematical function
- $\hat{y}$ (pronounced *"y-hat"*) = Model's predicted output

```text
Input Feature Vector: X = [6 hours, 8 sleep, 90% attendance]
                               │
                               ▼
                       [ Trained Model ]
                               │
                               ▼
            Predicted Output: ŷ ≈ 78 marks
```

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[Introduction to Machine Learning]]
- [[Supervised vs Unsupervised Learning]]

### Next Step
- [[Train-Test Split and Generalization]] — Why we must never train and evaluate a model on the exact same data.

## 🔗 Related Notes
- [[Classical ML/README|📁 Classical ML Foundations MOC]]
- [[Introduction to Machine Learning]]
- [[Supervised vs Unsupervised Learning]]
- [[Train-Test Split and Generalization]]
- [[End-to-End ML Pipeline]]
