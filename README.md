#  Wholesale Customers Clustering Analysis

This project performs **unsupervised learning** on the **Wholesale Customers dataset** using various clustering algorithms — **K-Means**, **Hierarchical Clustering**, and **DBSCAN** — after applying data preprocessing, outlier handling, and power transformation.


## Dataset Overview

**File:** `Wholesale customers data.csv`

**Shape:** `(440, 8)`
**Columns:**

* Channel
* Region
* Fresh
* Milk
* Grocery
* Frozen
* Detergents_Paper
* Delicassen

**Missing Values:** None
**Duplicate Rows:** 0


## Step 1: Data Preprocessing

### 1. Numerical Columns Selected

### 2. Skewness Check (Before Transformation)

| Feature          | Skewness |
| ---------------- | -------- |
| Fresh            | 2.56     |
| Milk             | 4.05     |
| Grocery          | 3.59     |
| Frozen           | 5.91     |
| Detergents_Paper | 3.63     |
| Delicassen       | 11.15    |

**Observation:** All features are right-skewed → need transformation.


## Step 2: Outlier Handling (IQR Clipping)

Outliers were clipped using the **Interquartile Range (IQR)** method:


Outliers reduced (confirmed via boxplots before and after).



## Step 3: Power Transformation

To normalize and reduce skewness, **Yeo-Johnson PowerTransformer** was applied:


### Skewness After Transformation

| Feature          | Skewness |
| ---------------- | -------- |
| Fresh            | -0.12    |
| Milk             | -0.05    |
| Grocery          | -0.01    |
| Frozen           | -0.06    |
| Detergents_Paper | -0.05    |
| Delicassen       | -0.08    |

**Observation:** Data distribution approximately normal.


## Step 4: Feature Scaling


All features are standardized to mean = 0 and variance = 1.


## Step 5: K-Means Clustering

### Elbow Method

Used to determine optimal clusters (k):


Elbow curve suggested **k = 3** as the optimal choice.

### Final KMeans Model

ls = kmeans.fit_predict(X_scaled)

**Silhouette Score:** `0.2586`
Moderate cluster separation.


## Step 6: Hierarchical Clustering (Agglomerative)

**Silhouette Score:** `0.2121`

 Similar clustering quality to KMeans, slightly lower cohesion.


## Step 7: DBSCAN Clustering

### Epsilon Estimation

Used **k-distance graph** to find elbow for suitable `eps`:


### DBSCAN Model


**Cluster Counts (including noise):**


**Silhouette Score (excluding noise):** `0.19`

DBSCAN found multiple small clusters and some noise points.


## Step 8: Model Comparison

| Algorithm    | No. of Clusters | Silhouette Score | Remarks                             |
| ------------ | --------------- | ---------------- | ----------------------------------- |
| K-Means      | 3               | 0.2586           | Best separation overall             |
| Hierarchical | 3               | 0.2121           | Similar but less defined            |
| DBSCAN       | 5 (+noise)      | 0.19             | Captures anomalies, less structured |


## Conclusion

* **Power Transformation (Yeo-Johnson)** effectively normalized the data.
* **Outlier clipping** improved model stability.
* **K-Means (k=3)** achieved the best clustering result among all algorithms.
* **DBSCAN** identified noise and smaller subgroups but less cohesive clusters.


##  Libraries Used

```python
pandas
numpy
matplotlib
seaborn
scikit-learn
scipy
```

##  Visualization Outputs

* Distribution plots before and after transformation
* Boxplots before and after outlier clipping
* Elbow curve for KMeans
* Dendrogram for Hierarchical clustering
* k-distance graph for DBSCAN



Would you like me to add **visual result images (Elbow, Dendrogram, DBSCAN plots)** as embedded markdown (`![image](path)`) for your README too?
