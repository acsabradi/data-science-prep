**Linear regression** assumes a linear relationship between an output (dependent variable) and one or more inputs (independent variables). Output is continuous and unbounded

Generalized Linear Model (GLM) is a more universal form of linear regression because it allows not continuous and unbounded outputs, even the relationship between input and output can be non-linear.

Example: We want to model the number of Covid cases based on population in an area. The output is constrained because it can only be a positive integer.

GLM enables us the calculate $F$ and $p$ values in such cases where a simple linear regression is not applicable. One example is the t-test (comparing the mean of 2 groups and see if they are significantly different from each other):

![[t-test-figure.png|500]]

Instead of fitting one line with relatively high error, GLM calculates the mean of both group and activates them with a design matrix:

![[t-test-category-parameters-and-means.png|500]]

The design matrix ($A$) gives us an abstract of the fitted lines:

$$
y = A * means =
\begin{bmatrix}  
1 & 0 \\  
1 & 0 \\
1 & 0 \\
1 & 0 \\
0 & 1 \\
0 & 1 \\
0 & 1 \\
0 & 1 \\
\end{bmatrix}
*
\begin{bmatrix}  
2.2 \\
3.6
\end{bmatrix}
= mean_{control}+mean_{mutant}
$$
The columns of the design matrix act as switch for each group. If the data belongs to the Control group, the design matrix activates the mean of that group, thus that will be the prediction (same for the other group).

Now we can calculate both $SS(mean)$ and $SS(fit)$ for the [[Linear Regression|F and p values]]:

![[t-test-ss-mean-and-fit.png|300]]

The $p_{mean}$ in case of GLM is 1 because one constant describes the mean, meanwhile $p_{fit}$ is 2 because 2 mean value controls the output via the design matrix.

GLM can be applied to ANOVA too:

![[anova-glm-example.png]]

In practice, the design matrix is controlled by the mean of one group and the difference of the 2 groups:

$$
A =
\begin{bmatrix}  
1 & 0 \\  
1 & 0 \\
1 & 0 \\
1 & 0 \\
1 & 1 \\
1 & 1 \\
1 & 1 \\
1 & 1 \\
\end{bmatrix}
$$
$$
y = mean_{control}+difference_{mutant-control}
$$
This form enables us to form a more general linear regression.

This is a design matrix of a linear regression:

$$
y = A * 
\begin{bmatrix}  
intercept \\
slope
\end{bmatrix}
=
\begin{bmatrix}  
1 & 0.9 \\  
1 & 1.6 \\
1 & 2.3 \\
1 & 3.5 \\
1 & 4.2 \\
1 & 5.1 \\
1 & 5.5 \\
1 & 5.6 \\
\end{bmatrix}
*
\begin{bmatrix}  
intercept \\
slope
\end{bmatrix}
$$
Suppose we have this data:

![[t-test-with-linear-regression.png|500]]

It seems that although we can use linear regression but the data splits to 2 groups. GLM enables us the apply t-test and linear regression combined.

We could fit one line with relatively high $R^2$, but it wouldn't tell us anything about the 2 groups. On the other hand, a t-test would ignore the possible relationship between weight and size. The solution is to fit 2 lines as the figure shows:

$$
y = controlIntercept + mutantOffset + slope
$$
The slope of the 2 lines are the same for simplicity's sake.

$$
A =
\begin{bmatrix}  
1 & 0 & 2.4 \\
1 & 0 & 3.5 \\
1 & 0 & 4.4 \\
1 & 0 & 4.9 \\
1 & 1 & 1.7 \\
1 & 1 & 2.8 \\
1 & 1 & 3.2 \\
1 & 1 & 3.9 \\
\end{bmatrix}
$$
The first column shows that both line goes through the y-axis. The second column is 1 for the mutant groups, it enables the group to have a fitted line with different intercept than the control group. The third column contains the input values (weights).

Now we can calculate all metrics to this model the usual way. $p_{combined}$ is 3 because we applied 3 parameters (in other words, there are 3 columns in the design matrix). The $p$-values tell us that the combined t-test plus linear regression is better for estimation than any simpler model (mean, t-test, linear regression), because we captured the groups' relationship and the linearity of the data.

Related topics:
[GLM Python implementation](https://matthew-brett.github.io/teaching/glm_intro.html)
[GLM predictors, link functions](https://towardsdatascience.com/generalized-linear-models-9cbf848bb8ab)
