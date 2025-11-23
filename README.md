# MSCS 634 Lab 5
## Hierarchical and DBSCAN Clustering on the Wine Dataset
### Overview
This repository contains the work completed for Lab 5 in MSCS 634. The objective of the lab is to apply and compare Hierarchical Clustering and DBSCAN using the Wine dataset from the sklearn library. The focus is on understanding how each method behaves, how parameter choices influence clustering, and how visualizations help interpret results.
### Data Preparation
The Wine dataset includes thirteen chemical features describing three categories of wine. All features were standardized using StandardScaler before clustering. Standardization ensured that Euclidean distance calculations treated each feature fairly and prevented variables with larger numeric ranges from dominating the clustering process.
### Hierarchical Clustering
#### Cluster Behavior
Agglomerative Hierarchical Clustering using Ward linkage was tested with several values of n_clusters.
When n_clusters was set to 2, the scatter plot showed two broad groups but with visible overlap. When set to 3, the clusters aligned more closely with the natural structure of the Wine dataset. Increasing n_clusters to 4 or 5 led to splitting existing clusters into smaller subgroups, which did not add meaningful structure. The best overall separation occurred at n_clusters equal to 3.
#### Dendrogram Interpretation
The dendrogram provided a visual representation of how clusters merged at different distances. Large vertical merges near the top indicated natural separation points. A horizontal cut at this level resulted in approximately three main clusters, supporting the conclusion that three clusters capture the essential structure of the dataset.
### DBSCAN Clustering
#### Parameter Behavior
DBSCAN was tested with various combinations of eps and min_samples. In every configuration, DBSCAN labeled all points as noise. This happened because the eps values used were too small relative to the distances between points in the thirteen-dimensional standardized dataset. As a result, DBSCAN did not identify any dense regions and produced only the label −1 for all samples.
#### Evaluation Metrics
Because DBSCAN produced only noise, valid silhouette scores could not be computed. Homogeneity was zero because the clustering did not separate the true classes. Completeness was one only because all samples received the same label. These metrics confirm that the tested DBSCAN parameter ranges were not appropriate for this dataset.
### Comparison of Methods
Hierarchical Clustering produced clear and interpretable structure, especially when using three clusters, which aligned well with the underlying wine categories. The dendrogram further supported selecting three clusters.
DBSCAN did not identify any clusters for the tested parameter values. Its performance was limited by parameter sensitivity and by the high dimensionality of the dataset. Larger eps values or dimensionality reduction techniques such as PCA may improve DBSCAN results.
### Key Insights
Standardization was essential for effective clustering. Hierarchical Clustering revealed meaningful structure and was well suited to this dataset. DBSCAN struggled due to the selected eps ranges and the dimensionality of the data. The dendrogram was useful for determining the number of clusters in hierarchical clustering. Overall, Hierarchical Clustering was the more effective algorithm for this lab.

### Challenges
The primary challenge was tuning DBSCAN parameters. All tested values resulted in every sample being labeled as noise. The high dimensionality of the dataset contributed to this difficulty. Selecting the number of clusters for hierarchical clustering required careful interpretation of the dendrogram.
