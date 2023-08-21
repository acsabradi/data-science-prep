Task: Decide if an email is a spam or not

Steps:
1. Create word frequency histogram for spam and not-spam emails.
2. $p(\text{given word is present}|\text{email is not spam})=\frac{\text{\# of times the word appeared in the not spam emails}}{\text{total \# of words in all of the not spam emails}}$
3. Prior probability: $p(\text{not spam})=\frac{\text{\# not spam emails}}{\text{\# all emails}}$
4. Example sentence: $p(\text{not spam})p(\text{"Example"}|\text{not spam})p(\text{"sentence"}|\text{not spam}) \approx p(\text{not spam}|\text{"Example sentence"})$
5. Repeat step 2-4 for spam emails.
6. Higher score wins.

Calculation of step 4 can result in zero if a word is not in the training data of a group but it is at the other group. To work around this issue, 1 count is added to each columns in the histograms.

It is a naive algorithm because it doesn't take into account the structure of the language, it treats all words as independent from each other. It has a high bias but low variance because of this.

The same steps can be applied for normal distributions, too. By calculating the mean and standard deviance of the data vectors, we can define normal distributions for all of them. The conditional probabilities come from these distributions instead of histograms.