We want to train a model. The best practice is to divide the set of labelled data into equal parts and use one part for testing and the others for training.

If the data is divided into $k$ parts, then we call it **$k$-fold cross validation**.

To avoid figuring out which parts are best for testing and training, cross validation tests all parts in both role (one part for testing, $k-1$ part for training) and selects the setup which ended up with the best results.

We can choose a setup where each parts contain a single data. This is called **Leave One Out Cross Validation**.

In practice, the 10-Fold Cross Validation is the most common.

Grid Search Cross Validation expands the basic cross validation with the evaluation of a range of possible hyperparameter (e.g. $\lambda$ of regularization) values. It is a brute force method thus computationally expensive.
