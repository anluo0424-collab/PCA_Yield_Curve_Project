# PCA Yield Curve Project

This project applies Principal Component Analysis (PCA) to analyze movements in the U.S. Treasury yield curve.

The analysis focuses on monthly yield changes for six maturities (1Y, 2Y, 3Y, 5Y, 7Y, and 10Y) obtained from the FRED database. PCA is used to identify the main factors driving yield curve dynamics.

---

## Data and Preprocessing

The dataset contains monthly U.S. Treasury yields for six maturities: 1Y, 2Y, 3Y, 5Y, 7Y, and 10Y.

Before applying PCA:

- Missing values are interpolated when necessary
- Monthly yield changes are computed
- The data is standardized using `StandardScaler.`

These steps ensure that differences in volatility across maturities do not dominate the PCA results.

---

## Method 1: PCA using sklearn

In the first approach, PCA is implemented using the `sklearn` library on standardized yield changes.  

This method directly computes:

- Principal components
- Explained variance ratios
- Factor loadings

The first three principal components are interpreted as:

- **PC1: Level factor**
- **PC2: Slope factor**
- **PC3: Curvature factor**

---

## Method 2: PCA using Eigenvalue Decomposition

In the second approach, PCA is implemented manually by computing the **correlation matrix** of the standardized yield changes and performing **eigenvalue decomposition**.

This method illustrates the mathematical foundation of PCA and produces results consistent with the sklearn implementation.

---

## Rolling Window Stability

To evaluate the stability of the factor structure, PCA is re-estimated using a **rolling 60-month window**.

This analysis examines whether the importance of the principal components remains stable over time.

---

## Reconstruction Test

To validate the effectiveness of the dimensionality reduction, the first three principal components are used to **reconstruct the original yield changes**.

The reconstructed series closely matches the original data, indicating that the **three-factor representation captures most of the variation in yield curve movements**.
