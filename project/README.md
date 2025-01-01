# PFDA

PWC Call Centra Data Analysis

Objective 
Analyze call centre data to improve performance and customer satisfaction.

Dataset 
The original dataset contained 10 columns and 5,000 rows. The dates within the dataset ranged from January 1st to March 31st 2021. The dataset was downloaded from Kaggle, added to a database I created in MySQL and then was connected to via Python.

Table of Contents:
1. Introduction
2. Data Preperation
3. EDA
4. KPI Analysis
5. Advanced / Interactive Plots
6. Advanced Analysis
7. Insights and Recommendations



1. Introduction : 

This notebook contains my analysis of PWC contact centre data. The original dataset contained 10 columns and 5,000 rows. The dates within the dataset ranged from January 1st to March 31st 2021. The dataset was downloaded from Kaggle, added to a database I created in MySQL and then was connected to via Python.

2. Data Preperation :

The first step of preperation was creating a database to store the data. This was done through a combination of bash scripts and MySQL queries. Once this was done I took the usual steps of setting the index, creating/dropping columns, dealing with null values, etc.

3. EDA :

This part of the notebook is where I explore the data, looking for potential trends through the creation of visuals. I used .info() and .describe() to get a better understanding of the data. The visuals created in this section were boxplots, barcharts, pie charts and a line plot. The most insightful visual was the pie chart which showed that 70% of unresolved issues were due to calls not being answered. The line plot shows how the call volumes can differ substantially day to day. In section 5, a more complex version of this plot is added use plotly.

4. KPI Analysis :

(i) Operational Efficiency - Average Call Duration & Resolution Rate :

In this section I look at average call duration and resolution rate to see if there are areas for improving performance. For call duration when looking at Agents and Topics they are pretty consistent across the board. Call duration by topic or agent are all within 10 seconds of the overall average. For that reason I dove deeper into the data looking at the combinations of Agents and Topics where the call duartion is above the total average. This shows specific topics agents can focus on to improve their numbers and close calls out quicker. I looked at outliers to narrow down the 5% of longest calls. That is more of a reference point again for potential areas to focus on improving. For example Agent Dan is in that top 5% 11 times for payment related calls.

With resolution rate I discovered in the EDA section that a high number of these unresolved issues is due to calls not being answered. When looking at resolution rates by Agent and Topic, similar to avg. call duration the results are quite even with the average resolution rate being 73%. I've highlighted in the analysis agent and topic combinations where PWC could focus on improving. Finally I reviewed the correlation between call volume and unanswered calls which was 0.9988 meaning that there is a strong positive relationship between the two variables.


(ii) Customer Satisfaction - Satisfaction Rating :

During my analysis of customer satisfaction I focused on the satisfaction rating agents get for each call. This rating ranges from 0-5. PWCs average rating was 2.76 which isn't great. Unanswered calls were bringing this average down as an unaswered call automatically gets a 0. The satisfaction rating when an issue was resolved was 3.40. I copied the same framework for this analysis as I did for operational efficientcy, getting the combinations of agents and topics that were below average. I finally added another line chart showing the satisfaction ratings overtime. For the majority of January the satisfaction ratings were above the average and then dipped substantially for February and March. With additional context or data I would be able to tell why this is happening. 

(iii) Agent Performance - Resolution Rate, Satisfaction Rate & Call Volume Handled

The agent performance analysis was a combination of what was done in the Operational Efficiency and Customer Satisfaction sections. These KPI's overlap so it made sense to approach it this way. I created bar charts with agents resolution and satisfaction ratings and then created heat maps adding in the topics to easily identify weak points. I finally looked at the correlation between resolution rate and satisfaction rating and visualized the results. The correlation between the two was 0.54. Which isn't very strong but does show there is a relationship there.


5. Advanced / Interactive Visuals : 

In this section a created multiple interactive visuals using plotly. The first is a stacked bar chart showing Satisfaction Rating by Agent and Topic. 

Next is a normal bar chart showing resolved issues by agent. This visual shows that Jim resolved the most issues at 485 with Stuart last at 424. 

The third visual is a funnel showing the total calls, answered calls and resolved calls. This is a straightforward visual that gives quick and easy to understand data. 

Visuals five and six are bar charts with an animation frame added. Visual five shows the frequncy in call volume day to day for agents where visual six uses .cumsum() to show the cumulative calls by agent.


6. Advanced Analysis : 

In this section I did ANOVA & Regression analysis using statsmodels. This analysis showed that when it comes to call duration, the topic has close to no impact on it. The only significant difference was for payment related calls which tend to be shorter. It also showed that the speed of answer, call duration and resolved issues had little to no impact on satisfaction rating.

7. Insights and Recommendations (Copy & Paste from Notebook)
#### Operational Efficiency:

Call Duration: While average call durations are consistent across agents and topics, a deeper analysis revealed that specific agent-topic combinations (e.g., Agent Dan and payment-related calls) contribute disproportionately to longer call durations. These could be targeted for training or process improvement.

Resolution Rate: Unanswered calls account for 70% of unresolved issues, as highlighted in the EDA. This is strongly correlated (0.9988) with call volume, indicating a need for better resource management during peak times.

#### Customer Satisfaction:
Unanswered calls are a major driver of poor satisfaction ratings, bringing down the average rating to 2.76. Resolved calls have a significantly higher average rating of 3.40.

Satisfaction ratings saw a steep decline in February and March, compared to January. This may indicate operational or seasonal challenges that need further exploration.

Agent Performance:
Performance across agents is fairly even, but specific agents and topics show weaknesses that can be addressed through training.
There is a moderate positive correlation (0.54) between resolution rates and satisfaction ratings, suggesting that resolving issues efficiently is a key driver of satisfaction.

#### Advanced Analysis:
Regression analysis showed that call duration and the speed of answering calls have minimal impact on satisfaction ratings. The main exception is payment-related calls, which are shorter and more efficient.
ANOVA analysis further supported that topics have little influence on call durations overall.

## Recommendation

1) Unanswered Calls - The biggest issue facing PWC is the volume of unanswered calls, this is impacting their KPIs; Satisfaction Rating and Resolution Rate. I'd recommend hiring additional agents to help handle the call volumes, especially during peak periods. 

2) Agent Training - Agents resolution rates at a high level are relatively positive but there are some combinations of topics and agents where there is room for improvement. I would recommend targeted training for these combinations. This should lead to overall improvements in resolution rates. Once the training is done paired t-Tests can be performed to see how beneficial the training was.

3) Data-Driven Decision Making - Use the heat maps and interactive visuals created to identify trends and performance gaps at a glance.

Adopting these recommendations will have a very positive impact on PWCs KPI's





