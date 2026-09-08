---
topic: Classical Machine Learning
type: concept
tags:
  - ml
  - train-test-split
  - generalization
  - overfitting
date: 2026-09-05
---

# Train-Test Split and Generalization

## 🚫 Why We Cannot Train on 100% of Data

Suppose you have a dataset with 1,000 historical examples.

A common beginner mistake is to feed all 1,000 examples into the model during training, and then evaluate the model's accuracy on those exact same 1,000 examples.

> [!warning] The Classroom Exam Analogy
> Imagine a teacher who gives students the **exact 100 exam questions and answers** to study the night before, and then gives them the **exact same 100 questions** on the final exam.  
> 
> If the students score 100%, does that mean they understand the subject?  
> **No.** They simply memorized the answers. To test true understanding, the teacher must test them on **unseen questions**.

---

## ✂️ The Train-Test Split

To accurately measure whether an ML model has learned generalizable patterns or simply memorized the data, we split the dataset into two disjoint sets:

```text
                        Full Dataset (1,000 Examples)
                                      │
                   ┌──────────────────┴──────────────────┐
                   ▼                                     ▼
          Training Set (80%)                      Test Set (20%)
           (800 Examples)                         (200 Examples)
                   │                                     │
                   ▼                                     ▼
        Model Learns Patterns                  Model NEVER sees this
        From Inputs & Labels                   During Training
                   │                                     │
                   └──────────────────┬──────────────────┘
                                      │
                                      ▼
                        [ Evaluate Model Performance ]
                        Model Predicts on Test Inputs (X_test)
                                      │
                                      ▼
                     Compare Predicted ŷ vs. Actual y_test
```

### Standard Split Proportions:
- **Training Set (70% – 80%)**: Used by the algorithm to adjust weights and learn parameters.
- **Testing Set (20% – 30%)**: Held out strictly to evaluate the final model on unseen data.

---

## 🎯 Generalization: The Core Goal of Machine Learning

> [!important] Key Principle
> The primary objective of Machine Learning is **Generalization** — the ability of a trained model to make accurate predictions on new, previously unseen data.

```text
Target Goal:
High Training Accuracy  +  High Test Accuracy  ──>  ✅ Good Generalization
```

---

## 🚨 What is Overfitting?

**Overfitting** occurs when a model learns the training data *too well* — memorizing noise, outliers, and idiosyncratic details rather than the true underlying pattern.

### The Warning Sign of Overfitting:

```text
Training Score:  99%  (Looks amazing on training data)
Testing Score:   55%  (Performs terribly on unseen test data)
```

```text
Simple Rule: Marks ≈ 10 × Hours + 20
  │
  ├── Training: (1hr -> 30), (2hr -> 40), (3hr -> 50), (4hr -> 60)
  │   Model learns general line: y = 10x + 20
  │
  └── Test: 5 Hours -> Actual: 70 marks
      Model predicts: 70 marks  ==>  ✅ Excellent Generalization

Overfitted Model:
  Memorizes extreme squiggly curve passing through every training point.
  When given 5 Hours, it predicts 12 marks because it failed to generalize!
```

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[Introduction to Machine Learning]]
- [[Features, Targets, and Datasets]]

### Next Step
- [[End-to-End ML Pipeline]] — Follow the complete lifecycle from raw data to evaluation.

## 🔗 Related Notes
- [[Classical ML/README|📁 Classical ML Foundations MOC]]
- [[Introduction to Machine Learning]]
- [[Supervised vs Unsupervised Learning]]
- [[Features, Targets, and Datasets]]
- [[End-to-End ML Pipeline]]
