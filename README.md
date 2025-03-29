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

![image](https://github.com/user-attachments/assets/7d1a7606-8152-426e-9b27-322883313c75)

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

![image](https://github.com/user-attachments/assets/f8956b5b-def6-4d1c-a335-2b4c5bbea84a)

![image](https://github.com/user-attachments/assets/3fffcbe1-d472-4367-bac0-032f5e3c19f7)

![image](https://github.com/user-attachments/assets/60a28989-6832-4fef-bc4e-83805cb56c20)

## Analysis and Insights

### Best Test Performance:
The Support Vector Machine (SVM) still delivers the highest test accuracy (88.73%), showing strong generalization. However, it has the longest training time by far (~15.9 seconds).

### Efficiency Winner:
K-Nearest Neighbors (KNN) trains almost instantly (~0.016s) and still performs very well (87.54% test accuracy). This makes it a great choice for quick, reliable classification.

### Decision Tree Observations:
While the Decision Tree had the highest training accuracy (90.88%), its drop in test accuracy (87.04%) suggests overfitting.

### Logistic Regression Underperformance:
Despite class balancing, Logistic Regression achieved the lowest test accuracy (61.51%).

### Final Recommendation:
For this dataset, SVM offers the best overall accuracy, though it's computationally expensive. KNN is the best trade-off between performance and speed. The Decision Tree is strong but may benefit from pruning or tuning. Logistic Regression underperforms.

## Improving the Model

1. If a gender feature were present, we would need to carefully evaluate whether to include it. While gender might contribute predictive value, such as bias or discrimination in the model's decisions.
2. Hyperparameter Tuning
   - Best parameters for KNN: {'n_neighbors': 18}
   - Best cross-validated accuracy: 0.8861566484517305
  
   - Best params for Decision Tree: {'max_depth': 3, 'min_samples_split': 2}
   - Best cross-val accuracy: 0.8873102610807528
  
  3. Adjusting the performance metric
     - KNN with f1 Score:
       -- Best parameters for KNN (F1): {'n_neighbors': 3}
       -- Best cross-validated F1 score: 0.13801727442463893

     - Decision Tree with f1 Score:
       -- Best parameters for Decision Tree (F1): {'max_depth': None, 'min_samples_split': 2}
       -- Best cross-validated F1 score: 0.12131858062114828

Using scoring='f1' in GridSearchCV allowed us to select hyperparameters that optimize the model’s ability to detect meaningful positive outcomes.

## Conclusion
In this project, I developed and compared several machine learning models to predict whether clients would subscribe to a term deposit based on marketing data. Starting with a logistic regression baseline, I explored more advanced models including K-Nearest Neighbors, Decision Trees, and Support Vector Machines. To address class imbalance, I used class weighting and evaluated performance using metrics such as F1-score and recall. Through feature exploration, metric adjustment, and hyperparameter tuning, I was able to improve model performance and gain a better understanding of the predictive patterns in the dataset.

