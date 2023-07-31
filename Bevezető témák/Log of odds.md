$$
\frac{probability}{1-probability}=odds
$$
The odds of something not happening can go from 0 to 1, and the odds of something happening from 1 to infinity. That's very unsymmetrical. 

We calculate the log of odds to make the possible values symmetrical.

$$
1/6=0.17 \rightarrow 6/1=6
$$
$$
log(1/6)=-1.79 \rightarrow log(6/1)=1.79
$$
**Logit function**:
$$
log(odds)=log(\frac{p}{1-p})
$$
**Odds ratio example:**

|                           | Has Cancer: Yes | No  |
|---------------------------|-----------------|-----|
| **Has mutated gene: Yes** | 23              | 117 |
| **No**                    | 6               | 210 |

$$
\frac{23/117}{6/210}=6.88 \rightarrow log(6.88)=1.93
$$
The odds are 6.88 times greater that someone with the mutated gene will also have cancer.

Odds ratio is similar to $R^2$ because both metric describes relationship. The higher the value, the stronger the examined relationship is.

Similar to $R^2$, we want to know if the odds ratio is statistically significant.

### [[Chi square test]]

$H_0$: Mutated gene doesn't have any effect on having cancer.

**Expected values:**

|                           | Has Cancer: Yes | No  |
|---------------------------|-----------------|-----|
| **Has mutated gene: Yes** | 11.2              | 128.8 |
| **No**                    | 17.3               | 198.7 |

### Wald test

The Wald test takes advantage of the fact that the log of the odd ratios are zero centered normally distributed.

Standard deviation: $\sqrt{\sum_i 1/observation_i}=0.47$  

$$
\frac{23/117}{6/210}=6.88 \rightarrow log(6.88)=1.93 \rightarrow 1.93/0.47=4.11
$$
The log of the odd ratios is 4.11 standard deviations away from the mean of the distribution.

The rule of thumb for normal distributions is that anything further than 2 standard deviations from the mean will have a $p$-value less than 0.05, so we know that the calculated log value is statistically significant.