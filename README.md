Credit Card Fraud Detection
===========================

This is my project in the Machine Learning course at university.

*To get the detailed report, read the pdf or ipynb file in this branch.*

Table of Contents
=================

1.  [General](#General)

2.  [Dataset](#Dataset)

3.  [Source Code](#Source-Code)

4.  [Result](#Result)

General
-------

In today's developing society, we are trending towards a cashless society.
According to World Payments Report, in 2016, there is a 10.1% increase in total
non-cash transaction in comparision to the previous year. However, along with
moving away from paying in cash, comes a huge problem: **Credit card fraud**.
Even with EMV smart chips, we still suffered massive loss due to credit card
fraud. Our project will try and build a model to prevent this crime and
therefore limit the loss.

[Dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud)
---------------------------------------------------------

### Kaggle dataset

The garthered dataset from Kaggle dataset contains 284,807 rows of data and 31
columns. Out of all the columns, the only ones that made the most sense were
Time, Amount, and Class (fraud or not fraud). The other 28 columns were
transformed using what seems to be a PCA dimensionality reduction in order to
protect user identities.

-   Time: Number of seconds elapsed between this transaction and the first
    transaction in the dataset.

-   V1 - V28: Result of a PCA Dimensionality reduction to protect user
    identities and sensitive features

-   Amount: Transaction amount

-   Class: 1 for fraudulent transactions, 0 otherwise

The data itself is short in terms of time (it’s only 2 days long), and these
transactions were made by European cardholders.

The datatype of Class attribute is int64, while datatype of other attributes are
float64.

### Exploratory data analysis

**Time Distribution**

Given that this distribution s two day's worth of data, it can be clearly seen
that most purchases are made during the daylight hours. The purchasing dwindles
down until the next day.

**Amount Distribution**

Most daily transactions aren’t extremely expensive (most are \< \$50), but it’s
likely where most fraudulent transactions are occurring as well.

**Class**

There were **492 fraud transactions of 284,807 transactions**, accounting for
**0.173%**. So this project's goal is detect fraudster as much as possible.

Amount of fraud transactions accounts for **0.24%** of total amount. However,
**nearly 60,128 dollars** is not a smalle value.

Source Code
-----------

### Choose attributes for training

We choose the columns based on correlation values. In this model, 10 chosen
columns are Class, V17, V14, V12, V10, V16, V3, V7, V11, V4.

Deviding dataset into 2 paths, namedly break and test. With break dataset, we
devided into 2 path is train and validation. The range of each attribute is
difference, so we using z-score to normalize the data.

### Training models

In this project, we use the Logistic Regression and Naive Bayes models.
Moreover, with each model, we find the best threshold to predict the label for
testing data (because the dataset is heavily imbalant). The default threshold is
0.5.

Result
------

Accuracy of logistic regression model: 0.9393981952880868

Accuracy of Naive Bayes model: 0.9841999929777746
