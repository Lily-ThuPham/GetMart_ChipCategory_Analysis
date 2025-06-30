# **GetMart Retail Strategy: Chip Category Analysis**
_**Author**: Thu Pham | **Date**: 06/2025_

## *Table of Contents*

1. [Project Background](#1-project-background)  
2. [Data Structure & Initial Checks](#2-data-structure--initial-checks)  
3. [Executive Summary](#3-executive-summary)  
4. [Insights Deep Dive](#4-insights-deep-dive)  
5. [Recommendations](#6-recommendations) 

## _**1. Project Backround**_

    This repository presents an independent, hypothetical data analysis project inspired by the Quantium Data Analyst virtual experience on Forage.

This project provides a strategic analysis for our client, **GetMart**, a mid-sized supermarket chain known for its focus on providing value to local communities. In preparation for the upcoming fiscal year, the GetMart Chip Category Manager requires a data-driven strategy to increase sales and better understand their customer base.

This analysis uses **12 months of transactional data to uncover key insights**. The core of the analysis focuses on customer segmentation and an A/B test evaluation, measured through key business metrics including _**Total Sales, Number of Customers, Number of Transactions, and Average Transaction Value**_. The goal is to identify high-value customer segments and validate strategic initiatives that can be implemented to drive growth in the chip category.

The analysis is broken down into two main components:

1. **Customer Analytics:** A deep dive into customer purchasing patterns to identify high-value segments.

2. **A/B Test Trial Assessment:** A statistical evaluation of a three-month trial involving a new store layout to measure its impact on sales and customer traffic.

The presentation report for stakeholder review is available here. [link]()

The Python code used to inspect and clean the data for this analysis can be found here [link](Data_cleaning.ipynb).

The Python code used to conduct deep-dive analysis on customer segmentations can be found here [link](EDA_SegmentAnalysis.ipynb).

The Python code used to conduct the A/B Store Trial assessment can be found here [link](Trial_assessment.ipynb).

## _**2. Data Structure and Initial Check**_
The analysis is based on two primary datasets provided by GetMart,`transaction_data`, `purchase_behaviour`, which were then used to create a third, normalized product table. A description of each table is as follows:

- **`transaction_data`:** This is a large dataset with over _**264,000 rows**_, where each row represents a chip purchase transaction. It covers the period _**from July 2018 to June 2019**_ and includes details for each unique transaction (`TXN_ID`), such as the quantity and value of chips purchased, and the customer's loyalty card ID.

- **`purchase_behaviour` / `customer_table`**: This table contains demographic information for _**over 75,000 unique loyalty card members**_. It categorizes each customer by their affluence (`PREMIUM_CUSTOMER`) and assigns them to one of seven distinct `LIFESTAGE` segments (e.g., 'Retirees', 'Young Families').

- **Product Dimension Table - `product_info`**: To enable brand and packaging analysis, a new product dimension table was created. This table normalizes the _**114 unique chip products**_ by extracting and cleaning their `BRAND` (21 unique brands) and `PACK_SIZE` (21 unique sizes), linking them to their original product number (`PROD_NBR`).

## _**3. Executive Summary**_

The core recommendation is to **implement a dual-strategy focusing on two keys, high-value customer segments: Budget Older Families and Mainstream Young Singles/Couples**.

- **Customer Insights**: The analysis revealed that sales growth is driven by purchase frequency, not spend per visit, as all segments spend a similar amount per transaction. We identified two key customer personas with distinct preferences: **Budget - Older Families**, who are a high-value segment preferring mainstream value brands, and **Mainstream - Young Singles/Couples**, a large segment representing a growth opportunity with a strong affinity for popular, flavor-focused brands.

- **Trial Validation**: A three-month in-store trial, which moved the chip category to a prominent end-cap, was a success. It **drove a statistically significant increase in both sales and customer traffic** in _two of the three trial stores_, validating that strategic changes to store layout can effectively boost performance.

## _**4. Insights and Deepdive**_
### **4.1. Customer Analytics: Who Are Our Most Valuable Segments?**
A deep dive into customer purchasing patterns revealed that the chip category is a mature market driven by specific, high-value customer segments with distinct brand preferences.
#### 4.1.1. Overall Market trend
An analysis of sales over the 12-month period shows a stable market with predictable seasonality. 
- Sales consistently peak in December, driven by the holidays, and experience a significant dip in the post-holiday period. 
-  A key observation is the near-perfect correlation between monthly total sales and the number of customers, indicating that the primary driver of sales is customer traffic. 
- This indicates that growth in this category must be strategically driven rather than relying on organic market trends.
![Supporting Figure: Monthly Sales and Customer Trends](Images/Monthly_Trend.png)

#### 4.1.2. Identifying High-Value Customer Segments:

_**Insights from Monthly Trends by Customer Affluence (from July 2018 - June 2019):**_ 
- **Mainstream (~751K - 39%) and Budget Segments (~676K - 35.0%)** drive the Bulk of Sales, while **Premium Customers Contribute the Least (~506K - 26%)**.
- Customer Quantity Aligns with Sales Rank: The number of customers for each segment (the bars) directly corresponds to their sales performance. The Mainstream group consistently has the highest number of customers, followed by Budget, and then Premium.
- **All Segments Follow the Same Seasonal Pattern:** All three affluence segments exhibit the same seasonal trends, with a clear sales **peak in December** and a corresponding **dip in February**. 
![Monthly Sales and Customer trends by Customer Affluence](Images/Monthly_Affluence_Segments.png)

_**Performance by Customer Affluence:**_ The data reveals that sales contribution is a direct function of the size and frequency of the customer group.
- **Mainstream customers drive the most sales (38.8%)** simply because they form the largest **customer base (40.3%)**
- **Budget customers** are the most frequent shoppers, with the highest average transactions per customer (3.78).
- Crucially, **the average transaction value is nearly identical** across all segments ($7.31 - $7.41), proving that no single group is inherently a "bigger spender" per trip.

![Affluencial Segment Metrics (Jul/18 - Jun/19)](Images/Affluencial_Metrics.png)

_**Identifying High-Value Personas:**_ Combining affluence with lifestage reveals our key target segments. By comparing a segment's size to its sales contribution, we can pinpoint who our most valuable customers are.

- **High-Value Performers (`Budget - Older Families`)**: This segment is the most valuable relative to its size, **contributing 18.2% of sales from only 13.5% of the customer base**. They are *high-volume, value-conscious shoppers* with a strong affinity for mainstream value brands like RRD and Smiths.

- **High-Potential Growth Segment (`Mainstream - Young Singles/Couples`)**: This is the *single largest segment* in our customer base **(11.1%)**. While their sales contribution is strong **(8.15%)**, their large size presents a significant opportunity for growth.

- **Stable Core Customers (`Retirees` and `Older Singles/Couples`)**: These two older, non-family lifestages form the stable core of the chip category, *making up a massive 40% of the customer base* and contributing a proportional *40% of total sales*. Their brand preferences are generally mainstream and consistent.

- **Under-Performing Segments (`New Families` and `Mid-aged Singles/Couples`)**: These groups are the least engaged. `New Families`, in particular, make up only **3.5% of the customer base and contribute just 2.6% of sales**, indicating a significant gap in the current product offering for this demographic. 

![Customer Base Distribution vs. Sales Contribution](Images/customer_sales_contributions.png)

#### **4.1.3. Brand Affinity of Key Segments:**
- **`Budget - Older Families` prefer Value and Family Brands**: This segment significantly over-indexes on brands like _**RRD (25% more likely), Woolworths (22% more likely), and Smiths (12% more likely)**_.
- **`Mainstream - Younger Singles/Couples`** audiences lean toward popular, market-leading brand such as Kettle or **Doritos (12% more likely)** and they are willing to pay more for their chips.
- **The 175g and 150g pack sizes are the most popular** across all customer segments, collectively accounting for nearly **40% of total sales**.

![Brand Affinity by Key Customer Segments](Images/Barnd_affinity_keysegment.png)



