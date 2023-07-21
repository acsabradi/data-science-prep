We want to fit a line (or plane) to the given test data.
$$
predictedOutput = slope * predictor + intercept = y = a * x + b 
$$
The goal is to find an optimal slope and intercept value which minimizes the sum of squared residuals:
$$
\sum_{i=1}^n (y_i - (a * x_i + b))^2
$$
Where $n$ is the sample size. It is called **Least squares method**: We take the derivative of sum of squared residuals, why find where it's zero, that's where it has a minimum.

Sum of squares around the mean:
$$
SS(mean)=\sum_i (y_{mean}-y_i)^2
$$
Variation around the mean:
$$
Var(mean) = \frac{SS(mean)}{n}
$$
Sum of squares around the least-squares fit: $SS(fit)$
So:
$$
Var(fit) = \frac{SS(fit)}{n}
$$
In general:
$$
Var(something) = \frac{SS(something)}{sampleSizeOfSomething}
$$
$R^2$: How much of the variation of the output can be explained by taking the input (predictor) into account.
$$
R^2 = \frac{Var(mean)-Var(fit)}{Var(mean)} =
\frac{SS(mean)-SS(fit)}{SS(mean)}$$
Example: $R^2$ is 0.6 (= 60%) -> There is a 60% reduction in variance if we take the input into account. Alternatively, the input explains 60% of the variation in the output.

Problem with $R^2$: If we have only 2 data points, then least squares will always produce a 100% $R^2$. Any random 2 points will produce the same. We have to determine if the calculated $R^2$ value is statistically significant.

$$
F = \frac{\frac{SS(mean)-SS(fit)}{p_{fit}-p_{mean}}}{\frac{SS(fit)}{n - p_{fit}}}
$$
$p_{fit}$: number of parameters in the fitted line -> y-intercept and slope -> $p_{fit} = 2$

$p_{mean}$: number of parameters in the mean line -> the mean is constant -> $p_{mean} = 1$

> [!info]
> The $F$ value compares a more complex model to a simpler one. In this case, the simpler model was a mean calculation, meanwhile the more complex one was the fitted line. This is a general calculation, e.g. you can compare a 2-input linear regression model to a 1-input one, so you can check if including an additional parameter was worth it.

The $F$ numerator is the variance explained by the extra parameter (slope) of the fitted line.
The $F$ denominator is the variance not explained by the fitted line.

$F$ is high if the fitted line is a good fit.

[[Calculating p value|Calculating p-value]]:

Generate a random set of dataset, calculate $F$ of it. Iterate a lot of times, then visualize the results in a histogram.
 
![[f-histogram.png|500]]

This is the $F$-distribution. If the original data has $F=6$, then:

![[p-value-calculated-from-f-histogram.png|500]]

In practice, the $p$-value is calculated from a function:

![[f-distributions.png|500]]

Related topics:
[[Regularization]]