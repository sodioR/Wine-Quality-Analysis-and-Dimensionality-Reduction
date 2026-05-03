# End-to-End Wine Quality Analysis

**Author:** Sadia Rahman  
**Focus:** EDA, Outlier Detection, and Dimensionality Reduction  

## Description

This project performs an end-to-end analysis of the Wine Quality dataset, including exploratory data analysis (EDA), multivariate outlier detection, feature scaling, and dimensionality reduction using Principal Component Analysis (PCA).

The goal is to understand how chemical properties relate to wine quality and to identify patterns that distinguish higher-quality wines.

## Dataset

- Source: UCI Machine Learning Repository (Wine Quality Dataset)  
- Includes both red and white wines  
- Features include acidity, sugar, sulfur dioxide, alcohol, and more  

## Methods

### Exploratory Data Analysis (EDA)

- Computed summary statistics:
  - Mean, standard deviation, trimmed mean  
  - Skewness and kurtosis  
- Grouped analysis by wine quality and type  

**Key Insight:**  
Higher-quality wines tend to have:
- Higher alcohol content  
- Lower residual sugar and volatile acidity  

### Data Visualization

<img width="945" height="398" alt="image" src="https://github.com/user-attachments/assets/5a11b8d6-2724-4063-b155-3aa90c001329" />

- Identified a clear inverse relationship between alcohol and volatile acidity  
- Higher-quality wines cluster at:
  - High alcohol  
  - Low volatile acidity  

### Outlier Detection (Mahalanobis Distance)

Mahalanobis distance:

$$
D^2 = (x - \mu)^T \Sigma^{-1} (x - \mu)
$$

- Used a 99% chi-square threshold:
  
$$
\text{Threshold} = \sqrt{\chi^2_{0.99, k}}
$$

- Detected ~3.83% of observations as outliers  

<img width="788" height="430" alt="image" src="https://github.com/user-attachments/assets/349aabe0-ea8e-4e60-95b1-e7917034977d" />

**Why this works:**  
Accounts for:
- Different feature scales  
- Correlation between variables  

### Feature Scaling

Applied Min-Max normalization:

$$
x' = \frac{x - x_{\min}}{x_{\max} - x_{\min}}
$$

- Verified all values fall within \([0,1]\)  
- Ensures fair contribution of all features  

### Principal Component Analysis (PCA)

- 6 components explain ~90% of variance  
- 8 components explain ~95% of variance  

<img width="632" height="411" alt="image" src="https://github.com/user-attachments/assets/0e5e62f9-0582-4c8a-b6b1-5224f3fabcfa" />

**Interpretation:**
- First component captures a “quality axis”:
  - High alcohol  
  - Low sugar, acidity, and density  
- PCA reveals patterns not easily visible in raw features  

## Key Findings

- Alcohol is the strongest positive indicator of wine quality  
- Volatile acidity is the strongest negative indicator  
- Higher-quality wines are more balanced and less variable  
- Outlier removal improves data consistency  
- PCA simplifies complex relationships into interpretable components  

## Tech

- Python  
- Pandas  
- NumPy  
- SciPy  
- Scikit-learn  
- Seaborn / Matplotlib  

## How to Run

1. Install dependencies:
```bash
pip install pandas numpy scipy scikit-learn seaborn matplotlib
