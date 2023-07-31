Logistic Regression's output is binary, not continuous. It's used for classification.

![[logistic-regression-example.png|500]]
### Continuous variables

The task is to transform the logistic regression into a linear one. We do this by map the y-axis of the logistic regression via the **logit function**. This maps the logistic regression's $[0,  1]$ domain to $]-\infty, +\infty[$. Now we can use the methods of linear regression. 

$$
y = -3.48+1.83*weight
$$

![[logistic-regression-coefficients.png|500]]

The $z$-value is the estimation divided by the standard deviation. Both estimation is closer to the mean than 2 standard deviations so they are not statistically significant (Wald test). The high $p$-values confirm this.

### Discrete variables

Logistic regression can be applied to t-test, too. We apply the ***logit function*** again.

![[logistic-regression-discrete-example.png|500]]
$$
size = mean_{normal}+(mean_{mutant}-mean_{normal})
$$
$$
log(oddsGene_{normal})=log(2/9)=-1.5
$$
$$
log(oddsGene_{mutated})=log(7/3)=0.85
$$
$$
size = log(oddsGene_{normal}) * B_1 + (log(oddsGene_{mutated})-log(oddsGene_{normal})) * B_2
$$
$$
size = log(oddsGene_{normal}) * B_1 + log(\frac{oddsGene_{mutated}}{oddsGene_{normal}}) * B_2
$$
$$
size = -1.5*B_1+2.35*B_2
$$
![[logistic-regression-discrete-example-means.png|500]]

The coefficients show the same result:

![[logistic-regression-discrete-coefficients.png|500]]

The Wald test shows that `geneMutant` is statistically significant, which is backed by its small $p$-value.

### Maximum Likelihood (ML)

We saw that we can transform a logistic regression into a linear one, where we need to find the best fit line. The problem is that the logit function pushed the initial data to the infinite, thus we can't apply the least squares method (we can't calculate residuals). We use ML in this case.

We define a fit line candidate, we calculate the log values it generates.

![[logistic-regression-ml-fit-line-candidate.png|500]]

Then, we calculate the probability values of the log values:

$$
p = \frac{e^{log(odds)}}{1+e^{log(odds)}}
$$
This equation comes from the logit function.

Finally, we add the logs of probabilities of classifying a record to the correct group:

That gives us the likelihood of the given slope. The algorithm tries to find the highest likelihood value.

### McFadden Pseudo $R^2$

We can't use the known steps of calculating $R^2$ because of infinite data points.

For the mean, we take $log(number_{1st}/number_{2nd})$ which is $log(5/4)=0.22$ based on the ML example. We project all data to this constant line and get their probability values, like in the case of ML. Then we get the log likelihood of them and we use it as a substitute for $SS(mean)$. The log likelihood of the fitted line substitutes $SS(fit)$:

$$
R^2=\frac{LL(overall)-LL(fit)}{LL(overall)}
$$
### $p$-value

$$
2(LL(fit)-LL(overall))
$$
This gives us a $\chi^2$-value, where the degrees of freedom is the parameter numbers' difference between the two models, which is 1 in this case (the fitted line has intercept and slope, the mean is a constant).

Note: The equations of the metrics above are simplified for the logistic regression, they omit the saturated model value.

Related topics:
[[Log of odds]]
[[Saturated model]]

