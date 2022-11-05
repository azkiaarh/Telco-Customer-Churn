# Use Case
#### Use Case Summary
#### Objective Statement:
* To find out how many customers are churn and non-churn 
* To gain insight on churn and non-churn customers based on customers demographic info such as gender, senior citizen, partner, and dependents.
* To gain insight on churn and non-churn customers based on customer services booked  such as phone service multiple lines, internet service, online security, online backup, device protection, tech support, streaming TV and streaming movies.
* To gain insight on churn and non-churn customers based on customer account information such as paperless billing, payment method, and contract.
* To gain insight into whether there is a relationship between monthly charges, total charges, and tenure on churn rate.
* Predict churn using machine learning logistic regression. 

#### Challenges:
* Large size of data, can not be maintained by excel nor spreadsheet.
* Dataset have a lot of missing values.
* Dataset have different data types.

#### Methodology / Analytic Technique:
* Exploratory analysis (Graph Analysis)
* Descriptive Statistics
* Classification model
* Statistical Analysis

#### Business Benefit:
* Know how to treat customers with specific criteria.
* Increase business income.

#### Expected Outcome:
* Know how many customers are churn and non-churn 
* Know insight on churn and non-churn customers based on customers demographic info such as gender, senior citizen, partner, and dependents.
* Know insight on churn and non-churn customers based on customer services booked  such as phone service multiple lines, internet service, online security, online backup, device protection, tech support, streaming TV and streaming movies.
* Know insight on churn and non-churn customers based on customer account information such as paperless billing, payment method, and contract.
* Know pattern between tenure, monthly charges, and total charges on customer behavior.
* Predict churn using machine learning logistic regression. 



# Business Understanding
* A telephone company, also known as a telco, telephone service provider, or telecommunications operator, is a kind of communications service provider, more precisely a telecommunications service provider, that provides telecommunications services such as telephony and data communications access.
* Churn rate is the rate at which customers stop doing business with a company over a given period of time.

This case requires data-driven answers to the following questions:
* How many customers are churn and non-churn?
* What's the insight on churn and non-churn customers based on customers demographic info such as gender, senior citizen, partner, and dependents?
* What's the insight on churn and non-churn customers based on customer services booked  such as phone service multiple lines, internet service, online security, online backup, device protection, tech support, streaming TV and streaming movies?
* What's the insight on churn and non-churn customers based on customer account information such as paperless billing, payment method, and contract?
* What's the insight into whether there is a relationship between monthly charges, total charges, and tenure on churn rate?



# Data Understanding
#### Data Source
* Data of customer retention programs.
* The dataset has 21 columns and 7043 rows.
* Source Data: Telco Customer Churn by International Business Machines Corporations (IBM) Sample Data Set.
    https://www.kaggle.com/datasets/blastchar/telco-customer-churn

#### Data Dictionary
Classification labels
* Churn — Whether the customer churned or not (Yes or No)

Customer services booked
* PhoneService — Whether the customer has a phone service (Yes, No)
* MultipleLines — Whether the customer has multiple lines (Yes, No, No phone service)
* InternetService — Customer’s internet service provider (DSL, Fiber optic, No)
* OnlineSecurity — Whether the customer has online security (Yes, No, No internet service)
* OnlineBackup — Whether the customer has online backup (Yes, No, No internet service)
* DeviceProtection — Whether the customer has device protection (Yes, No, No internet service)
* TechSupport — Whether the customer has tech support (Yes, No, No internet service)
* StreamingTV — Whether the customer has streaming TV (Yes, No, No internet service)
* StreamingMovies — Whether the customer has streaming movies (Yes, No, No internet service)

Customer account information
* Tenure — Number of months the customer has stayed with the company
* Contract — The contract term of the customer (Month-to-month, One year, Two year)
* PaperlessBilling — Whether the customer has paperless billing (Yes, No)
* PaymentMethod — The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
* MonthlyCharges — The amount charged to the customer monthly
* TotalCharges — The total amount charged to the customer

Customers demographic info
* customerID — Customer ID
* Gender — Whether the customer is a male or a female
* SeniorCitizen — Whether the customer is a senior citizen or not (1, 0)
* Partner — Whether the customer has a partner or not (Yes, No)
* Dependents — Whether the customer has dependents or not (Yes, No)

# Data Preparation
Code Used :
* Python Version : !python -V (Python 3.8.8)
* Packages : Pandas, Numpy, Matplotlib, Seaborn, SKlearn, Warnings

# Data Cleansing
* There are 12 columns with each missing 14.3% of its data. We need to fill it so we don't have to lose a lot of data. Missing data that are categorical is filled with "unknown".
* The TotalCharges column has a numeric data type so it is adjusted to float.
* The SeniorCitizen column has a float data type so it is adjusted to be categorical (integer) and and the missing data from the table is filled with the median value.

# Exploratory Data Analysis

- How many customers are churn and non-churn?

![image](https://user-images.githubusercontent.com/83635356/200105012-d9c51c74-7382-4d1c-9ed7-cf093f9be367.png)

There are 73.46% of customers who are still using the service and 26.54% of customers who stop using the service.

#### What's the insight on churn and non-churn customers based on customers demographic info such as gender, senior citizen, partner, and dependents?

#### Gender

![image](https://user-images.githubusercontent.com/83635356/200104970-a91e0e5b-2353-48f1-a7cf-4ba1505d0444.png)

- Female churn customers are are almost even with male churn customers.
- Male customers who are still subscribed are 43.12%, female customers are 42.91%, and customers whose gender is unknown are 13.69%.
- Male customers who unsubscribed are 43.27%, female customers are 42.27%, and customers whose gender is unknown are 14.46%.

#### Citizen
![image](https://user-images.githubusercontent.com/83635356/200105068-5664bf6c-63a2-4d77-a1b3-f10ff7130c0d.png)

- Young citizens are the biggest customers, but also the customers with the highest churn percentage.
- Young customers who are still subscribed are 64%, senior customers are 14%, and customers whose age category is unknown are 22%.
- Young customers who have not subscribed are 74.6%, senior customers are 10.9%, and customers whose age category is not known are 14%.

#### Partner

![image](https://user-images.githubusercontent.com/83635356/200105110-25528114-f8ba-4697-9351-b4d72d7abe8e.png)

- Customers who do not have a partner are more likely to stop using the service.
- Customers who no longer use services that have a partner are 30.8%, smaller than customers who do not have a partner, which is 55.2%, and those who are not known are 14%.
- Customers who still use services that have a partner are 40.2%, smaller than customers who do not have a partner, which is 45.4%, and those who are not known are 14.5%.

#### Dependents

![image](https://user-images.githubusercontent.com/83635356/200105169-43e36eae-071e-41d6-b65a-fcbfdd6ca7db.png)

- Customers who have dependents are more likely to stop using the service.
- Customers who no longer use services with dependents are 15.1%, smaller than customers who do not have dependents, which are 70.9%, and those who are not known are 14%.
- Customers who still use services with dependents are 29.3%, smaller than customers who do not have dependents, which are 56.3%, and those who are not known are 14.5%.

#### What's the insight on churn and non-churn customers based on customer services booked such as phone service, multiple lines, internet service, online security, online backup, device protection, tech support, streaming TV, and streaming movies.

#### Phone Service

![image](https://user-images.githubusercontent.com/83635356/200105203-d60784c8-b3db-4024-9a74-3ca7120782ce.png)

- Customers who have phone service are more likely to stop using the service.
- Customers who no longer use services that have phone service are 90.9%, smaller than customers who do not have phone service, which is 9.1%.
- Customers who still use services that have phone service are 90.1%, smaller than customers who do not have phone service, which is 9.9%.

#### Multiple Lines

![image](https://user-images.githubusercontent.com/83635356/200105263-b4e72b9d-9a8e-49e3-a1f3-25ccfb09ffd3.png)

- Customers who have and do not have multiple lines who are no longer using the service are not significantly different even though those who have multiple lines are more in number. 
- Customers who no longer use services that have multiple lines are 38.7%, smaller than customers who do not have multiple lines, namely 39.4%, users who do not have phone service are 7.9%, and those who are unknown are 14%.
- Customers who still use services that have multiple lines are 34.8%, smaller than customers who do not have multiple lines, namely 42.2%, users who do not have phone service are 8.5%, and those who are unknown are 14.5%.

#### Internet Service

![image](https://user-images.githubusercontent.com/83635356/200105502-f9b89071-1e19-4ad1-b4f5-e754d1b29642.png)

- Customers who use Fiber optic internet service tend to stop using the service, followed by DSL type internet service.
- Customers who no longer use services that have fiber optic internet service are 59.3%, smaller than customers who use DSL internet service, which is 21.5%, users who do not have internet service are 14%, and those who are unknown are 5.2%.
- Customers who still use services that have fiber optic internet service are 32.7%, bigger than customers who use DSL internet service, which is 29.2%, users who do not have internet service are 23.6%, and those who are unknown are 14.5%. 

#### Online Security

![image](https://user-images.githubusercontent.com/83635356/200105644-e410f5fc-bf6a-4600-bc9a-48b9651dc45e.png)

- Customers who do not use online security tend to stop using the service.
- Customers who no longer use services that have online security are 14%, smaller than customers who use online security as much as 67.4%, users who do not have internet service are 13.4%, and those who are unknown are 5.2%.
- Customers who still use services that have online security are 28.4%, smaller than customers who use online security as much as 33.5%, users who do not have internet service are 23.6%, and those who are unknown are 14.5%.

#### Online Backup

![image](https://user-images.githubusercontent.com/83635356/200105676-b0bf4cc2-aa3f-4e39-943a-015a4403e755.png)

- Customers who do not use online backup tend to stop using the service. 
- Customers who no longer use services that have online backups are 23.7%, smaller than customers who use online backups as much as 57.1%, users who do not have internet service as much as 14%, and those who do not know are 5.2%.
- Customers who still use services that have online backups are 30.5%, smaller than customers who use online backups of 31.4%, users who do not have internet service are 23.6%, and those who are unknown are 14.5%.

#### Device Protection

![image](https://user-images.githubusercontent.com/83635356/200105718-a215873b-43e5-4e45-bf1d-db378285e2ff.png)

- Customers who do not use device protection tend to stop using the service. 
- Customers who no longer use services that have device protection are 29.4%, smaller than customers who use online backup as much as 37.5%, users who do not have internet service as much as 18.8%, and those who are unknown are 14.3%. 
- Customers who still use services that have device protection are 25%, smaller than customers who use online backup as much as 55.8%, users who do not have internet service are 14%, and those who are not known are 5.2%.

#### Tech Support

![image](https://user-images.githubusercontent.com/83635356/200105763-684f34f8-5fa6-44d0-a005-3efc18407070.png)

- Customers who do not use tech support tend to stop using the service.
- Customers who no longer use services that have tech support are 14.7%, smaller than customers who have tech support as much as 66.1%, users who do not have internet service are 14%, and those who are unknown are 5.2%.
- Customers who are still using services that have tech support are 28.3%, smaller than customers who have tech support as much as 33.6%, users who do not have internet service are 23.6%, and those who are unknown are 14.5%.

#### Streaming TV

![image](https://user-images.githubusercontent.com/83635356/200105787-f645043b-9f6a-4546-99d1-1a798cc369f8.png)

- The use of streaming TV services for subscribers who have not used the service does not seem to have a noteworthy effect because the percentage of users (37.9%) and non-users (42.9) are both high.
- Customers who no longer use services that use TV streaming services are 37.9%, smaller than customers who do not use TV streaming services by 42.9%, users who do not have internet services by 14%, and unknown ones by 5.2%.
- Customers who still use services that use TV streaming services are 30.9%, smaller than customers who do not use TV streaming services by 31%, users who do not have internet services by 23.6%, and those who are not known by 14.5%.

#### Streaming Movies

![image](https://user-images.githubusercontent.com/83635356/200105809-c91ab883-64d2-4342-8e4d-e20ecef39568.png)

- Customers who no longer use services who do not use movie streaming services are more likely to unsubscribe.
- Customers who no longer use services that use movie streaming services are 37.3%, smaller than customers who do not use streaming movies services as much as 43.5%, users who do not have internet services by 14%, and unknown ones by 5.2%.
- Customers who still use services that use movie streaming services are 30.6%, smaller than customers who do not use streaming movies services by 31.3%, users who do not have internet services by 23.6%, and unknown ones by 14.5%.

#### What's the insight on churn and non-churn customers based on customer account information such as paperless billing, payment method, and contract?

#### Contract
![image](https://user-images.githubusercontent.com/83635356/200105864-68102e6b-7819-4374-a2a1-4b2ab3a081e5.png)

- Customers who have not used services that have a Month-to-month contract are more likely to unsubscribe than those who have a One-year and Two-year contracts.
- Customers who no longer use services that have Month-to-month contracts are 88.6%, significantly larger than customers who have One year contracts as much as 2.6%, and Two year contacts as much as 8.9%.
- Customers who still use services that have a Month-to-month contract are 31.8%, smaller than customers who have a One-year contract of 25.3%, and a Two-year contract of 31.8%.

#### Paperless Billing

![image](https://user-images.githubusercontent.com/83635356/200105878-2d820887-19b8-4b45-bf25-26548c241e10.png)

- Customers who no longer use services that use paperless billing are more likely to unsubscribe. 
- Customers who no longer use services that use paperless billing are 74.9%, significantly larger than customers who do not use paperless billing as much as 25.1%. 
- Customers who still use services that use paperless billing are 53.6%, significantly larger than customers who do not use paperless billing as much as 46.4%.

#### Payment Method

![image](https://user-images.githubusercontent.com/83635356/200105917-7c37f914-8583-4089-ac20-0bc8ad5da2ad.png)

- Customers who no longer use services that use the electronic check payment method are more likely to unsubscribe.
- For customers who still use the service, the four types of payment methods are almost evenly used around 24.9%-25.2%.
- Customers who no longer use services that use the electronic check payment method are 57.3%, significantly larger than other payment methods, 16.5% mailed check payment methods, 13.8% bank transfer (automatic) payment methods, and credit payment methods. card (automatic) as much as 12.4%.
- Customers who still use services that use the electronic check payment method are 25.2%, significantly larger than other payment methods, the mailed check payment method is 25%, the bank transfer payment method (automatic) is 24.9%, and the credit card payment method (automatic) as much as 24.9%.

#### What's the insight into whether there is a relationship between monthly charges, total charges, and tenure on churn rate?

#### Monthly Charges

![image](https://user-images.githubusercontent.com/83635356/200105936-6846fee6-8cf7-4ce1-bd01-b2c015849168.png)

- Customer tends to stop using the service when the if the monthly charges are high.
- The total monthly charges for customers who stop using the service are 31%, while those who are still using the service are 69%.
- The average monthly charges for customers who are not using the service are \\$74.4, while those who are still using the service are $61.2.

#### Total Charges

![image](https://user-images.githubusercontent.com/83635356/200106005-87171e12-2ff3-4531-b4db-80f2c7fbb06a.png)

- Customes tend to stop using the service when the if the total charges are high.
- The total charges for customers who stop using the service are 18%, while those who are still using the service are 82%.
- The average total charges of customers who have not used the service are \\$1531.8, while those who are still using the service are $2552.9.

#### Tenure

![image](https://user-images.githubusercontent.com/83635356/200106049-cac20c81-d7c7-457c-aa6d-ce821c4f506e.png)

- Customers tend to stop using the service if their tenure is short. 
- The total tenure of customers who stop using the service are 15%, while those who are still using services are 85%.
- The average tenure of customers who have not used the service is 17 months, while those who are still using the service are 37 months.

We can conclude that higher monthly charge at lower tenure results into lower total charge. Hence, higher monthly charge, lower tenure, and lower total charge are linked to why customers stopped using the service.

# Feature Engineering
* #### One Hot Encoding and Map
Use One-Hot Encoding feature for categorical data and the map feature which for ordinal data.

* #### Scaler using standart scaler
Scale tenure and MonthlyCharges feature with StandardScaler.

# Preprocessing Modeling
Before entering the modeling stage, we enter the preprocessing stage first.<br>
At this stage we do several things, such as:
* #### Feature Selection
We drop customerID because it is a Identifier and TotalCharges because it is a Multicollinear.

* #### Feature Importance
Use Feature Importance barchart using ExtraTreesClassifier algorithm.
![image](https://user-images.githubusercontent.com/83635356/200107432-77797b45-877c-4f9b-bc79-b48a05878db6.png)

* #### Split Train-Test The Data
Split train-test the data using train_test_split function.

# Modeling 
### Machine Learning Classification | Logistic Regression
Logistic regression is a fundamental classification technique. Logistic regression is fast and relatively uncomplicated, and it’s convenient for you to interpret the results.

# Evaluate Model
After doing the modeling stage such as choosing a model, training the model and making predictions with the model, then we need to evaluate the results of our model predictions so that we can improve our model to be better or more accurate.<br>
In the evaluate modeling stage we do several things, such as:

* #### Confusion Matrix
Confusion matrix, also known as an error matrix, is a specific table layout that allows visualization of the performance of an algorithm.
![image](https://user-images.githubusercontent.com/83635356/200107507-02c9f58f-8ad3-460b-86aa-93e58ad27552.png)

* #### Overfit and Underfit
Check whether the model is Overfit or Underfit by comparing the accuracy scores of the train and the test model, if the difference is more than 5% then the model is Overfit or Underfit.
![image](https://user-images.githubusercontent.com/83635356/200107626-dd5ed6b6-c614-43cb-8c6a-2e2be5fef9d1.png)
the model does not have Overfit and Underfit.

* #### AUC/ROC
AUC/ROC is a graph that can shows if the model is Overfit or Underfit.
![image](https://user-images.githubusercontent.com/83635356/200107652-78fba9da-bcf8-498b-9988-f4d8e2f79fd4.png)
the model does not have Overfit and Underfit.

* #### Building Model with Cross Validation
Cross-validation is a technique for evaluating ML models by training several ML models on subsets of the available input data and evaluating them on the complementary subset of the data.

* #### Hyperparameter Tuning 
Hyperparameter tuning consists of finding a set of optimal hyperparameter values for a learning algorithm while applying this optimized algorithm to any data set. That combination of hyperparameters maximizes the model's performance, minimizing a predefined loss function to produce better results with fewer errors.

## Remodeling
In the re-modeling stage we use best parameters from to Hyperparameter Tuning improve the model.
![image](https://user-images.githubusercontent.com/83635356/200107940-170f174f-87ef-4a38-bd21-9891cd4d5915.png)

The accuracy rate of predicting customer churn accuracy using machine learning Logistics Regression and after evaluating the model using Hyperparameter Tuning is improved from 0.8232789212207239 to 0.8239886444286728.

# Result

- There are 73.46% of customers who are still using the service and 26.54% of customers who stop using the service.

- The total monthly charges for customers who stop using the service are 31%, while those who are still using the service are 69%. The average monthly charges for customers who are not using the service are \\$74.4, while those who are still using the service are \\$61.2.

- The total charges for customers who stop using the service are 18%, while those who are still using the service are 82%. The average total charges of customers who have not used the service are \\$1531.8, while those who are still using the service are \\$2552.9.

- The total tenure of customers who stop using the service are 15%, while those who are still using services are 85%. The average tenure of customers who have not used the service is 17 months, while those who are still using the service are 37 months.

- We can conclude that higher monthly Charge at lower tenure results into lower total charge. Hence, higher monthly charge, lower tenure, and lower total charge are linked to high churn.

- Female churn customers are are almost even with male churn customers. Male customers who are still subscribed are 43.12%, female customers are 42.91%, and customers whose gender is unknown are 13.69%. 

- Young citizens are the biggest customers (71.8%), but also the customers with the highest churn percentage. Young customers who are still subscribed are 64%, senior customers are 14%, and customers whose age category is unknown are 22%. 

- Customers who do not have a partner are more likely to stop using the service. Customers who no longer use services that have a partner are 30.8%, smaller than customers who do not have a partner, which is 55.2%, and those who are not known are 14%. 

- Customers who have dependents are more likely to stop using the service. Customers who no longer use services with dependents are 15.1%, smaller than customers who do not have dependents, which are 70.9%, and those who are not known are 14%.

- Customers who have phone service are more likely to stop using the service. Customers who no longer use services that have phone service are 90.9%, smaller than customers who do not have phone service, which is 9.1%.

- Customers who have and do not have multiple lines who are no longer using the service are not significantly different even though those who have multiple lines are more in number. Customers who no longer use services that have multiple lines are 38.7%, smaller than customers who do not have multiple lines, namely 39.4%, users who do not have phone service are 7.9%, and those who are unknown are 14%.

- Customers who use Fiber optic internet service tend to stop using the service, followed by DSL type internet service. Customers who no longer use services that have fiber optic internet service are 59.3%, smaller than customers who use DSL internet service, which is 21.5%, users who do not have internet service are 14%, and those who are unknown are 5.2%.

- Customers who do not use online security tend to stop using the service. Customers who no longer use services that have online security are 14%, smaller than customers who use online security as much as 67.4%, users who do not have internet service are 13.4%, and those who are unknown are 5.2%.

- Customers who do not use online backup tend to stop using the service. Customers who no longer use services that have online backups are 23.7%, smaller than customers who use online backups as much as 57.1%, users who do not have internet service as much as 14%, and those who do not know are 5.2%.

- Customers who do not use device protection tend to stop using the service. Customers who no longer use services that have device protection are 29.4%, smaller than customers who use online backup as much as 37.5%, users who do not have internet service as much as 18.8%, and those who are unknown are 14.3%.

- Customers who do not use tech support tend to stop using the service. Customers who no longer use services that have tech support are 14.7%, smaller than customers who have tech support as much as 66.1%, users who do not have internet service are 14%, and those who are unknown are 5.2%.

- The use of streaming TV services for subscribers who have not used the service does not seem to have a noteworthy effect because the percentage of users (37.9%) and non-users (42.9) are both high. Customers who no longer use services that use TV streaming services are 37.9%, smaller than customers who do not use TV streaming services by 42.9%, users who do not have internet services by 14%, and unknown ones by 5.2%.

- Customers who no longer use services who do not use movie streaming services are more likely to unsubscribe. Customers who no longer use services that use movie streaming services are 37.3%, smaller than customers who do not use streaming movies services as much as 43.5%, users who do not have internet services by 14%, and unknown ones by 5.2%.

- Customers who have not used services that have a Month-to-month contract are more likely to unsubscribe than those who have a One-year and Two-year contracts. Customers who no longer use services that have Month-to-month contracts are 88.6%, significantly larger than customers who have One year contracts as much as 2.6%, and Two year contacts as much as 8.9%. 

- Customers who no longer use services that use paperless billing are more likely to unsubscribe. Customers who no longer use services that use paperless billing are 74.9%, significantly larger than customers who do not use paperless billing as much as 25.1%.

- Customers who no longer use services that use the electronic check payment method are more likely to unsubscribe. For customers who still use the service, the four types of payment methods are almost evenly used around 24.9%-25.2%. Customers who no longer use services that use the electronic check payment method are 57.3%, significantly larger than other payment methods, 16.5% mailed check payment methods, 13.8% bank transfer (automatic) payment methods, and credit payment methods. card (automatic) as much as 12.4%.

- The accuracy rate of predicting customer churn accuracy using machine learning Logistics Regression and after evaluating the model using Hyperparameter Tuning is 82%.(0.82).

# Recommendation

- Young people are the biggest customers, but also customers with the highest churn percentage, which is 64%. To minimize churn for young people, adjusting service prices can be one way considering their finances.

- Focus on non-fiber optic users, electronic checks, and customers who don't have partners. Another solution is to please customers with these criteria with interesting services so that they feel valued.

- Churn users are associated with short tenure, business teams need to treat customers with interesting discounts or service so customers would repurchase.

- TV streaming services and movie streaming services need to be investigated for why customers tend not to use them and stop using the service.

- Customers who have One-year and Two-year contracts are more likely to remain customers and show loyalty to services than customers who have Month-to-month contracts. Business teams need to focus on activating customers and increasing their loyalty, especially for customers with Month-to-month contracts.

- To keep customers loyal, the business team needs to optimize the budget for campaign and pamper senior customers considering they have a low churn rate.
