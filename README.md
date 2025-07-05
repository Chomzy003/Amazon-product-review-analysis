# Amazon-product-review-analysis
Excel-based analysis of Amazon product reviews and pricing to uncover insights for sellers. Includes data cleaning, pivot tables, calculated columns, and a dashboard.
# Amazon Product Review Analysis

## Overview

This project was developed as part of a data analytics case study focused on e-commerce product performance and customer engagement on Amazon.  
RetailTech Insights, a company providing analytics solutions to online sellers, needed actionable insights to guide product improvement, optimize marketing strategies, and improve customer experience.

The analysis leverages real-world Amazon product review data to answer key business questions, identify trends, and highlight opportunities for sellers to increase revenue and customer satisfaction.

This project also marks the beginning of my portfolio-building and DSA (Data Structures & Analytics) journey — showcasing my proficiency with Microsoft Excel, data cleaning, pivot table modeling, calculated columns, and dashboard storytelling.

## Dataset

The dataset was scraped from Amazon product pages and included:
- Product details: name, category, actual price, discounted price, discount percentage, rating
- Customer engagement: number of reviews, review titles, and review content
- Granularity: each row represented one unique product, with aggregated review data

**Dataset Size:**
- Rows: 1,465 products
- Columns: 16 attributes

## Business Goals

- Identify underperforming and overperforming product categories
- Understand how discounting relates to product rating and sales potential
- Help sellers prioritize product lines with the highest potential revenue
- Discover pricing strategies that correlate with higher ratings and engagement
- Create a clear, visual dashboard for decision-makers

## Data Cleaning & Preparation

The raw dataset was unstructured, with inconsistent formats and some invalid data. Cleaning steps included:
- Shortened excessively long product names to their first 4 words for readability
- Removed duplicate entries based on `product_id`
- Removed rows with null or invalid numeric values (price, discount, reviews)
- Standardized data types (e.g., prices and discounts as numeric)
- Split product categories into **Main Category** and **Sub-Categories** for better grouping and analysis
- Created new calculated columns:
  - `Price Range Bucket` — groups products into price bands (`<₹200`, `₹200–₹500`, `>₹500`)
  - `Discount Range Bucket` — groups products by discount percentage
  - `Total Potential Revenue` — estimated as `actual_price × number_of_reviews`

These steps made the data structured, consistent, and analysis-ready.

## Business Questions Answered

The following business questions were addressed using pivot tables, calculated fields, and dashboard visuals:

- What is the average discount percentage by product category?
- How many products are listed under each category?
- What is the total number of reviews per category?
- Which products have the highest average ratings?
- What is the average actual price vs discounted price by category?
- Which products have the highest number of reviews?
- How many products have a discount of 50% or more?
- What is the distribution of product ratings (e.g., 3.0, 4.0, etc.)?
- What is the total potential revenue by category?
- How many unique products fall into each price range bucket?
- How does the rating relate to the level of discount?
- How many products have fewer than 1,000 reviews?
- Which categories have products with the highest discounts?
- Identify the top 5 products by combining high rating and high number of reviews.

## Codes / Formulas Used
Some of the Excel formulas used to implement calculated columns and analysis are documented below.

### Shortened Product Name
Combines the first four words of the product name:
```excel
==TRIM(LEFT(B3,FIND("#",SUBSTITUTE(B3," ","#",4)&"#")-1))
```
### Price Range Bucket
Assigns each product into one of three price segments:

Less than ₹200
Between ₹200 and ₹500
Greater than ₹500
``` excel
=IF([@discounted_price]<200,"<₹200", IF(OR([@discounted_price]=200,[@discounted_price]<=500),"₹200-₹500",">₹500"))
```

### Discount Range Bucket
Groups products by discount level:
``` excel
=IF(M2<=10%,"0 - 10%",IF(M2<=20%,"11 - 20%",IF(M2<=30%,"21 - 30%",IF(M2<=40%,"31 - 40%",IF(M2<=50%,"41 - 50%",IF(M2<=60%,"51 - 60%",IF(M2<=70%,"61 - 70%", IF(M2<=80%,"71 - 80%",IF(M2<=90%,"81 - 90%","91-100%")))))))))
```

### Total Potential Revenue
Calculates potential revenue as actual price multiplied by number of ratings:
``` excel
=[@actual_price]*[@rating_Count]
```

### Top Product Score
Ranks products by rating and number of reviews combined:
``` excel
=[@rating]+([@rating_count/1000)
```
### Discount Range Bucket
to determine which products have a discount of 50% or more
``` excel
=IF([@discount_percentage]>=50%, "50% or more", "<50%")
```

## Dashboard

An interactive Excel dashboard was created to visualize the insights derived from the pivot tables.  
Features of the dashboard:
- Category-level summaries (counts, average discounts, average ratings)
- Pricing analysis (actual vs discounted prices)
- Rating distributions
- Total potential revenue by category
- Top-performing and underperforming products
- Slicers for filtering the dashboard by category, price range, and discount range

The dashboard enables sellers and stakeholders to interactively explore product performance and make informed decisions.
`DASHBOARD SAMPLE`
<img width="1060" alt="Screenshot 2025-07-05 at 13 42 25" src="https://github.com/user-attachments/assets/164e324f-8f15-4863-aed1-07223c0792d9" />


## Key Insights

Some findings from the analysis:
- Categories with the largest discounts did not necessarily have the highest customer ratings, suggesting quality concerns at deep discounts
- Most products clustered in the ₹200–₹500 price range, which also corresponded to moderate ratings
- A few products with deep discounts (>50%) and high ratings stood out as high-potential items
- The top 5 products combined high ratings with high engagement (number of reviews), indicating strong customer approval and brand loyalty
- Revenue potential was highly concentrated in a handful of product categories, implying room for growth in less-served segments

## Techniques and Tools Used

- Microsoft Excel
  - Data cleaning (remove duplicates, handle nulls, type corrections)
  - Formula-based calculated columns
  - Pivot tables and charts
  - Slicers for interactivity
  - Dashboard design and storytelling
- Analytical thinking and business problem-solving

## Repository Contents

- `Chioma_Ejigha_Amazon_Analysis_File.xlsx` — Excel file containing:
  - Sheet 1: Raw Data (Original)
  - Sheet 2: Cleaned Data
  - Sheet 3: Structured Table
  - Sheet 4: Pivot Tables
  - Sheet 5: Final Dashboard
  - Sheet 6: (Cleared sheet — ignored)
- `README.md` — this documentation

## How to Explore

1. Download and open `Chioma_Ejigha_Amazon_Analysis_File.xlsx` in Microsoft Excel.
2. Review the sheets in order:
   - Original Data
   - Cleaned Data
   - Structured Table
   - Pivot Tables
   - Dashboard
3. Use slicers in the Dashboard to interact with the visuals and explore trends by category, discount, or price band.

## Author

**Ejigha Chioma**  
Data Analyst  
Email: [Chiomaejigha2@gmail.com]  
Portfolio: [My portfolio](https://github.com/Chomzy003)

---

This project is where I began my portfolio-building and DSA journey, combining technical analysis with business-driven storytelling.
