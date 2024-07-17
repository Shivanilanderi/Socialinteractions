# Speed-Dating-ML

## Introduction
For this machine learning project, we chose a speed date experiment dataset. The
experiment was originally conducted from 2002 to 2004 where each participant was asked a
series of questions and was matched up to other participants for quick dates. The result of the
speed dating including the participants’ impression towards each other and the number of
call-backs was also recorded. We are interested in exploring this dataset by using machine
learning techniques to predict whether a subject is likely to get callbacks from speed dating, as
well as finding out whether a predefined standard of the opposite sex has an impact on the
subject getting callbacks from speed dating.

We chose two particular questions asked before the participants were sent their matches.
The questions are “How do you think you measure in terms of traits?” and “How do you think
others perceive you?”. Each question is broken down to five traits: attractiveness, sincerity,
intelligence, fun and ambition. The participants were asked to give a number between 0 to 10
inclusive for each trait to answer the question. The subjects were also asked the question, “What
do you look for in the opposite sex in terms of traits,” and we used the answers to this question
and constructed an average for each five trait for male and female as the predefined “standard”
within sample size. The output value returns one if the participant gets any callback at all and
zero otherwise. We choose to approach this problem as a binary classification problem, and we
select logistic regression, SVM, and neural network as our three models for the problem.

## Logistic Regression Models
For the logistic regression model, we chose to evaluate the model with L1 Lasso
regularization and L2 Ridge regularization, and we repeated the same regularizations but with
polynomial-transformed input variables. We experimented with the different ‘C’ values in order
to find the most optimal strength of regularization, and we used the model on both an input
variable without the weight of the opposite sex standard, as well as an input variable with the
weight of the opposite sex standard in order to see whether there is a difference in accuracy in
the predictions. For the training and test data set, we divided the original data using the default
train_test_split, and achieved a ratio of 75:25.

Experiment:
- C = [0.0001, 0.001, 0.01, 0.1, 1, 10, 100]

Regularizations:
- L1 (Lasso)
- L2 (Ridge)
- L1 (Lasso Poly-transformed)
- L2 (Ridge Poly-transformed)
- SVM (RBF Kernel)
- SVM (Polynomial Kernel)

## Neural Network Model
For the neural network model, we chose binary cross entropy as loss functions and used
7-fold validation to test the quality of our model. We experimented with different values with
some hyperparameters while keepings some constant. The different variables are shown below,
where experimented variables are presented in arrays of values we experimented with.

Constants:
- Learning rate = 0.01
- Epoch = 20
- Batch = 1

Experiments:
- Activation function = [‘sigmoid’, ‘tanh’, ‘relu’]
- Hidden layer number = [0, 5, 10]
- Optimizer = [‘SGD’, ‘Adam‘, ‘Nadam’]
- Dropout rate = [0, 0.2, 0.5]
- Lasso lambda = [0, 0.001, 0.1]
- Ridge lambda = [0, 0.001, 0.1]

For the training set and validation set, we divided the original data set in 7 to 3 ratio. 

## Conclusion
In conclusion, both the logistic regression model and the SVM model were successful in
training and predicting the data, with the SVM model using RBF kernel achieving the maximum
accuracy on test data of 0.71, while the neural network model failed to train and predict the data
set. With regards to the context of the experiment, we concluded that the parameters used to
answer the questions, “how do you think you measure in terms of traits?” and “how do you think
others perceive you?” is effective in training and predicting the data set, thus it can be implied
that the five attributes can be reasonably used to predict whether the subject will get callbacks
from speed dating. We also concluded that there is no predefined standard in terms of the five
traits discussed above, and even if there exists such standard, it has no impact over the outcome
of the subject getting a callback or not due to most models achieving same accuracy on training
and test data with and without standardized variables. However, there are many problems that
can be raised regarding this project. First of all, the sample size is rather small in standard
machine learning training. The second concern is that the discrete numerical values given in this
experiment can contain noise caused by each subject’s different interpretation of the
meaningfulness of each numerical values. The third concern is that it is difficult to interpret the
output value being chosen. A value of 1 simply indicates that the subject has gotten a callback
from the match, it carries over no information regarding the number of dates had by the subject
and therefore cannot directly imply the general desirability of the subject.
