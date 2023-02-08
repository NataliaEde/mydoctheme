---
layout: post
title:  "Classification Problem of Bank’s Telemarketing Campaign"
featured_image_thumbnail:
featured_image: assets/images/posts/2018/project_3.jpg
---
## Introduction 

Retail banks collect term deposits as part of their core business investment products. Banks generate a profit by lending funds held in deposit accounts for a higher rate than it pays the customer. Therefore, banks emphasize their marketing efforts to attract customers to deposit funds.

Although most marketing channels are transitioning to a digital form and telemarketing campaigns are fading away, there is still space in advertising to utilize the phone as a tool for remote marketing. While remote marketing is moving gradually into robocalls, prospects still prefer to talk to a human rather than a robot-speaking voice.

In finance, an individual who buys a term deposit is called a subscriber. Subscription refers to a potential investor signing up for an investment vehicle agreement involving cash flow and money transfer. Different elements, such as a personal financial situation or high-interest rate, which makes the cost of borrowing more appealing, affect the subscription decision of the prospect. As such, banks benefit from data analysis and prediction models to optimize their campaigns by targeting certain segments of individuals.

## Dataset and Methodology

In April 2014, Apple CEO Tim Cook told The Wall Street Journal that the company was planning to launch new product categories that year, but did not reveal any specifics. In June 2014, Reuters reported that production was expected to begin in July for a release in October.

Apple Watch was first unveiled after a classic and ever infamous “We do have ‘one more thing’…” slide, which heard enormous applause, on September 9, 2014 during a press event which also saw the introduction of the iPhone 6. After the reveal video, the auditorium erupted with applause while Tim Cook rolled back his sleeve, revealing an Apple Watch on his wrist. Speaking about the device, Apple CEO Tim Cook explained that Apple Watch was “a new, intimate way to communicate from your wrist, and a comprehensive health and fitness device.”


## Dataset and Methodology

Dataset and Methodology
Our data on individuals have been taken from UCI machine learning repository online from May 2008 to November 2010. The dataset includes 45,211 observations from a Portuguese retail bank for which it has dependent variables, whether the prospect subscribes to a term deposit or not, and the independent variables are listed below.

- age — age of the costumer (numeric)
- job type of job (categorical: ‘admin.’,’blue-collar’,’entrepreneur’,’housemaid’,’management’,’retired’,’self-employed’,’services’,’student’,- ’technician’,’unemployed’,’unknown’)
- marital marital status (categorical: ‘divorced’,’married’,’single’,’unknown’; note: ‘divorced’ means divorced or widowed)
- education — (categorical:’basic.4y’,’basic.6y’,’basic.9y’,’high.school’,’illiterate’,’professional.course’,’university.degree’,’unknown’)
- default — has credit in default? (categorical: ‘no’,’yes’,’unknown’)
- housing has housing loan? (categorical: ‘no’,’yes’,’unknown’)
- loan — has personal loan? (categorical: ‘no’,’yes’,’unknown’)
- contact — contact communication type (categorical: ‘cellular’,’telephone’)
- month -last contact month of year (categorical: ‘jan’, ‘feb’, ‘mar’, …, ‘nov’, ‘dec’)
- day_of_week -last contact day of the week (categorical: ‘mon’,’tue’,’wed’,’thu’,’fri’)
- duration last contact duration, in seconds (numeric). Important note: this attribute highly affects the output
target (e.g., if duration=0 then y=’no’). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
- campaign -number of contacts performed during this campaign and for this client (numeric, includes last contact)
- pdays: — number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
- previous -number of contacts performed before this campaign and for this client (numeric)
- poutcome — outcome of the previous marketing campaign (categorical: ‘failure’,’nonexistent’,’success’)
- emp.var.rate — employment variation rate — quarterly indicator (numeric)
- cons.price.idx — consumer price index — monthly indicator (numeric)
- cons.conf.idx — consumer confidence index — monthly indicator (numeric)
- uribor3m — euribor 3 month rate — daily indicator (numeric)
- nr.employed- number of employees — quarterly indicator (numeric)
- subscribed- has the client subscribed a term deposit? (binary: ‘yes’,’no’)
source: https://archive.ics.uci.edu/ml/datasets/bank+marketing


We use python as a programming language utilizing the tools of Scikit-learn for our machine learning approach. We are employing the following classified algorithms, Logistic Regression, Decision Tree, Random Forest, and XGBoost for our prediction.

## Purpose

Our goal is to build a model to predict if a prospect will subscribe to a term deposit campaign.

Using historical data, we built a model to predict future investors in bank term deposit in order to develop a targeted telemarketing strategy for the bank of Portugal.

## Data Analysis and Coding Technicalities

We analyzed the data to determine the rate of subscribers per category within each feature.

We used a loop function to calculate the percentage of subscribers from prospects contacted. We extracted a data set for each feature and the subscribed column. We used the size() method to count the number of instances while applying a pivot function to create a column for ‘yes’ and ‘no’ to calculate the percentage rate per each category (e.g. university graduates, high school graduates) within a feature (e.g. education, marital). In the second part of the loop function, we plotted the results for each feature. We will touch upon a few graphs we generated.

`![Image description](assets/images/posts/2018/age_graph.jpg)`


Seniors' (ages 65 to 98) subscription rate is three times as much as Older Adults (ages 56–65) and Young adults (ages 17–35). Middle Aged Adults (ages 36–65) have the lowest rate of subscription at 8.65%.
Occupation





Students and retired individuals were twice or three times more likely to subscribe than any other profession. Unemployed and administration professionals were the next highest group, ranging from 11.3% to 13% rate of subscribers, whereas the rest of the groups were less than 11.31%.
Method of Communication
The rate of subscription for people contacted by cellular phone is 10% higher than for those contacted on a regular phone.
Building Predictive Models
After cleaning the data and exploring different trends, I prepared the data to run the following classified models for our prediction: Logistic Regression, Decision Tree, Random Forest, and XGBoost.
In our data, there are two possible outcomes: whether an individual subscribes to a term deposit or not. Given that our data is unbalanced, where only 11% of the individuals subscribed and not even equality represented with the group that unsubscribed, it can lead to inaccurate results when we employ a predictive model. In such scenarios of class imbalance, it is recommended to use Synthetic Minority Over - Sampling Technique. We implemented SMOTE- Nominal and Continuous ('SMOTE-NC') on our training data which contains categorical and numerical data.
Score and Pipeline Function
We built a function that captures the classified models, trains them, and produces the scoring results (Accuracy, Precious Recall, and F1_Score). We added an "if statement" with a display element to have the option to not display when unnecessary.
We used a pipeline to streamline several steps that are required to pass through the data before implementing the predictive classified model. The pipeline was also helpful when we split the data into training and testing because we did not want the information from training data to be leaked into the unseen testing data.
We inserted the pipeline as part of a function so that it can loop around when we employed the various classified models.
Our data contains numerical and categorical variables. We separated the data sets into numerical and categorical data, since the StandardScaler() feature is only needed for the numerical data, and the OntHotEncoder() function is only needed to convert the categorical subset to a numerical form.
When the data passed through the pipeline, it went through the first step of StandardSclare() and OneHotEncoder(). The adjusted data fit the model/classifier and ultimately produced predictive values for the testing and training data and reverted back to the model scoring.
In this project, if the model predicts falsely that a prospect will subscribe when in fact, they are unlikely to subscribe to the term deposit campaign, then it is not worth the cost of pursuing leads that offer no potential for a positive return on investment.
Similarly, if a prospect is falsely labeled as a customer who is not likely to subscribe when in fact, they are likely to subscribe, then it is a missed opportunity for the bank to gain a client that might deposit funds.
Therefore, it is important to focus on the f1 score, which takes into consideration both false predictions.
We hyper-tuned Random Forest using GridSearch:
param_grid_rf = {
'model__n_estimators': [100, 300, 600, 900, 1200],
'model__max_features': [2, 4,6,8,10,12,14],
'model__max_depth' : [50, 100, 200],
'model__criterion' :['gini', 'entropy']
}
grid_clf_rf = GridSearchCV(pipeline_rf, param_grid_rf, scoring='accuracy',
cv=3, n_jobs=-1,verbose=2)
GridSEarchCV suggested the following criteria, which produced the following results:
{'model__criterion': 'gini',
'model__max_depth': 200,
'model__max_features': 14,
'model__n_estimators': 900}
Training_Accuracy: 0.9960036496350365
Test_Accuracy: 0.8729356906936079
Precision: 0.8685113598591178
Recall: 0.8729356906936079
F1_Score: 0.8706234452833183
The model generated the following features of importance:
​​
Conclusions:
In this project, we implemented data analysis and predictive classified models to predict term deposit subscriptions at a Portuguese bank institution. With an F1 Score of 87% using Random Forest, the following business recommendations are:
Pay close attention to socioeconomic data:
3 Month Euribor rate - The Euribor rate is based on the average interest rates at which Eurozone banks lend funds to other banks. Ramp up the campaign when rates are high. A prospect is more likely to invest in a term deposit, knowing that they will receive a high-interest rate.
Consumer Confidence Index - Individuals are more likely to invest if their financial situation is good and if the country's outlook is optimistic.
Target telemarketing calls toward selecting individuals who belong to a specific age group and occupation. Seniors, Students, and Retired Individuals are more likely to subscribe to a term deposit.
Conduct the campaign during specific months. March, September, and October have been shown to have a higher rate of subscriptions.

source : https://archive.ics.uci.edu/ml/datasets/bank+marketing
The data is related to direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe to a term deposit (variable y).
[Moro et al., 2014] S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22–31, June 2014
https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html
https://stackoverflow.com/questions/38787612/how-to-extract-feature-importances-from-an-sklearn-pipeline
https://www.investopedia.com/terms/f/financialinstrument.asp
https://www.investopedia.com/terms/e/euribor.asp
https://academic.oup.com/gerontologist/article/42/1/92/641498
https://www.global-rates.com/en/interest-rates/euribor/euribor-interest-3-months.aspx
