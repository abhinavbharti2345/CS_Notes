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
   - The fundamental paradigm shift (Programming vs ML)
   - What is a "Model"? (Mathematical approximation of patterns)
   - Real-world intuition: Hours studied $\rightarrow$ Exam marks

2. **[[Supervised vs Unsupervised Learning]]**
   - **Supervised Learning**: Labeled data
     - *Regression*: Predicting continuous numerical values (e.g., house prices, marks)
     - *Classification*: Predicting discrete categories (e.g., spam vs not spam, cat vs dog)
   - **Unsupervised Learning**: Unlabeled data (Finding intrinsic structure, Customer segmentation, Clustering, PCA)

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
