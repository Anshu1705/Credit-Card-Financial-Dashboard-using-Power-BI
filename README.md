# "CreditVision: Power BI Insights for Credit Card Financials"


Here, we've crafted a dynamic weekly dashboard that offers real-time insights into crucial performance metrics and trends. This tool empowers stakeholders to efficiently monitor and analyze credit card operations, ensuring informed decision-making and proactive management. Dive into our dashboard and unlock the power of data-driven insights for optimizing credit card operations!






# DAX Queries

AgeGroup = SWITCH(

TRUE(),

'public cust_detail'[customer_age] < 30, "20-30",

'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",

'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",

'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",

'public cust_detail'[customer_age] >= 60, "60+",

"unknown"

)


IncomeGroup = SWITCH(

TRUE(),

'public cust_detail'[income] < 35000, "Low",

'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",

'public cust_detail'[income] >= 70000, "High",

"unknown"

)


# DAX Queries 


week_num2 = WEEKNUM('public cc_detail'[week_start_date])

Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

Current_week_Reveneue = CALCULATE(

SUM('public cc_detail'[Revenue]),

FILTER(

ALL('public cc_detail'),

'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))

Previous_week_Reveneue = CALCULATE(

SUM('public cc_detail'[Revenue]),

FILTER(

ALL('public cc_detail'),

'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))



# Project Overview

[Credit.Card.Financial.Dashboard.pdf](https://github.com/user-attachments/files/15774523/Credit.Card.Financial.Dashboard.pdf)





# Project Insights

WoW change:

• Revenue increased by 28.8%,

• Total Transaction Amt & Count increased by xx% & xx%

• Customer count increased by xx%

Overview YTD:

• Overall revenue is 57M

• Total interest is 8M

• Total transaction amount is 46M

• Male customers are contributing more in revenue 31M, female 26M

• Blue & Silver credit card are contributing to 93% of overall
transactions

• TX, NY & CA is contributing to 68%

• Overall Activation rate is 57.5%

• Overall Delinquent rate is 6.06%









