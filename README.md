# sentiment-analysis


Briefing
The task is to predict whether the reviews of goods are positive or negative. 

Evaluation
Submissions are evaluated on area under the ROC curve between the predicted probability and the observed target.

Submission File
For each id in the test set, you must predict a probability for the target variable. The file should contain a header and have the following format:

Id,Probability
1,0.003
2,0.001
3,0.000
etc.

## Data description:

x_train.txt, x_test.txt – plain text reviews separated by \n.
y_train.csv – target, 1 for positive review and 0 for negative.
random_prediction.csv – a sample submission file in the required format (target is uniformly sampled).


## To download data: kaggle competitions download -c iad-deep-learning-sentiment

## Model and its specific:

Initially, data preprocessing was done: removing punctuation, converting to lower case. Pretrained embeddings from the GloVe model were used as embeddings. The neural network architecture is simple: only 2 Bidirectional layers and 1 Dropout. At the same time, the quality is very high: 0.9881.

The problem of solving this problem first became the problem of memory. With a closer look at the data, it was noticed that the main point of each review goes to ':' - the information before the colon in the review is like the main idea of ​​the review. Therefore, it was decided to truncate each review to ':'. This problem was on the kaggle-kernel and, accordingly, when the data decreased significantly, it disappeared. On google colab, there was no problem with RAM, so it was possible not to trim the data, but to train the model on a full dataset. That is why you can find 2 laptops in the repository: with and without a cropped dataset.
