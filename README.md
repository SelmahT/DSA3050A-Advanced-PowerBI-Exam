# Advanced E-Commerce Analytics: The Olist Marketplace Case Study

<div align="center">

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Python](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

</div>

---

## 1. Project Title

**Advanced E-Commerce Analytics: The Olist Marketplace Case Study**  
*End Semester Examination — DSA 3050A Business Intelligence & Analytics*

---

## 2. Student Information

| Field | Details |
|---|---|
| **Name** | Selmah Tzindori |
| **Admission Number** | 602 |
| **University** | United States International University (USIU) |
| **Course Code** | DSA 3050A |
| **Class** | Business Intelligence and Analytics |
| **Date Submitted** | 17th April 2025 |
| **Semester** | Spring Semester 2026 |

---

## 3. Course Code and Class

- **Course Code:** DSA 3050A  
- **Course Name:** Business Intelligence and Analytics  
- **Examination:** Advanced Power BI End Semester Exam  
- **Total Marks:** 100

---

## 4. Project Overview

This project delivers a complete, end-to-end Power BI analytical solution built on the **Brazilian E-Commerce Public Dataset by Olist**. Starting from 8 raw CSV files containing over **99,000 transactional records**, the project executes the full Business Intelligence lifecycle:

1. Raw data acquisition and schema planning  
2. Power Query data cleaning and transformation (11 documented steps)  
3. Dimensional data modelling (Snowflake Schema)  
4. DAX calculation layer (8 measures + 3 calculated columns)  
5. Three-page interactive dashboard design  
6. Analytical insight generation and business recommendations  

---

## 5. Problem Statement

Olist, Brazil's largest multi-vendor department store marketplace, faces a **critical operational visibility gap**. Key business questions this solution answers:

- **Sales Performance:** Which Brazilian regions and product categories drive the highest revenue?
- **Logistics Efficiency:** How does delivery lag (actual vs. estimated delivery) affect customer satisfaction, and which shipping tier is the primary failure point?
- **Profitability:** Are high freight costs in specific states eroding net margins — and is the marketplace on track to hit its annual revenue target?

Without structured BI analytics, these questions cannot be answered consistently, and operational decisions are made on intuition rather than evidence.

---

## 6. Dataset Description

| Attribute | Detail |
|---|---|
| **Source** | [Brazilian E-Commerce Public Dataset by Olist — Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) |
| **Coverage** | Real, anonymised commercial data from 2016–2018 |
| **Main Table Rows** | 99,441+ orders (exceeds 9,000-row requirement) |
| **Number of Files** | 8 CSV files |
| **Data Types** | Geographic, temporal, categorical, numerical financial |

### Source Tables

| Table | Role | Key Fields |
|---|---|---|
| `olist_orders_dataset` | Central Fact | `order_id`, `customer_id`, `order_status`, `order_purchase_timestamp` |
| `olist_order_items_dataset` | Fact/Transaction | `order_id`, `product_id`, `price`, `freight_value` |
| `olist_order_payments_dataset` | Fact/Detail | `order_id`, `payment_type`, `payment_value` |
| `olist_products_dataset` | Product Dimension | `product_id`, `product_category_name` |
| `olist_customers_dataset` | Customer Dimension | `customer_id`, `customer_state`, `customer_zip_code_prefix` |
| `olist_sellers_dataset` | Seller Dimension | `seller_id`, `seller_city`, `seller_state` |
| `olist_geolocation_dataset` | Geo Dimension | `geolocation_zip_code_prefix`, `geolocation_lat`, `geolocation_lng` |
| `product_category_name_translation` | Lookup | `product_category_name`, `product_category_name_english` |

---

## 7. Tools Used

| Tool | Purpose |
|---|---|
| **Microsoft Power BI Desktop** | Primary BI and dashboard tool |
| **Power Query Editor** | Data ingestion, cleaning, and transformation |
| **DAX (Data Analysis Expressions)** | Measure and calculated column creation |
| **CALENDARAUTO()** | Auto-generated continuous date table |
| **Kaggle** | Dataset sourcing |
| **GitHub** | Version control and submission repository |

---

## 8. Steps Followed

### Phase 1: Data Acquisition
1. Downloaded all 8 CSV files from Kaggle (Olist Brazilian E-Commerce dataset)
2. Reviewed raw data in Excel to plan the schema and identify quality issues
3. Documented domain, business problem, and analytical objectives

### Phase 2: Data Cleaning and Transformation (Power Query — 11 Steps)

| # | Step | Technique |
|---|---|---|
| 1 | Load all 8 CSV files into Power BI | CSV Import / Source Connection |
| 2 | Merge product translations (Portuguese → English) | Merge Queries — Left Outer Join |
| 3 | Replace null English categories with "Uncategorized" | Replace Values |
| 4 | Consolidate orders + items + payments into `Fact_Sales` | Multi-table Merge → Rename |
| 5 | Remove duplicate `order_id` entries | Remove Duplicates |
| 6 | Extract Year and Month Name from purchase timestamp | Add Column > Date |
| 7a | Create `Delivery Performance` conditional column (Late / On-Time) | Conditional Column |
| 7b | Convert price and freight to Fixed Decimal (Currency) | Data Type Conversion |
| 8 | Remove redundant metadata columns | Choose Columns |
| 9 | Capitalise seller city names (e.g. sao paulo → Sao Paulo) | Text.Proper transformation |
| 10 | Convert lat/lng from Text to Decimal Number | Data Type Assignment |
| 11 | Disable Load on intermediate staging tables | Query Properties |

### Phase 3: Data Modelling
1. Built a **Snowflake Schema** with `fact_sales` as the central fact table
2. Created `dim_date` using `CALENDARAUTO()` with Year, Month, Quarter columns
3. Established 6 relationships (all One-to-Many, single-direction cross-filter)
4. Marked `dim_date` as the official Date Table
5. Organised tables and disabled staging query loads

### Phase 4: DAX Development
1. Created 3 calculated columns: `Sales Segment`, `Is Weekend`, `Shipping Tier`
2. Created 8 measures grouped in a `Key Measures` Display Folder
3. Tested all measures against raw data totals for accuracy

### Phase 5: Dashboard Design
1. Built Page 1 (Executive Summary) with KPI cards, trend chart, category bar
2. Built Page 2 (Detailed Analysis) with Decomposition Tree, Matrix, AI Key Influencers
3. Built Page 3 (Insights & Monitoring) with Gauge, Top/Bottom tables, Donut slicer
4. Applied consistent navy/slate-grey corporate theme across all pages
5. Added slicers, tooltips, and cross-filtering behaviour

### Phase 6: Analysis and Documentation
1. Derived 5 analytical insights from dashboard evidence
2. Formulated 5 actionable business recommendations
3. Wrote full PDF report with screenshots at every stage
4. Structured and uploaded GitHub repository

> [!TIP]
> **Project Assets & Build Documentation**
> To inspect the data model, DAX measures, or read the full project analysis, use the links below:
> * 📊 **[Source Power BI File (.pbix)](https://github.com/SelmahTzindori/DSA3050A-Advanced-PowerBI-Exam/raw/main/powerbi/DSA3050_EndSem_Practical.pbix)** — *Direct download of the model.*
> * 📄 **[Final Technical Report (PDF)](https://github.com/SelmahTzindori/DSA3050A-Advanced-PowerBI-Exam/blob/main/report/DSA3050A_Finals_Report.pdf)** — *Full documentation of the analytical journey.*

---

## 9. Dashboard Features

### Page 1: Executive Summary
- **4 KPI Cards:** Total Revenue (Ksh 16M), Total Orders (99K), Average Order Quantity (158), % of Total Sales
- **Area Trend Chart:** Revenue by Month Name — highlights seasonal peaks (May–Aug) and September trough
- **Horizontal Bar Chart:** Top 5 product categories by revenue (Top N filtered)
- **Slicers:** Year (tile) and Customer State (radio button)
- **Cross-filtering:** Clicking a category bar filters the trend chart dynamically

### Page 2: Detailed Analysis
- **Decomposition Tree:** Hierarchical revenue breakdown — Category → State → Shipping Tier
- **Matrix with Heatmap:** Revenue by Product × Shipping Tier with conditional background colour scaling
- **Drillable Bar Chart:** Regional revenue by State → City (drill-down enabled)
- **Key Influencers AI Visual:** Statistical drivers of late delivery — Economy tier = 16.23× higher risk

### Page 3: Insights and Performance Monitoring
- **Clustered Column Chart:** High Value vs. Standard segment revenue across 2016–2018
- **Gauge Chart:** Actual revenue (Ksh 15.74M) vs. annual target (Ksh 18M)
- **Top Performers Table:** Categories ranked by descending revenue
- **Bottom Performers Table:** Categories ranked by ascending revenue (dead stock identification)
- **Shipping Tier Donut Chart:** Order distribution — Economy 66%, Standard 24%, Express 7%

---

## 10. Key DAX Measures

```dax
-- Total Revenue
Total Revenue = SUM(fact_sales[payment_value])

-- Total Orders (unique count)
Total Orders = DISTINCTCOUNT(fact_sales[order_id])

-- Average Order Value
Avg_Order = DIVIDE([Total Revenue], [Total Orders])

-- Revenue Year-to-Date
Revenue YTD = TOTALYTD([Total Revenue], 'dim_date'[Date])

-- Previous Year Revenue
Previous Year Rev = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('dim_date'[Date]))

-- Year-over-Year Growth %
Revenue Growth % = DIVIDE([Total Revenue] - [Previous Year Rev], [Previous Year Rev], 0)

-- Top Category Rank
Top Category Rank = RANKX(ALL(dim_products[product_category_name]), [Total Revenue])

-- % of Total Sales
% of Total Sales = DIVIDE([Total Revenue], CALCULATE([Total Revenue], ALL(fact_sales)))
```

### Calculated Columns

```dax
-- Sales Segment
Sales Segment = IF(fact_sales[payment_value] > 500, "High Value", "Standard")

-- Is Weekend
Is Weekend = IF(WEEKDAY(fact_sales[order_purchase_timestamp], 2) > 5, "Weekend", "Weekday")

-- Shipping Tier
Shipping Tier =
VAR DaysToDeliver = DATEDIFF(
    fact_sales[order_purchase_timestamp],
    fact_sales[order_delivered_customer_date],
    DAY
)
RETURN
SWITCH(TRUE(),
    ISBLANK(DaysToDeliver), "In Transit",
    DaysToDeliver <= 3,     "Express",
    DaysToDeliver <= 7,     "Standard",
    "Economy"
)
```

---

## 11. Key Insights

| # | Insight | Evidence |
|---|---|---|
| 1 | **Regional Concentration Risk** — SP (São Paulo) generates Ksh 6M, more than 3× the next state (RJ) | Revenue by States bar chart, Page 2 |
| 2 | **Economy Shipping Failure** — Economy tier increases late delivery likelihood by **16.23×** | Key Influencers AI visual, Page 2 |
| 3 | **September Dead Zone** — Revenue drops 59% MoM from August (Ksh 1.7M) to September (Ksh 0.7M) | Revenue by Month trend chart, Pages 1 & 3 |
| 4 | **High-Value Segment Growth** — High Value orders grew to Ksh 2.1M in 2018; Standard remains dominant at Ksh 6.5M | Clustered column by segment, Page 3 |
| 5 | **Long-Tail Category Risk** — Top 3 categories generate Ksh 1M+ each; Security & Services earns only Ksh 324 total | Top/Bottom Performers tables, Page 3 |

---

## 12. Challenges Encountered

| Challenge | How It Was Resolved |
|---|---|
| Duplicate `order_id` values causing relationship failure | Applied `Remove Duplicates` on the Orders table before loading (Step 5) |
| Portuguese product category names in raw data | Merged with the translation lookup table using Left Outer Join (Step 2) |
| Null values in merged English category column | Replaced nulls with "Uncategorized" using Replace Values (Step 3) |
| Floating-point rounding errors in financial columns | Converted price and freight to Fixed Decimal Number (Currency) data type (Step 7b) |
| Text-formatted latitude/longitude breaking map visuals | Converted geolocation coordinates to Decimal Number type (Step 10) |
| Intermediate staging tables cluttering the field pane | Disabled Load on all staging queries — data already consolidated into Fact/Dim tables (Step 11) |
| RANKX returning tied ranks across filter contexts | Applied `ALL()` to override dimension filters, ensuring global ranking regardless of slicer state |

---

## 13. Conclusion

This Power BI solution demonstrates the full Business Intelligence lifecycle applied to a real-world e-commerce dataset. The Olist marketplace analysis reveals three critical operational priorities for business leadership:

1. **Fix Economy Shipping immediately** — a 16.23× late delivery multiplier is an existential customer satisfaction risk
2. **Diversify geographic revenue** — São Paulo concentration is a strategic vulnerability  
3. **Activate September** — a 59% monthly revenue collapse is a predictable, preventable loss

Beyond solving these immediate problems, the model architecture (Snowflake Schema, CALENDARAUTO Date Table, DAX Display Folders) is built for scalability — new data loads will automatically refresh all visuals, and the measure library can be extended without restructuring the model.

The solution is fully documented, reproducible, and ready for stakeholder deployment.

---

## Repository Structure

```
DSA3050A-Advanced-PowerBI-Exam/
│
├── data/
│   ├── olist_orders_dataset.csv
│   ├── olist_order_items_dataset.csv
│   ├── olist_order_payments_dataset.csv
│   ├── olist_products_dataset.csv
│   ├── olist_customers_dataset.csv
│   ├── olist_sellers_dataset.csv
│   ├── olist_geolocation_dataset.csv
│   └── product_category_name_translation.csv
│
├── screenshots/
│   ├── raw_data/
│   ├── power_query/
│   ├── model_view/
│   ├── dax_formulas/
│   └── dashboard_pages/
│
├── report/
│   └── DSA3050A_Selmah_Tzindori_602_Report.pdf
│
├── powerbi/
│   └── DSA3050A_OlistAnalytics.pbix
│
└── README.md
```

---

<div align="center">

**DSA 3050A | Selmah Tzindori | ID: 602 | USIU | Spring 2026**

*Dataset: [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — Kaggle*

</div>
