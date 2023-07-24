# Pearson's chi square test - Goodness of fit

[Source](https://www.youtube.com/watch?v=2QeDRsxSF9M)

Restaurant owner gives us a distribution about the number of customers.
We want to check **how good the given distribution fits the observed data**.

|                                  | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday |
|----------------------------------|--------|---------|-----------|----------|--------|----------|
| Given amount of customers (%) | 10     | 10      | 15        | 20       | 30     | 15       |
| Observed number of customers     | 30     | 14      | 34        | 45       | 57     | 20       |

$H_0$: Given distribution is correct.
$H_1$: Given distribution is not correct.
Significance level: $\alpha = 0.05 = 5\%$

Getting such or more extreme results is less likely than 5%? If yes then we reject $H_0$.

Assuming that $H_0$ is correct, what result should have we observed?

Total number of customers during the week is 200, thus expected number of customers on Monday is 20:

|                                        | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday |
|----------------------------------------|--------|---------|-----------|----------|--------|----------|
| Given amount of customers (%)       | 10     | 10      | 15        | 20       | 30     | 15       |
| Observed number of customers           | 30     | 14      | 34        | 45       | 57     | 20       |
| Expected amount of costumer (based on $H_0$) | 20     | 20        | 30          | 40         | 60       | 30         |

$$
\chi^2=\sum_{i}\frac{(Expected_i-Observed_i)^2}{Observed_i}=\frac{(30-20)^2}{20}+...=11.44
$$
Degree of freedom: Number of observed data points - 1 = 5

![[chi-square-table.pdf]]

The critical $\chi^2$ value is 11.07, our result is more extreme than this, we reject $H_0$.

# Contingency table chi-square test

[Source](https://www.youtube.com/watch?v=hpWdDmgsIRE)

ToDo