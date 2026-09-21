---
topic: AI & ML
type: concept
tags:
  - machine-learning
  - data-preprocessing
  - categorical-encoding
  - one-hot-encoding
  - ordinal-encoding
  - feature-engineering
date: 2026-09-21
---

# 🏷️ Categorical Encoding: Nominal vs. Ordinal

> [!abstract] Executive Summary
> Machine learning models are mathematical optimization functions that operate on numerical tensors ($\mathbb{R}^n$). **Categorical Encoding** is the data preprocessing process of transforming non-numerical attributes (categories, labels, strings) into structured numerical vectors without introducing false mathematical assumptions or distorting underlying relationships.

---

## 🧩 1. What is a Categorical Variable?

A **variable (feature)** represents an observed characteristic of a data sample. Features broadly fall into two fundamental classes:

| Feature Type | Definition | Example Values | Representation in Raw Data |
| :--- | :--- | :--- | :--- |
| **Numerical Feature** | Quantitative measurements with intrinsic mathematical scale. | `Hours Studied: 5.5`, `Age: 21`, `Salary: $85,000` | Continuous floats or discrete integers |
| **Categorical Feature** | Qualitative labels representing groups, states, or classes. | `City: Delhi`, `Color: Red`, `Rating: High` | Strings, text labels, or discrete IDs |

```mermaid
flowchart TD
    subgraph RawData ["📥 Raw Input Sample"]
        direction TD
        F1["Hours Studied: 5 (Numerical)"]
        F2["City: Delhi (Categorical)"]
    end
    
    F1 --> Tensor["🔢 Mathematical Vector:<br/><code>[5.0, 1.0, 0.0, 0.0]</code> ──► ML Model"]
    F2 --> E["🏷️ Categorical Encoder"] --> Tensor

    classDef raw fill:#0ea5e918,stroke:#0ea5e9,stroke-width:1.8px;
    classDef enc fill:#f59e0b18,stroke:#f59e0b,stroke-width:1.8px;
    classDef vec fill:#10b98118,stroke:#10b981,stroke-width:1.8px;
    class F1,F2 raw;
    class E enc;
    class Tensor vec;
```

---

## ⚖️ 2. The Two Types of Categorical Data: Nominal vs. Ordinal

Before selecting an encoding strategy, the feature's semantic structure must be analyzed:

```mermaid
flowchart TD
    Cat["🏷️ Categorical Variable"]
    
    Cat --> Ord["1️⃣ ORDINAL (Intrinsic Order Exists)<br/>• Satisfaction: Low < Medium < High<br/>• Size: S < M < L < XL<br/>• Education: High School < Bachelor's < Master's < PhD"]
    
    Cat --> Nom["2️⃣ NOMINAL (No Natural Order)<br/>• City: Delhi, Mumbai, Bangalore<br/>• Color: Red, Green, Blue<br/>• Animal: Cat, Dog, Bird"]

    classDef root fill:#8b5cf618,stroke:#8b5cf6,stroke-width:2px;
    classDef ord fill:#10b98118,stroke:#10b981,stroke-width:1.8px;
    classDef nom fill:#0ea5e918,stroke:#0ea5e9,stroke-width:1.8px;
    class Cat root;
    class Ord ord;
    class Nom nom;
```

---

## 📈 3. Ordinal Encoding (Preserving Inherent Rank)

When categorical levels possess a clear, unambiguous ranking, **Ordinal Encoding** maps each category to an integer that preserves this monotonic order:

$$\text{Low} \to 0, \quad \text{Medium} \to 1, \quad \text{High} \to 2$$

Because $0 < 1 < 2$, the mathematical model accurately learns that $\text{Low} < \text{Medium} < \text{High}$.

```python
from sklearn.preprocessing import OrdinalEncoder

# Explicitly declare category order
categories_order = [["Low", "Medium", "High"]]
encoder = OrdinalEncoder(categories=categories_order)

X_train_encoded = encoder.fit_transform(X_train[["satisfaction_level"]])
```

> [!important] Explicit Ordering Rule
> Always specify the explicit category ordering when configuring an ordinal encoder. If left to default alphabetical ordering, `"High"` might be assigned `0`, `"Low"` `1`, and `"Medium"` `2`, destroying the true semantic relationship.

---

## 🚨 4. The Nominal Integer Encoding Trap (False Ordering)

What happens if we arbitrarily assign integers to **Nominal** (unordered) features?

$$\text{Delhi} \to 0, \quad \text{Mumbai} \to 1, \quad \text{Bangalore} \to 2$$

```mermaid
flowchart TD
    subgraph Trap ["❌ Artificial Mathematical Distortion"]
        direction TD
        N0["Delhi (0)"] --> N1["Mumbai (1)"] --> N2["Bangalore (2)"]
    end
    
    Trap --> E1["1. Implies False Ranking: Bangalore > Mumbai > Delhi"]
    Trap --> E2["2. Implies Distance Distortion: Dist(Delhi, Bangalore) = 2x Dist(Delhi, Mumbai)"]
    Trap --> E3["3. Linear/Distance Models get corrupted gradients"]

    classDef bad fill:#f43f5e18,stroke:#f43f5e,stroke-width:1.8px;
    classDef desc fill:#f59e0b18,stroke:#f59e0b,stroke-width:1.8px;
    class N0,N1,N2,Trap bad;
    class E1,E2,E3 desc;
```

> [!danger] Critical Modeling Hazard
> In linear models ($y = w_1 x_1 + b$) and distance-based algorithms (KNN, K-Means, SVMs), assigning nominal categories arbitrary integers forces the optimizer to treat the category as a linear continuum, corrupting loss gradients and predictive logic.

---

## 🔲 5. One-Hot Encoding (OHE)

To encode **Nominal** features without creating artificial ranking, **One-Hot Encoding** creates a separate binary ($0$ or $1$) indicator column for every unique category:

```mermaid
flowchart TD
    subgraph Before ["Original Categorical Feature"]
        C["City: [Delhi, Mumbai, Bangalore, Delhi]"]
    end

    subgraph After ["One-Hot Encoded Binary Matrix"]
        M["| City_Delhi | City_Mumbai | City_Bangalore |<br/>| :---: | :---: | :---: |<br/>| 1 | 0 | 0 |<br/>| 0 | 1 | 0 |<br/>| 0 | 0 | 1 |<br/>| 1 | 0 | 0 |"]
    end

    Before -->|OneHotEncoder| After

    classDef before fill:#0ea5e918,stroke:#0ea5e9,stroke-width:1.8px;
    classDef after fill:#10b98118,stroke:#10b981,stroke-width:1.8px;
    class Before,C before;
    class After,M after;
```

### Properties of One-Hot Encoding:
- **Equidistant Representation:** In Euclidean space, the distance between any two one-hot vectors is identically $\sqrt{2}$, ensuring no two cities are artificially "closer" than others:
  $$d(\text{Delhi}, \text{Mumbai}) = \sqrt{(1-0)^2 + (0-1)^2 + (0-0)^2} = \sqrt{2}$$
- **Dimensionality Consideration:** If a categorical feature has $K$ distinct categories, One-Hot Encoding adds $K$ new columns. For high-cardinality features (e.g., `Postal Code` with 5,000 values), target encoding or frequency encoding is preferred.

```python
from sklearn.preprocessing import OneHotEncoder

ohe = OneHotEncoder(sparse_output=False, handle_unknown="ignore")
X_train_ohe = ohe.fit_transform(X_train[["City"]])
```

> [!tip] `handle_unknown='ignore'`
> Setting `handle_unknown='ignore'` in Scikit-Learn ensures that if a new, unseen category appears in the test set or production inference, the encoder gracefully assigns all $0$s across the one-hot columns instead of throwing a runtime error.

---

## 🧠 6. Encoding Decision Matrix

| Characteristic | 🟢 Ordinal Encoding | 🔲 One-Hot Encoding |
| :--- | :--- | :--- |
| **Category Structure** | Natural inherent ranking ($\text{Low} < \text{Med} < \text{High}$) | Unordered nominal groups ($\text{Red}, \text{Blue}, \text{Green}$) |
| **New Columns Added** | **0** (Replaces column in-place with integers) | **$K$ columns** (where $K$ = number of unique categories) |
| **Mathematical Assumption** | $0 < 1 < 2 < \dots < K$ | Orthogonal, equidistant unit vectors |
| **Primary Danger** | False ranking if applied to nominal data | High memory / Dimensionality curse if $K$ is very large |

---

## 🔗 Related Notes & Next Concepts

- **Parent MOC:** [[AI & ML/Data Preprocessing/README|🧹 Data Preprocessing & Feature Engineering MOC]]
- **Prerequisites:**
  - [[AI & ML/Classical ML/Introduction to Machine Learning|🧠 Introduction to Machine Learning]]
  - [[AI & ML/Data Preprocessing/Data Leakage|🛡️ Data Leakage & Safe Transformation]]
- **Next Logical Topics:**
  - [[AI & ML/Data Preprocessing/Feature Scaling|📐 Feature Scaling & Loss Surface Geometry]]
  - `[[AI & ML/Data Preprocessing/Scikit-Learn Pipelines]]` — Combining Imputation, One-Hot Encoding, and Scaling safely into `ColumnTransformer`.
