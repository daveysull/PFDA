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

---

#### 1. Introduction : 

This notebook contains the analysis of PWC contact centre data. The goal of this notebook is to identify trends as well as behaviours that may impact PWC’s contact centre performance. The original dataset contains 10 columns and 5,000 rows. The dates within the dataset range from January 1st to March 31st, 2021. The dataset is downloaded from Kaggle, added to a database created in MySQL, and then connected to through Python.

#### 2. Data Preperation :

The first step of preparation is creating a database to store the data. This is done in MySQL, and the Excel data is added to the database via bash scripts before the data is loaded to the notebook using Python. A detailed description of what is done is included in the notebook. Once this is completed, the usual steps of setting the index, creating/dropping columns, dealing with null values, etc., are taken.

#### 3. EDA :

This part of the notebook explores the data, looking for potential trends through the creation of visuals. The methods .info() and .describe() are used to better understand the data. The visuals created in this section include boxplots, bar charts, pie charts, and a line plot. The most insightful visual is the pie chart, which shows that 70% of unresolved issues are due to calls not being answered. The line plot shows how call volumes differ substantially day-to-day. In Section 5, a more complex version of this plot is added using Plotly.

#### 4. KPI Analysis :

(i) Operational Efficiency - Average Call Duration & Resolution Rate :

In this section, the average call duration and resolution rate are analyzed to identify areas for performance improvement. Call durations, when analyzed by agents and topics, are consistent across the board. Call durations by topic or agent are all within 10 seconds of the overall average. Further analysis focuses on the combinations of agents and topics where call durations exceed the total average. This reveals specific topics agents can focus on to improve their numbers and close calls quicker. Outliers are examined to narrow down the 5% longest calls, serving as a reference for potential areas of improvement. For instance, Agent Dan appears in the top 5% 11 times for payment-related calls.

For resolution rates, the EDA reveals that a high number of unresolved issues are due to calls not being answered. When examining resolution rates by agent and topic, results are similarly consistent, with an average resolution rate of 73%. Combinations of agents and topics are highlighted where PWC can focus on improvement. The correlation between call volume and unanswered calls is 0.9988, indicating a strong positive relationship between the two variables.


(ii) Customer Satisfaction - Satisfaction Rating :

During the analysis of customer satisfaction, the focus is on the satisfaction rating agents receive for each call. This rating ranges from 0-5. PWC’s average rating is 2.76, which is suboptimal. Unanswered calls lower this average, as they automatically receive a rating of 0. Resolved calls have a significantly higher average rating of 3.40. The same framework used for operational efficiency is applied, identifying combinations of agents and topics below average. A line chart is added to show satisfaction ratings over time. For most of January, satisfaction ratings are above average but dip substantially in February and March. Additional context or data would be needed to explain this trend.

(iii) Agent Performance - Resolution Rate, Satisfaction Rate & Call Volume Handled

The agent performance analysis combines elements from the Operational Efficiency and Customer Satisfaction sections. Overlapping KPIs justify this approach. Bar charts visualize agents’ resolution and satisfaction ratings, and heat maps include topics to identify weak points. Finally, the correlation between resolution rate and satisfaction rating is reviewed and visualized. The correlation is 0.54, indicating a moderate positive relationship between the two metrics.


#### 5. Advanced / Interactive Visuals : 

In this section, multiple interactive visuals are created using Plotly. The first is a stacked bar chart showing Satisfaction Rating by Agent and Topic.

Next, a standard bar chart shows resolved issues by agent. This visual reveals that Jim resolves the most issues at 485, while Stuart resolves the least at 424.

The third visual is a funnel chart showing the total calls, answered calls, and resolved calls. This is a straightforward visual for quick and easy data understanding.

Visuals five and six are bar charts with animation frames. Visual five shows the frequency of call volume day-to-day for agents, while visual six uses .cumsum() to display cumulative calls by agent.


#### 6. Advanced Analysis : 

In this section, ANOVA and regression analysis are conducted using Statsmodels. The analysis reveals that call duration is minimally impacted by the topic, except for payment-related calls, which tend to be shorter. Additionally, the speed of answering calls, call duration, and resolved issues have little impact on satisfaction ratings.

#### 7. Insights (Copy & Paste from Notebook)
#### Operational Efficiency:

Call Duration: While average call durations are consistent across agents and topics, deeper analysis reveals that specific agent-topic combinations (e.g., Agent Dan and payment-related calls) contribute disproportionately to longer call durations. These can be targeted for training or process improvement.

Resolution Rate: Unanswered calls account for 70% of unresolved issues, as highlighted in the EDA. This is strongly correlated (0.9988) with call volume, indicating a need for better resource management during peak times.

#### Customer Satisfaction:
Unanswered calls are a major driver of poor satisfaction ratings, lowering the average rating to 2.76. Resolved calls have a significantly higher average rating of 3.40.

Satisfaction ratings decline steeply in February and March compared to January. This indicates operational or seasonal challenges that need further exploration.

Agent Performance:
Performance across agents is fairly even, but specific agents and topics show weaknesses that can be addressed through training.
There is a moderate positive correlation (0.54) between resolution rates and satisfaction ratings, suggesting that resolving issues efficiently is a key driver of satisfaction.

#### Advanced Analysis:
Regression analysis shows that call duration and the speed of answering calls have minimal impact on satisfaction ratings. The main exception is payment-related calls, which are shorter and more efficient.
ANOVA analysis further supports that topics have little influence on call durations overall.

#### Recommendation

1) Unanswered Calls - The biggest issue PWC faces is the volume of unanswered calls, which impacts their KPIs: Satisfaction Rating and Resolution Rate. Hiring additional agents to handle call volumes, especially during peak periods, is recommended.

2) Agent Training - While agents’ resolution rates are relatively positive, certain combinations of topics and agents show room for improvement. Targeted training for these combinations is recommended, which would lead to overall improvements in resolution rates. After the training, paired t-tests can be performed to evaluate its effectiveness.

3) Data-Driven Decision Making - Using the heat maps and interactive visuals created allows trends and performance gaps to be identified at a glance.

Adopting these recommendations will positively impact PWC’s KPIs.




