# Manifold Visualization and Veracity Analysis of the Yeast Dataset

## Overview

This project focuses on understanding the **underlying structure and quality (veracity)** of the *Yeast* multi-label dataset using **manifold learning techniques** — primarily **t-SNE** and **Isomap**.  
Through these visualizations, we explore how gene expression data, originally represented in a 103-dimensional feature space, can be projected into a meaningful 2-D representation that preserves local and global relationships.

The analysis provides insight into the **complex, curved manifold** structure of biological data and highlights challenges such as **label noise, overlapping categories, and non-linear separability**, which directly influence classification difficulty.

---

## Dataset Description

- **Dataset:** Yeast gene expression dataset  
- **Samples:** 2417  
- **Attributes:** 103 numeric features + 14 binary label columns  
- **Nature:** Multi-label (each sample may belong to multiple functional categories)

Each instance corresponds to a yeast gene, represented by a set of quantitative descriptors and functional labels indicating the biological processes in which the gene is involved.

---

## Objectives

1. **Visualize** high-dimensional gene expression data using manifold learning methods.  
2. **Simplify label representation** to facilitate meaningful visualization.  
3. **Compare** the behavior of t-SNE (local structure) and Isomap (global structure).  
4. **Assess data veracity** by identifying:
   - Noisy or ambiguous labels  
   - Outliers  
   - Hard-to-learn regions  
5. **Interpret manifold curvature** and its implications on classification difficulty.

---

## Manifold Learning Techniques

### **A. t-SNE (t-Distributed Stochastic Neighbor Embedding)**
- Projects high-dimensional data into 2-D by preserving **local similarity probabilities**.  
- Experiments were conducted with **perplexities 5, 30, and 50**.  
- **Perplexity = 30** provided the most balanced embedding:
  - Preserved local structure while maintaining global cohesion.
  - Formed compact, interpretable clusters.
- Used for **veracity inspection** to locate noisy, ambiguous, and overlapping samples.

### **B. Isomap**
- A **global** manifold learning algorithm that preserves **geodesic distances** between samples.  
- Constructs a nearest-neighbor graph and computes shortest paths along it to unfold the manifold.  
- Produces a smoother, continuous representation of the dataset’s intrinsic geometry.  
- Reveals overall topology rather than isolated clusters.

---

## Veracity Inspection

Visual analysis of the t-SNE manifold identified:

| **Type** | **Description** |
|:--|:--|
| **Noisy/Ambiguous Labels** | Points of one color embedded within another cluster, suggesting overlapping gene functions or labeling errors. |
| **Outliers** | Isolated points or small clusters far from the main manifold, representing rare or anomalous gene expressions. |
| **Hard-to-Learn Regions** | Mixed-color regions where labels overlap densely, indicating high label correlation and classification difficulty. |

These findings demonstrate that the dataset has **noisy, highly overlapping labels**, making it a realistic but challenging benchmark for classification models.

---

## Comparison: t-SNE vs. Isomap

| **Aspect** | **t-SNE** | **Isomap** |
|:--|:--|:--|
| **Focus** | Preserves *local* structure | Preserves *global* structure |
| **Appearance** | Tight, distinct clusters (“islands”) | Continuous, stretched structure (“V” or “U” shaped) |
| **Interpretation** | Highlights neighborhood-level similarity | Reveals overall manifold topology |
| **Use Case** | Identifying subgroups and local outliers | Understanding global geometry and curvature |

- **t-SNE** is ideal for observing local neighborhood relationships.  
- **Isomap** provides a more faithful view of the *global* connectivity between clusters.  
Together, they give a comprehensive view of both local and global data organization.

---

## Manifold Curvature and Classification Difficulty

The Isomap embedding reveals that the yeast data lies on a **highly curved, non-linear manifold**.  
If the structure were linear, the embedding would appear spherical or uniform.  
Instead, the curvature and bending suggest complex, interdependent gene relationships.

**Implications:**
- Linear classifiers (e.g., Logistic Regression) will struggle to separate these classes effectively.  
- Accurate classification requires **non-linear models** (e.g., kernel SVM, neural networks) capable of following the curved manifold structure.  
- The curvature directly correlates with the **difficulty of learning** discriminative boundaries between functional classes.

---

## Key Insights and Conclusions

1. The *Yeast* dataset exhibits **strong label co-occurrence** and **multi-functionality**, typical of biological data.  
2. **t-SNE** reveals local micro-clusters, while **Isomap** highlights global connectivity and curvature.  
3. The presence of ambiguous and overlapping regions confirms high **data complexity** and **veracity challenges**.  
4. The manifold’s curvature implies that **linear decision boundaries** are inadequate, necessitating **non-linear learning approaches**.  
5. Manifold visualization thus serves as both an exploratory and diagnostic tool for understanding the data’s intrinsic geometry.

