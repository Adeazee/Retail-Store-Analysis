# Fashion Store Analysis
Retail store data using SQL for data extraction and Analysis and power bi for visualization.

## Table of content

* [Project overview](Project-overview)
* [Tools & technologies](Tools--technologies)
* [Dataset overview](Dataset-overview) 
* [Data Engineering & SQL Analysis](DataEngineering--SQLAnalysis)
* [power BI Dashboard](powerBI-Dashboard)
* [Insights](Insights)
* [Recommendations](Recommendations)

### Project overview
This project focuses on a mid sized fashion store chain struggling with declining sales despite increasing marketing spend. The business wants to understand why revenue is dropping and how to optimize operations

## Tools and Techniques Used
#### Tools
* SQL - Data aggregation and Analysis
* power bi - data visualization
* GitHub - Version control and Project Documentation
#### Techniques
* Data Validation
* Aggregation and grouping (store, channel, product category)
* Customer segmentation (one-time, returning, loyal customers)
* Inventory analysis (overstock, understock, optimal, and stockout flag evaluation)
* Performance comparison across stores and sales channels

## Dataset Overview
columns:
transaction_id, store_name, sales_channel, product_category, units_sold, unit_price, discount_applied, campaign_id, campaign_channel, marketing_spend, campaign_exposure_status, customer_id,customer_segment, inventory_level, stockout_flag, revenue

sample preview:
| transaction_id | store_name | sales_channel | product_category | units_sold | unit_price | discount_applied | campaign_id | campaign_channel|marketing_spend | campaign_exposure_status | customer_id |customer_segment |inventory_level|  stockout_flag | revenue | 
|----------------| ---------  | -----| ---------| -------------| -------- | -------- | ------- | -------- | -------- | -------- | --------- | ---------- | ---------- | ------- | -------- |
| 3843 | Central Mall| App |	Accessories| 3 | 60 |40 |CAMP-A| Social | 50| Seen| CUST_2404 | Loyal | Overstocked |Yes|180|


## Data Engineering & SQL Analysis
This section documents all SQL operations performed in this project. Each query was written to answer a specific business objective using the retail dataset.

1. Data Exploration
Objective: Preview the dataset and understand available fields.
```sql
SELECT * 
FROM store.retail;
```
2. Revenue vs Marketing Spend Comparison
Objective: Compare total revenue generated against total marketing spend.
```sql
SELECT 
    SUM(revenue) AS revenue, 
    SUM(marketing_spend) AS marketing_spend
FROM store.retail;
```
3. Revenue vs Marketing Spend Comparison
Objective: Compare total revenue generated against total marketing spend.
```sql
SELECT 
    SUM(revenue) AS revenue, 
    SUM(marketing_spend) AS marketing_spend
FROM store.retail;
```

4. Store Performance Analysis
Objective: Analyze revenue and marketing spend across different stores.
```sql
SELECT 
    store_name, 
    SUM(revenue) AS Revenue, 
    SUM(marketing_spend)
FROM store.retail
GROUP BY store_name
ORDER BY SUM(revenue) DESC;
```

5. Sales Channel Performance
Objective: Identify where the business makes the most sales by channel.
```sql
SELECT 
    sales_channel, 
    SUM(revenue), 
    SUM(marketing_spend)
FROM store.retail
GROUP BY sales_channel
ORDER BY SUM(revenue) DESC;
```

6. Product Category Revenue Analysis
Objective: Evaluate revenue and marketing spend by product category.
```sql
SELECT 
    product_category, 
    SUM(revenue) AS revenue, 
    SUM(marketing_spend) AS marketing_spend
FROM store.retail
GROUP BY product_category
ORDER BY revenue DESC;
```

7. Campaign Channel Performance
Objective: Analyze returns across different marketing campaign channels.
```sql
SELECT 
    campaign_channel, 
    SUM(marketing_spend), 
    SUM(revenue) AS revenue
FROM store.retail
GROUP BY campaign_channel
ORDER BY revenue;
```

8. Customer Segmentation Analysis
Objective: Examine customer distribution by customer segment.
```sql
SELECT 
    customer_segment, 
    COUNT(customer_segment)
FROM store.retail
GROUP BY customer_segment
ORDER BY COUNT(customer_segment);
```

9. Inventory Level Analysis
Objective: Assess inventory distribution across different inventory levels.
```sql
SELECT 
    inventory_level, 
    COUNT(inventory_level)
FROM store.retail
GROUP BY inventory_level
ORDER BY COUNT(inventory_level) DESC;
```

10. Stockout Analysis
Objective: Analyze the frequency of stockout occurrences.
```sql
SELECT 
    stockout_flag, 
    COUNT(stockout_flag)
FROM store.retail
GROUP BY stockout_flag
ORDER BY COUNT(stockout_flag) DESC;
```

power BI Dashboard
The power BI Dashboard includes the following visuals:
* Marketing spend on Customer segment
* campaign exposure
* customer segment
* marketing spend on sales channel
* transactions affected by stockout
* customer count across sales channels
* return on investment by campaign channel
* campaign exposure distribution across stores
* return on investment by stores
* return on investment by product category
* revenue response to marketing
<img width="1185" height="651" alt="Screenshot 2026-01-30 225341" src="https://github.com/user-attachments/assets/885dfd76-41ff-4979-8d92-37c39f5e6839" />
<img width="1171" height="669" alt="Screenshot 2026-01-30 225446" src="https://github.com/user-attachments/assets/0b1fee87-5c14-43a7-b872-07948698ddae" />
<img width="1089" height="643" alt="Screenshot 2026-01-30 225536" src="https://github.com/user-attachments/assets/2638ee2e-8dfb-42f7-94c0-cd86cbe5064b" />



## KEY INSIGHTS

Insight 1: Marketing spend is not translating proportionally into revenue
Despite high overall marketing spend, revenue remains comparatively low, indicating inefficient use of marketing resources.

Insight 2: Certain campaign channels generate low ROI
Some campaign channels consume a significant portion of marketing spend but generate relatively low revenue.

Insight 3: High campaign exposure does not guarantee conversion
Some stores show high campaign exposure but low revenue, indicating low conversion effectiveness.

Insight 4: Operational issues limit marketing effectiveness
Frequent stockouts prevent marketing-driven demand from converting into actual sales.

Insight 5: Customer retention is weak
A large proportion of customers are one-time buyers, reducing long-term revenue growth despite ongoing marketing efforts.

## RECOMMENDATIONS

Recommendation 1: Reallocate marketing budget based on ROI
Shift marketing spend away from low-ROI channels, stores, and product categories toward high-performing segments.

Recommendation 2: Optimize campaign strategy by channel
Pause or redesign campaigns with consistently low ROI and scale campaigns that show stronger revenue response.

Recommendation 3: Strengthen customer retention initiatives
Introduce loyalty programs, personalized offers, and post-purchase engagement to convert one-time customers into repeat buyers.

Recommendation 4: Strengthen collaboration between sales and inventory teams to proactively manage stock levels for high-demand products and reduce frequent stockouts

Recommendation 5: Focus marketing on high-performing product categories
Increase promotion of categories with higher ROI and reconsider marketing spend on low-demand categories.





