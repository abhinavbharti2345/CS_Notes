---
type: concept
topic: Data Structures & Algorithms
subtopic: Trees & BST
date: 2026-10-07
tags:
  - dsa
  - trees
  - bst
  - recursion
---

# 🌳 Trees & Binary Search Trees (BST)

> Non-linear hierarchical data structures composed of root nodes and recursive child subtrees, balancing ordered fast retrieval and recursive decomposition.

---

## 🎯 Why It Matters
- **Hierarchical Representation:** Models file systems, DOM trees in browsers, JSON/XML schemas, and syntax trees in compilers.
- **Database Indexing:** Powers self-balancing search trees (AVL, Red-Black Trees, and database B-Trees / B+Trees).
- **Mastery of Recursion:** Trees are recursive by definition; solving tree problems is the fastest way to master recursive divide-and-conquer paradigms.

---

## 🧠 Core Concepts & Traversals

### 1. Depth-First Search (DFS)
- **Inorder (`Left ➔ Root ➔ Right`):** Produces strictly sorted output on a Binary Search Tree (BST).
- **Preorder (`Root ➔ Left ➔ Right`):** Used for tree serialization and copying.
- **Postorder (`Left ➔ Right ➔ Root`):** Used for bottom-up calculation (calculating subtree height, diameter, memory cleanup).

### 2. Breadth-First Search (BFS / Level Order)
- Traverses level-by-level using a `Queue`.
- Used for finding the shortest path in unweighted structures and vertical/zigzag views.

---

## 🛠️ Code Example: Lowest Common Ancestor (LCA) in Binary Tree

```java
public class TreeNodeLCA {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
    }

    public static TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null || root == p || root == q) return root;

        TreeNode left = lowestCommonAncestor(root.left, p, q);
        TreeNode right = lowestCommonAncestor(root.right, p, q);

        if (left != null && right != null) return root; // p and q found in different subtrees
        return (left != null) ? left : right;
    }
}
```

---

## 🔗 Related Notes
- Detailed Concept Note: **[[CS/DSA/07. Trees & BSTs/01. Binary Tree Fundamentals|🌳 Detailed Binary Tree Fundamentals]]**
- Recursion Foundation: **[[CS/DSA/05. Recursion & Backtracking/01. Recursion Fundamentals|⚡ Recursion Fundamentals]]**
- Heaps & Trees: **[[BrainOS/02 - Foundations/DSA/Heaps & Priority Queues|Heaps & Priority Queues]]**
- DSA Master Hub: **[[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]**
