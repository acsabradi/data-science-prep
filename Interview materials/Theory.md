# Topics

- Stats
	- Expectation
	- [[Principle Component Analysis (PCA)#^eee9be|Variance]]
	- [[Principle Component Analysis (PCA)#^a25bc2|Covariance]]
	- Correlation
- Random variables
	- Uniform
	- [[Logistic Regression#^b892dc|Bernoulli]]
	- [[Logistic Regression#^b62f00|Binomial]]
	- Geometric
	- Poisson
	- [[#Normal distribution|Normal]]
	- $\chi^2$
- [[#You picked a coin. What's the chance of the coin being biased (both sides are tails) if all 5 flips were tails?|Bayes Theorem]]
- Joint Distribution

## Standard deviation

$$
\sqrt{\frac{1}{n}\sum_{i=1}^N (x_i-x_{mean})^2}
$$
Allows variance to be interpretable by scaling.

## Pearson Correlation

$$
\frac{\sum_{i=1}^N(x_i-x_{mean})(y_i-y_{mean})}{\sigma_X\sigma_Y}
$$
$$
\sigma:\text{Standard deviation}
$$
Describes the strength of a linearity between 2 variables.

## Handling outliers

Outliers deflate or inflate the correlation.

### Inter-Quartile Range (IQR) Method

Suppose that the dataset is ordered.

- Median is Q2.
- Q1 is the 1st quartile: 25% of the data lies between minimum and Q1.
- Q3 is the 3rd quartile: 75% of the data lies between minimum and Q3
- IQR = Q3-Q1
- Decision range:
	- (Q1 - 1.5 IQR, Q3 + 1.5 IQR)
	- Any data outside this is considered as outlier

### Robust data scaling

It's a common practice to scale the data using this formula: $x_{scaled}=\frac{x-x_{mean}}{\sigma_X}$. Outliers can skew a probability distribution, so the calculated mean and standard deviation are skewed, too.

The solution is the robust data scaling with the help of the IQR method:
$$
x_{scaled}=\frac{x-Q_2}{IQR}
$$
## Normal distribution

Probability Density Function:
$$
f(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}
$$
![[normal-distribution-rule-of-thumb.png|500]]
## Central Limit Theorem (CLT)

Distribution of sample means approximates a normal distribution regardless of the population distribution.

## Hypothesis Testing

PM says that on average customers spend 50$ per month. You sample 100 customers and the sample mean is 85$. Can you reject the PMs claim? 

>[!tip] Definition
>Hypothesis testing is a way to test an assumption about a population parameter.

Steps:
1. Hypothesis: State the null ($H_0$) and the alternative hypothesis ($H_a$).
2. Sample data: Take sample.
3. Statistical test: Calculate $p$-value $\rightarrow$ the probability of observing a sample value or a more extreme value given that $H_0$ is assumed to be true.
4. Statistical decision: If $p$-value is less than the significance level ($\alpha$), we reject $H_0$, we fail to reject otherwise.

We calculate the z-statistics which scales the sample mean to a standard normal distribution ($\sim N(0,1)$):
$$
z=\frac{X_{mean}-\mu}{\frac{\sigma}{\sqrt{n}}}
$$
$\alpha$ is the probability of rejecting $H_0$ assumed to be true. It is usually set to 0.05.

We assume that the population standard deviation is 20.

$H_0$: average spend per user is 50$
$H_a$: average spend per user is greater than $50

$$
z=\frac{85-50}{\frac{20}{\sqrt{100}}}=17.5
$$

We need a [z-table](https://www.z-table.com/) to calculate the $p$-value. The highest z-value is 3.49 and it has 0.9998 under the curve area. So the probability of getting 3.49 or higher is 0.0002. Considering that 17.5 is higher than 3.49, we can assume that it has an even smaller $p$-value:
$$
\text{p-value of 17.5} <0.0002<\alpha
$$
As the $p$-value of 17.5 is smaller then the significance level, we can reject $H_0$.

---
# What is the $\beta$ coefficient of a multi-variant regression? How do you derive it? How do you derive it in a non-closed form?

>[!note]
>Start the explanation from the ground up: What is a simple linear regression? What is the $\beta$ coefficient there? What is a multivariate regression? What are the $\beta$ coefficients in that case?

==Least squares closed form==:
$$
L(Data,\beta)=||Y-X\beta||^2=(Y-X\beta)^T(Y-X\beta)=
$$
$$
=
Y^TY-Y^TX\beta-\beta^TX^TY+\beta^TX^TX\beta
$$
$$
\frac{\partial L(Data,\beta)}{\partial \beta}=-2X^TY+2X^TX\beta=0
$$
>[!note]
>$Y^TX\beta=\beta^TX^TY$

$$
X^TY=X^TX\beta
$$
$$
\beta=(X^TX)^{-1}X^TY
$$
==Non-closed form==:
[Maximum Likelihood Estimation](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote08.html)

# Suppose that the target variable is zero-inflated. How would you build your model?

- Are the target variables censored? Are the values valid?
- The values are valid, 80% of target data is zero.
- Use ==tobit model==. It is used when the dependent variable is continuous but bounded at one end (e.g. wage information - it's bounded at the minimum because of minimum wage)
- As a sanity check treat the target as binary: zero and everything else.

# Explain the confidence interval of the logistic regression

- 95% confidence interval: 95% of the time the actual coefficient will fall into the estimated confidence interval $\rightarrow [\mu-2\sigma, \mu+2\sigma]$ **-> ToDo**
- It represents our uncertainty around the variable.
- What if the confidence interval includes zero in the log-odds domain?
	- The coefficient is not statistically distinguishable from zero.
	- If a hypothesis testing would be performed then the null hypothesis (output is dependent on input - its coefficient is not zero) wouldn't be rejected
- What if the confidence interval includes one in the odds ratio domain?
	- Same question as before because $OR=e^\beta$, so odds ratio is one if the coefficient is zero.
	- In this case, OR is not statistically distinguishable from one.

# You picked a coin. What's the chance of the coin being biased (both sides are tails) if all 5 flips were tails?

==Bayes Theorem==:
$$
P(\text{Biased}|\text{5 Tails})=
\frac{P(\text{5 Tails}|\text{Biased})P(\text{Biased})}
{P(\text{5 Tails})}
$$
Suppose that $P(\text{Biased})=0.5$. If a biased coin is chosen then:
$$
P(\text{5 Tails}|\text{Biased})=1.0
$$
Using ==Law of Total Probability== to calculate:
$$
P(\text{5 Tails})=P(\text{5 Tails}|\text{Fair})P(\text{Fair})+
P(\text{5 Tails}|\text{Biased})P(\text{Biased})
$$
We need to calculate $P(\text{5 Tails}|\text{Fair})$ using Binomial Probability:
$$
P(\text{5 Tails}|\text{Fair})=
\frac{5!}{5!0!} 0.5^5 0.5^0
$$