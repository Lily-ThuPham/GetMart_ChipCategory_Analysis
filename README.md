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


