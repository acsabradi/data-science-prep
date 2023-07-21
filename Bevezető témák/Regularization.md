# Ridge (L2) Regression

The fitted line can be overfitted to the training data which results to high variance to the testing data. Regularization introduces bias to the model. The goal is the reduce high amount of test data variance by adding a small amount of bias.

Ridge Regression does this by minimizing:

$$
(\sum_{i=1}^n (y_i - (a * x_i + b))^2) + \lambda * a^2
$$
$\lambda * a^2$ adds a penalty to the expression to be minimized. Minimalizing this expression adds a small bias to the fitted line by lowering the slope. Lower slope means that the output is less sensitive to the changes of the input.

$\lambda$ controls how much do we want to penalize high slopes. Higher $\lambda$ means lower slope, the slope asymptotically approaches 0 as $\lambda$ increases to infinity.

We use [[Cross validation|cross validation]] to determine the ideal value for $\lambda$.

Ridge Regression can be used for discrete variables, too (e.g. t-test setup).

Linear Models showed that in case of t-test:

$$
y = firstGroupMean + meanDifference*secondGroupSwitch
$$

Ridge Regression minimizes the mean difference instead of the slope in this scenario.

In general, the penalty is:

$$
\lambda * \sum_{i=1}^{n}\beta_i^2
$$

Where $\beta_i$ are the parameters, except of the y-intercept.

# Lasso Regression

The Lasso Regression's penalty is $\lambda * |a|$. 

In general, the penalty is:

$$
\lambda * \sum_{i=1}^{n}|\beta_i|
$$

Where $\beta_i$ are the parameters, except of the y-intercept.

Unlike Ridge Regression, Lasso Regression can push the slope to zero with high enough $\lambda$, thus it can eliminate useless variables by setting their coefficient to zero.

**Rule of thumb**: Use Ridge if we suspect that most variables are useful, use Lasso in other cases.

![[ridge-v-lasso-visualization.png]]

Ridge Regression's optimal slope never reaches zero, even with extremely high $\lambda$. Lasso Regression's optimal slope can be zero with relatively low $\lambda$.

# Elastic Net Regression

It combines the features of the Ridge and Lasso Regression. The penalty is:

$$
\lambda_{lasso} * \sum_{i=1}^{n}|\beta_i| + \lambda_{ridge} * \sum_{i=1}^{n}\beta_i^2
$$

Related topics:
[[Bias and variance]]