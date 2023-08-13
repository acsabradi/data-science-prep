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