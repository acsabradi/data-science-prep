**Goals:**
Similar to PCA, but LDA focuses on separability among known categories instead of increasing variance. LDA is supervised method, PCA is unsupervised.

**Steps (2 dimensions, 2 categories):**
Define a fit line candidate, map the data points on it. The best fit line satisfies 2 criteria applied on the mapped values:
- Maximize the distance between the means of the 2 groups.
- Minimize the variance (scatter) within each groups.
- ==Summarized==: maximize $\rightarrow\frac{(\mu_1-\mu_2)^2}{s_1^2+s_2^2}=\frac{d^2}{s_1^2+s_2^2}$

In case of more than 2 categories we maximize the distances between the central point (mean of all data points) and the central points of each groups.

**Math background:**

==Separation:==
$$
S = W^{-1}B
$$

$W$: pooled within-group covariance
$B$: between-groups covariance

In case of equal sample size:
$$
W = \frac{Cov(Group1)+Cov(Group2)}{2}
$$
Not equal sample size:
$$
W = \frac{(n_1-1)Cov(Group1)+(n_2-1)Cov(Group2)}{n_1+n_2-2}
$$
==Total covariance== (calculated for all data points without separating them into groups; PCA uses this matrix to calculate eigenvalues and eigenvectors):
$$
T=B+W \rightarrow B = T-W
$$
Now we can calculate $S$ and its eigenvalues and eigenvectors. The eigenvectors give us the weights for LD1 and LD2 which enables us to calculate the ==discriminant scores==.

The weights are usually normalized by dividing them with the standard deviation calculated from the pooled variance of all discriminant scores. The recalculated discriminant scores will have a pooled variance of 1.

**Notes:**

For normalization of data points, the standard deviation is calculated from the pooled variance, not the variance off all data points.

LDA can be used for classification. After calculating the discriminant scores, we can define a cut-off value (e.g. mean).

If we can presume that the scores follow a normal distribution, then we can define normal distributions for each group by calculating the means and standard deviations. We can calculate probability this way.