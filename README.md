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

###To prepare the data for modeling, we have to do:
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

###Summary of Preprocessing Steps

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

