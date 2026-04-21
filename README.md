# Quick Commerce Business Intelligence Dashboard (Blinkit Analytics)
**Tech Stack**: Power BI, Data Modeling (Star Schema), DAX Measures,Power Query (ETL)

## Business Problem
Quick commerce platforms like Blinkit operate in a highly competitive environment where delivery speed, customer segmentation, and category performance directly impact 
revenue and retention. Without a unified analytics view, operational inefficiencies go undetected and marketing spend remains untargeted.
This project builds an end-to-end Power BI solution across 4 relational tables to surface actionable insights on sales, delivery, customers, and product categories.

## Objectives
- Analyze sales and order trends over time
- Evaluate delivery performance (on-time vs delayed)
- Identify high-value customer segments
- Understand category-wise revenue contribution
- Provide actionable insights for operational optimization

## Dataset
- **Source:** Kaggle (Blinkit Quick Commerce Dataset)
- **Tables & Size:**

| Table | Rows | Key Fields |
|---|---|---|
| blinkit_customers | 2,500 | customer_id, customer_name, area, customer_segment, avg_order_value, total_orders |
| Orders | 5,000 | order_id, order_date, order_total, delivery_status, actual_delivery_time, promised_delivery_time, payment_method |
| Order_items | 5,000 | order_id, product_id, quantity, unit_price |
| Products | 268 | product_id, product_name, brand, category, price, mrp |


## Approach
### 1. Data Transformation (Power Query)
- Cleaned and standardized raw tables
- Standardized date formats, delivery status labels, and category names
- Removed nulls and validated referential integrity across all 4 tables

  
### 2. DAX Measures Developed
- **Total Sales** — sum of order totals across all orders
- **Total Orders** — distinct order count
- **Average Order Value** — Total Sales / Total Orders
- **On Time Delivery %** — % orders where actual delivery ≤ promised delivery time
- **Average Order Value** per customer segment

### 3. Dashboard Features
- Monthly sales trend (full year Jan–Dec view)
- City-wise sales ranking (18 cities tracked)
- Customer segment revenue breakdown (Regular / New / Premium / Inactive)
- Order delivery status distribution
- Category-level revenue analysis (12 categories)
- Filter panel: Segment -- Month -- Area -- Delivery Status -- Payment Method

## KPIs at a Glance
| Metric | Value |
|---|---|
| Total Sales | ₹11M |
| Total Orders | 5,000 |
| Average Order Value | ₹2,000 |
| On-Time Delivery % | 69.4% |
| On-Time Orders | 3,470 (69.4%) |
| Delayed Orders | 1,037 (20.7%) |

## Key Insights
### Sales Performance
- Total revenue of ₹11M across 5,000 orders
- Sales peaked mid-year (May–July ~₹1.1M–₹1.2M/month)
- Declined toward year-end (Nov–Dec ~₹0.6M) — suggesting seasonal demand drop or data cutoff
- Monthly AOV stable at ~₹2K throughout the year

### Delivery Performance
- Only 69.4% of orders delivered on time — nearly 1 in 3 orders is delayed
- 20.7% significantly delayed — direct risk to customer satisfaction and retention
- Improving on-time rate to 85%+ could significantly reduce churn

### Customer Segmentation
- Revenue evenly distributed: Regular ₹2.9M -- New ₹2.8M -- Premium ₹2.7M -- Inactive ₹2.6M
- Low differentiation between segments suggests Premium customers are undermonetized
- "New" segment revenue (₹2.8M) signals strong acquisition but conversion to Premium needs focus

### Category Performance
- Top 3 categories: Dairy & Breakfast (₹1.24M) -- Household Care (₹1.14M) -- Pet Care (₹1.13M)
- Daily essentials dominate — typical quick commerce purchase pattern
- Baby Care and Instant Food at ₹0.74M each — underperforming relative to platform potential

### Geographic Performance
- Top city: Orai (₹100K) followed by Deoghar (₹95K) and Nandyal (₹83K)
- 18 cities tracked with significant revenue variation
- Tier-2 cities driving strong performance — opportunity for targeted expansion

## Dashboard Preview
### Main Dashboard
Main Dashboard(images/main_dashboard.png)

### Data Model (Star Schema)
Data Model(images/data_model.png)

## Business Impact
| Area | Finding | Recommended Action |
|---|---|---|
| Logistics | 30.6% delayed orders | Audit delivery partners by city |
| Revenue | Mid-year peak, year-end drop | Plan promotions for Oct–Dec |
| Customer value | Premium ≈ Regular revenue | Launch Premium loyalty program |
| Categories | Essentials dominate | Cross-sell Baby Care + Frozen Food |
| Geography | Tier-2 cities strong | Expand inventory in top 5 cities |


## How to Use
1. Download `blinkit_dashboard.pbix` from `/dashboard/`
2. Open in Power BI Desktop (January 2026 or later)
3. Use the Filter Panel to slice by:
   - Customer Segment (Regular/New/Premium/Inactive)
   - Month
   - Area
   - Delivery Status
   - Payment Method
4. Explore KPI cards, trend charts, and category breakdowns on Page 1
