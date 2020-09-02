# CLUSTERING
# INTRODUCTION TO CLUSTERING 
* Unsupervised Learning Method
  - Trying to find hidden structure in unlabeled data.
* The task of grouping the data items such that items in the same group are similar.
* **Example** :
  - A cellular company deciding the location of its tower so that its customers get optimum signal strength.
* Grouping is done such that there is -
  - **High intra_cluster similarity** (with in groups high similarity (or) low difference)
  - **Low inter_cluster similarity** (across groups low similarity (or) high difference)
* Grouping is done based on our requirements
<br>For example **Grouping a class of students**
  1. Based on Gender.
  2. Based on qualification.
  3. Based on area.
  4. Based on experienced or fresher.
  5. Based on scores.
  6. Based on height.
  7. Based on IT or non IT background.
* **What is similarity ?**
  - The quality or state of being similar; likeness; resemblance; as a similarity of features.
  - Similarity is hard to define!
* **Distance Measure** :
  - Let A, B be two objects from the universe of possible objects. The distance(dissimilarity) between A, B is a real number denoted by D(A, B)
  - For numerical data, we use Euclidean distance, Mahalanobis distance etc.
  - **Properties of Distance Measure** :
    1. **SYMMETRY** : D(A, B) = D(B, A)
    2. **REFLEXIVE** : D(A, B) = 0 iff A = B
    3. **TRIANGLE INEQUALITY** : D(A, B) <= D(A, C) + D(B, C)
* **When we say clustering algorithm is good?**
  - Efficiency of clustering is measured in terms of **Scatter Coefficient.**
  <br><img src="https://render.githubusercontent.com/render/math?math={SC}={\frac{\text{Average intra_cluster distance}}{\text{Average inter_cluster distance}}}">
  - Lower the scatter coefficient, better is the clustering.
* **Intra clustering** : Within the groups every combination
<br><img src="https://render.githubusercontent.com/render/math?math={\bar c_1}={\frac{1}{m}}{\sum d(a,b)}{\quad \quad \forall a,b \in cluster1 }">
<br><img src="https://render.githubusercontent.com/render/math?math={\bar c_2}={\frac{1}{n}}{\sum d(u,v)}{\quad \quad \forall u,v \in cluster2 }">
<br> Where
<br>&emsp; m = Total number of observations in cluster1
<br>&emsp; n = Total number of observations in cluster2
<br><img src="https://render.githubusercontent.com/render/math?math={\text{AVG Intra cluster}}={\frac{{\bar c_1} %2B {\bar c_2}}{2}}">
* **Inter clustering**: Every combination across the group
<br><img src="https://render.githubusercontent.com/render/math?math={\frac{1}{m %2B n}}{\sum d(a,u)}{\quad \quad \forall a \in cluster1, \forall u \in cluster2}">
# TYPES OF CLUSTERING
* **Partitional Clustering(Nonhierarchical clustering)** : 
  - Construct various partitions and then evaluate them by some criterion(K means clustering).
  - **Kmeans partitional** means 2 or more groups exactly one of non overlapping cluser.
  - Partitional clustering, each instance is placed in exactly one of K non-Overlapping clusters.
  - since only one set of clusters is output, the user normally has to input the desired number of clusters K.
* **Hierarchical Clustering** : 
  - Create a hierarchical decomposition of the set of objects using some criterion.
  - Keep combining most similar items together finally we end up with tree called as **dendrogram**. 
  - **Chapping** of dendrogram is based on number of groups required. [There is a chance of overlapping in cluster]
  - **Types of Hierarchical Clustering** :
    * **Bottom-up(agglomerative)** : Starting with each item in its own cluster, find the best pair (Finding Similarity) to merge into a new cluster. Repeat untill all clusters are fused together. (n --> Finding Similarity --> 2 or more)
    * **Top-down(divisive)** : Starting with all the data in a single cluster, consider every possible way to divide the cluster into two (Finding Disimilarity). Choose the best division and recursively operate on both sides. (1 --> Finding Disimilarity --> 2 or more)
# KMeans Clustering :
* **Challenge** :
  - What must be the value of K?
* **Elbow Method** :
  - Run the algorithm for a range of K (say 1 to 10)
  - Compute SSE (Sum of Squared Error) for each k
  - Plot K v/s SSE
  - Choose K, which is elbow of the arm-shaped graph
  <p align="left">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/UnSupervised%20Learning/Clustering/Img/elbow.png" width="400px" height="300px"/></p>
* **Hierarchical Clustering** :
  - Choose K with the help of Dendogram
  - Apply Bottom-up(agglomerative) clustering.
# Hierarchical Clustering
Linkage Methods:
- **ward** minimizes the variance of the clusters being merged.
- **average** uses the average of the distances of each observation of the two sets.
- **complete** or maximum linkage uses the maximum distances between all observations of the two sets.
- **single** uses the minimum of the distances between all observations of the two sets.    
