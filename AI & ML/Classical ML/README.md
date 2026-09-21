---
topic: Classical Machine Learning
type: moc
tags:
  - ml
  - classical-ml
  - foundations
date: 2026-09-05
---

# 📊 Classical Machine Learning Foundations

> [!important] Core Objective
> Forget complex mathematical formulas for a moment. This module builds the **core intuition, paradigms, and vocabulary** behind Machine Learning from scratch before diving into specific algorithms.

---

## 📖 Learning Path

1. **[[Introduction to Machine Learning]]**
   - Core intuition: Examples $\rightarrow$ Discover Pattern $\rightarrow$ Predict $\hat{y}$
   - The 3 Pillars: Input $X$, Target $y$, and Model (Learned Pattern)
   - What is "Learning"? (Iterative parameter adjustment loop: predict $\rightarrow$ error $\rightarrow$ adjust $\rightarrow$ repeat)
   - Paradigm shift (Traditional rule-based code vs Data-driven ML)

2. **[[Supervised vs Unsupervised Learning]]**
   - **Supervised Learning** ($X + y$): Labeled examples (flashcard analogy)
     - *Regression*: Continuous numerical targets (e.g., house prices ₹75L, weather 31.5°C, salary ₹85k, marks)
     - *Classification*: Discrete categorical targets (e.g., pass/fail, spam/not spam, cat/dog, fraud, disease)
   - **Unsupervised Learning** ($X$ only): Unlabeled pattern discovery & grouping (e.g., clustering, PCA)
   - The Master Mental Map & Taxonomy

3. **[[Features, Targets, and Datasets]]**
   - Features ($X$) = Inputs used for prediction
   - Target ($y$) = Output being predicted
   - Samples & Rows in a Dataset
   - Mathematical mapping: $X \rightarrow \text{Model} \rightarrow y$

4. **[[Train-Test Split and Generalization]]**
   - Why we never evaluate models on training data
   - Training Data vs Test Data (e.g., 80/20 split)
   - The ultimate goal: Generalization to unseen data
   - What is **Overfitting**? (Memorization vs learning true patterns)

5. **[[End-to-End ML Pipeline]]**
   - The complete 10-stage machine learning workflow:
     `Raw Data` $\rightarrow$ `Understand` $\rightarrow$ `Clean` $\rightarrow$ `Split` $\rightarrow$ `Preprocess` $\rightarrow$ `Model` $\rightarrow$ `Train` $\rightarrow$ `Predict` $\rightarrow$ `Evaluate` $\rightarrow$ `Improve`

---

## 🔗 Connections

### Prerequisites
- Basic programming concepts (variables, conditions, loops, arrays) in [[Variables and Data Types|Python / JS]].

### Next Topics
- **Linear Regression**: Finding optimal weights and biases via Gradient Descent.
- **Logistic Regression & Classification**: Sigmoid function and decision boundaries.
- **Model Evaluation**: Precision, Recall, F1-Score, MSE, RMSE.

---

## 🔗 Related Notes
- [[AI & ML/README|🤖 AI & ML Master MOC]]
- [[Dashboard|🧭 Main Command Center]]
