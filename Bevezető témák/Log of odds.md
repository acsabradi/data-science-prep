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

**Wald test**



