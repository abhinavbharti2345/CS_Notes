---
topic: Data Preprocessing & Feature Engineering
type: moc
tags:
  - ml
  - preprocessing
  - feature-engineering
date: 2026-09-21
---

# 🧹 Data Preprocessing & Feature Engineering

> [!abstract] Module Overview
> Raw real-world data is noisy, incomplete, categorical, and measured across disparate scales. This module covers the core transformation techniques used to convert raw features into optimal mathematical representations for machine learning algorithms without data leakage.

---

## 📖 Module Topics

1. **[[Data Leakage]]**
   - Definition: Unintended information transfer from outside the training partition
   - False confidence in development vs catastrophic real-world failure
   - Preprocessing leakage & why fitting before splitting fails
   - The Golden Workflow: `Split` $\to$ `fit() on train` $\to$ `transform() on train & test`

2. **[[Categorical Encoding]]**
   - Nominal vs. Ordinal categorical variables
   - Ordinal Encoding: Preserving natural monotonic rankings ($0 < 1 < 2$)
   - The False Ordering Hazard of integer encoding nominal features
   - One-Hot Encoding (OHE): Orthogonal indicator columns and equidistant vectors

3. **[[Missing Value Imputation]]**
   - Handling incomplete data matrices (`NaN` / null values)
   - Numerical strategies: Mean, Median (outlier-robust), and Constant imputation
   - Preventing Imputation Leakage across train/test splits
   - Implementation via Scikit-Learn `SimpleImputer`

4. **[[Feature Scaling|Feature Scaling & StandardScaler]]**
   - The scale disparity problem (e.g., hours vs income)
   - Why scale matters: Loss surface geometry & Gradient Descent optimization
   - **StandardScaler**: Formula ($z = \frac{x - \mu}{\sigma}$), zero-centering, and unit variance
   - The `fit()` vs `transform()` paradigm in scaling

---

## 🔄 Module Workflow Graph

```mermaid
flowchart TD
    Raw["📄 Raw Tabular Dataset"] --> Split["✂️ Train / Test Split"]
    
    Split --> Train["📦 X_train, y_train"]
    Split --> Test["🔒 X_test, y_test"]
    
    Train --> Impute["🩹 Missing Value Imputation<br/><i>Fit on X_train, transform X_train</i>"]
    Impute --> CatEnc["🏷️ Categorical Encoding (OHE/Ordinal)<br/><i>Fit on X_train, transform X_train</i>"]
    CatEnc --> Scale["📐 Feature Scaling (StandardScaler)<br/><i>Fit on X_train, transform X_train</i>"]
    
    Scale --> Model["🤖 Train ML Model (fit)"]
    
    Test -.-> TestTrans["Transform X_test using Train Imputer, Encoder & Scaler"]
    TestTrans --> Eval["📊 Evaluate Model on Clean X_test"]
    Model --> Eval

    classDef step fill:#1e293b,stroke:#3b82f6,stroke-width:1.5px,color:#fff;
    classDef train fill:#1e293b,stroke:#10b981,stroke-width:1.5px,color:#fff;
    classDef test fill:#1e293b,stroke:#f59e0b,stroke-width:1.5px,color:#fff;
    classDef model fill:#1e293b,stroke:#8b5cf6,stroke-width:2px,color:#fff;
    class Raw,Split step;
    class Train,Impute,CatEnc,Scale train;
    class Test,TestTrans,Eval test;
    class Model model;
```

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[AI & ML/Classical ML/README|Classical ML Foundations MOC]]
- [[AI & ML/Classical ML/Introduction to Machine Learning|Introduction to Machine Learning]]
- [[AI & ML/Classical ML/Supervised vs Unsupervised Learning|Supervised vs Unsupervised Learning]]

### Next Steps
- [[AI & ML/Data Preprocessing/Data Leakage|Data Leakage]]
- [[AI & ML/Data Preprocessing/Categorical Encoding|Categorical Encoding]]
- [[AI & ML/Data Preprocessing/Missing Value Imputation|Missing Value Imputation]]
- [[AI & ML/Data Preprocessing/Feature Scaling|Feature Scaling]]

---

## 🔗 Related Notes
- [[AI & ML/README|🤖 AI & ML Master MOC]]
- [[AI & ML/Classical ML/README|📁 Classical ML Foundations MOC]]
- [[Dashboard|🧭 Main Command Center]]

