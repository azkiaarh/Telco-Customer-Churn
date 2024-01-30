# Use Case
#### Use Case Summary
#### Objective Statement:
- Determine the churn rate of the customer base.
- Identify factors that are associated with churn, such as gender, senior citizen status, partner status, dependents, number of services booked, paperless billing, payment method, contract type, monthly charges, total charges, and tenure.
- Develop a machine learning model to predict customer churn.

#### Expected Outcome:
- A comprehensive understanding of customer churn drivers
- A machine learning model that can accurately predict customer churn
- Recommendations for targeted interventions to reduce churn
- Increased customer retention and revenue

# Business Understanding
* A telephone company, also known as a telco, telephone service provider, or telecommunications operator, is a kind of communications service provider, more precisely a telecommunications service provider, that provides telecommunications services such as telephony and data communications access.
* Churn rate is the rate at which customers stop doing business with a company over a given period of time.

This case requires data-driven answers to the following questions:
* How many customers are churning?
* What's the insight on churn and non-churn customers based on customers demographic info such as gender, senior citizen, partner, and dependents?
* What's the insight on churn and non-churn customers based on customer services booked  such as phone service, multiple lines, internet service, online security, online backup, device protection, tech support, streaming TV and streaming movies?
* What's the insight on churn and non-churn customers based on customer account information such as paperless billing, payment method, and contract?
* Is there a relationship between monthly charges, total charges, and tenure on churn rate?



# Data Understanding
#### Data Source
* The data set is a collection of customer retention programs.
* The data set has 7043 rows and 21 columns.
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

The majority of customers are still using the service (73.46%), while a minority of customers have stopped using the service (26.54%).

#### What's the insight on churn and non-churn customers based on customers demographic info such as gender, senior citizen, partner, and dependents?

#### Gender

![image](https://user-images.githubusercontent.com/83635356/200104970-a91e0e5b-2353-48f1-a7cf-4ba1505d0444.png)

- **Female churn customers are almost as likely as male churn customers to stop using the service**.

- About 43% of male customers and 42% of female customers have stopped using the service.

- About 43% of male customers and 43% of female customers are still subscribed to the service.

#### Citizen
![image](https://user-images.githubusercontent.com/83635356/200105068-5664bf6c-63a2-4d77-a1b3-f10ff7130c0d.png)

- **Young customers are the biggest users of the service, but they are also the most likely to stop using it**.

- About 64% of young customers are still subscribed to the service, while about 74.6% of young customers have stopped using the service.

- About 14% of senior customers are still subscribed to the service, while about 10.9% of senior customers have stopped using the service.

- About 22% of customers have an unknown age category.

#### Partner

![image](https://user-images.githubusercontent.com/83635356/200105110-25528114-f8ba-4697-9351-b4d72d7abe8e.png)

- **Customers without a partner are more likely to stop using the service than customers with a partner**.

- About 55% of customers without a partner have stopped using the service, while only 31% of customers with a partner have stopped using the service.

- About 45% of customers with a partner are still using the service, while only 40% of customers without a partner are still using the service.

- About 14% of customers have an unknown partner status.

#### Dependents

![image](https://user-images.githubusercontent.com/83635356/200105169-43e36eae-071e-41d6-b65a-fcbfdd6ca7db.png)

- **Customers with dependents are more likely to stop using the service than customers without dependents**.

- About 71% of customers with dependents have stopped using the service, while only 15% of customers without dependents have stopped using the service.

- About 56% of customers without dependents are still using the service, while only 29% of customers with dependents are still using the service.

- About 14% of customers have an unknown dependent status.

#### What's the insight on churn and non-churn customers based on customer services booked such as phone service, multiple lines, internet service, online security, online backup, device protection, tech support, streaming TV, and streaming movies.

#### Phone Service

![image](https://user-images.githubusercontent.com/83635356/200105203-d60784c8-b3db-4024-9a74-3ca7120782ce.png)

- **Customers with phone service are less likely to continue using the service than customers without phone service**.

- About 91% of customers with phone service have stopped using the service, while only 9% of customers without phone service have stopped using the service.

- About 90% of customers without phone service are still using the service, while only 9% of customers with phone service are still using the service.

- About 10% of customers have an unknown phone service status.

#### Multiple Lines

![image](https://user-images.githubusercontent.com/83635356/200105263-b4e72b9d-9a8e-49e3-a1f3-25ccfb09ffd3.png)

- **Customers with multiple lines are not more likely to stop using the service than customers without multiple lines**.

- About 39% of customers with multiple lines have stopped using the service, while about 38% of customers without multiple lines have stopped using the service.

- About 42% of customers without multiple lines are still using the service, while about 35% of customers with multiple lines are still using the service.

- About 14% of customers have an unknown multiple line status.

#### Internet Service

![image](https://user-images.githubusercontent.com/83635356/200105502-f9b89071-1e19-4ad1-b4f5-e754d1b29642.png)

- **Customers who use fiber optic internet service are more likely to stop using the service than customers who use DSL internet service**.

- About 59% of customers who use fiber optic internet service have stopped using the service, while about 22% of customers who use DSL internet service have stopped using the service.

- About 33% of customers who use fiber optic internet service are still using the service, while about 30% of customers who use DSL internet service are still using the service.

- About 14% of customers do not have internet service.

- About 5% of customers have an unknown internet service status.

#### Online Security

![image](https://user-images.githubusercontent.com/83635356/200105644-e410f5fc-bf6a-4600-bc9a-48b9651dc45e.png)

- **Customers who do not use online security are more likely to stop using the service than customers who do use online security**.

- About 86% of customers who do not use online security have stopped using the service, while only 33% of customers who do use online security have stopped using the service.

- About 66% of customers who use online security are still using the service, while only 28% of customers who do not use online security are still using the service.

- About 13% of customers do not have internet service.

- About 5% of customers have an unknown online security status.

#### Online Backup

![image](https://user-images.githubusercontent.com/83635356/200105676-b0bf4cc2-aa3f-4e39-943a-015a4403e755.png)

- **Customers who do not use online backup are more likely to stop using the service than customers who do use online backup**.

- About 76% of customers who do not use online backup have stopped using the service, while only 43% of customers who do use online backup have stopped using the service.

- About 69% of customers who use online backup are still using the service, while only 30% of customers who do not use online backup are still using the service.

- About 14% of customers do not have internet service.

- About 5% of customers have an unknown online backup status.

#### Device Protection

![image](https://user-images.githubusercontent.com/83635356/200105718-a215873b-43e5-4e45-bf1d-db378285e2ff.png)

- **Customers who do not use device protection are more likely to stop using the service than customers who do use device protection**.

- About 70% of customers who do not use device protection have stopped using the service, while only 62.5% of customers who do use device protection have stopped using the service.

- About 75% of customers who use device protection are still using the service, while only 25% of customers who do not use device protection are still using the service.

- About 19% of customers do not have internet service.

- About 5% of customers have an unknown device protection status.

#### Tech Support

![image](https://user-images.githubusercontent.com/83635356/200105763-684f34f8-5fa6-44d0-a005-3efc18407070.png)

- **Customers who do not use tech support are more likely to stop using the service than customers who do use tech support**.

- About 85% of customers who do not use tech support have stopped using the service, while only 34% of customers who do use tech support have stopped using the service.

- About 66% of customers who use tech support are still using the service, while only 28% of customers who do not use tech support are still using the service.

- About 14% of customers do not have internet service.

- About 5% of customers have an unknown tech support status.

#### Streaming TV

![image](https://user-images.githubusercontent.com/83635356/200105787-f645043b-9f6a-4546-99d1-1a798cc369f8.png)

- **There is no significant difference in the churn rate between customers who use streaming TV services and customers who do not use streaming TV services**.

- About 38% of customers who use streaming TV services have stopped using the service, while about 43% of customers who do not use streaming TV services have stopped using the service.

- About 31% of customers who use streaming TV services are still using the service, while about 31% of customers who do not use streaming TV services are still using the service.

- About 14% of customers do not have internet service.

- About 5% of customers have an unknown streaming TV service status.

#### Streaming Movies

![image](https://user-images.githubusercontent.com/83635356/200105809-c91ab883-64d2-4342-8e4d-e20ecef39568.png)

- **Customers who do not use movie streaming services are more likely to stop using the service than customers who do use movie streaming services**.

- About 43% of customers who do not use movie streaming services have stopped using the service, while only 37% of customers who do use movie streaming services have stopped using the service.

- About 31% of customers who use movie streaming services are still using the service, while about 30% of customers who do not use movie streaming services are still using the service.

- About 14% of customers do not have internet service.

- About 5% of customers have an unknown movie streaming service status.

#### What's the insight on churn and non-churn customers based on customer account information such as paperless billing, payment method, and contract?

#### Contract
![image](https://user-images.githubusercontent.com/83635356/200105864-68102e6b-7819-4374-a2a1-4b2ab3a081e5.png)

- **Customers who do not use month-to-month contracts are significantly more likely to stop using the service than customers who have one-year or two-year contracts**.

- About 89% of customers who do not use month-to-month contracts have stopped using the service, while only 2% of customers who have one-year contracts and 9% of customers who have two-year contracts have stopped using the service.

- About 32% of customers who do not use month-to-month contracts are still using the service, while about 25% of customers who have one-year contracts and 32% of customers who have two-year contracts are still using the service.

#### Paperless Billing

![image](https://user-images.githubusercontent.com/83635356/200105878-2d820887-19b8-4b45-bf25-26548c241e10.png)

- **Customers who do not use paperless billing are significantly more likely to stop using the service than customers who do use paperless billing**.

- About 75% of customers who do not use paperless billing have stopped using the service, while only 25% of customers who do use paperless billing have stopped using the service.

- About 54% of customers who use paperless billing are still using the service, while about 46% of customers who do not use paperless billing are still using the service.

#### Payment Method

![image](https://user-images.githubusercontent.com/83635356/200105917-7c37f914-8583-4089-ac20-0bc8ad5da2ad.png)

- **Customers who use the electronic check payment method are more likely to stop using the service than customers who use other payment methods**.

- About 57% of customers who use the electronic check payment method have stopped using the service, while about 17% of customers who use mailed checks, 14% of customers who use bank transfers (automatic), and 12% of customers who use credit cards (automatic) have stopped using the service.

- About 25% of customers who use the electronic check payment method are still using the service, while about 25% of customers who use mailed checks, 25% of customers who use bank transfers (automatic), and 25% of customers who use credit cards (automatic) are still using the service.

#### What's the insight into whether there is a relationship between monthly charges, total charges, and tenure on churn rate?

#### Monthly Charges

![image](https://user-images.githubusercontent.com/83635356/200105936-6846fee6-8cf7-4ce1-bd01-b2c015849168.png)

- **Customers who are charged high monthly fees are more likely to stop using the service than customers who are charged lower monthly fees**.

- About 69% of customers who are charged high monthly fees are still using the service, while about 31% of customers who are charged high monthly fees have stopped using the service.

- The average monthly fee for customers who are charged high monthly fees is \$74.4, while the average monthly fee for customers who are charged low monthly fees is \$61.2.

#### Total Charges

![image](https://user-images.githubusercontent.com/83635356/200106005-87171e12-2ff3-4531-b4db-80f2c7fbb06a.png)

- **Customers who are charged higher total fees are more likely to stop using the service than customers who are charged lower total fees**.
- About 82% of customers who are charged higher total fees are still using the service, while about 18% of customers who are charged higher total fees have stopped using the service.
- The average total fee for customers who are charged higher total fees is \\$2552.9, while the average total fee for customers who are charged lower total fees is \\$1531.8.

#### Tenure

![image](https://user-images.githubusercontent.com/83635356/200106049-cac20c81-d7c7-457c-aa6d-ce821c4f506e.png)

- **Customers who have been with the company for a shorter period of time are more likely to stop using the service than customers who have been with the company for a longer period of time**.
- About 85% of customers who have been with the company for a shorter period of time are still using the service, while about 15% of customers who have been with the company for a shorter period of time have stopped using the service.
- The average tenure for customers who have been with the company for a shorter period of time is 17 months, while the average tenure for customers who have been with the company for a longer period of time is 37 months.

We can conclude that a higher monthly charge at lower tenure results in a lower total charge. Hence, higher monthly charges, lower tenure, and lower total charges are linked to why customers stopped using the service.

# Feature Engineering
* #### One Hot Encoding and Map
Use the One-Hot Encoding feature for categorical data and the map feature which for ordinal data.

* #### Scaler using standard scaler
Scale tenure and MonthlyCharges feature with StandardScaler.

# Preprocessing Modeling
Before entering the modeling stage, we enter the preprocessing stage first.<br>
At this stage, we do several things, such as:
* #### Feature Selection
We drop customerID because it is an Identifier and TotalCharges because it is a Multicollinear.

* #### Feature Importance
Use Feature Importance bar chart using ExtraTreesClassifier algorithm.
![image](https://user-images.githubusercontent.com/83635356/200107432-77797b45-877c-4f9b-bc79-b48a05878db6.png)

* #### Split Train-Test The Data
Split train-test the data using the train_test_split function.

# Modeling 
### Machine Learning Classification | Logistic Regression
Logistic regression is a fundamental classification technique. Logistic regression is fast and relatively uncomplicated, and it’s convenient for you to interpret the results.

# Evaluate Model
After doing the modeling stage such as choosing a model, training the model, and making predictions with the model, we need to evaluate the results of our model predictions so that we can improve our model to be better or more accurate.<br>
In the evaluation modeling stage we do several things, such as:

* #### Confusion Matrix
A confusion matrix, also known as an error matrix, is a specific table layout that allows visualization of the performance of an algorithm.
![image](https://user-images.githubusercontent.com/83635356/200107507-02c9f58f-8ad3-460b-86aa-93e58ad27552.png)

* #### Overfit and Underfit
Check whether the model is Overfit or Underfit by comparing the accuracy scores of the train and the test model, if the difference is more than 5% then the model is Overfit or Underfit.
![image](https://user-images.githubusercontent.com/83635356/200107626-dd5ed6b6-c614-43cb-8c6a-2e2be5fef9d1.png)
The model does not have Overfit and Underfit.

* #### AUC/ROC
AUC/ROC is a graph that can show if the model is Overfit or Underfit.
![image](https://user-images.githubusercontent.com/83635356/200107652-78fba9da-bcf8-498b-9988-f4d8e2f79fd4.png)
The model does not have Overfit and Underfit.

* #### Building Model with Cross Validation
Cross-validation is a technique for evaluating ML models by training several ML models on subsets of the available input data and evaluating them on the complementary subset of the data.

* #### Hyperparameter Tuning 
Hyperparameter tuning consists of finding a set of optimal hyperparameter values for a learning algorithm while applying this optimized algorithm to any data set. That combination of hyperparameters maximizes the model's performance, minimizing a predefined loss function to produce better results with fewer errors.

## Remodeling
In the re-modeling stage we use best parameters from to Hyperparameter Tuning improve the model.
![image](https://user-images.githubusercontent.com/83635356/200107940-170f174f-87ef-4a38-bd21-9891cd4d5915.png)

The accuracy rate of predicting customer churn accuracy using machine learning Logistics Regression and after evaluating the model using Hyperparameter Tuning is improved from 0.8232789212207239 to 0.8239886444286728.

# Result

- The churn rate is 26.54%, while the customer retention rate is 73.46%.
  
- Customers who stop using the service tend to have higher monthly charges, shorter tenures, and lower total charges.
  
- Female customers are almost as likely to churn as male customers. Young customers are the most likely to churn, while senior customers are the least likely to churn.
  
- Customers who do not have a partner or dependents are more likely to churn. Customers who have phone service are also more likely to churn.
  
- Customers who use fiber optic internet service are more likely to churn than customers who use DSL internet service.
  
- Customers who do not use online security, online backup, device protection, tech support, streaming TV, or movie streaming services are more likely to churn.
  
- Customers with month-to-month contracts are more likely to churn than customers with one-year or two-year contracts. Customers who do not use paperless billing are also more likely to churn.
  
- Customers who use electronic check payment are more likely to churn than customers who use other payment methods.
  
- The accuracy rate of predicting customer churn using machine learning is 82%.

# Recommendation

- Offer lower monthly charges to customers with shorter tenures. This may help to offset the higher costs associated with acquiring new customers.
  
- Offer discounts to customers who bundle services. This may help to encourage customers to stay with the company and use more of its services.
  
- Target marketing campaigns to customers who are at risk of churning. This may help to identify and address the specific needs of these customers.
  
- Improve customer service. This may help to resolve customer issues and complaints more quickly and effectively.
  
- Make it easy for customers to switch payment methods. This may help to reduce the number of customers who churn due to frustration with the payment process.
  
- Develop a customer loyalty program. This can help to reward customers for their continued patronage and encourage them to stay with the company.
