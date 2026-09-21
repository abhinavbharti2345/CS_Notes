# 🧭 Computer Science Knowledge Vault: Command Center

> [!quote]- Daily Engineering Focus
> *"The mind is not a vessel to be filled, but a fire to be kindled."* — Plutarch

---

## 🗺️ Vault Architecture & Domain Map

```mermaid
flowchart TD
    Vault["🧭 <b>CS Knowledge Graph</b>"]
    
    Vault --> AIML["🤖 <b>AI & ML</b><br/>Classical ML • Preprocessing • Math"]
    Vault --> NET["🌐 <b>Computer Networking</b><br/>OSI/TCP-IP • Routing • Subnetting • Performance"]
    Vault --> BACK["⚡ <b>WebDev & Backend</b><br/>Node.js • Express • MongoDB • Security"]
    Vault --> DSA["🌳 <b>DSA</b><br/>Strings • Linked Lists • Bit Manipulation • Two Pointers"]
    Vault --> CORE["☕ <b>Core Systems & Languages</b><br/>Java • Python • OS • DBMS"]

    classDef root fill:#8b5cf618,stroke:#8b5cf6,stroke-width:2.5px;
    classDef aiml fill:#0ea5e918,stroke:#0ea5e9,stroke-width:2px;
    classDef net fill:#10b98118,stroke:#10b981,stroke-width:2px;
    classDef back fill:#f59e0b18,stroke:#f59e0b,stroke-width:2px;
    classDef dsa fill:#ec489918,stroke:#ec4899,stroke-width:2px;
    classDef core fill:#6366f118,stroke:#6366f1,stroke-width:2px;
    
    class Vault root;
    class AIML aiml;
    class NET net;
    class BACK back;
    class DSA dsa;
    class CORE core;
```

---

## ⚡ Quick Actions & Reference Utilities

> [!abstract]+ ⚡ High-Yield Cheatsheets & Roadmaps
> - ⚡ **DSA Rapid Reference:** [[Quick Look|⚡ Quick Look (Java & DSA Cheatsheet)]]
> - 🌳 **DSA Master Roadmap:** [[DSA/README|🌳 DSA Master Hub]]
> - 🌐 **Networking Master Roadmap:** [[Computer Networking/README|🌐 Networking Master Hub]]
> - 🤖 **AI & ML Master Roadmap:** [[AI & ML/README|🤖 AI & ML Master Hub]]
> - ⚡ **Backend Master Roadmap:** [[WebDev/Backend/README|⚡ Backend Development Hub]]
> - 🎓 **Course Resources:** [[Extra_Courses]]

---

## 🧠 Core Domain Master MOCs (Study Order)

> [!tip]+ 🤖 Artificial Intelligence & Machine Learning
> - [[AI & ML/README|🤖 AI & Machine Learning Master Roadmap (MOC)]]
>   - **01. Classical Machine Learning Foundations**
>     - [[AI & ML/01. Classical ML/01. Introduction to Machine Learning|🧠 01. Introduction to Machine Learning]]
>     - [[AI & ML/01. Classical ML/02. Supervised vs Unsupervised Learning|⚖️ 02. Supervised vs Unsupervised Learning]]
>     - [[AI & ML/01. Classical ML/03. Features, Targets, and Datasets|📊 03. Features, Targets & Datasets]]
>     - [[AI & ML/01. Classical ML/04. Train-Test Split and Generalization|✂️ 04. Train-Test Split & Generalization]]
>     - [[AI & ML/01. Classical ML/05. End-to-End ML Pipeline|🔁 05. End-to-End ML Pipeline]]
>     - [[AI & ML/01. Classical ML/06. Linear Regression Assumptions|📐 06. Linear Regression Assumptions & Residuals]]
>     - [[AI & ML/01. Classical ML/07. Regression Evaluation Metrics|📊 07. Regression Evaluation Metrics (MSE, RMSE, MAE, R²)]]
>   - **02. Data Preprocessing & Feature Engineering**
>     - [[AI & ML/02. Data Preprocessing/01. Data Leakage|🛡️ 01. Data Leakage & Safe Transformation (3 Types)]]
>     - [[AI & ML/02. Data Preprocessing/02. Categorical Encoding|🏷️ 02. Categorical Encoding (Nominal vs Ordinal)]]
>     - [[AI & ML/02. Data Preprocessing/03. Missing Value Imputation|🩹 03. Missing Value Imputation (MCAR / MAR / MNAR)]]
>     - [[AI & ML/02. Data Preprocessing/04. Feature Scaling|📐 04. Feature Scaling & Loss Surface Geometry]]
>     - [[AI & ML/02. Data Preprocessing/05. Scikit-Learn Pipeline|🚂 05. Scikit-Learn Pipeline & ColumnTransformer]]

> [!info]+ 🌐 Computer Networking
> - [[Computer Networking/README|🌐 Computer Networks Master Roadmap (MOC)]]
>   - [[01. Introduction to Computer Networks|🌍 01. Introduction to Computer Networks]]
>   - [[02. Packets and Packet Switching|📦 02. Packets and Packet Switching]]
>   - [[03. Switching Techniques - Packet vs Circuit|🔄 03. Switching Techniques (Packet vs Circuit)]]
>   - [[04. Network Performance - Delay, Latency, Throughput|⏱️ 04. Delay, Latency & Nodal Delays]]
>   - [[05. Network Hardware - Hub, Switch, Router, Modem|🔌 05. Network Hardware (Hub, Switch, Router, Modem)]]
>   - [[06. OSI vs TCP-IP Model|🧱 06. Layered Models (OSI vs TCP/IP & PDUs)]]
>   - [[07. Network Protocols and Standards|📜 07. Network Protocols & Standards]]
>   - [[08. Encapsulation and Decapsulation|📦 08. Encapsulation & Decapsulation]]
>   - [[09. Data Units - Segment, Packet, Frame, Bits|📊 09. PDUs & TCP vs UDP]]
>   - [[10. Ethernet and MAC Addressing|🏷️ 10. Ethernet & MAC Addressing]]
>   - [[11. MTU and Fragmentation|✂️ 11. MTU & IP Fragmentation]]
>   - [[12. IP Addressing Fundamentals|🌐 12. IPv4 & Binary Fundamentals]]
>   - [[13. Network ID and Host ID|🎯 13. Network ID vs Host ID]]
>   - [[14. Subnet Masks and CIDR Notation|🎭 14. Subnet Masks & CIDR Notation]]

> [!note]+ 🌳 Data Structures & Algorithms (DSA)
> - [[DSA/README|🌳 DSA Master Roadmap (MOC)]]
>   - [[Quick Look|⚡ Quick Look & Cheatsheet (Frequently Forgotten Syntax)]]
>   - [[DSA/01. Strings/README|🔤 01. Strings & Character Arrays (Master Hub)]]
>     - [[DSA/01. Strings/StringBuilder|🏗️ 01. StringBuilder (Architecture & Growth Model)]]
>     - [[DSA/01. Strings/Add Binary & String Arithmetic|➕ 02. Add Binary & String Arithmetic]]
>     - [[DSA/DSA Problems/67. Add Binary|💡 03. LeetCode 67: Add Binary]]
>   - [[Binary Search|🔍 02. Binary Search & Halving Search Spaces]]
>   - [[DSA/03. Linked Lists/README|🔗 03. Linked Lists (Master Hub)]]
>     - [[01. Linked List Fundamentals|🧱 01. Linked List Fundamentals]]
>     - [[02. Linked List Patterns|🧠 02. Linked List Patterns (Tortoise & Hare, In-Place Reversal)]]
>   - [[Bit Manipulation|⚡ 04. Bit Manipulation (Master Hub)]]
>     - [[01. Bitwise Operators|🔢 01. Bitwise Operators & Truth Tables]]
>     - [[02. Bit Tricks|🪄 02. Bit Tricks & Low-Level Masking]]
>     - [[03. XOR Patterns|🔮 03. XOR Properties & Duplicate Cancellation]]
>     - [[04. Bit Manipulation Problems|💡 04. Bit Manipulation Problem Set]]

> [!important]+ ⚡ Web Development & Backend Engineering
> - [[WebDev/Backend/README|🌐 Backend Master Roadmap (MOC)]]
>   - [[WebDev/Backend/JavaScript/README|🟨 01. JavaScript Foundations & Async Engine]]
>   - [[WebDev/Backend/Node.js/README|🟢 02. Node.js Runtime & Event Loop]]
>   - [[ShopKart Auth Project|🛒 03. ShopKart Authentication & JWT Architecture]]

> [!example]+ ☕ Programming Languages & Core Systems
> - [[JAVA/README|☕ 01. Java Foundations & OOP Architecture (MOC)]]
> - [[Python|🐍 02. Python Language Hub & Scientific Computing]]
> - **03. Operating Systems (OS) & DBMS Foundations** *(Structured directories ready for upcoming modules)*
