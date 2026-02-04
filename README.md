# Diabetic Foot Ulcer Data Analysis

This repository contains statistical analysis, machine learning classification, and unsupervised analysis of diabetic foot ulcer–related biological data.  
All methods and results documented here are strictly based on the work implemented in the Google Colab notebooks provided in this repository.

---

## Dataset Description

The dataset contains **14 samples** divided into two groups:

- **Group 1 (Healthy / Good = 1)**
- **Group 0 (Unhealthy / Diseased = 0)**

Each sample includes the following biological and vascular features:

- Permeability  
- LDL Uptake  
- Total Reactive Oxygen Species (ROS)  
- Vascular Marker  
- Cell Signalling  
- Tube Formation  
- In-vivo Recovery  

The dataset is manually created and checked for duplicates (none found).

---

## Notebook 1: Statistical Analysis, Classification, and Health Scoring  
**File:** `Diabetic-Ulcer-1.ipynb`

This notebook focuses on **statistical validation, visualization, classification, and health score generation**.

---

### 1. Exploratory Data Analysis (EDA)

- Overall descriptive statistics (mean, standard deviation, min, max)
- Group-wise descriptive statistics for each feature
- Clear numerical separation observed between healthy and unhealthy groups

---

### 2. Statistical Hypothesis Testing

#### a) Independent t-Test
- Applied feature-wise between Group 0 and Group 1
- All features show statistically significant differences (p < 0.05)

#### b) Mann–Whitney U Test
- Non-parametric test used due to small sample size
- Confirms statistically significant differences across all features

#### c) MANOVA
- Multivariate comparison across all features
- Extremely low p-values indicate strong group separation

#### d) PERMANOVA
- Distance-based multivariate test (Euclidean distance)
- Statistically significant group differences confirmed

---

### 3. Data Visualization

- Scatter plots (e.g., Permeability vs Total ROS)
- Histograms for individual feature distributions
- Boxplots for outlier inspection
- Pair plots for multivariate separation
- Correlation heatmaps for:
  - Healthy group
  - Unhealthy group
  - Combined dataset

---

### 4. Anomaly / Outlier Detection

- Z-score based anomaly detection
- IQR-based outlier detection
- One mild outlier detected in LDL uptake (Group 0)
- No extreme anomalies affecting overall analysis

---

### 5. Classification Using Machine Learning Models

Supervised classification is performed to distinguish between healthy and unhealthy samples.

The following models are implemented:

- **Logistic Regression**
- **Support Vector Machine (SVM)**
- **Principal Component Analysis (PCA)**

Evaluation includes:
- Train–test split
- Accuracy score
- Confusion matrix
- Classification report
- ROC curve and AUC score

The results show **very high separability**, indicating that the features are highly discriminative.

---

### 6. Health Score Generation

Two different approaches are used to create a **Health Score**:

#### a) Equal Weighting Approach
- Biological features are grouped into **domain-specific indicators**
  (e.g., vascular function, oxidative stress, cellular activity, recovery)
- For each indicator, feature values are normalized to a common scale
- **Two weighting strategies are applied**:
  - **Equal weighting**: all indicators contribute equally to the final health score
  - **Differential weighting**: indicators are assigned different weights based on their relative importance
- A composite health score is calculated using weighted aggregation
- The final score is mapped to indicator domains to interpret overall health condition
- This approach provides both **interpretability** (equal weights) and **domain sensitivity** (different weights)

#### b) Data Driven Health Score
- Health score is derived from **predicted class probabilities** of trained classification models
- A higher predicted probability of the “Healthy” class corresponds to a higher health score
- This provides a **model-driven and data-driven risk interpretation**
- In addition, a **PCA-based health score** is computed:
  - Principal components are obtained from standardized feature values
  - The dominant principal component(s), capturing maximum variance, are used to construct a continuous health score
- The PCA-based score reflects overall biological state in a reduced-dimensional space
- Together, probability-based and PCA-based scores provide **complementary perspectives** on health status


Both approaches clearly differentiate healthy and unhealthy samples.

---

## Notebook 2: Visualization and Clustering  
**File:** `Diabetic-Ulcer-2.ipynb`

This notebook focuses on **unsupervised learning and multivariate visualization**.

---

### 1. Feature-wise Group Comparison

- Group-wise mean comparison using bar plots
- Healthy group shows better vascular function and recovery
- Unhealthy group shows higher permeability and oxidative stress

---

### 2. PCA (Principal Component Analysis)

- Standardization using `StandardScaler`
- Dimensionality reduction from 7D to 3D
- Explained variance:
  - PC1 ≈ 88%
  - PC2 ≈ 7%
  - PC3 ≈ 1.6%

---

### 3. PCA Visualization

- Interactive 3D PCA scatter plots
- PCA biplot with feature vectors
- Clear separation between healthy and unhealthy samples
- Permeability and ROS dominate PC1

---

### 4. Interactive Multidimensional Visualization

- Interactive 3D scatter plots with selectable axes
- Interactive 2D scatter plots
- Parallel coordinates plots
- Strong and consistent multivariate separation observed

---

### 5. Clustering Analysis

Unsupervised clustering is performed to identify natural groupings in the data without using class labels.

The following clustering models are used:

- K-Means Clustering
- Hierarchical (Agglomerative) Clustering
- DBSCAN
- Gaussian Mixture Model (GMM)

Across all clustering methods:
- Cluster assignments align closely with biological group labels
- Clear separation is observed between healthy and unhealthy samples
- The results confirm the presence of a strong natural structure in the data

---

## Tools and Libraries Used

- Python
- NumPy
- Pandas
- SciPy
- scikit-learn
- statsmodels
- scikit-bio
- Matplotlib
- Seaborn
- Plotly
- Google Colab
  
---

## Repository Structure
```
Diabetic-foot-ulcer/
│
├── Diabetic-Ulcer-1.ipynb   # Statistics, classification & health scoring
├── Diabetic-Ulcer-2.ipynb   # PCA, clustering & visualization
├── README.md                # Project documentation
├── requirements.txt         # Required version
```
