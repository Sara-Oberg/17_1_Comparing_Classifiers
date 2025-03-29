# 17_1_Comparing_Classifiers
This project explores and compares multiple machine learning classifiers to predict whether a client will subscribe to a term deposit based on data from a Portuguese banking institution's telemarketing campaigns.

# Understanding the Data
According to the information provided in the UCI Machine Learning Repository and the article "A Data-Driven Approach to Predict the Success of Bank Telemarketing" (Moro et al., 2014), the dataset contains data collected from 17 different marketing campaigns. These campaigns were conducted by a Portuguese banking institution over the period from May 2008 to November 2010. The purpose of these campaigns was to promote term deposit subscriptions through telemarketing calls.

After successfully loading the dataset into the df DataFrame, I examined the first few rows and confirmed that the data was read correctly. Each row represents a single telemarketing contact with a client, and each column corresponds to a specific feature, such as:

Client Information (e.g., age, job, marital status, education)
Contact Details (e.g., contact method, last contact month and day)
Campaign-related Info (e.g., number of contacts during the campaign)
Socioeconomic Context (e.g., employment variation rate, consumer confidence index)
Target Variable (y): whether the client subscribed to a term deposit
The dataset appears clean and well-structured, making it suitable for further preprocessing and modeling tasks.

# Business Objective:

The primary business objective is to predict whether a client will subscribe to a term deposit based on their personal, financial, and interaction data collected during previous telemarketing campaigns.
By analyzing past campaign data and client attributes, it can be aimed to build a model that can accurately classify potential clients into those who are likely to subscribe (yes) and those who are not (no). This will help the bank prioritize high-potential leads and enhance the effectiveness of future strategies.

![Encoded_Class_Distribution](https://github.com/user-attachments/assets/6302a274-d20e-4ed2-9691-874eaad187b0)
