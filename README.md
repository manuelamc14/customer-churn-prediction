# customer-churn-prediction

## 1. Problem Statement and Motivation:

Telco, a telecommunications company, provides home phone and Internet services. The Telco customer churn data contains information about 7043 customers in California in Q3, which indicates that the company is experiencing a massive customer churn rate. To find out what factors caused this huge churn rate and how to deploy customer retention strategies to reduce customer churn.  The main goals with this project are:

- Develop a predictive model to classify customer churn risk.
- Identify customer pain points.
- Identify strategy/methods to lower churn and increase customer retention.
   
The motivation to work on this project is the challenges the data involves as:

- Inaccurate or messy customer data.
- Lack of information and domain knowledge.
- Choice of metrics to validate churn model performance.
-Imbalance data (class imbalance issue).

## 2. Introduction and Description of Data:

### 2.1. Data Source

IBM Cognos Telco Customer Churn Dataset [https://www.kaggle.com/yeanzc/telco-customer- churn-ibm-dataset](https://www.kaggle.com/yeanzc/telco-customer-churn-ibm-dataset). There are 7043 observations with 33 variables.

### 2.2. Data Understanding
   
We classify 33 columns of data into six domains. The six categories in the domain include Customer, Demographics, Location, Services, Billing, and Customer Status

- Customer: A unique customer ID identifies each of the 7,043 unique customers in our sample, with an average tenure of 0 to 72 months. 
- Demographic: Customer demographic information includes gender, partner, senior citizen (indicates if the customer is 65 or older: Yes, No), and Dependents.
- Location: Geographic location includes country, state, zip code, latlong, latitude, and Longitude.
- Services: Ten services include phone services, multiple lines, internet service, online security, online back, device protection, tech support, streaming TV, and streaming movies.
- Billing: Includes contract type, billing configuration, and monthly charges.
- Customer status: Churn value (target variable), Churn Reasons, and two TelCo metrics for Churn Score and Customer Lifetime Value.

## 3. Modeling Approach: 

According to the dataset, we have a binary classification problem. The output of the predictiv emodel is the target-dependent variable “Churn Value” 1 (churn) or 0 (retain).

To create a baseline for the project, we selected nine Machine Learning Algorithms with basic hyper-parameter appropriated for handling these types of problems: LogisticRegression, GaussianNB, KNeighborsClassifier, RandomForestClassifier, SVC kernel=linear, SVC kernel=rbf, SVC kernel=poly, AdaBoostClassifier, ExtraTreesClassifier, BaggingClassifier, and XGBClassifier.

## 4. Results and Analysis

The final model obtained is based on the XGBoosting algorithm and presented the following scores when applied to the current dataset:

| Results     | ROC AUC     | Recall     |  Precision | Accuracy  | F1-Score |
| :---        |    :----:   |     :----: |    :----:  |  :----:   | ----:    |
| Initial     | 0.7041      | 0.5208     | 0.6144     | 0.7935    | 0.5637   |
| Final       | 0.8623      | 0.8578     | 0.5093     | 0.7425    | 0.6385   |


We discovered that there is a trade-off between Recall and Precision after comparing the initial performance results to the final results. The model's Recall score increased, indicating that it reduced the number of false negatives. The number of false positives, on the other hand, increased, lowering the Precision score.

Considering the current customers, the histogram below presents the distribution of probabilities of churn using a threshold of 0.75, pointing out that about 17.1% of the customers have a probability of more than 75% canceling their services, which requires immediate action from our
client.

Given the obtained results, our main recommendations for the the company are:

- Offer discounts on monthly charges to customers most likely to churn, subject to longer period contracts or a loyalty period.
- Offer benefits to recently acquired customers, subject to longer period contracts or a loyalty period.
- Verify the existence of reported issues related to the use of the services by dependents, like complaints related to the use of streaming and gaming.
- Focus on reducing the Electronic Check payment, offering benefits for use of automatic recurrent types of payments, like credit card or debit authorization.
- Verify the overall Fiber Optic service quality.

## 5. Conclusion and Future Work

The project was very successful as we created a very useful model that can predict churn rate with high accuracy. This model can be used to properly analyze the factors that most contribute to the churn rate as well as the individual churn risk of current customers. And more importantly, the model can provide valuable information for defining the actions required to reduce customer churn.

The biggest challenge after building the model, it is the impact that the reduction in the Precision Score could have in the company. To determine if targeting false positives is a necessary problem to address, it would be appropriate to assess the cost of doing so and the impact on the company's profit. Updating and increasing the amount of data used to train the model could be one solution.
