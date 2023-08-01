**Bias** is a type of error that occurs in a data science model because of using an algorithm that is not strong or complex enough to capture the underlying patterns or trends that exist in the data. In other words, this error occurs when the data is too complicated for the algorithm to understand, so it ends up building a model that makes simple assumptions. This leads to lower accuracy because of **underfitting**. Algorithms that can lead to high bias are linear regression, logistic regression, etc.

Model with high **variance** pays a lot of attention to training data and does not generalize on the data which it hasn’t seen before. As a result, such models perform very well on training data but has high error rates on test data, causing **overfitting**.

**Bias-variance tradeoff**:
In case of an underfitted model, we can lower the bias by increasing the complexity of the model (e.g. by introducing new parameters). But if the model is too complex, then the variance can be high while the bias is low. We need to find an optimum complexity where the amount of both type of errors are acceptable.

$$
TotalError = Bias^2 + Variance + IrreducibleError
$$
![[bias-variance-tradeoff.webp|500]]