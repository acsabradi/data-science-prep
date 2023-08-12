**Null Model**: The simplest one parameter model, suppose a normal distribution with a mean equal to the mean of the data points.

**Proposed Model**: The model we want to use and test. It should be more complex than the Null Model, suppose it contains 2 overlapping normal distribution fitted to the data.

**Saturated Model**: It fits normal distributions to each data point, the means are equal to the corresponding data values. This model represents the maximum likelihood value that can be achieved.

![[saturated-model.png|500]]

$$
R^2=\frac{LL(Null)-LL(Proposed)}{LL(Null)-LL(Saturated)}
$$
Without the scaling factor of $LL(Saturated)$ the $R^2$ value could be higher than 1.

==**Residual Deviance**==: $2*(LL(Saturated)-LL(Proposed))$ which gives us a $\chi^2$-value with degree of freedom equal to the difference in the number of parameters.

==**Null Deviance**==: $2*(LL(Saturated)-LL(Null))$ which gives us a $\chi^2$-value with degree of freedom equal to the difference in the number of parameters.

> [!tip] Likelihood ratio test (LRT)
> $p$-value of the log-likelihood $R^2$ is: Null Deviance - Residual Deviance
>Simpler version: $2*(LL(Proposed)-LL(Null))$

The logistic regression omits the saturated model because it would mean the best fit line going through all the data:

![[saturated-model-logistic-regression-example.png|500]]
The log-likelihood of such line would be zero.