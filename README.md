# Customer Acquisition & Retention through Data Mining
GOAL: To help Banks and other institutions understand their customers and their individual usage patters to recommend/ cross-sell other products and services, using Association Rule Mining or otherwise known as Market Basket Analysis.

<img src="img/bank.jpg?raw=true"/>

## INTRODUCTION
Data Mining helps in the process of optimized targeting, making it easier for banks to instantly identify the high-value customer segments most likely to respond. The customer base can further expand by acquiring the right type of customer. Based on a report, it was seen the banks that adopted data & analytics had an increase of about 10%  in new customer opportunities over a year. <br>

Also data mining helps banks and financial institutions retain their customers. It: <br>

1. Identifies the customers most likely to defect before they end their relationship.
2. Keeps the right customers longer.
3. Predicts which actions will earn their loyalty.
4. Discovers the churn patterns and develop profiles of users who have left, 
5. Get an insight of why they left and discover strategies to keep them satisfied.

Customer retention is another area where banks need to focus more today in order to reduce customer sapping. Loyal customers need to be rewarded and customer attrition needs to be minimized. Sometimes it gets too late to retain a customer because they tend to have a large customer base and hence lose track of them. It’s easy to look out for a new customer but the old ones are always valuable. Data Mining helps identify which customers are willing to switch to any other bank and the reason behind their decision. It examines customer’s service performance, spending, past service and other behavior patterns to predict the likelihood of a customer wanting to stop its services anytime in the near future.

### Association Rule Mining/ Market Basket Analysis/ Affinity Analysis

Unsupervised learning is all about pattern discovery. It is a type of machine learning where the main focus is to find regularly occurring patterns in a group of data. Usually these patterns are hidden or buried deep in the data and are undetected. This type of machine learning needs no supervision as the input data has no references or labels for the algorithm to learn, enabling it to learn on its own without any bias, gather inferences and find out patterns. One such technique is ssociation rule mining. <br>

Affinity analysis is a data analysis and data mining technique that discovers co-occurrence relationships among activities performed by specific individuals or groups. In general, this can be applied to any process where agents can be uniquely identified and information about their activities can be recorded. It is one of the key techniques used by large organizations to uncover associations between items. It works by looking for combinations of items that occur together frequently in transactions. To put it another way, it allows companies to identify relationships between the items that people buy.

### Data Preparation

<img src="img/1.png?raw=true"/>

#### Data Exploration:

<img src="img/2.png?raw=true"/>

This data set contains 32367 rows. The unit level of analysis i.e. each row represents the each visit of the customer to the bank. The dataset has records of each visit of the customer separately irrespective of some customers visiting more than once. One customer could occupy multiple rows depending on how many times he/she visited the bank. Therefore, if a customer spans across many rows, it simply means that they have visited the bank multiple times.  

<img src="img/3.png?raw=true"/>

Maximum number of visits made among all customers is 11.

#### Variable plots
•	Account

<img src="img/4.png?raw=true"/>

•	Service

<img src="img/5.png?raw=true"/>

•	Visit

<img src="img/6.png?raw=true"/>

### Variable Selection & Role Definiton

<img src="img/7.png?raw=true"/>

•	We have Rejected visit because we are interested in analysing co-adoption at a customer level and not at a customer-visit level. <br>
•	Account – is the ID because our analysis is per customer, since each customer has a unique account number, it becomes the ID for them to uniquely identify them to understand the adoption of different services provided by the bank. <br>
•	Service- is the Target because we are interested in association rules in the variable service for each account, therefore different service provided by the bank becomes our target variable for this analysis.

### Building the Association Model

<img src="img/8.png?raw=true"/>

### Model Evaluation

The basic criteria used to evaluate association rules include Support and Confidence. Lift is another measure that can be used for evaluation. 
•	Support <br>
Support measures the relevance of the rule.  <br>
Support= (L&R count)/Total N <br>

The numerator has the frequency of body & head of the rule co-occurring while the denominator consists of the total number of rows in the data set. <br>
Having a defined set value for minimum Support will help in ruling out the association rules whose body and head do not have enough representation in the data set. For example if we have a shopping store data set with 100 rows, if the body and head of the association rule co-occur 10 times, say milk and eggs co-occur 10 times in all the shopping transactions for a store, then the support would be 10/100 => 10 %, indicating the rule might not be very useful to the data set. <br>

•	Confidence <br>
Confidence measures the strength of the rule. <br>
Confidence= (L&R count)/L count <br>

This formula gives the proportion of transactions that has the head provided it has the body.<br>
Higher the value of confidence, stronger the association rule. Therefore, we can set a minimum confidence measure to eliminate rules that do not satisfy. For example, if we use a rule If {milk} -> Then {eggs},  and eggs are bought in all 10 cases where milk was bought, then our confidence would be 10/10= 100% implying that that whenever milk is bought, customers will also buy eggs all the time. <br>

•	Lift <br>
Lift measures the likeliness of the head provided the body has occurred. <br>
Lift= confidence/ frequency of head <br>

From our example, If {milk} -> Then {eggs}, if 20 customers buy milk, 5 customers buy eggs and 10 customers buy milk and eggs together out of 100 customers, then confidence= 10/20= 50 %. Frequency of head = 5/ 100 = 5%. Therefore, lift will be 50/5= 10. This essentially means that customers buying milk are 10 times more likely to buy eggs as well, which sounds like it will be an extremely promising association rule to the store owner.  <br>


<img src="img/9.png?raw=true"/>

Highest lift value for the resulting rules: 3.33

<img src="img/10.png?raw=true"/>

Top 10 rules with highest lift value:

<img src="img/11.png?raw=true"/>

### Results Interpretation

•	Based on the highest lift value, we can see customers who have Checking Account (CKING) and credit card (CCRD), they are 3.33 times more likely to have Check/Debit card (CKCRD). The confidence is a bit low though at 37.5% and support is about 5.58% which is fine. <br>

•	Following that we have customers who have Check/Debit card (CKCRD), they are 3.33 times more likely to have Checking Account (CKING) and credit card (CCRD). While this has the same support & lift values as the previous one, it has a better confidence of 49.3%. <br>

•	At the third position, we have customers having Check/Debit card (CKCRD), they are 3.19 times more likely to have credit card (CCRD). This rule has a support of 5.5 %, confidence of 49.3 % with a good lift value as well of 3.19.

### Conclusions

Link Grapgh: 

<img src="img/12.png?raw=true"/>

<img src="img/13.png?raw=true"/>

From the link graph, we can see AUTO has links to ATM, CKING, SVG, CKING & ATM, SVG & CKING. This essentially means that these services have association rules that involve AUTO- Automobile loans. <br>
Therefore, for customers who have taken automobile loans, the recommendation would be to take standalone products/ services like: <br>
•	Checking account <br>
•	Saving account <br>
•	Automated teller machine debit card <br>

From the link graph, we could also recommend a combination of services including: <br>
•	Checking account & ATM <br>
•	Checking account & saving account <br>

### Business Recommendations

1.	For customers having a Checking Account (CKING) and credit card (CCRD), recommend Check/Debit card (CKCRD). <br>
Support- We have customers who have Checking Account (CKING) and credit card (CCRD), they are 3.33 times more likely to have Check/Debit card (CKCRD). The confidence is a 37.5% and support is about 5.58%. <br>

2.	For customers having a Check/Debit card (CKCRD), cross sell a bundle of Checking Account (CKING) and credit card (CCRD). <br>
Support- We have customers who have Check/Debit card (CKCRD), they are 3.33 times more likely to go for Checking Account (CKING) and credit card (CCRD). While this has a support of around 5.6% & high lift values of 3.33, it has a confidence of 49.3% which is very good. <br>

3.	For customers having a Check/Debit card (CKCRD), promote the bank credit card (CCRD) with great partner offers/ discount vouchers. <br>
Support- We have customers having Check/Debit card (CKCRD), they are 3.19 times more likely to have credit card (CCRD). This rule has a support of 5.5 %, confidence of 49.3 % with a good lift value as well of 3.19 <br>

<img src="img/14.png?raw=true"/>

4.	For customers having a savings account, give them offers to open a checking account. <br>
Support- From the graph below, we can say that for customers having a savings account, they also go for a checking account. This association rule sits on top of the graph with high confidence of 87.5% and support of 54.17 %. <br>

<img src="img/15.png?raw=true"/>
