> **Clustering** is the most well-known unsupervised learning technique. It finds structure in unlabeled data by identifying similar groups, or _clusters_. Examples of clustering applications are:
> 
> - **Recommendation engines:** group products to personalize the user experience
> - **Search engines:** group news topics and search results
> - **Market segmentation:** group customers based on geography, demography, and behaviors
> - **Image segmentation:** medical imaging or road scene segmentation on self-driving cars

==Dataset used for explanation = Iris dataset==

![[Pasted image 20260218104240.png]]

features include sepal length, width, petal length, width.

```
from sklearn import datasets
iris = darasets.load_iris()
iris.data() gives the complete dataset
iris.DESCR gives the description  
```

- K random centroids selection randomly 
- assign data samples to nearest centroids 
- update centroids based on the added data samples 

So now that we have to select centroids randomly

![[Pasted image 20260219132106.png]]So basically to measure how good the clusters one calculates inertia- it tells how close the members of the clusters are with the centroid. Lower the inertia the better the cluster.
Ultimately, this will always be a trade-off. The goal is to have low inertia _and_ the least number of clusters.

One of the ways to interpret this graph is to use the _elbow method_: choose an “elbow” in the inertia plot - when inertia begins to decrease more slowly.

[[https://scikit-learn.org/stable/datasets.html]]


#  **K-Means++ algorithm**


K-Means++ changes the way centroids are initalized.

- **1.1** The first cluster centroid is randomly picked from the data points.
- **1.2** For each remaining data point, the distance from the point to its nearest cluster centroid is calculated.
- **1.3** The next cluster centroid is picked according to a probability proportional to the distance of each point to its nearest cluster centroid. This makes it likely for the next cluster centroid to be far away from the already initialized centroids.

