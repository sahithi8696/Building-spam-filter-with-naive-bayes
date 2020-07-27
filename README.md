# Building-spam-filter-with-naive-bayes

In this project, we study the practical side of Naive Bayes algorithm by building a spam filter for SMS messages.

Our first task is to teach the computer how to classify messages. To do this, we'll use the multinomial Naive Bayes algorithm along with a dataset of 5,572 SMS messages that are already classified by humans.

## Data
The dataset used in this project can be downloaded directly from [this link](https://archive.ics.uci.edu/ml/datasets/sms+spam+collection).

For this project, our goal is to create a spam filter that classifies new messages with an accuracy greater than 80%.

Hence, once we build our spam filter, we'll need to test how good it is with classifying new messages. To test the spam filter, we are first going to split our dataset into two categories:

- A training set, which we'll use to "train" the computer on how to classify messages
- A test set, which we'll use to test how well the spam filter works in classifying new messages
We are going to keep 80% of our dataset for training, and 20% for testing (we want to train the algorithm on as much data as possible, but we also want to have enough test data).

### Data cleaning

When a new message comes in, the Naive Bayes algorithm will make the classification based on the computed probabilities.

To calculate all these probabilities, we'll first need to perform a bit of data cleaning to bring the data in a format that will allow us to extract easily all the information we need. To make the calculations easier, we want bring the data to the following format:

|   | Label | secret | prize | claim | now | coming | to | my| party | winner|
| --- | --- | ------ | ------ | ----- | ---- | ---- | ---- | ---- | ----- | ----- |
| 0  | spam  | 2 | 2 | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| 1  | ham  | 1 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 |

After cleaning the dataset, we perform the following steps:

- create a vocabulary for the messages in the training dataset. The vocabulary is a Python list containing all the unique words across all messages
- use the vocabulary to make the data transformation we need.
- create the spam filter 
  * compute the constants P(Spam) and P(Ham), N<sub>Spam</sub>, N<sub>Ham</sub>, N<sub>Vocabulary</sub> whicih have the same value for every new message
  * compute the parameters P(wi|Spam) and P(wi|Ham) which vary depending on the word, but the probability for each individual word is constant for every new message.
  * After we've calculated all the constants and parameters we need, we create the spam filter.
  * Finally, we measure the spam filter's accuracy by using the test data
