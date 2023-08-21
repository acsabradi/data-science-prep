If one cluster is embedded in another, then a simple clustering algorithm won't be able to differentiate between the two.

DBSCAN identifies high density areas (clusters) and low density areas (outliers).

Calculate how many close data points are there for each data points. The radius for this is user defined.

Select core points with high number of close points. This number is also user defined. The remaining points are the not-core points.

Randomly pick a core point, assign it to the 1st cluster. Its close points are added to the cluster. Then the close core points of the cluster points also join the cluster.

Finally, we add the close not-core points to the cluster. These points' close points don't join the cluster.

If there are core points left that are not in the first cluster, then they will define the second cluster. Repeat the same steps.

The outlier data points are the ones that are not in any cluster after all of the core points are clustered.