Project name: A/B Testing.
Description of the data: logs of online store orders, data on visitors belonging to control or test group, a list of hypotheses that may help boost revenue.
Task: to prioritize these hypotheses, launch an A/B test, and analyze the results.
Libraries used: pandas, numpy, matplotlib, datetime, plotly.express, plotly.graph_objects, sidetable.
Results: 
ICE and RICE scores were used for hypotheses prioritizing. REACH parameter turned out to be very important, it changed priority ranking a lot. 
For the raw data and for filtered data with anomalous users and orders dropped:
- the difference in total conversion and in average daily conversion between the groups is not statistically significant.  
- the difference in average order size between the groups is not statistically significant.   
In all parameters that were analized we didn't see any tendency to improvement for group B in comparison with group A, so the test is unsuccessful and should be stopped. 