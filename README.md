# upm-product-title-matching
Reimplementation and reproduction of the Unsupervised Product Matcher (UPM) algorithm for product title matching.
# Unsupervised Product Matcher (UPM) — Reproduction

## Overview

This project presents a Python reimplementation and experimental reproduction of the Unsupervised Product Matcher (UPM), proposed by Akritidis et al. (2020) in *A Self-Verifying Clustering Approach to Unsupervised Matching of Product Titles*.

The objective is to identify product listings from different vendors that refer to the same real-world product using product titles, without requiring labelled training data.

This project was completed as part of the **MSc Applied Data Science — Data Wrangling** course at Utrecht University.

## Research Paper

**Akritidis, L., Fevgas, A., Bozanis, P., & Makris, C. (2020).**  
*A Self-Verifying Clustering Approach to Unsupervised Matching of Product Titles.*

[Read the paper](https://link.springer.com/article/10.1007/s10462-020-09807-8)

## Algorithm

UPM performs product matching through three main stages:

1. **Title Analysis:** Product titles are tokenized and analyzed to identify informative token combinations.
2. **Initial Clustering:** Token combinations are scored using frequency, length, position, and token importance. Products are assigned to initial clusters based on these scores.
3. **Cluster Verification:** Clusters are verified using vendor constraints and similarity-based reassignment to reduce incorrect matches.

The algorithm combines token-combination scoring with a verification stage to improve matching quality.

## Implementation

The algorithm was reimplemented in Python using a Jupyter Notebook.

The implementation includes:

- Product title preprocessing and tokenization
- Token-combination generation and scoring
- Initial cluster assignment
- Cluster verification and reassignment
- Pairwise precision, recall, and F1 evaluation
- Experiments examining input-order sensitivity and implementation choices

## Dataset

The reproduction uses the PriceRunner aggregate product-title dataset from the Product Classification and Clustering dataset.

The dataset used in this implementation contains **35,311 rows**. The paper reports 35,305 titles for its aggregate PriceRunner benchmark. The difference in dataset statistics is discussed in the accompanying report.

[Dataset source — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/837/product+classification+and+clustering)

## Experimental Results

The paper reports a pairwise F1 score of **0.588** for UPM on the PriceRunner aggregate dataset.

The Python reproduction achieved:

| Experiment | Pairwise F1 |
|---|---:|
| Original dataset order | 0.5798 |
| Mean across three shuffled runs | 0.5752 ± 0.0010 |

The reproduced results are close to, but do not exactly match, the paper's reported result. Differences in dataset statistics and implementation details are discussed in the report.

## Repository Contents

- `UPM_reproduction.ipynb` — Python implementation, experiments, and evaluation.
- `pricerunner_aggregate.csv` — Dataset used for the reproduction, if included.

## How to Run

1. Clone or download this repository.
2. Install the required Python libraries.
3. Ensure the dataset is available in the notebook's working directory.
4. Open the notebook in Jupyter Notebook or JupyterLab.
5. Run the notebook cells sequentially.

The notebook uses a relative dataset path:

```python
df = pd.read_csv("pricerunner_aggregate.csv")
```

## References

Akritidis, L., Fevgas, A., Bozanis, P., & Makris, C. (2020). *A Self-Verifying Clustering Approach to Unsupervised Matching of Product Titles*.  
[https://doi.org/10.1007/s10462-020-09807-8](https://doi.org/10.1007/s10462-020-09807-8)
