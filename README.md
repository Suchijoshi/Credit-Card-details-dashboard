
#Credit_Card_Financial_Dashboard
This project aims to develop a comprehensive credit card weekly dashboard using Power BI and SQL, providing real-time insights into key performance metrics and trends. The dashboard allows stakeholders to effectively monitor and analyze credit card operations, aiding in data-driven decision-making.

🚀 Project Objective
The main objective of this project is to create an interactive dashboard that offers insights into:
-Revenue Trends
-Transaction Metrics (Amount and Count)
-Customer Segmentation
-Delinquency and Activation Rates

🔑 Key Features
-Real-time Insights: Monitors critical KPIs such as revenue, transaction amounts, customer count, and delinquency rate.
-Year-to-Date Overview: Displays a summary of overall revenue (57M), interest (8M), and transaction amount (46M).
-Customer Analysis: Highlights contributions by male and female customers, and the distribution of card types (Blue & Silver).
-Geographical Insights: Analyzes the contributions from key regions (TX, NY, CA).
-Activation and Delinquency Rate: Tracks the overall activation rate (57.5%) and delinquency rate (6.06%).

🛠️ Technologies Used
-Power BI: For developing interactive dashboards and data visualization.
-SQL: For querying and processing data from a relational database.
-GitHub: For project version control and sharing.

📊 Data Insights
-Week 53 Insights: A detailed report of the week’s key changes, including a 28.8% increase in revenue, and increases in total transaction amounts and counts.
-Customer Demographics: Insights into male and female customer contributions to revenue, with male customers contributing more at 31M vs. 26M from female customers.
-Card Type Analysis: 93% of all transactions are contributed by Blue & Silver credit cards.

📊 DAX Queries Used
In this project, several DAX queries were implemented to analyze and categorize customer data, as well as to compute revenue metrics for weekly tracking. Below are the key DAX formulas used in the development of the dashboard:
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
'public cust_detail'[income] < 35000, "Low Income", 
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Medium Income", 
'public cust_detail'[income] >= 70000, "High Income", 
"unknown"
)

week_num2 = WEEKNUM('public cc_detail'[week_start_date])

Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

Current_week_Revenue = CALCULATE( 
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))

Previous_week_Revenue = CALCULATE( 
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

📢 Connect If you found this project useful or interesting, let’s connect on [LinkedIn](https://www.linkedin.com/in/joshisuruchi/).
