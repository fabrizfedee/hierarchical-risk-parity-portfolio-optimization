# Hierarchical Risk Parity for Portfolio Optimization

Implementation and analysis of Marcos López de Prado's **Hierarchical Risk Parity (HRP)** methodology for portfolio allocation.

This project reproduces the core mechanics of HRP in Python, with particular attention to the mathematical intuition, financial interpretation, and algorithmic structure behind the methodology.

The objective is to study a portfolio construction approach designed to address some of the instability and concentration issues associated with traditional covariance-based portfolio optimization.

---

## Project Overview

Traditional mean-variance portfolio optimization can become highly sensitive to estimation errors, particularly when asset returns are strongly correlated and the covariance matrix is ill-conditioned.

Hierarchical Risk Parity approaches the allocation problem differently. Instead of directly inverting the covariance matrix, HRP uses hierarchical clustering to identify the dependency structure among assets and allocates portfolio risk according to that hierarchy.

The implementation focuses on the three core stages of HRP:

1. **Hierarchical Clustering**
2. **Quasi-Diagonalization**
3. **Recursive Bisection**

The notebook combines the Python implementation with concise explanations of the mathematical and financial reasoning behind each stage.

---

## Methodology

### 1. Hierarchical Clustering

Asset correlations are transformed into a distance measure:

$$
d_{ij} = \sqrt{\frac{1-\rho_{ij}}{2}}
$$

where $\rho_{ij}$ represents the correlation between assets $i$ and $j$.

This transformation converts correlation information into a distance representation that can be used by hierarchical clustering algorithms.

The purpose of this stage is to identify groups of assets that exhibit similar dependence structures and organize them into a hierarchical tree.

### 2. Quasi-Diagonalization

The assets are reordered according to the hierarchical structure identified by the clustering algorithm.

The objective is to place highly related assets close to each other, revealing clusters in the covariance structure without changing the original investment basis.

Unlike techniques such as Principal Component Analysis, this step does not require a change of basis. The portfolio continues to be expressed in terms of the original assets.

### 3. Recursive Bisection

Portfolio weights are allocated recursively across the hierarchical tree.

At each stage, the ordered set of assets is divided into two subsets. The allocation between the two clusters is determined according to their relative risk.

The process is repeated recursively until weights are assigned to all individual assets.

This produces a top-down allocation mechanism that incorporates both asset-specific risk and the hierarchical dependence structure of the investment universe.

---

## Why Hierarchical Risk Parity?

HRP is particularly interesting from a quantitative research perspective because it combines:

- portfolio theory;
- covariance and correlation analysis;
- hierarchical clustering;
- graph-based representations of asset relationships;
- risk-based asset allocation.

Traditional quadratic portfolio optimization methods often rely on the inversion of the covariance matrix.

When the covariance matrix is ill-conditioned, small estimation errors can produce large changes in the inverse matrix and therefore unstable portfolio weights.

HRP avoids direct covariance matrix inversion and instead exploits the hierarchical structure of asset relationships.

This provides a different framework for diversification, where capital is allocated not only across individual securities but also across clusters of related assets.

---

## Quantitative Intuition

A key idea behind HRP is that diversification should reflect the **dependency structure between assets**.

Two assets with similar risk characteristics and high correlation may provide limited diversification benefits even if they are treated as separate securities.

Hierarchical clustering helps reveal this structure by grouping similar assets together.

The allocation procedure can therefore distribute risk across different branches of the hierarchy rather than treating every asset as an independent allocation decision.

Conceptually, the workflow can be summarized as:

**correlation structure → distance representation → hierarchical clustering → asset ordering → recursive risk allocation**

---

## Repository Structure

```text
hierarchical-risk-parity-portfolio-optimization/
│
├── README.md
├── hrp_portfolio_optimization.ipynb
├── requirements.txt
├── .gitignore
└── LICENSE
```

The main research implementation is contained in:

`hrp_portfolio_optimization.ipynb`

The notebook includes both the Python implementation and Markdown explanations connecting the code to the underlying quantitative methodology.

---

## Research Scope

The project focuses on understanding and implementing the core **Hierarchical Risk Parity allocation algorithm**.

The main objective is not simply to reproduce Python code, but to connect:

**financial intuition → mathematical formulation → algorithmic implementation**

Particular attention is given to the relationship between:

- asset dependence;
- covariance and correlation structures;
- hierarchical clustering;
- portfolio diversification;
- recursive risk allocation.

The repository focuses on the core mechanics of HRP rather than a complete replication of every empirical experiment presented in the original research.

---

## Technologies

- Python
- NumPy
- pandas
- SciPy
- Matplotlib
- Jupyter Notebook

---

## Skills Demonstrated

This project demonstrates experience with:

- quantitative portfolio construction;
- statistical dependence analysis;
- covariance and correlation matrices;
- hierarchical clustering;
- machine-learning techniques applied to finance;
- risk-based asset allocation;
- implementation of academic research in Python;
- interpretation of quantitative methodologies;
- technical documentation for reproducible research.

---

## How to Use

Clone the repository:

```bash
git clone https://github.com/fabrizfede/hierarchical-risk-parity-portfolio-optimization.git
```

Move into the project directory:

```bash
cd hierarchical-risk-parity-portfolio-optimization
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
hrp_portfolio_optimization.ipynb
```

---

## Reference

López de Prado, M. (2016).  
**Building Diversified Portfolios that Outperform Out of Sample.**  
*The Journal of Portfolio Management*, 42(4), 59–69.

The implementation is also based on the extended discussion of Hierarchical Risk Parity presented in:

López de Prado, M.  
**Advances in Financial Machine Learning.**  
Wiley.

---

## Disclaimer

This repository is intended for educational and quantitative research purposes only.

It does not constitute investment advice or a recommendation to buy or sell any financial instrument.
