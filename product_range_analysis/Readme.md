# Final Project_3

**E-Commerce Product Range Analysis**

**Objective**:
Analyze the transaction history of an online household goods store to provide recommendations for increasing revenue.

**Dataset Overview**  

**Timeframe:** November 29, 2018 – December 7, 2019 

**Transactions:** 541,909  

**Columns:** InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID 

**Libraries used:** &nbsp;pandas, numpy, datetime, seaborn, plotly, plotly.express, plotly.graph_objects, math, stats.

New dataframe for per product analysis was prepared for 4060 products, some additional metrics were calculated: revenue, max and min price, number of price variants, max and min dates of purchase, number of days on sale. 
​
###**Results:**
- product distribution over time is revealed;
- product categories are defined, several product ratings are developed;​ 
- products are clustered into 9 groups with RFM approach;​
- hypothesis about everyday products’ behavior in summer and autumn are tested;​ 
- recommendations based on ratings , products clustering and hypothesis testing results are given.​
   
🚀&nbsp;Check out my  Google Colab Notebook

STEPS OF ANALYSIS

# Step 1: Data Preprocessing  

- Cleaning and Formatting:  
	- Standardized column names  
- Handled missing values:  
	- CustomerID: 135,080 missing values filled with 0  
	- Description: 1,454 missing values restored where possible  
- Converted data types where necessary  
- Removed 5,268 duplicate rows (&lt;1%)
 
# Step 2: Exploratory Data Analysis (EDA) 

**Transaction Overview:**

Quantity: Mean = 9.55, Max = 80,995  

Price: Mean = $4.61, Max = $38,970  

Revenue: Mean = $17.90, Max = $168,469  

Sales Trends Over Time:  
- Daily: Revenue and quantity drop in mid-December, hitting a low on January 3, 2019.  
- Weekly: Most profitable weeks occur in autumn, with a decline in winter and gradual recovery.  
- Monthly: November is the best month; February and April are the worst.  
- Days of the Week Ranking (by revenue):  
	Friday  
	Wednesday  
	Thursday  
	Tuesday &amp;
	Saturday  
	Monday

# Step 3: Product-Level Analysis 

Data was grouped by product and price in a &nbsp;
new&nbsp;product&nbsp;df

We got 17900 rows of data, with a separate row for the same product with different prices - on average, there are 4.5 price variants per product. 

Then the data was grouped once again by stockcode&nbsp;in&nbsp;pr&nbsp;table, now each product has only one row with such metrics as number of price variants, min and max and average price, summed revenue, min and max dates, number of unique dates, description (most common variant), number of description variants.

Rows with descriptions referring to the postage or shipping fees&nbsp;were excluded, so finally we got a dataset with 4,060 unique products .

Several product categories are analyzed.

## A. Fixed VS Flexible Prices 

466 products had a fixed price, while 208 products had 8+ price variations.
For fixed-price products the mean quantity is much smaller than that of the whole sample (21.6 VS 1308.5), so the revenue is smaller too(54.3 VS 2484.5).

Flexible price products do not differ from other products by price, but the mean quantity and revenue are much greater (5337.2 VS 1308.5, 13517.2 VS 2484.5).  

## B. High VS Low Prices

Top 10 and Bottom 10 products by price are found.

The highest price  is  $649.5 for PICNIC BASKET WICKER SMALL.

The cheapest products with negative price (returned) or zero price are mostly products that were destroyed at the very beginning and returned.

Among products with non-zero initial price there are some cheap products sold in huge quantities which bring a significant revenue - like &nbsp;POPART WOODEN PENCILS ASST - $0.12 per unit, total revenue $380.&nbsp;

## C. Large VS small quantity  

Top 10 by popularity products are found.

Most Sold Product: Popcorn Holder – 56,450 units 

Least Popular Products: 57 items were sold only once.

## D. Returned Products  

1,119 products were returned, impacting revenue.  

Most Returned Product: Travel Card Wallet I Love London – 14,418 units returned. 

## E. High vs. Low Revenue Products  

- Top Revenue Product: Regency Cakestand 3 Tier – $164,459.49  
- Worst Revenue Product: White Cherry Lights – Revenue: -$54  
- 19 products with negative revenue brought losses from $-0.02 to -54.00.
- 136 products give 0 revenue (- damaged products or given for free).
  
## F. Sales Duration  

The interval between max and min dates of purchase was calculated: the mean is 276 days, max 373 days (the whole observation period).&nbsp;

- Long-term Products: 1,206 products were on sale for ≥370 days.  
- Short-term Products: 239 products were sold in 1 day, 370 products in 1 month.  

## G. Everyday Products  

- Number of unique purchase days  varies from 1 to 305 with the mean 69 days, the median is 47 days. The leader is WHITE HANGING HEART T-LIGHT HOLDER sold 305 days (all days the store was open).&nbsp;
- Top 50 everyday products (sold on 270+ days) account for 15.7% of total revenue.
-  
So, everyday products constitute a very important category - high demand goods, most often sold through the whole year, bringing more than 15% of total revenue.

# Step 4: Hypothesis Testing: The share of everyday products among all products in summer and winter is different.

The test of proportions was used with alpha 0.05 to check the hypotheses:
- HO: The shares of everyday products in total sales(quantity, revenue) are the same in summer and autumn.
- H1: The shares of everyday products in total sales (quantity, revenue) are different in summer and autumn.
- 
Summer and autumn samples were compared, quantity and revenue values for total products were considered as trials, the same metrics for everyday products as successes.

For both quantity and revenue we got the same result: p-value is much lower than alpha, so we should reject the null hypothesis about equality.

So, the difference between the proportions is statistically significant by quantity as well as by revenue. This test results confirm that everyday products constitute a speciall group, different from other products. Its monthly quantity and revenue do not grow so much in autumn, its share among all products in summer and in autumn is different (decreasing  in autumn), and this difference is statistically significant.**

# Step 5: RFM Analysis (Recency, Frequency, Monetary Value) 

Products were clustered with RFM method : values for Recency, Frequency and Monetary Value were split into ranges and labeled, each product got rfm score. In&nbsp;pr&nbsp;df we already have Frequency (=quantity) and Monetary value(= revenue) for each product. 

Then qcut() function was used to perform quantile-based splitting of each variable range into discrete intervals so that each of them represents a similar portion of the data. We got 4 ranges:
- Recency: [0; 9], [10; 120], [121; 320], [322; 373] days from the end of the observation period; 
- Frequency: [-14468; 41], [42; 333], [334; 1321], [1323; 56427] units sold; 
- Monetary_value: [-54; 95.94], [96.5; 613.17], [615.37; 2080,85], [2082.9; 164459.49] $ total revenue.
  
Each product was assigned to 1 of 4 ranges by each parameter and got RFM score, there were 61 different scores.&nbsp; 61 RFM scores were grouped into 9 clusters:
- Star – Best-selling, highest revenue, frequently purchased (rfm 444)
- Best – Strong sales, good revenue (rfm 443, 442, 434, 424, 433, 344, 343, 334, 333, 324, 314, 244) 
- Reliable – Steady performance (rfm 431, 432, 342, 332, 322, 313, 323, 321, 331, 311, 312)
- Promising – Growing potential (rfm 234, 243, 242, 224, 241, 233, 223, 213)
- Actual – Selling well but needs attention  ( rfm 423, 422, 421, 414, 413, 412, 411)
- Still Alive – Declining sales but still relevant  (rfm 222, 231, 232, 221, 211, 212)
- Losing Revenue – Low revenue, decreasing sales  (rfm 144, 143, 134, 133, 124, 123, 114, 113)
- Loosing Cheap – Low-value products with diminishing demand  (rfm 112, 122, 121, 132, 131, 141, 142)
- Trash – Poor performance, outdated  (rfm 111)
  
**Observations:**

- Star Products and Best Products are the leaders, they bring 65.3% of total monetary value, so their sales should be promoted to increase the store's revenue. Close to them are Reliable products with smaller revenue but with teady demand, they need marketing support. 
- Promising  and Steel Alive were sold  months ago, but Pomising were more successful and they may return later (in case of seasonal dependency), while Steel Alive have less chance of success and may leave the stage.
- Actual products may have just went on sale, we need time to understant to what extent they will be popular.
- Loosing Revenue and Loosing Cheap products were sold almost a year ago (more than 332 days ago), but while Loosing Cheap  products can be dropped almost without any noticeable lost, Loosing Revenue products need special attention. These products brought significant revenue in the past (22%), but then nobody buys them - why? Are they out of fashion and there's no sense to keep them selling, or are they sold once a year(Happy New Year!) and will be sold just in a week or two? Further investigation is needed.
- Trash products should not be sold at all.
  
## **Conclusions &amp; Recommendations**  

We analyzed the online store’s product range, focusing on key metrics, seasonality, product categories, hypothesis testing, and RFM clusters. Based on our findings, we propose the following recommendations to increase revenue:
1.Optimize Pricing Strategies:  
- Implement discounts and dynamic pricing for more products to encourage sales.  
- Adjust pricing based on demand patterns and seasonal fluctuations.
   
2.Enhance Product Assortment:  
- Use the ratings and metrics obtained to expand the product range strategically.  
- Prioritize the most popular, most profitable, and most frequently sold products that generate the highest revenue.  

3.Reduce Returns &amp; Improve Product Handling:  
- Investigate reasons behind high return rates and address issues with low-rated, frequently returned products.  
- Ensure proper storage and reliable delivery of all products to minimize damage and losses.
   
4.Strengthen Everyday Product Availability:  
- Maintain a steady stock of top-selling everyday products that drive consistent revenue.  

5.Capitalize on Seasonal Trends:  
- Adjust inventory and marketing strategies based on seasonal demand shifts, particularly the decrease in everyday product sales during autumn.  
- Conduct a deeper analysis of seasonal sales fluctuations across all product categories to refine inventory planning.  

6.Target High-RFM Clusters for Growth:  
- Focus marketing efforts on Star, Best, and Reliable product groups, as they contribute the most to revenue.  
- Discontinue or minimize investment in low-performing products, specifically those in the bottom 10 by revenue and popularity (which also belong to the Trash and Losing Cheap RFM segments).  

By implementing these strategies, the store can maximize revenue, reduce losses, and optimize product offerings to align with customer preferences and market trends.

