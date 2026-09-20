# Ecommerce_Sales_Analysis_Dashboard

## Project Overview

This project presents an interactive **E-Commerce Sales & Profit Analytics Dashboard** developed using Tableau.

The dashboard analyzes **115,746 e-commerce order records** across multiple markets, customer segments, product categories, 
and regions. It provides a consolidated view of sales performance, profitability, order quantity, market contribution,
and year-over-year category performance.

The project combines **data preparation, Tableau calculated fields, KPI development, interactive visualization, 
dashboard design, and business analysis**.

## Business Problem

E-commerce businesses generate large volumes of transactional data across products, customers, markets, and regions. Raw transactional data alone does not provide an efficient way for management to understand business performance.

The key business questions addressed by this project are:

1. How are current-year sales performing compared with the previous year?
2. Is profit growing at the same rate as sales?
3. Which product categories are increasing or decreasing in sales?
4. Which markets contribute the largest share of total sales?
5. How does order quantity vary across markets and months?
6. Which customer segments contribute the most revenue?
7. Where should management focus attention to improve sales and profitability?

---

## Project Objectives

The main objectives of the project are to:

- Develop an interactive Tableau sales dashboard.
- Monitor key business KPIs.
- Compare current-year performance against the previous year.
- Analyze category-level sales performance.
- Identify positive and negative year-over-year trends.
- Analyze sales contribution by market.
- Analyze monthly order quantity patterns by market.
- Understand customer segment contribution.
- Provide actionable business insights from transactional data.
- Present the analysis in a portfolio-ready business intelligence project.

---

## Dataset

The dataset contains **115,746 records and 20 fields** covering e-commerce transactions from **2023 to 2024**.

### Dataset Dimensions

| Attribute | Details |
|---|---:|
| Records | 115,746 |
| Columns | 20 |
| Period | 2023–2024 |
| Markets | 5 |
| Customer Segments | 3 |
| Product Categories | 50 |

##  Tools & Technologies

- **Tableau** – Data visualization and dashboard development
- **CSV** – Source dataset
- **Tableau Calculated Fields** – KPI and analytical calculations
- **Interactive Filters / Actions** – Dashboard exploration

- ## Tableau Calculated Fields

The dashboard uses calculated fields to support KPI calculations and year-over-year analysis.

#### 1. YTD Sales

Calculates sales for the latest year available in the dataset.

```text
{ FIXED :
    SUM(
        IF YEAR([Order Date]) = {MAX(YEAR([Order Date]))}
        THEN [Sales]
        END
    )
}
```

#### 2. PYTD Sales

Calculates sales for the previous year.

```text
{ FIXED :
    SUM(
        IF YEAR([Order Date]) = {MAX(YEAR([Order Date])) - 1}
        THEN [Sales]
        END
    )
}
```

#### 3. YOY Sales %

Calculates the percentage change in sales compared with the previous year.

```text
([YTD Sales] - [PYTD Sales]) / [PYTD Sales]
```

#### 4. YTD Profit

Calculates current-year profit using `Profit Per Order`.

```text
{ FIXED :
    SUM(
        IF YEAR([Order Date]) = {MAX(YEAR([Order Date]))}
        THEN [Profit Per Order]
        END
    )
}
```

#### 5. PYTD Profit

Calculates previous-year profit.

```text
{ FIXED :
    SUM(
        IF YEAR([Order Date]) = {MAX(YEAR([Order Date])) - 1}
        THEN [Profit Per Order]
        END
    )
}
```

#### 6. YOY Profit %

```text
([YTD Profit] - [PYTD Profit]) / [PYTD Profit]
```

#### 7. YTD Order Quantity

Calculates the current-year order quantity.

```text
{ FIXED :
    SUM(
        IF YEAR([Order Date]) = {MAX(YEAR([Order Date]))}
        THEN [Order Quantity]
        END
    )
}
```

#### 8. PYTD Order Quantity

```text
{ FIXED :
    SUM(
        IF YEAR([Order Date]) = {MAX(YEAR([Order Date])) - 1}
        THEN [Order Quantity]
        END
    )
}
```

#### 9. YOY Order Quantity %

```text
([YTD Quantity] - [PYTD Quantity]) / [PYTD Quantity]
```

#### 10. Performance Indicator

The dashboard uses conditional symbols to make year-over-year performance easier to understand.

```text
IF [YOY Sales %] > 0 THEN
    "▲"
ELSEIF [YOY Sales %] < 0 THEN
    "▼"
END
```

## Dashboard

### Ecommerce_Sales_Analysis_Dashboard

<img width="695" height="367" alt="image" src="https://github.com/user-attachments/assets/b1482290-3a3c-4a23-84de-0d0e00102e20" />

### Key Performance Indicators

| KPI | 2024 | YoY Change |
|---|---:|---:|
| Sales | $14.11M | +5.04% |
| Profit | $1.30M | -0.46% |
| Order Quantity | 157,978 | +15.02% |

This combination indicates that sales and order volume increased while profit remained approximately flat.

## Dashboard Visualizations

### 1. Sales KPI

Displays:

- Current-year sales
- Year-over-year percentage change
- Sales trend

**Purpose:** Monitor overall revenue performance and identify changes over time.

### 2. Profit KPI

Displays:

- Current-year profit
- Year-over-year percentage change
- Profit trend

**Purpose:** Monitor profitability and identify whether profit is keeping pace with sales.

### 3. Order Quantity KPI

Displays:

- Current-year order quantity
- Year-over-year change
- Order quantity trend

**Purpose:** Understand changes in transaction/order volume.

### 4. Market Share by Sales

A donut chart displays the contribution of each market to total sales.

| Market | Sales Share |
|---|---:|
| LATAM | 45.86% |
| Europe | 43.37% |
| Pacific Asia | 8.32% |
| Africa | 2.25% |
| USCA | 0.21% |

LATAM and Europe together account for approximately **89.23% of 2024 sales**.

### 5. Category-wise YTD vs PYTD Sales

A horizontal bar chart compares current-year category sales with previous-year performance.

The visualization uses conditional formatting to distinguish:

- **Greater than PY**
- **Less than PY**
- **No Sales in PY**

This makes it easier to identify categories experiencing growth or decline.

### 6. Market-wise Monthly Order Quantity Ranking

The dashboard compares monthly **Order Quantity rankings by Market**.

The visualization uses:

- Market as the color dimension
- Month as the time dimension
- Order Quantity ranking

## Key Insights

### 1. Sales increased while profit remained almost flat

2024 sales reached approximately **$14.11M**, representing **+5.04% YoY**.

Profit was approximately **$1.30M**, with a **-0.46% YoY** change.

This indicates that revenue growth did not translate into equivalent profit growth.

The approximate profit-to-sales ratio decreased from about **9.75% in 2023 to 9.24% in 2024**, based on the dashboard's Sales and Profit measures.

### 2. Order volume increased significantly

Order quantity increased to **157,978**, representing approximately **+15.02% YoY**.

The increase in order volume was considerably larger than the increase in sales.

This suggests that average revenue generated per order/order quantity may have declined or that additional volume came from lower-value transactions.

### 3. LATAM is the largest sales market

LATAM contributed **45.86%** of 2024 sales, while Europe contributed **43.37%**.

Together, these two markets generated approximately **89.23% of total sales**.

This indicates that sales performance is heavily concentrated in these two markets.

### 4. Several major categories declined

| Category | 2024 Sales | YoY |
|---|---:|---:|
| Cardio Equipment | $2.34M | -4.05% |
| Fishing | $1.90M | -24.98% |
| Camping & Hiking | $1.66M | +12.55% |
| Water Sports | $1.34M | +21.10% |
| Cleats | $1.20M | -26.34% |
| Women's Apparel | $0.86M | -24.51% |
| Men's Footwear | $0.80M | -25.18% |

Overall sales growth is therefore not evenly distributed across product categories.

### 5. Camping & Hiking and Water Sports show positive growth

Two significant categories show positive year-over-year performance:

- Camping & Hiking: **+12.55%**
- Water Sports: **+21.10%**

These categories contributed meaningful sales while also showing positive year-over-year movement.

## Business Recommendations

### 1. Investigate Profit Margin Pressure

Sales increased by 5.04%, while profit decreased slightly.

Management should investigate:

- Product-level margins
- Discounting
- Product costs
- Shipping costs
- Market-level profitability
- Category-level profitability

The objective is to understand why increased sales volume did not result in equivalent profit growth.

### 2. Investigate Declining High-Value Categories

Categories such as:

- Fishing
- Cleats
- Women's Apparel
- Men's Footwear

experienced significant year-over-year declines.

Further analysis could examine:

- Pricing
- Product availability
- Customer demand
- Promotions
- Regional performance
- Competitive conditions

### 3. Evaluate Successful Categories

Camping & Hiking and Water Sports show positive year-over-year sales growth.

Management could evaluate:

- Inventory availability
- Product assortment
- Marketing investment
- Cross-selling opportunities
- Market-specific demand

before deciding whether to increase investment in these categories.

### 4. Analyze Market Concentration

LATAM and Europe account for approximately 89% of sales.

The business could evaluate whether this concentration represents:

- Strong market penetration
- Opportunity for further growth
- Geographic concentration risk

Additional market-level profitability analysis would help determine where future investment should be considered.

## Tableau Dashboard

The final dashboard provides an interactive analytical interface containing:

- Sales KPI
- Profit KPI
- Order Quantity KPI
- Market Share by Sales
- Category-wise YTD vs PYTD Sales
- Market-wise Monthly Order Quantity Ranking
- Market filter
- Customer Segment filter

👉 **[View Interactive Dashboard on Tableau Public](https://public.tableau.com/app/profile/nagajothi/viz/Ecommerce_Sales_Dashboard_17899123953900/EcommerceSales?publish=yes)**

## Project Outcome

The project transformed a raw dataset containing **115K+ e-commerce transactions** into an interactive business intelligence dashboard.

The final solution enables users to:

- Monitor sales performance
- Track profitability
- Compare current-year and previous-year performance
- Identify category-level growth and decline
- Understand market sales contribution
- Analyze order quantity patterns
- Compare customer segment performance
