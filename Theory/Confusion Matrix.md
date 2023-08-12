Confusion Matrix is used to evaluate the performance of machine learning models with discrete outputs.

|                                 | Actually has heart disease | Actually doesn't have heart disease |
|---------------------------------|----------------------------|-------------------------------------|
| **Predicted: heart disease**    | 142                         | 22                                  |
| **Predicted: no heart disease** | 29                       | 110                                |

The columns represent the known facts, the rows represent the output of a trained model.

The size of the matrix is $n * n$ where $n$ is the number of possible outcomes.

**Sensitivity or recall or true-positive rate**: 
true positives / (true positives + false negatives) $= \frac{142}{142+29}=0.83$
83% of the people with heart disease was correctly identified by the model.

**Specificity**:
true negatives / (true negatives + false positives) $=\frac{110}{110+22}=0.83$
83% of the people without heart disease was correctly identified by the model.

If correctly identifying people with disease is more important, then we choose a model with higher sensitivity. If correctly identifying healthy people is more important, then we choose a model with higher specificity.