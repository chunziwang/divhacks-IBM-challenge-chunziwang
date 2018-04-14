
# Handwriting Digits - Easy or hard? An IBM DIV HACKS Project

----

## Load in data

csv file and ubyte data downloaded online.

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

![](https://github.com/chunziwang/whole-foods-market-basket-analysis/blob/master/figs/19.jpg)






