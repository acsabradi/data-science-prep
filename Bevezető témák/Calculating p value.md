Suppose we have a coin, we flip it 5 times and there are 4 heads and 1 tail. We want to check if the coin is special.

We form a **null hypothesis**:

> [!tip] Although we flipped the coin 5 times and we got 4 heads and 1 tail, the coin is not special.

The null hypothesis has to focus on the normal coin (= known behavior).

If the calculated $p$-value is less than a given threshold (which is usually 0.05), then the null hypothesis is rejected and we can conclude that the coin is special.

First we have to count how many possible coin flip possibility is there after 5 flips:

- There is 0 tail out of 5 flips: $5 \choose 0$ = 1
- There is 1 tail out of 5 flips: $5 \choose 1$ = 5
- There are 2 tails out of 5 flips: $5 \choose 2$ = 10
- There are 3 tails out of 5 flips: $5 \choose 3$ = 10
- There are 4 tails out of 5 flips: $5 \choose 4$ = 5
- There are 5 tails out of 5 flips: $5 \choose 5$ = 1

We used combination because the order of the heads and tails doesn't matter in this situation.

$p$-value equals to the sum of:
+ probability of the tested result $\to {5 \choose 1}/2^5$
+ sum probability of any other possible outcome with the same possibility as the tested result $\to {5 \choose 4}/2^5$
+ sum probability of any other possible outcome with less possibility than the tested result's possibility $\to {5 \choose 0}/2^5 + {5 \choose 5}/2^5$

The result is 0.375. It is bigger than the threshold, so we failed to reject the null hypothesis. We need more flips if we want to go below the threshold.

**2 sided $p$-value**

In case of continuous data, we calculate $p$-value by calculating the area under a statistical distribution.

![[p-value-normal-distribution.png|500]]

Suppose we measure someone 142 cm tall and we want to know if the known distribution is correct or there is another distribution that explains the data better (e.g. a normal distribution with mean of 142).

Null hypothesis: The measured 142 cm is not special and it comes from the known distribution.

$p$-value is $2 * 0.025$, because we count the area of 142 cm and smaller plus 169 cm and taller. The tails of the distribution is 0.025 by definition. The result is 0.05 so the test is inconclusive which is expected because 142 cm is a borderline value.

$p$-value of 141 cm is 0.03, thus the null hypothesis is rejected, we can say that the measured value is special and maybe another distribution would be a better fit.

**1 sided $p$-value**

Suppose we have a distribution of an illness recovery time which is a normal distribution with mean of 10 days with 95% probability that the recovery time is between 5 and 15 days.

We tested a new drug and the result is that the average recovery time is 4.5 days if the drug is taken. We want to test if this is a special measurement -> Did the drug work?

In this case we are only interested in the area of 4.5 and smaller, because that's the direction we want to go to. If we utilized the 2 sided calculation, it's possible that the result would be above threshold thus the measurement would be unnoticed.

This calculation should be used with care because it can distort the result.