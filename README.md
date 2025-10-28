Wholesale Customers Clustering Project
Project Overview

This project performs clustering analysis on the Wholesale Customers Dataset using three popular clustering algorithms:

K-Means

Hierarchical Clustering (Agglomerative)

DBSCAN (Density-Based Spatial Clustering)

The goal is to explore customer segmentation patterns based on product spending categories such as Fresh, Milk, Grocery, Frozen, Detergents_Paper, and Delicassen.

Dataset Information

File used: Wholesale customers data.csv

Columns:

Channel: Type of sales channel (1 = Horeca, 2 = Retail)

Region: Customer region

Fresh: Annual spending on fresh products

Milk: Annual spending on milk products

Grocery: Annual spending on groceries

Frozen: Annual spending on frozen products

Detergents_Paper: Annual spending on detergents and paper products

Delicassen: Annual spending on delicatessen products

Shape: (440, 8)
Missing Values: None
Duplicates: None

Data Preprocessing Steps
1. Skewness Check

Each numeric feature was checked for skewness to understand data distribution.

Fresh: 2.56
Milk: 4.05
Grocery: 3.59
Frozen: 5.90
Detergents_Paper: 3.63
Delicassen: 11.15

All columns were highly skewed → transformation required.

2. Outlier Handling

Outliers were clipped using the IQR (Interquartile Range) method.
Boxplots before and after clipping confirmed reduced extreme values.

3. Power Transformation

Applied Yeo-Johnson transformation (suitable for zero and negative values).
This transformation made all distributions approximately normal.

Post-transformation skewness:
Fresh: -0.12
Milk: -0.05
Grocery: -0.01
Frozen: -0.06
Detergents_Paper: -0.05
Delicassen: -0.08

4. Feature Scaling

StandardScaler was used to normalize all numeric features before clustering.

Clustering Algorithms and Results
1. K-Means Clustering

Optimal number of clusters: 3 (determined by Elbow Method)

Silhouette Score: 0.2586

Interpretation:
K-Means produced moderately separated clusters, suggesting some overlap between customer segments.

2. Hierarchical (Agglomerative) Clustering

Linkage method: Ward

Number of clusters: 3

Silhouette Score: 0.2120

Interpretation:
Hierarchical clustering formed slightly less distinct groups than K-Means.

3. DBSCAN Clustering

Parameters: eps = 1.0, min_samples = 7

Cluster counts (including noise): {-1: 174, 0: 96, 1: 150, 2: 7, 3: 7, 4: 6}

Silhouette Score (excluding noise): 0.19

Interpretation:
DBSCAN detected multiple small clusters and significant noise points, showing that density-based clustering struggled with this dataset.

Conclusion

K-Means gave the best clustering performance (Silhouette ≈ 0.26).

Hierarchical clustering showed similar but slightly weaker results.

DBSCAN identified many outliers but lower overall separation.

Power transformation and outlier clipping improved data distribution and helped achieve better clustering stability.

Libraries Used

pandas

numpy

scikit-learn

seaborn

matplotlib
