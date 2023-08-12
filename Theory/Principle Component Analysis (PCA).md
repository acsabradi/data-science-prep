Goals:
- Reducing data dimensions so it can be plotted $\rightarrow$ PCA-plot.
- Tells us which variable is most valuable for clustering.

Steps:
1. Shift the data so the center (the mean of all data) is on top of the origin.
2. Find a fitted line that goes through the origin.
	- Minimize the distance of the line and the data points.
	- Or map the data points to the line and maximize the mapped points' distances from the origin (sum of squared distances).
3. This fitted line is called Principal Component 1 (PC1).
4. 