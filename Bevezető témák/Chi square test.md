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

> [!note]
> The degree of freedom is the number of observed data points minus 1 because if we would know a statistical metric (e.g. mean) of the data, then the last data point could be deduced using the other data points and the metric.

![[chi-square-table.pdf]]

The critical $\chi^2$ value is 11.07, our result is more extreme than this, we reject $H_0$.

# Contingency table chi-square test

[Source](https://www.youtube.com/watch?v=hpWdDmgsIRE)

Drug test result (contingency table):

|                | Drug 1 | Drug 2 | Placebo | Total |
|----------------|--------|--------|---------|-------|
| **# sick**     | 20     | 30     | 30      | 80    |
| **# not sick** | 100    | 110    | 90      | 300   |
| **Total**      | 120    | 140    | 120     | 380   |

$H_0$: The drugs do nothing.
$H_1$: The drugs do something.
$\alpha=0.1=10\%$

|                | Drug 1 | Drug 2 | Placebo | Total |
|----------------|--------|--------|---------|-------|
| **# sick**     | 20     | 30     | 30      | 80    |
| **Expected**   | 25.3   | 29.4   | 25.3    | 21%   |
| **# not sick** | 100    | 110    | 90      | 300   |
| **Expected**   | 94.7   | 110.6  | 94.7    | 79%   |
| **Total**      | 120    | 140    | 120     | 380   |

We assume that $H_0$ is true, so we take the whole population (380) and calculate how many of them was sick or not (21% and 79%). Based on this we calculate the expected values of each test group.

We get the $\chi^2$ the same way as before:
$$
\chi^2=\sum_{i}\frac{(Expected_i-Observed_i)^2}{Observed_i}=\frac{(25.3-20)^2}{20}+...=2.528
$$

Degree of freedom: (number of rows - 1) * (number of columns - 1) = 2

The table above shows that the critical $\chi^2$ value is 4.6, our value is less extreme, thus we can't reject $H_0$.