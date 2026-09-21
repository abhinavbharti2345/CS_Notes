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

1. **[[01. Data Leakage]]**
   - Master definition: Information reaching the model that wouldn't be available at prediction time
   - **The 3 Leakage Patterns:**
     - 1️⃣ *Preprocessing Leakage*: Computing statistics over full dataset before splitting ($\text{Test} \to \text{Train}$)
     - 2️⃣ *Target Leakage*: Using features only known after the target event ($\text{After} \to \text{Before}$)
     - 3️⃣ *Temporal Leakage*: Future data leaking into past predictions via random splits ($\text{Future} \to \text{Past}$)
   - Safe workflows: `train_test_split`, `TimeSeriesSplit`, and Scikit-Learn `Pipeline`

2. **[[02. Categorical Encoding]]**
   - Nominal vs. Ordinal categorical variables
   - Ordinal Encoding: Preserving natural monotonic rankings ($0 < 1 < 2$)
   - The False Ordering Hazard of integer encoding nominal features
   - One-Hot Encoding (OHE): Orthogonal indicator columns and equidistant vectors

3. **[[03. Missing Value Imputation]]**
   - Handling incomplete data matrices (`NaN` / null values)
   - **The 3 Mechanisms:** **MCAR** (Random), **MAR** (Observed data), and **MNAR** (Hidden value itself)
   - Numerical strategies: Mean vs. Median (outlier-robust) & Categorical strategies (Mode, `"Unknown"`)
   - The Missing Indicator feature (`was_missing` / `add_indicator=True`)
   - Statistical side-effects of Mean Imputation (variance shrinkage & correlation attenuation)
   - Preventing Imputation Leakage across train/test splits

4. **[[04. Feature Scaling|Feature Scaling & StandardScaler]]**
   - The scale disparity problem (e.g., hours vs income)
   - Why scale matters: Loss surface geometry & Gradient Descent optimization
   - **StandardScaler**: Formula ($z = \frac{x - \mu}{\sigma}$), zero-centering, and unit variance
   - The `fit()` vs `transform()` paradigm in scaling

5. **[[05. Scikit-Learn Pipeline|Scikit-Learn Pipeline & ColumnTransformer]]**
   - Chaining transformers and estimators into a single leak-proof object
   - Internal mechanics of `fit()` (training) vs `predict()` (inference)
   - Heterogeneous column pipelines via `ColumnTransformer`
   - Safe Cross-Validation without data leakage

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

    classDef step fill:#0ea5e918,stroke:#0ea5e9,stroke-width:1.8px;
    classDef train fill:#10b98118,stroke:#10b981,stroke-width:1.8px;
    classDef test fill:#f59e0b18,stroke:#f59e0b,stroke-width:1.8px;
    classDef model fill:#8b5cf618,stroke:#8b5cf6,stroke-width:2px;
    class Raw,Split step;
    class Train,Impute,CatEnc,Scale train;
    class Test,TestTrans,Eval test;
    class Model model;
```

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[AI & ML/01. Classical ML/README|Classical ML Foundations MOC]]
- [[AI & ML/01. Classical ML/01. Introduction to Machine Learning|Introduction to Machine Learning]]
- [[AI & ML/01. Classical ML/02. Supervised vs Unsupervised Learning|Supervised vs Unsupervised Learning]]

### Next Steps
- [[AI & ML/02. Data Preprocessing/01. Data Leakage|Data Leakage]]
- [[AI & ML/02. Data Preprocessing/02. Categorical Encoding|Categorical Encoding]]
- [[AI & ML/02. Data Preprocessing/03. Missing Value Imputation|Missing Value Imputation]]
- [[AI & ML/02. Data Preprocessing/04. Feature Scaling|Feature Scaling]]

---

## 🔗 Related Notes
- [[AI & ML/README|🤖 AI & ML Master MOC]]
- [[AI & ML/01. Classical ML/README|📁 Classical ML Foundations MOC]]
- [[Dashboard|🧭 Main Command Center]]

