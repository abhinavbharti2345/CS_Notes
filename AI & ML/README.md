---
topic: Artificial Intelligence & Machine Learning
type: moc
tags:
  - ai
  - ml
  - machine-learning
  - roadmap
date: 2026-09-05
---

# 🤖 Artificial Intelligence & Machine Learning Knowledge Base

> [!abstract] Master AI & ML Hub
> Welcome to the **AI & Machine Learning Knowledge Base**. This repository contains interconnected study notes covering the principles, mathematical patterns, algorithms, and practical workflows of modern Machine Learning — from foundational classical algorithms to deep learning.

---

## 🗺️ Machine Learning Learning Path

```mermaid
flowchart TD
    P1["📊 PART 1: Classical ML Foundations<br/><i>Paradigm shift, Supervised vs Unsupervised, Generalization</i>"]
    P2["🧹 PART 2: Data Preprocessing & Feature Engineering<br/><i>Leakage prevention, Categorical Encoding, Imputation, Scaling</i>"]
    P3["📈 PART 3: Supervised Learning — Regression<br/><i>Linear Regression, Cost Functions, Gradient Descent</i>"]
    P4["🎯 PART 4: Supervised Learning — Classification<br/><i>Logistic Regression, Decision Trees, SVM, KNN</i>"]
    P5["📐 PART 5: Model Evaluation & Validation<br/><i>Metrics, Confusion Matrix, Cross-Validation, Bias-Variance</i>"]
    P6["🔍 PART 6: Unsupervised Learning<br/><i>K-Means Clustering, PCA, Dimensionality Reduction</i>"]
    P7["🌲 PART 7: Ensemble Methods<br/><i>Random Forests, Gradient Boosting, XGBoost</i>"]
    P8["🧠 PART 8: Deep Learning & Neural Networks<br/><i>Perceptrons, Backpropagation, PyTorch</i>"]

    P1 --> P2 --> P3 --> P4 --> P5 --> P6 --> P7 --> P8

    classDef active fill:#10b98118,stroke:#10b981,stroke-width:2px;
    classDef planned fill:#0ea5e918,stroke:#0ea5e9,stroke-width:1.5px;
    class P1,P2 active;
    class P3,P4,P5,P6,P7,P8 planned;
```

---

## 📚 Core Modules

### 1. [[01. Classical ML/README|01. Classical ML Foundations]]
The fundamental paradigm, mental models, and vocabulary of machine learning:
- **01.** [[01. Introduction to Machine Learning]] — Traditional Programming vs ML paradigm & what is a "Model"
- **02.** [[02. Supervised vs Unsupervised Learning]] — Supervised (Regression vs Classification) & Unsupervised (Clustering, PCA)
- **03.** [[03. Features, Targets, and Datasets]] — Features ($X$), Targets ($y$), Samples, and matrix representation
- **04.** [[04. Train-Test Split and Generalization]] — Unseen data evaluation & introduction to Overfitting
- **05.** [[05. End-to-End ML Pipeline]] — The complete 10-step lifecycle from raw data to model iteration
- **06.** [[06. Linear Regression Assumptions]] — Residual analysis ($e = y - \hat{y}$), homoscedasticity vs heteroscedasticity, and log transformations

### 2. [[02. Data Preprocessing/README|02. Data Preprocessing & Feature Engineering]]
Preparing and transforming raw numerical & categorical features for optimal algorithmic performance:
- **01.** [[01. Data Leakage]] — Test contamination, development vs production performance, and the golden workflow protocol
- **02.** [[02. Categorical Encoding]] — Nominal vs. Ordinal features, Ordinal Encoding, the False Ordering Hazard, and One-Hot Encoding
- **03.** [[03. Missing Value Imputation]] — Handling missing values via mean, median (outlier-robust), and preventing imputation leakage
- **04.** [[04. Feature Scaling]] — Scale disparity, StandardScaler ($z = \frac{x-\mu}{\sigma}$), loss surface geometry, and the `fit()` vs `transform()` paradigm
- **05.** [[05. Scikit-Learn Pipeline]] — Leak-proof sequential workflows, `fit()` vs `predict()`, and `ColumnTransformer`

---

## 🔄 Knowledge Flow Graph

```mermaid
flowchart TD
    Intro["Introduction to Machine Learning"] --> Sup["Supervised vs Unsupervised Learning"]
    Sup --> Feat["Features, Targets, and Datasets"]
    Feat --> TTS["Train-Test Split and Generalization"]
    TTS --> Leak["Data Leakage Prevention Protocol"]
    
    Leak --> Cat["Categorical Encoding (OHE / Ordinal)"]
    Leak --> Imp["Missing Value Imputation"]
    Leak --> Scale["Feature Scaling (StandardScaler)"]
    
    Cat --> Pipe["End-to-End ML Pipeline"]
    Imp --> Pipe
    Scale --> Pipe

    classDef f fill:#0ea5e918,stroke:#0ea5e9,stroke-width:1.8px;
    classDef p fill:#10b98118,stroke:#10b981,stroke-width:2px;
    class Intro,Sup,Feat,TTS,Leak,Cat,Imp,Scale f;
    class Pipe p;
```

---

## 🔗 Quick Links
- [[Dashboard|🧭 Main Command Center]]
- [[01. Classical ML/README|📁 Classical ML Foundations MOC]]
- [[02. Data Preprocessing/README|🧹 Data Preprocessing MOC]]
- [[02. Categorical Encoding|🏷️ Categorical Encoding Note]]
- [[01. Data Leakage|🚨 Data Leakage Note]]
- [[03. Missing Value Imputation|🩹 Missing Value Imputation]]
- [[04. Feature Scaling|📏 Feature Scaling & StandardScaler]]
- [[01. Introduction to Machine Learning|🧠 Introduction to ML Note]]
- [[05. End-to-End ML Pipeline|⚙️ End-to-End ML Pipeline]]

