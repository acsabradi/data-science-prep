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

Related topics:
[[Log of odds]]

