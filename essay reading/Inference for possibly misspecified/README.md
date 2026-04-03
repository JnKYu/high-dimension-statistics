# Inference for possibly misspecified generalized linear models with nonpolynomial-dimensional nuisance parameters

## Basic Information

| Field | Content |
| :--- | :--- |
| **Title** | Inference for possibly misspecified generalized linear models with nonpolynomial-dimensional nuisance parameters |
| **Authors** | Shaoxin Hong, Jiancheng Jiang, Xuejun Jiang, Haofeng Wang |
| **Journal** | Biometrika |
| **Year** | 2024 |
| **Volume/Issue/Pages** | Vol. 111, No. 4, pp. 1387-1403 |

## Keywords

- High-dimensional statistical inference
- Post-selection inference
- Generalized linear models (GLM)
- Quasi-likelihood
- Dimension-reduced generalized likelihood ratio test (DR-GLR)
- Cross-fitting
- Nonpolynomial dimensionality
- Oracle property

## Contributions

1. **Two-step framework**: Proposes the DR-GLR test — first reduce dimensionality via regularization (SCAD/MCP) on nuisance parameters, then construct a quasi-likelihood ratio test on the reduced model. Solves the post-selection inference problem in high-dimensional GLMs.

2. **Penalize only nuisance parameters**: Only the nuisance parameters β are penalized; the parameters of interest γ always remain in the model. This avoids selection bias on γ and improves testing power.

3. **Quasi-likelihood framework**: Does not assume the data come from an exponential family — only requires the first two moments. Robust to model misspecification.

4. **Cross-fitting version**: For ultra-high-dimensional settings, proposes a cross-fitted DR-GLR test. Splits the data into two halves — one for variable selection, the other for inference — eliminating the influence of spurious variables without requiring the model selection consistency condition (Condition A6).

5. **Oracle property**: Proves that the asymptotic power of the DR-GLR test equals that of the optimal test that knows the true model.

## Main Content

### Problem Background

In high-dimensional GLMs, the parameter dimension \(p_n\) can be much larger than the sample size \(n\). The common practice is to first perform variable selection (e.g., LASSO) and then conduct inference on the selected model. However, this "post-selection inference" suffers from selection bias — using the same data for both selection and inference leads to inflated Type I error. Additionally, the classical likelihood ratio test no longer follows a \(\chi^2\) distribution in high dimensions (Wilks' theorem fails).

### Method

**Step 1 (Dimensionality reduction)**:
\[
\tilde{\theta} = \arg\max_{\theta} \left\{ Q_n(\theta) - n \sum_{j=1}^{p_n} p_{\lambda_n}(|\beta_j|) \right\}
\]
Only the nuisance parameters β are penalized; the parameters of interest γ are not.

**Step 2 (Test statistic)**:
\[
T_{n,2} = 2\hat{\phi}^{-1} \{ Q_n(\hat{\theta}) - Q_n(\hat{\theta}_0) \} \xrightarrow{d} \chi^2_{m_n}
\]

**Cross-fitting version**: Randomly split the data into two halves. Use one half for variable selection and the other half for inference. This eliminates the influence of spurious variables.

### Main Theorems

| Theorem | Core Result |
| :--- | :--- |
| Theorem 1 | Upper bound on the number of falsely selected variables: \(|\hat{N}| = O(s_n + q_n)\) |
| Theorem 2 | Under \(H_0\), \(T_{n,2} \sim \chi^2_{m_n}\) |
| Theorem 3 | Under local alternatives, \(T_{n,2} \sim \chi^2_{m_n}(\eta^2_{n,o})\) (Oracle property) |
| Theorem 4 | SIC consistently selects the true model |
| Theorems 7-8 | Cross-fitted test is asymptotically (non-central) \(\chi^2\) without requiring Condition A6 |

### Numerical Simulations

- Tested linear regression, logistic regression, Poisson regression, and Poisson-Gamma mixture regression
- Dimensions: \(r_n = 200, 500, 2000, 5000\)
- Cross-fitted DR-GLR achieves the best Type I error control in high dimensions (close to nominal 5%)

### Real Data Application (Breast Cancer Data)

- Data: 97 samples, 24,189 genes
- Test: Overall significance of 5 candidate genes
- Result: The 5 genes are jointly significant; cross-fitting selects 4 important genes (12801, 13742, 402, 8349)

## Connection to ESL Textbook

- **Section 3.2 (Linear Regression and Least Squares)** : Linear regression is a special case of GLM (normal distribution + identity link); least squares is a special case of quasi-likelihood estimation
- **Section 3.2 (Gauss-Markov Theorem)** : OLS is BLUE; the paper generalizes this optimality to GLM (Oracle property)
- **Section 3.2 (Regression by Successive Orthogonalization)** : Gram-Schmidt orthogonalization is conceptually related to the projection matrices and cross-fitting in the paper

## Open Questions

- [ ] Condition A6 (strong irrepresentable condition): what does it mean in practice, and how can it be verified?
- [ ] Detailed derivation of the Bahadur representation
- [ ] Is there an optimal sample splitting ratio for cross-fitting?

## References

- Hong, S., Jiang, J., Jiang, X., & Wang, H. (2024). Inference for possibly misspecified generalized linear models with nonpolynomial-dimensional nuisance parameters. *Biometrika*, 111(4), 1387-1403.
- Shi, C., Song, R., Chen, Z., & Li, R. (2019). Linear hypothesis testing for high dimensional generalized linear models. *Annals of Statistics*, 47(5), 2671-2703.
- Fan, J., & Li, R. (2001). Variable selection via nonconcave penalized likelihood and its oracle properties. *Journal of the American Statistical Association*, 96(456), 1348-1360.
- McCullagh, P., & Nelder, J. A. (1989). *Generalized Linear Models* (2nd ed.). Chapman and Hall.
- Hastie, T., Tibshirani, R., & Friedman, J. (2009). *The Elements of Statistical Learning* (2nd ed.). Springer.

---

**Date**: 2025-04-03
