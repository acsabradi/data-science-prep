$K$: How many clusters do we want to identify?

Steps:
1. Select randomly $K$ data point, these are the initial clusters.
2. Assign the remaining data points to the nearest initial cluster.
3. Calculate the mean of the clusters.
4. Re-assign the data points to the nearest cluster mean.
5. Repeat step 3 and 4
6. We are done if there was no re-assignment.

The clustering is evaluated by calculating the variance of the groups. Usually the described steps are executed multiple times and the clustering with the lowest variance will be selected.

Optimization for $K$ (elbow-plot):

Perform the steps with increasing $K=1,2,3..$ Calculate the best variance of each iteration. The variance will go to zero when $K$ reaches the number of data points. There is a threshold for $K$: The variance will not go lower as quickly as before after this threshold. This is the optimal $K$ value.