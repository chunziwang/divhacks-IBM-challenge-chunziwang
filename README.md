
# Handwriting Digits - Easy or hard? An IBM DIV HACKS Project

----
## Problem to solve

Given the MNIST data and recognition results from 21 ML algorithms (a value of 1 means that the corresponding ML algorithm has correctly recognized the digit, and a value of 0 means that the corresponding ML algorithm did not recognize the digit correctly), the hyposis is: some handwriting digits are inherently easier to recognize than others – this can be indicated by how easily a digit can be correctly predicted by those 21 ML algorithms. If a digit can be easily recognized by most ML algorithms, it is probably safe to assume that the digit is easy to recognize. If a digit can NOT be recognized correctly by most ML algorithms, it is probably safe to assume that the digit is HARD to recognize.

The goal is to design a binary classifier for these handwriting digits so that we can correctly predict if a digit is easy or hard to recognize. 

![](https://github.com/chunziwang/divhacks-IBM-challenge-chunziwang/blob/master/figs/mnistExamples.png)

## Load in data

csv file of 21 ML algorithm recognition results and MINST data in ubyte form downloaded from online.

## Calculate prediction accuracy and labeling EASY and HARD

Summary of the proportion accurately predicted for each image:

![](https://github.com/chunziwang/divhacks-IBM-challenge-chunziwang/blob/master/figs/3.png)

Given that the median of both train and test set is 0.9048, I'll set the threshold to 0.9. A digit will get a "EASY" label if it has PC >= 0.9, otherwise "HARD".

## Among 0-9, find which digits are easier to predict than others

![](https://github.com/chunziwang/divhacks-IBM-challenge-chunziwang/blob/master/figs/1.png)

![](https://github.com/chunziwang/divhacks-IBM-challenge-chunziwang/blob/master/figs/2.png)

Every digit has about the same number of observations. ~ 6000.

+ It's noticed that 1 and 0 are the easiest to predict because the strokes of the digits are simple.
+ 6 and 7 are easy to predict as well from the simplicity of the digits.
+ 8, 5, 9, 2, 3, 4 are harder to predict given they are more complicated to write and machine may misinterpret them as something else.

## Binary Classifier using logistic regression and random forest

First step: change EASY and HARD label into binary. EASY -> 0, HARD -> 1.

Second step: seperating training and validation set for cross-validation.

Third step: calculating training and test accuracy using trained models.

Prediction results:

![](https://github.com/chunziwang/divhacks-IBM-challenge-chunziwang/blob/master/figs/accuracy_result.png)

I found that random forest has a higher prediction accuracy on test data but it takes a long time to train the model. Logistic regression model is much faster to train but the accuracy result is not as well.

By observing the confusion matrix of two models' prediction on test set, I found that the difference in accuracy mainly results from logistic regression's failure to predict HARD as HARD. Logistic Regression only accurately predicted 11.93% of HARD images as HARD and the number for Random Forest accurately is 38.09%. Turns out images labeled as EASY are much easier to classify then the ones labeled as HARD. I'll look at this finding more in detail. 

Random Forest test data confusion matrix:

![](https://github.com/chunziwang/divhacks-IBM-challenge-chunziwang/blob/master/figs/rf.png)

Logistic Regression test data confusion matrix:

![](https://github.com/chunziwang/divhacks-IBM-challenge-chunziwang/blob/master/figs/lr.png)






