# Project Background

The dataset works with marketing campaign data from a Portugal bank in the financial service industry. The goal was to explore customer response patterns to outbound calls promoting term deposit products (similar to U.S. CDs). Some clients received multiple contact attempts to increase conversion rate among existing customers. Key business metrics analyzed were total campaigns ran, client response rate, contact frequency, and demographic insight to clients that subscribed. 

Insights and recommendations are provided on the following key areas:

- **Category 1: Client Financial Status**
- **Category 2: Demographics and Monthly Subscription Trends**
- **Category 3: Contact and Campaign Volume**

Main Dataset, Pivot Tables, and Statistical Test in Excel [link]

SQL queries were used to categories age groups and analyze trends in call times and peak months [link](https://github.com/jhern31627/bank_mkt/blob/601a5cd9396b033d34e7c77debaeda286579f35a/bank_mkt.sql).

Dashboard used to report exploratory analysis of demographics and call times [link](https://github.com/jhern31627/bank_mkt/blob/185797eb224492217ee9b382ef6785f4e7ea6218/bank_dashboard.xlsx)
# Data Structure & Initial Checks

The main dataset consist of 1 table and 2 reference tables.First table contains the core campaign data, reference table 1 displays clients job types and reference table 2 showcases clients highest level of education 

- **Bank Marketing Table**
- **Job Type:** Treated as nominal data, as it represents categories with no order
- **Education:** Shows the clients highest level of education 

![image](https://github.com/jhern31627/bank_mkt/blob/cc47fd46f706d133fddfa7fb3a18459b046019eb/images/ERD.png)
# Executive Summary

### Overview of Findings

From my analysts there seems to be several factors that influence clients subscription behavior, though not all variables showed significant impact. Financial indicators such as personal loans, housing loans, or default history had little impact on whether a client subscribed. In contrast age and job type showed patterns of possible trends. 

Clients ages between 29-38 were key influencers for monthly performance, accounting for 43% of all subscriptions in March due to the large population size. However, the Chi-Square test revealed that younger ages (17-28) and older ages (59+) subscribed at higher-than-expected rates relative to their group size. This suggests a stronger conversion potential within these age demographics.

Job Type played a role in subscription behavior with blue-collar workers, technicians, and administrative roles ranking among the highest across all age groups. Notably, repeat contact with the same client has a negative impact on clients decisions. This would suggest that follow-up strategies may need adjustment. 

Call duration showed a moderate positive relationship between average call times and successful subscriptions. Longer response times were associated with higher subscription counts. It is suggested that extended conversations may reflect greater client engagement and improve the likelihood of client subscribing.

# Insight Deep Dive 

### Category 1: Client Financial Loyalty

**Main insight 1:**
Clients financial loyalty to the bank such as personal loan, housing loan, or defaulted to the bank did not have strong correlation with subscription outcomes<br><br>
**Correlation Values:**
- Default: -0.099
- Housing Loan: 0.009
- Personal Loan: -0.005

![image alt](https://github.com/jhern31627/bank_mkt/blob/2052f2a686f589e389448dc4eb48d9a93ab810db/images/fin.png)<br><br>
### Category 2: Demographics and Monthly Subscription Trends
**Main Insight 1:**
Subscription behavior varied significantly across both ages demographics and months. Months of May, August, and July showed the highest total subscriptions, with May having the highest at 886 subscriptions. 

Across all months the age demographic of 29-38 contributed the largest share of subscriptions, making this age group the key driver of monthly performance. In May, this age group (29-38) had 374 out of 886 subscriptions (42%). However, closer analysis revealed other age groups had a stronger part in current months: 

- 17-28 showed strong performance in spring, peaking at 130 subscriptions in May. 
- 59+ had notable contributions in the months of October and August, with 64 and 87 subscriptions. This showed an increase in responsiveness despite the smaller group size. 

The patterns indicate that, while the 29-38 age group remains the dominant segment based on volume, other age groups show meaningful contribution during certain months. Seasonal outreach to younger and older crowds could boost campaign effectiveness, especially in high performance months. 

![image alt](https://github.com/jhern31627/bank_mkt/blob/57e183ebde9acd147b2dedc6b0e10fa8730d4186/images/chi_test.png)<br><br>
![image alt](https://github.com/jhern31627/bank_mkt/blob/5c3fb7c25dc2b57150bb192c7426f1541894751a/images/age_group_month.png)
![image](https://github.com/jhern31627/bank_mkt/blob/3e8b964b0cbb9937b23251dd341d7f1cae9fec93/images/total_subs.png)
<br><br>**Main Insight 2:**
There was a small correlation when combining clients' education (0.057) and job type (0.025) together, accounting for 8% correlation. Despite jobs having a low correlation (0.025) to subscription behavior, repeat job titles were among the top 3 of all the age demographics. Job types  of admin, technician, and blue-collar, where among one of the top job types in each age demographics. Further analysis should be done to see if job type has more of a significance to subscription behavior. <br><br>

![image alt](https://github.com/jhern31627/bank_mkt/blob/60dc62954fd133ad99af364978a332b7167313c5/images/topJobs.png)

### Category 3: Contact and Campaign Volume

**Main Insight 1:** 
There is a strong relationship between the number of calls made and subscription behavior. We found that a negative correlation (r= -0.59) showed as the number of calls increased, chances of subscriptions declined. In addition, exponential trendline yielded 
R²=.96. This indicates the exponential model explains 96% of variation in subscription outcomes. Diminishing returns occur as continuous outreach to customers occurs.

![image alt](https://github.com/jhern31627/bank_mkt/blob/2052f2a686f589e389448dc4eb48d9a93ab810db/images/frequency.png)<br><br>
**Main Insight 2:** 
Exploratory analysis was done to determine if average call duration times affect whether age group is more likely to subscribe. There was a moderate positive relationship, showing longer response times were associated with higher subscription counts. 

![image](https://github.com/jhern31627/bank_mkt/blob/f94134ce3153c045c2bbdeae85cbbbc67ee18085/images/pivot_table_age_month_duration.png)

*Supporting Analysis*

Subscriptions totals were broken down by age group and month. For each age group in each month we compared the average call duration (secs) it took before a positive response for a subscription. A correlation test returned a value of .59 indicating a moderate positive linear relationship between response and subscription count.

In order to check validation linear regression was performed using average response times as independent variable and total "yes" subscriptions count as the dependent variable. Results showed: 

- R² = 0.35, showing average response times explain 35% of the variation in subscription counts 

- p-value = 6.2 × 10⁻⁶, indicating results are statistically significant 

- Slope = 0.29, for every additional second in average response times, there should be an expected increase of approximately 0.29 subscriptions 

Results would suggest that longer call duration may be associated with more successful subscriptions. This could reflect greater client engagement or interest during extended conversations.

![image](https://github.com/jhern31627/bank_mkt/blob/f94134ce3153c045c2bbdeae85cbbbc67ee18085/images/duration_age.png)
<br><br>


**Main Insight 3:**
An analysis of 1,544 calls revealed a statistically significant negative relationship between call duration and subscription likelihood. Each additional minute on a call was associated with a 0.15 decrease in the probability of a client subscribing (coefficient = -0.00242). While the effect per minute is small, it becomes more meaningful as call times increase. Overall, call duration explained 26% of the variation in subscription outcomes, indicating that longer calls may be less effective.

![image alt](https://github.com/jhern31627/bank_mkt/blob/2052f2a686f589e389448dc4eb48d9a93ab810db/images/camp_vol.png)

# Recommendations 

Based on the insights and findings above, recommendation as followed:

- The 29-38 age group accounted for the largest share of total subscriptions (40%). However, the Chi-Square test showed that younger age groups (17-28) and older age groups (59+) subscribed at higher rates relative to their group size. We recommend continuing to target the 29-38 age demographic based on the volume, but campaign efforts should also focus on younger and older age groups, who may offer higher conversion rates.


- Job types appears to have a modest effect on clients willingness to subscribe, particularly among blue-collar, technician, and administrative roles. Our suggestion is incorporating job type segmentation into campaign planning to better tailor messaging. 

- Repeat outreach to the same clients negatively impacted subscription likelihood. We advise the Outreach or CRM Team to prioritize reaching a higher volume of unique clients rather than re-contacting the same clients.

- Call Center Operations should shift away from meeting target duration requirements, as it appeared that longer call lengths affect subscription volume. New efforts should focus on improving call quality and adjust message delivery based on clients. These factors will likely influence a client's decision to subscribe to a product.
  
# Assumptions and Caveats:

Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

- **Assumption 1:** Some assumption was made regarding clients financial indicators. Although we access if they have a current loan or defaulted, amount owed and other finances were not addressed in the dataset. I believe that additional financial variables (credit score, income level, debt level) should be considered before drawing conclusions about financial influence on clients subscription behavior. 

-  **Assumption 2:** The analysis was based solely on outbound call campaigns and did not include data from other marketing channels (e.g. emails, SMS, digital ads). This limits our ability to compare performance across channels and may skew results of campaign effectiveness   

- **Caveat 1:** The dataset only covers 1 year of data. As a result trends such as age demographics and call durations may be limited. Historical or multi-year data would provide more insight and help account for seasonality or patterns. 
