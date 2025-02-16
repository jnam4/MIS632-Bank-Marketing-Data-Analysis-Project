# MIS631-Bank-Marketing-Data-Analysis-Project
### Why I chose this dataset
I chose the Bank Marketing Data Analysis Project for my MIS631 course because it aligns closely with my academic background and professional aspirations. With an undergraduate degree in Finance, I have always been fascinated by the intersection of financial strategies and data-driven decision-making. This project allowed me to combine my foundational knowledge in finance with advanced skills in database management and analytics, which are critical in today’s data-centric business environment.

My interest in cutomer service derives me to have curiosity in the deep understanding customer behavior and optimizing marketing strategies motivated me to explore this dataset. Through analyzing banking marketing campaigns dataset, it allow me to uncover actionable insights that directly impact business performance. Moreover, thoroughout this project, I was able to deepen my expertise in data modeling, SQL, and visualization tools like Tableau, while also gaining hands-on experience in leveraging data to solve real-world business problems.

This project reflects my passion for bridging financial acumen and analytical skills to drive meaningful outcomes, and it serves as a strong foundation for my future career in data analytics.


## Overview
This project analyzes customer subscription patterns in a banking marketing dataset using PostgreSQL. 
The goal is to derive actionable insights to optimize campaign strategies.

### Features
- Relational database design and implementation.
- Analysis of 40,000+ records to uncover patterns in customer behavior.
- Key focus on call durations, contact methods, and financial attributes.

### Project Highlights
- Discovered the actionable insights for the business to perform and achieve higher targeting performance
- Normalized and structured raw data for enhanced usability.
- Visualized insights using Tableau and Excel.

### Tools Used
- PostgreSQL: Relational database for data storage and querying.
- SQL: Complex queries for insights on customer behavior and campaign success.
- Tableau/Excel: Visualization of trends and patterns.



# Problem statement
### Current Situation
Banks rely heavily on marketing campaigns to promote their financial products. However, intense competition in the market, driven by factors such as fluctuating interest rates on mortgage and certificate of deposit (CD) products and the increasing reliance on digital platforms, has made it challenging for banks to attract customers. Additionally, many banks are no longer hiring traditional bankers due to emerging technological innovations that allow customers to independently compare financial products and apply for them online. Therefore, an effective marketing strategy has become crucial for banks to remain competitive in the market

Despite significant investments in marketing, banks often struggle with low conversion rates, as many campaigns fail to successfully convert leads into customers. Furthermore, insufficient targeting leads to higher costs and reduced return on investment (ROI), ultimately impacting the overall performance of marketing campaigns and business profitability.

### Business Problem
In this competitive landscape, banks need effective strategies to attract and retain customers who are more likely to subscribe to term deposit products. 

Achieving this requires identifying key factors influencing customer decisions and optimizing marketing efforts to focus on high-potential leads, thereby enhancing conversion rates and reducing costs.


### Goal
The goal is to develop a database system that supports predictive analytics, enabling banks to derive actionable insights for improved customer targeting. By analyzing data, the system aims to predict with greater accuracy whether a client is likely to subscribe to a term deposit through direct marketing campaigns.





# Data Exploration
### Dataset
- Source: [Bank Marketing Dataset] (https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)
- Authors: Paulo Cortez (Univ. Minho) and Sérgio Moro (ISCTE-IUL), 2012
- Size:
    Rows: 4,521 clients
    Columns: 17 attributes
![alt text](images/image-4.png)
![alt text](images/image-2.png)
- Key Attributes
    - Demographics: age, job, marital status, education.
    - Financial Data: balance, housing loan, personal loan.
    - Campaign Details: contact type, day, month, duration, previous outcomes.
    - Target Variable: y (indicates if the customer subscribed to a term deposit: yes/no).  


### Data Cleaning Process
To ensure the dataset is ready for analysis, the following cleaning steps were applied.
1. Handling Missing and Unknown Values:
Certain fields, such as job and education, contained missing or incomplete data labeled as “UNKNOWN.” These accounted for less than 3% of the dataset and were replaced with the most frequently occurring value (mode) for accuracy.

2. Detecting and Managing Outliers:
Outliers were detected in the "balance" attribute using the Interquartile Range (IQR) method.
Extreme values waere either capped or removed to reduce their impact on the analysis


### Data Modeling
![alt text](images/image-3.png)
This analysis distinguishes three key entities in the dataset: Customer, Campaign, and Customer_Campaign.

- Customer: Represents individual clients. Each customer can participate in multiple campaigns, establishing a one-to-many relationship between customers and campaigns.
- Campaign: Represents marketing efforts. Each campaign records one response per customer, forming a one-to-one relationship between campaigns and customer responses.
- Customer_Campaign: Serves as a linking entity that connects customers to campaigns and tracks their interactions.

By looking at these entities, I was able to come up with some ideas to explore
1. **Customer Profiles** : What customer characteristics or profiles are more likely to result in a subscription to a term deposit?
2. **Campaign Success**: Which campaigns demonstrate the highest success rates in achieving customer subscriptions?
3. **Contact Duration**: How does the duration of contact during a campaign influence its success?


### Data Observation
![alt text](images/image.png)

The analysis of the dataset reveals interesting patterns in customer profiles and their job distribution.

**Educational Influence on Jobs**: As education levels rise, the proportion of individuals in high-skilled occupations, such as "Management," increases significantly. Conversely, roles that are labor-intensive, such as "Blue-collar" jobs, are predominantly associated with individuals who have only primary education. This trend reinforces traditional employment patterns where higher education levels align with greater career mobility and access to skilled job opportunities.

**Educational Insights**: Lower education levels are generally linked to routine or manual labor roles. This observation underscores the importance of education in shaping job prospects and advancing career trajectories.

# Key Finding and Analysis
### Observation 1: Relationship Between Loan, Housing, Default, and Job
![alt text](images/image-6.png)
![alt text](images/image-5.png)
- Customers with no housing or personal loans and those not in default exhibited higher financial stability, leading to increased campaign success rates. Jobs such as management represent financially stable and high-value targets, making them ideal for premium banking services.
- Blue-collar and technician customers showed mixed financial stability, often with lower balances among those with loans or housing loans. In contrast, customers with extreme negative balances may require debt restructuring or personalized financial counseling.

- Insight: Focus on targeting financially stable customers while designing tailored support for those with lower financial stability to improve overall conversion rates.


### Observation 2: Effectiveness of Contact Methods
![alt text](images/image-7.png)
![alt text](images/image-8.png)
- Cellular contacts contributed the highest total volume of successful subscriptions despite a slightly lower success rate (14.36%) compared to telephone (14.62%). The unknown contact method underperformed with a 4.61% success rate.

- Insight: While telephone campaigns are more efficient for smaller, focused groups, the large reach of cellular campaigns makes them the most impactful overall. A balanced strategy leveraging both methods is essential to maximize outreach and conversions.


### Observation 3: Relationship Between Previous Campaign Outcomes and Success Rate
![alt text](images/image-9.png)
![alt text](images/image-10.png)
- Customers with a successful previous campaign outcome (poutcome = success) had a significantly high 64.34% success rate, demonstrating the importance of nurturing existing relationships.
- In contrast, those with a failure outcome had only a 12.86% success rate, while the unknown group—despite being the largest segment—achieved just 9.10% success.

- Insight: Prioritize customers with previous successes and develop targeted engagement strategies for the unknown group to improve conversion rates. Minimize marketing efforts for customers with prior failures unless new insights suggest otherwise.


### Observation 4: Relationship Between Call Duration and Success Rate
![alt text](images/image-11.png)
![alt text](images/image-12.png)
- Long calls (>300 seconds) demonstrated the highest success rate (28.19%), indicating meaningful and productive customer interactions. Medium calls (100–300 seconds) had a significantly lower success rate (6.86%), suggesting room for improvement in engagement strategies during these calls. Short calls (<100 seconds) were largely ineffective, with only a 1.32% success rate, possibly reflecting rushed or unproductive interactions.

- Insight: Focus marketing efforts on customers who show interest during initial interactions, prioritizing long, meaningful calls to maximize conversions. Enhance engagement tactics for medium-duration calls and avoid relying on short calls as they lack effectiveness.




# Recommendations
To address the challenges of low conversion rates in banking marketing campaigns, several strategies can be implemented to optimize customer targeting and engagement. One key recommendation is to train staff to focus on extending meaningful conversations during calls, particularly with high-potential customers. Analysis has shown that long-duration calls result in significantly higher success rates (28.19%), emphasizing the importance of productive and engaging customer interactions.

Additionally, targeted marketing strategies should prioritize customers with previous successful outcomes and high account balances, as these groups are more likely to convert. For customers with unknown or prior failed outcomes, personalized campaigns tailored to their profiles can improve engagement and increase conversion rates. By leveraging predictive analytics, banks can identify key customer segments and develop strategies that maximize the return on investment (ROI) for marketing campaigns.

While cellular and telephone channels both play important roles, the focus should not be limited to either method. Instead, efforts should center on ensuring meaningful conversations, regardless of the communication channel. Cellular campaigns, due to their broad reach, remain essential for maximizing total contact volume, while telephone campaigns offer higher success rates for focused, smaller groups.

These recommendations directly address the business problem of improving customer acquisition in a competitive banking environment. By combining targeted strategies, meaningful engagement, and data-driven decision-making, banks can enhance their campaign effectiveness, reduce costs, and achieve sustainable growth.


### Recommendation ideas
1. Focus resources on **longer call durations** and train staff to foster meaningful interactions.
2. Develop personalized re-engagement strategies for customers with `unknown` or `failure` outcomes.
3. Prioritize **telephone** and **cellular** channels while improving data quality for `unknown` contacts.
4. Use financial stability indicators (e.g., balance, loan status) to segment and target high-value customers.



# Repository Structure
- `data/`: Contains the original dataset.
- `sql_scripts/`: SQL scripts for creating tables, inserting data, and running queries.
- `analysis/`: Insights and visualizations derived from the analysis.
- `docs/`: Final presentation and report documents.


# Contact
- name: Jiyun Nam
- email: jnam4@stevens.edu
- linkedin: [Click Here](https://www.linkedin.com/in/jiyunnam/)
