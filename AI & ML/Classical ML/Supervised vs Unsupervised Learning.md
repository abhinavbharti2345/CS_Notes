---
topic: Classical Machine Learning
type: concept
tags:
  - ml
  - supervised
  - unsupervised
  - classification
  - regression
date: 2026-09-05
---

# Supervised vs Unsupervised Learning

Classical Machine Learning is fundamentally divided into two major learning paradigms based on whether the training dataset contains **correct answers (labels)**.

```text
                           Machine Learning
                                   │
                ┌──────────────────┴──────────────────┐
                ▼                                     ▼
      Supervised Learning                    Unsupervised Learning
     (Answers/Labels Given)                 (No Answers/Labels Given)
        │              │                               │
        ▼              ▼                               ▼
   Regression    Classification                    Clustering / PCA
 (Continuous)     (Categorical)                  (Find Hidden Patterns)
```

---

## 1. Supervised Learning (Labels Provided)

In **Supervised Learning**, the training dataset contains both the **inputs ($X$)** and the corresponding **correct ground-truth answers ($y$)**.

The model analyzes these pairs and learns how to map new inputs to correct outputs.

```text
Input Features (X) + Correct Answers (y) ──> [ Supervised Model ] ──> Learned Function
```

Supervised learning problems fall into two categories:

### A. Regression (Predicting a Continuous Number)
The target output is a continuous numerical value (a quantity, price, score, or measurement).

| Input Features ($X$) | Target Output ($y$) | Problem Type |
| :--- | :--- | :--- |
| House square footage, bedrooms, location | ₹ Price (e.g., `45,00,000`) | House Price Prediction |
| Hours studied, attendance percentage | Exam score (e.g., `82.5`) | Grade Prediction |
| Age, experience, education level | Annual salary (e.g., `₹ 75,000 / mo`) | Salary Estimation |

```text
Features ──> [ Regression Model ] ──> Continuous Numeric Value (e.g., 45,00,000)
```

---

### B. Classification (Predicting a Discrete Category)
The target output is a specific label, group, or class from a predefined set of categories.

| Input Features ($X$) | Target Output ($y$) | Problem Type |
| :--- | :--- | :--- |
| Email sender, subject, body keywords | `"Spam"` vs. `"Not Spam"` | Binary Classification |
| Image pixel values | `"Cat"` vs. `"Dog"` vs. `"Bird"` | Multi-class Classification |
| Bank transaction amount, location, time | `"Fraud"` vs. `"Normal"` | Fraud Detection |

```text
Features ──> [ Classification Model ] ──> Category Label (e.g., "Spam")
```

---

## 2. Unsupervised Learning (No Labels Provided)

In **Unsupervised Learning**, the training dataset contains only inputs ($X$) **without any target labels ($y$)**.

The model must autonomously inspect the data to uncover hidden patterns, similarities, clusters, and intrinsic structures.

```text
Input Features (X) with NO Answers ──> [ Unsupervised Algorithm ] ──> Discovered Patterns & Clusters
```

### Example: Customer Segmentation
Suppose an e-commerce platform has data on 10,000 customers (Age, Income, Total Purchases), but no column labeled `Customer Type`:

```text
Customer A: Age 21, Income ₹25,000, Purchases: 1
Customer B: Age 45, Income ₹1,50,000, Purchases: 15
Customer C: Age 23, Income ₹20,000, Purchases: 2
```

An unsupervised clustering algorithm (like K-Means) groups customers based on mathematical distance:

```text
All Customer Data
        ↓
[ Clustering Algorithm ]
        ↓
 ├── Group 1 ──> Young customers with lower spending
 ├── Group 2 ──> Young professionals with high spending
 └── Group 3 ──> Older customers with high savings & steady spending
```

### Common Unsupervised Techniques:
- **Clustering**: Grouping similar data points together (e.g., K-Means, DBSCAN).
- **Dimensionality Reduction**: Compressing high-dimensional feature spaces while preserving essential variation (e.g., Principal Component Analysis - PCA).

---

## ⚖️ Summary Comparison

| Dimension | Supervised Learning | Unsupervised Learning |
| :--- | :--- | :--- |
| **Ground Truth ($y$)** | ✅ Provided with training data | ❌ Not provided |
| **Primary Goal** | Predict the target $y$ for new inputs $X$ | Discover hidden clusters and structure |
| **Core Types** | **Regression** (numeric) & **Classification** (labels) | **Clustering** & **Dimensionality Reduction** |
| **Evaluation** | Compare predicted $\hat{y}$ vs actual $y$ | Evaluate cluster cohesion and separation |

> [!tip] Quick Memory Rule
> - **Supervised** = *Answers given* (Learning with a teacher).
> - **Unsupervised** = *Answers not given* (Self-discovery of patterns).

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[Introduction to Machine Learning]]

### Next Step
- [[Features, Targets, and Datasets]] — Learn how data is structured as matrices and vectors in ML.

## 🔗 Related Notes
- [[Classical ML/README|📁 Classical ML Foundations MOC]]
- [[Introduction to Machine Learning]]
- [[Features, Targets, and Datasets]]
- [[Train-Test Split and Generalization]]
- [[End-to-End ML Pipeline]]
