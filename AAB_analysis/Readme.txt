Project name: AAB Analysis
Description of the data: startup sellings food products log data (224126 rows 4 columns) for users belonging to 3 groups (two control groups(A) and test group B).
Task:   to investigate user behavior for the company's app and to evaluate effectiveness of new test fonts.
Libraries used: pandas, numpy, seaborn, plotly.express, plotly.graph_objects, math, scipy, sidetable, cufflinks.
Results: the main differences between churned and non-churned users are found. Two models for binary classification were built to predict user churn: logistic regression and random forest. **Logistic regression** model gives better results and can be used for predicting user churn. The users were devided into 5 clusters, ordered by **churn rate** from the most loyal to the least loyal. Recommendations to prevent churn are given.
After the preprocessing and EDA the funnel analysis was conducted. We used proportion test to compare groups A, A and B. No statistically significant difference between control and test groups found, so new fonts didn't really influence user behavior.
