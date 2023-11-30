# #3 Telecom_plans. Statistical Data Analysis.
**Project description**
You work as an analyst for the telecom operator Megaline. The company offers its clients two prepaid plans, Surf and Ultimate. The commercial department wants to know which of the plans brings in more revenue in order to adjust the advertising budget.
You are going to carry out a preliminary analysis of the plans based on a relatively small client selection. You'll have the data on 500 Megaline clients: who the clients are, where they're from, which plan they use, and the number of calls they made and text messages they sent in 2018. Your job is to analyze clients' behavior and determine which prepaid plan brings in more revenue

**Description of the plans**
Note: Megaline rounds seconds up to minutes, and megabytes to gigabytes. For calls, each individual call is rounded up: even if the call lasted just one second, it willbe counted as one minute. For web traffic, individual web sessions are not rounded up. Instead, the total for the month is rounded up. If someone uses 1025 megabytes this month, they will be charged for 2 gigabytes.

Surf

Monthly charge: $20
500 monthly minutes, 50 texts, and 15 GB of data
After exceeding the package limits:
1 minute: 3 cents
1 text message: 3 cents
1 GB of data: $10
Ultimate

Monthly charge: $70
3000 monthly minutes, 1000 text messages, and 30 GB of data
After exceeding the package limits:
1 minute: 1 cent
1 text message: 1 cents
1 GB of data: $7
**Instructions on completing the project**
* Step 1. Open the data file and study the general information (5 files)
* Step 2. Prepare the data
Convert the data to the necessary types
Find and eliminate errors in the data
Explain what errors you found and how you eliminated them.For each user, find:
The number of calls made and minutes used per month
The number of text messages sent per month
The volume of data per month
The monthly revenue from each user (subtract the free package limit from the total number of calls, text messages, and data; multiply the result by the calling plan value; add the monthly charge depending on the calling plan)
* Step 3. Analyze the data
Describe the customers' behavior. Find the minutes, texts, and volume of data the users of each plan require per month. Calculate the mean, variance, and standard ndeviation. Plot histograms. Describe the distributions.

* Step 4. Test the hypotheses
The average revenue from users of Ultimate and Surf calling plans differs.
The average revenue from users in NY-NJ area is different from that of the users from other regions.
You decide what alpha value to use. Explain:

How you formulated the null and alternative hypotheses.
What criterion you used to test the hypotheses and why.
* Step 5. Write an overall conclusion
Format: Complete the task in Jupyter Notebook. Put the programming code in code cells and text explanations in markdown cells, then apply formatting and headings.

