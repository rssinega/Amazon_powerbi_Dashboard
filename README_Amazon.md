# Amazon Sales Intelligence Dashboard (Power BI)

An interactive Power BI dashboard that analyses Amazon sales across products, customers and regions. It is built on a star-schema data model and spread over five report pages, with KPI cards, charts, slicers and a detailed drill-through table.

## Dashboard Preview

![Amazon Sales Intelligence Dashboard](amazon_dashboard_screenshot.png)

## Project File

| File | Description |
|------|-------------|
| `Amazon_dashboard.pbix` | Power BI report containing the data model, measures and all report pages |

Open it with **Power BI Desktop** (free, Windows).

## Data Model

The model follows a star schema: one fact table in the centre, surrounded by four dimension tables.

| Table | Type | Fields used in the report |
|-------|------|---------------------------|
| `FACT_TABLE` | Fact | `SALES_ID`, `SALES_AMOUNT`, `PROFIT`, `QUANTITY`, `PAYMENT_METHOD`, `TOTAL_ORDERS` |
| `DIM_DATE` | Dimension | `DATE` (Year > Quarter > Month > Day hierarchy), `MONTH` |
| `PRODUCT` | Dimension | `PRODUCT_NAME`, `CATEGORY` |
| `CUSTOMER` | Dimension | `CUSTOMER_NAME`, `CUSTOMER_TYPE`, `GENDER` |
| `REGION` | Dimension | `Region`, `State`, `City` |

### Measures

| Measure | Purpose |
|---------|---------|
| Total Sales | Sum of sales amount |
| Total Profit | Sum of profit |
| Total Quantity | Units sold |
| Total Orders | Number of orders |
| Profit Margin % | Profit as a share of sales |
| Average Order Value | Sales per order |
| Total Customer | Count of customers |
| Top Product / Top Product Sales / Top product Profit | Best-performing product and its figures |
| Top Customer Sales | Sales of the best customer |
| Top Region / Top Region Sales / Top Region Profit | Best-performing region and its figures |

## Report Pages

### 1. Amazon Front (Home)
Landing page with the headline KPIs and an overview of the business.
- **KPI cards:** Total Sales, Total Profit, Total Quantity, Total Orders, Profit Margin %
- **Charts:** monthly sales trend (line), sales by region (bar), sales by category (donut), sales by product (bar), orders by payment method (donut)
- **Slicers:** Region, Category, Month
- **Highlight:** top-performing region (South, 30.1% of total sales)
- Navigation buttons to the other pages

### 2. Product Performance
- **KPI cards:** top product, its sales and its profit
- **Charts:** sales by product (bar), profit by product (donut), quantity by product (column)
- **Table:** Product Performance Details with product, category, orders, sales, profit and quantity

### 3. Customer Analytics
- **KPI cards:** total customers, average order value, top customer sales
- **Charts:** top customers by sales (bar), sales by customer type (donut), sales by gender (column)
- **Matrix:** customer name by product category, showing sales

### 4. Region-wise Performance
- **KPI cards:** top region, its sales and its profit
- **Charts:** sales by region (bar), sales by state (bar), sales by city (pie), profit by region (column)
- **Slicer:** Region

### 5. Sales Detail Explorer
A transaction-level view for digging into individual sales.
- **KPI cards:** Total Sales, Profit, Orders, Quantity
- **Table:** sales ID, customer, product, region, date (year, quarter, month, day), quantity, sales amount and profit
- **Slicers:** Product Name, Region
- **Drill-through:** filters on product and region let you jump here from other pages

## Key Metrics (from the dashboard)

| Metric | Value |
|--------|-------|
| Total Sales | 428.58K |
| Total Profit | 84.51K |
| Total Quantity | 306 |
| Total Orders | 100 |
| Profit Margin | 0.20 (20%) |
| Top Region | South, 30.1% of total sales |

**Sales by category**

| Category | Sales | Share |
|----------|-------|-------|
| Electronics | 152.21K | 35.52% |
| Fashion | 93.43K | 21.80% |
| Home Appliances | 75.27K | 17.56% |
| Accessories | 68.88K | 16.07% |
| Home & Kitchen | 38.79K | 9.05% |

**Other observations**
- Top products by sales: Smart Watch, Running Shoes and Coffee Maker.
- Orders are split evenly across payment methods: Cash on Delivery, Credit Card, Debit Card and UPI, 25 orders (25%) each.
- Regions by sales, highest to lowest: South, East, West, North.
- Monthly sales fall from about 56K in August to about 26K in February.

## Key Insights Available

- Which region, product and customer generate the most sales and profit
- Monthly sales trends and seasonality
- Profit margin across the business
- How sales split by product category, customer type and gender
- Preferred payment methods by order count

## How to Use

1. Open `Amazon_dashboard.pbix` in Power BI Desktop.
2. Use the navigation buttons at the top of each page to move between pages.
3. Use the slicers (Region, Category, Month, Product) to filter the visuals on a page.
4. Click a bar, slice or column to cross-filter the other visuals.
5. Use the Sales Detail Explorer page to check individual transactions.
6. If the data source path has changed on your machine, go to **Home > Transform data > Data source settings** and update it, then click **Refresh**.

## Tech Stack

- Power BI Desktop
- DAX (measures)
- Power Query (data loading)
- Star-schema data modelling

## Notes

- Table, field and measure names above were read from the report layout in the `.pbix` file. Relationship details, DAX formulas and the original data source are stored in the compressed data model, so add them here if you want them documented.
- The monthly sales line chart in the screenshot is ordered by value rather than by calendar, so months appear out of order (August, March, April, June...). Sorting the month column by month number in Power BI would fix this.
- Static text such as "South" and "30.1% of total sales" on the home page is typed into a text box, not calculated. It will not update if the data changes.

## Author

Sinegavalli.S
