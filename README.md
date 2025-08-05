# Project Background

The dataset works with marketing campaign data from a Portugal bank in the financial service industry. The goal was to explore customer response patterns to outbound calls promoting term deposit products (similar to U.S. CDs). Some clients received multiple contact attempts to increase conversion rate among existing customers. Key business metrics analyzed were total campaigns ran, client response rate, contact frequency, and demographic insight to clients that subscribed. 

Insights and recommendations are provided on the following key areas:

- **Category 1: Client Financial Status**
- **Category 2: Demographics**
- **Category 3: Contact and Campaign Volume**

SQL queries were used to categories age groups and analyze trends in call times and peak months [link].

# Data Structure & Initial Checks

The main dataset consist of 1 table and 2 reference tables . First table contains the core campaign data, reference table 1 displays clients job types and reference table 2 showcases clients highest level of education 

- **Bank Marketing Table**
- **Job Type:** Treated as nominal data, as it represents categories with no order
- **Education:** Shows the clients highest level of education 


# Executive Summary

### Overview of Findings

From my analysts there seems to be several factors at play that can effect clients subscription behavior. Financial indicators such as personal loans, housing loans, or default history had little impact on whether a client subscribed. However, age and call duration played a small to moderate role in subscription behavior. Clients ages between 29-38 were key drivers of monthly performance, accounting for 43% of subscriptions in March. A slight trend was also observed by job types job type, with blue-collar workers, technicians, and administrative roles ranking among the highest across all age groups. Notably, repeat contact with the same client has a negative impact on clients decisions. However, focus on call duration should be taken into account as 20 minute or less seems to be when clients where more willing to subscribe. 


# Insight Deep Dive 

### Category 1: Client Financial Loyalty

**Main insight 1:**
Clients financial loyalty such as personal loan, housing loan, or defaulted to the bank did not have strong correlation with subscription outcomes
	Correlation Values: 
		-Default: -0.099
		-Housing Loan: 0.009
		-Personal Loan: -0.005


### Category 2: Demographics

**Main Insight 1:**
Age demographics appears to have some influence on how well a month performs. In particular ages 29-38 seemed to be most responsive on how well a month performed. They accounted for 39% of all subscriptions. 

**Main Insight 2:**
There was a small correlation of 8% when combining clients education and job type. Admin appeared amongst the top 3 job types in all demographics. In the age   age demographic of 29-38, admin job type accounted for 14% of job types that subscribed in this demographic 


### Category 3: Contact and Campaign Volume

**Main Insight 1:** 
There is a strong relationship between the number of calls made and subscription behavior. We found that a negative correlation (r= -.59) showed as the number of calls increased, chances of subscriptions declined. In addition, exponential trendline yielded 
R²=.96. This indicates the exponential model explains 96% of variation in subscription outcomes. Diminishing returns occur as continuous outreach to customers occurs.

**Main Insight 2:** 
Our linear regression analysis found a strong negative relationship between the number of campaigns and the number of subscriptions. Campaign volume explained 56% of the variation in "yes" responses, and the regression coefficient (-104) indicates that for each additional campaign, approximately 104 fewer clients subscribed on average. This suggests diminishing returns with high campaign frequency

**Main Insight 3:**
An analysis of 1,544 calls revealed a statistically significant negative relationship between call duration and subscription likelihood. Each additional minute on a call was associated with a 0.15 decrease in the probability of a client subscribing (coefficient = -0.00242). While the effect per minute is small, it becomes more meaningful as call times increase. Overall, call duration explained 26% of the variation in subscription outcomes, indicating that longer calls may be less effective.


# Recommendations 

Based on the insights and findings above, we would recommend the **Marketing Strategy Team** to consider the following:

- Clients aged 29–38 consistently showed the highest subscription rates, accounting for 40% of sign-ups. We recommend targeting this age group more heavily in future campaigns to maximize conversion potential.

- Job types appears to have a modest effect on clients willingness to subscribe, particularly among blue-collar, technician, and administrative roles. Our suggestion is incorporating job type segmentation into campaign planning to better tailor messaging. 

- Repeat outreach to the same clients negatively impacted subscription likelihood. We advise the Outreach or CRM Team to prioritize reaching a higher volume of unique clients rather than re-contacting the same clients.

- Call duration had a noticeable effect, clients were more likely to subscribe during calls under 20 minutes. We would advise the Training and Call Center Operations Team to focus on optimizing call scripts to stay within this time window.

# Assumptions and Caveats:

Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

- **Assumption 1:** Some assumption was made regarding clients financial indicators. Although we access if they have a current loan or defaulted, amount owed and other finances were not addressed in the dataset. I believe that additional financial variables (credit score, income level, debt level) should be considered before drawing conclusions about financial influence on clients subscription behavior. 

-  **Assumption 2:** The analysis was based solely on outbound call campaigns and did not include data from other marketing channels (e.g. emails, SMS, digital ads). This limits our ability to compare performance across channels and may skew results of campaign effectiveness   

- **Caveat 1:** The dataset only covers 1 year of data. As a result trends such as age demographics and call durations may be limited. Historical or multi-year data would provide more insight and help account for seasonality or patterns. 
