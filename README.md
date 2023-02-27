# Telecom_Churn_Case_Study


## Problem Statement:
In the telecom industry, customers are able to choose from multiple service providers and actively switch from one operator to another. In this highly competitive market, the telecommunications industry experiences an average of 15-25% annual churn rate. Given the fact that it costs 5-10 times more to acquire a new customer than to retain an existing one, customer retention has now become even more important than customer acquisition.

For many incumbent operators, retaining high profitable customers is the number one business goal.

To reduce customer churn, telecom companies need to predict which customers are at high risk of churn.

### Understanding and defining churn
There are two main models of payment in the telecom industry - postpaid (customers pay a monthly/annual bill after using the services) and prepaid (customers pay/recharge with a certain amount in advance and then use the services).

In the postpaid model, when customers want to switch to another operator, they usually inform the existing operator to terminate the services, and you directly know that this is an instance of churn.

However, in the prepaid model, customers who want to switch to another network can simply stop using the services without any notice, and it is hard to know whether someone has actually churned or is simply not using the services temporarily (e.g. someone may be on a trip abroad for a month or two and then intend to resume using the services again).

Thus, churn prediction is usually more critical (and non-trivial) for prepaid customers, and the term ‘churn’ should be defined carefully.  Also, prepaid is the most common model in India and Southeast Asia, while postpaid is more common in Europe in North America.

## Modelling
Build models to predict churn. The predictive model that you’re going to build will serve two purposes:

It will be used to predict whether a high-value customer will churn or not, in near future (i.e. churn phase). By knowing this, the company can take action steps such as providing special plans, discounts on recharge etc.

It will be used to identify important variables that are strong predictors of churn. These variables may also indicate why customers choose to switch to other networks.

In some cases, both of the above-stated goals can be achieved by a single machine learning model. But here, you have a large number of attributes, and thus you should try using a dimensionality reduction technique such as PCA and then build a predictive model. After PCA, you can use any classification model.


# Outcome:

### General

- The initial dataset consists of 226 independent variables, which has been reduced to 130 after performing the Feature engineering and EDA.
- The dependent variable that predicts whether the customer will churn or not is derived based on 70th percentile of the average recharge amount in the 6th and 7th-month i,e in the good phase.

### Recommendations

- Based on the analysis a pattern is observed as the customer has stopped or minimises the usage of the services during the action phase as compared to the good phase, then this customer is most likely to churn.
- The customers who are using the STD_OG services during the good phase are most likely to be churning, which may be because of the competitive recharge price or network issues.
- Average revenue per user should also be monitored for a reduction in consumption which would indicate potential customer churn
- If the customer reduces the recharge amount during the action phase as compared to the good phase, the system should trigger that particular customer is likely being churned.
- The Age on a network (AON), indicates that newly joined customers have high chances of churn. This might be because of adaptation issues or unsatisfactory services.
Customer who have not recharged in recent days even after the recharge is due, are more likely to churn in the churning phase.


### Model Performance

- We aim to reduce the False Negative errors while reduction hence we need to maximise the recall score during the deployment phase.
- The unsupervised Principal component analysis is implemented to reduce the dimensions in a dataset to increase the computation power. The Boosting and Logistic regression models are implemented on top of PCA and the original datasets.
- For the PCA dataset, in terms of accuracy the Random Forest Classifier algorithm is best. it gives an accuracy of 85.40% for train and 84.77% for test dataset. For this the recall is higher in the case of train dataset which is 81.21% as compared to test dataset 76.61%.
- The combination of PCA and logistic regression can false negative values very well, for the train and test dataset it gives 82.59% and 92.54% recall score, With an accuracy of 84.08% and 58.99% respectively.
- In original datasets, XGBClassifier works very well in terms of accuracy and recall score. In the case of the train dataset accuracy and recall value is observed as 95.45% and 99.61%, while for the test dataset it is 92.09% and 78.66% respectively.
- Similarly, logistic regression gives almost constant performance over accuracy and recall matrix. The accuracy for the train and test datasets is 81.34% and 80.45% respectively whereas the recall score for the train is 82.64% and 80.72% for the test dataset.

