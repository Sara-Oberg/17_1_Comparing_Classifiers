# Assignment 17.1 Comparing Classifiers
This project explores and compares multiple machine learning classifiers to predict whether a client will subscribe to a term deposit based on data from a Portuguese banking institution's telemarketing campaigns.

## Understanding the Data
According to the information provided in the UCI Machine Learning Repository and the article "A Data-Driven Approach to Predict the Success of Bank Telemarketing" (Moro et al., 2014), the dataset contains data collected from 17 different marketing campaigns. These campaigns were conducted by a Portuguese banking institution over the period from May 2008 to November 2010. The purpose of these campaigns was to promote term deposit subscriptions through telemarketing calls.

After successfully loading the dataset into the df DataFrame, I examined the first few rows and confirmed that the data was read correctly. Each row represents a single telemarketing contact with a client, and each column corresponds to a specific feature, such as:

Client Information (e.g., age, job, marital status, education)
Contact Details (e.g., contact method, last contact month and day)
Campaign-related Info (e.g., number of contacts during the campaign)
Socioeconomic Context (e.g., employment variation rate, consumer confidence index)
Target Variable (y): whether the client subscribed to a term deposit
The dataset appears clean and well-structured, making it suitable for further preprocessing and modeling tasks.

## Business Objective:

The primary business objective is to predict whether a client will subscribe to a term deposit based on their personal, financial, and interaction data collected during previous telemarketing campaigns.
By analyzing past campaign data and client attributes, it can be aimed to build a model that can accurately classify potential clients into those who are likely to subscribe (yes) and those who are not (no). This will help the bank prioritize high-potential leads and enhance the effectiveness of future strategies.

## Engineering Features

### To prepare the data for modeling, we have to do:
- Selecting relevant features
- Encoding categorical variables
- Separating features and the target column

For this task, the bank client information features will be used.
Based on the description, the bank-related features are:
- age (numeric)
- job (categorical)
- marital (categorical)
- education (categorical)
- default (categorical)
- housing (categorical)
- loan (categorical)
Target:
- y (binary: 'yes' or 'no')

### Summary of Preprocessing Steps

- Data Loading
- Checked for Missing Values
- Removed Duplicates
- Handled 'unknown' Values in Categorical Columns
- Selected Bank Client Features
- age, job, marital, education, default, housing, loan
- Encoded Categorical Variables
- Encoded the target variable y, converting:
-- 'no' -> 0
-- 'yes' -> 1

Counted the values of the target variable:
No (0): 36537 clients
Yes (1): 4639 clients

![Encoded_Class_Distribution](https://github.com/user-attachments/assets/6302a274-d20e-4ed2-9691-874eaad187b0)

## Train/Test Split

To evaluate our models effectively, I split the data into two sets:
- Training set: used to train the model
- Test set: used to evaluate the model’s performance on unseen data

It was used 80% for training and 20% for testing, which is a common practice.
- test_size=0.2: 20% of the data will go to the test set.
- random_state=42: Ensures reproducibility
- stratify=y: Ensures the class distribution is preserved in both training and test sets

The results are:
- Training set shape: (32940, 22) (32940,)
- Test set shape: (8236, 22) (8236,)

## A Baseline Model

In a classification problem, a common baseline is the accuracy of always predicting the most frequent class.
From earlier, we saw the class distribution in the target variable y:
- 0 (no) -> 36537 samples
- 1 (yes) -> 4639 samples
baseline_accuracy = 36537 / (36537 + 4639) = 0.8873

## A Simple Model
Logistic Regression has been used to build a basic model on the data.
The results are as follows:
- Logistic Regression Accuracy: 0.6151
- Classification Report:
              precision    recall  f1-score   support

           0       0.92      0.62      0.74      7308
           1       0.16      0.56      0.25       928

    accuracy                           0.62      8236
   macro avg       0.54      0.59      0.49      8236
weighted avg       0.83      0.62      0.69      8236

- Confusion Matrix:
[[4550 2758]
 [ 412  516]]

## Score the Model

Logistic Regression Accuracy is: 0.6151

## Model Comparisons

I trained and evaluated multiple models and compare the following properties:

- Training time
- Training accuracy
- Test accuracy

for the following models:

1. Logistic Regression
2. K-Nearest Neighbors (KNN)
3. Decision Tree
4. Support Vector Machine (SVM)
