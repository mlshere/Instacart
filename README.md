# Instacart Grocery Basket Analysis

## Introduction
Instacart, a leading online grocery store, seeks to enhance its customer segmentation and marketing strategies through data analysis. As a data analyst, our goal is to perform an exploratory analysis of Instacart's sales data to uncover patterns in customer behavior and order trends. The insights derived from this project will help optimize Instacart’s targeted marketing efforts and improve customer engagement.

## Data Used
The analysis relies on multiple datasets, including:

1. **Instacart Open Source Data** (2017):
   - Provided by Instacart and available on Kaggle.
   - Contains information on grocery orders, product categories, and user interactions.

2. **Customer Data Set** (Fabricated for the project):
   - Includes demographic and behavioral attributes of Instacart customers.
   - Helps in profiling customer segments.

3. **Data Dictionary**:
   - Provides definitions for variables across datasets.
   - Helps in understanding the meaning and relationships of different fields.
  
## Data Cleaning and Preprocessing
To ensure the data was ready for analysis, several cleaning and preprocessing steps were followed:

1. **Handling Missing Values:**
   - Checked for null values in all datasets.
   - Imputed missing values where necessary (e.g., replacing missing `days_since_last_order` with median values).
   - Removed rows with excessive missing data.

2. **Renaming Columns:**
   - Renamed `order_dow` to `orders_day_of_week` for better readability.
   - Ensured consistency across all dataset column names.

3. **Fixing Data Types:**
   - Converted categorical variables (e.g., `orders_day_of_week`, `order_hour_of_day`) to appropriate formats.
   - Ensured numeric variables (e.g., `income`, `prices`) were stored as float or integer types.

4. **Removing Duplicates:**
   - Identified and dropped duplicate records to prevent data inconsistencies.

5. **Merging Datasets:**
   - Combined `orders`, `customer_data`, and `products` datasets using `user_id` and `product_id` as unique keys.
   - Verified the integrity of merged data by checking for unmatched records.

     
## Data Overview
### Orders Dataset 
Contains order-related details of Instacart customers.
- `order_id`: Unique identifier for each order.
- `user_id`: Unique identifier for each customer.
- `order_number`: The sequential number of the order for a given customer.
- `orders_day_of_week`: Day of the week the order was placed (0=Sunday, 6=Saturday).
- `order_hour_of_day`: The hour of the day the order was placed (0-23).
- `days_since_last_order`: Days since the customer’s last order.

### Customer Dataset 
Contains demographic information of Instacart customers.
- `user_id`: Unique identifier for each customer.
- `first_name`: Customer’s first name.
- `last_name`: Customer’s last name.
- `gender`: Customer’s gender (Male/Female).
- `state`: The state where the customer resides.
- `age`: Customer’s age.
- `date_joined`: The date the customer joined Instacart.
- `n_dependants`: Number of dependents in the customer’s household.
- `fam_status`: Family status (e.g., married, single).
- `income`: Annual income of the customer.

### Products Dataset 
Contains details about breakfast-related products.
- `product_id`: Unique identifier for each product.
- `product_name`: Name of the product.
- `aisle_id`: Aisle identifier where the product is located.
- `department_id`: Department identifier the product belongs to.
- `prices`: Price of the product.

### Department Dataset 
Contains information about various product departments.
- `department_id`: Index column.
- `department`: Name of the department (e.g., frozen, bakery, produce, alcohol).

## Key Insights and Takeaways

### 1. Order Trends
- **Busiest Days and Hours:**
  - Peak order hours are from 10 AM to 10 PM, with minimal orders between midnight and early morning.

      ![heatmap](https://github.com/user-attachments/assets/c595952f-8597-4f9f-ad04-dd450529688f)

    
  - The highest number of orders are placed on weekends, specifically on Saturday and Sunday.

      ![bar_days](https://github.com/user-attachments/assets/4b35f468-7afb-4def-87ff-9085345b807e)

    
  - Orders gradually increase from early morning, peaking in the early afternoon, and decline towards the night.

      ![hist_order](https://github.com/user-attachments/assets/18677802-e95a-45f9-939a-f9350eade36c)


  Spending fluctuates over the day, with slightly higher spending occurring in the early morning and evening hours.
 

### 2. Customer Segmentation
Customer segmentation was established based on behavioral and demographic criteria:
- **Loyalty Categories:**
  - New Customers (1st-time shoppers), Regular Customers (repeat but inconsistent shoppers), and Loyal Customers (frequent shoppers).

    ![bar_loyalty](https://github.com/user-attachments/assets/e3785020-9520-4145-970a-61a23ae2d4b5)

  - Loyal customers have a higher frequency of repeat purchases and a larger average basket size.

- **Demographics:**
  - Segmentation based on age and number of dependants:
      * Single young: age between 18 and 35, no dependants
      * Young parent: age between 18 to 35 with one or more dependents
      * Singe adult: age 35 to 60, no dependents
      * Family Shopper: age 35+, multiple dependents
      * Senior Shopper: age 60+, fewer or no dependents
     
    ![bar_total_orders](https://github.com/user-attachments/assets/5a887676-61c1-47b0-8898-b0f1a9155815)
  
  This bar chart shows the distribution of customer profiles based on a segmentation of age and number of dependents. Here is how we can describe the chart:
    * The "Family Shopper" profile dominates, with a significantly higher count compared to the others. This suggests that a large portion of customers are in the 30+ age range and have multiple dependents, likely shopping for family-sized products or groceries.
    * The "Senior Shopper" profile is the second most common, which could indicate a significant number of customers over 60 who may be shopping for essential or convenience items, and possibly fewer or no dependents.
    * The "Young Parent" profile also shows a noticeable number of customers, indicating a group of younger individuals (aged 18-30) with children or dependents.
    * The "Single Young" profile is the least common, which could reflect that fewer young, independent individuals without dependents are frequent shoppers in this dataset.
    * The 'Single Adult' profile is in the middle.
    
   
The two following visualizations, average spending and standard deviation spending, provide insights into the spending behaviors of different customer profiles.

  - Average Spending:
      * The average spending by customer profile is relatively similar across all groups, with Family Shoppers, Senior Shoppers, Single Adults, Young Parents, and Single Young shoppers spending around the same amount (around 7.7 for all segments).
      * This suggests that while the total spending differs between profiles (with Family Shoppers being the largest spenders), the average spending per transaction is consistent across these groups.
   
         ![bar_avg_spending](https://github.com/user-attachments/assets/882b4d66-369e-4e14-9662-ade5407fd1ff)

  - Standard Deviation Spending:
      * The standard deviation of spending is also comparable among all customer segments, with each profile showing similar variability in their spending (ranging from 3.7 to 4).
      * This indicates that, despite differences in total spending, customers within each group demonstrate consistent shopping behaviors in terms of spending per order.
      * The even spread of standard deviation across segments suggests that marketing efforts should aim to keep the spending patterns consistent, particularly for Family Shoppers, who are the largest contributors to total spending.
   
        ![bar_std_spending](https://github.com/user-attachments/assets/8af3b143-7b1b-45fb-ae8c-96acc3c8b550)
        
Both visualizations help highlight that while average spending varies slightly across segments, the variation in spending remains consistent, implying that consistent purchasing behaviors could be promoted for all profiles.

****

### 3. Income Segmentation
  * Low income: below the mean minus one standard deviation
  * Middle income: between the mean minus one standard deviation and the mean plus one standard deviation.
  * High income: above the mean plus one standard deviation
    
      ![pie_income](https://github.com/user-attachments/assets/b6e0fd2a-b45b-4cb3-94bb-b951da8a9ae5)

This bar chart illustrates the distribution of customer income groups across different regions. Here are some points:

  ![income_by_region_bar](https://github.com/user-attachments/assets/506c49ec-a526-4120-b785-6a609fcc3e26)

* Middle income customers make up the largest proportion in every region, with a notable spike in the South and West regions.
* Low income customers are particularly prominent in the South, though they are also represented in all regions, but to a lesser extent compared to middle-income customers.
* High income customers have a smaller share overall, with a slight increase in the South and West regions.

### 3. Product Preferences
 
  ![product_customer_bar](https://github.com/user-attachments/assets/165e8a78-ee2d-4664-ac90-7005123364b6)

This stacked bar chart shows the distribution of product groups by customer segment. Here's the main takeaways:
  
  * Food is the largest category by far (it also has the most items available), especially for Family Shoppers.
  * Other product groups have significally fewer items and are sold less. As expected Family Shoppers and Young Parents are the ones who buy most of baby care.
  * Family Shopper contributes the most to the Food category, followed by smaller contributions to Baby Care and Drink.
  * Single Adult and Young Parent segments also show notable participation in Food. Senior Shopper and Young Adult have smaller contributions overall.
  * Food is the most popular category across all segments, while other categories like Pet Care and Non-consumable are less significant.

### 4. Regionality

![segment_by_region_bar](https://github.com/user-attachments/assets/d3e2489b-00ad-4b16-b7b6-fe0d7059e30f)

Family Shoppers dominate the South and West, while Senior Shoppers are more prominent in the South and Midwest. The Northeast has a more even distribution, and the South has the highest number of shoppers.


## Decisions and Best Practices in Data Classification
- **Ensuring Data Integrity:** Data was cleaned to remove duplicates, handle missing values, and correct inconsistent data types.
- **Segmentation Methodology:** Customers were segmented using quantitative (spending levels, order frequency) and qualitative (demographic factors) approaches.
- **Actionable Insights:** Findings were aligned with Instacart’s marketing goals to improve targeted campaigns and optimize sales strategies.
- **Visualization and Communication:** Clear visualizations (bar charts, histograms, scatter plots) were used to illustrate key patterns, making the analysis accessible to stakeholders.
- **Time-of-Day Marketing Strategies:** Understanding when customers are most likely to make purchases can help Instacart tailor promotions and service availability accordingly.

---
**Citation:**
- "The Instacart Online Grocery Shopping Dataset 2017", Accessed from [Instacart Kaggle Dataset](https://www.kaggle.com/datasets/psparks/instacart-market-basket-analysis)
- Customer data set provided by CareerFoundry for educational purposes.

