# Automotive Sales Intelligence

> **Turning automotive transaction data into commercial intelligence for sales, product, customer, and market decisions.**

## Live Power BI Dashboard

[**View Interactive Dashboard →**](https://app.powerbi.com/view?r=eyJrIjoiYzc0YjAwYzUtZWE2Yy00NzU4LTg1YjctODU4MTJjYWM2NzgwIiwidCI6IjVhNTNlYzEyLTIzMGMtNDYxNi05ZjUxLWYyYjA4Mjg3ZDM5NyJ9)



## Project Overview

The **Automotive Sales Intelligence** project analyzes historical automotive sales transaction data to understand **sales performance, product contribution, customer value, geographic performance, pricing, and deal-size dynamics**.

The project transforms raw transactional records into a structured analytical framework that helps answer four core business questions:

1. **How is overall sales performance changing over time?**
2. **Which products and markets are driving revenue?**
3. **Which customers and customer segments contribute the most commercial value?**
4. **Where are the key opportunities and weaknesses in sales performance?**

The analysis combines **data cleaning, exploratory analysis, business intelligence, KPI development, and interactive Power BI reporting** to provide management with a consolidated view of commercial performance.

---

## Business Problem

The automotive business has accumulated transactional data covering:

* Orders
* Products
* Customers
* Pricing
* Sales
* Order dates
* Product lines
* Geographic markets
* Deal sizes
* Order status

However, raw transaction records alone do not provide sufficient visibility into commercial performance.

Management needs a structured analytical system capable of identifying:

* Sales growth and decline over time
* High- and low-performing product lines
* Geographic markets contributing to revenue
* High-value customers
* Deal-size distribution
* Revenue concentration
* Changes in purchasing activity
* Potential areas for commercial improvement

The objective of this project is therefore to convert transactional sales data into **decision-ready commercial intelligence**.

---

# Analytical Objectives

The project focuses on five analytical dimensions:

### 1. Sales Performance

Evaluate how revenue and order activity change over time.

### 2. Product Performance

Identify which product lines and individual products generate the greatest commercial contribution.

### 3. Customer Intelligence

Understand customer purchasing behavior and identify high-value accounts.

### 4. Geographic Performance

Compare sales contribution across countries and markets.

### 5. Deal & Order Analysis

Understand the relationship between deal size, order volume, sales value, and order status.

---

# Key Business Questions

## Section 1 — Sales & Market Performance

1. How is total sales performance changing over time?
2. Which product lines generate the highest sales?
3. Which countries contribute the most revenue?
4. How does sales performance vary across deal sizes?
5. Which products generate the highest sales value?

## Section 2 — Customer & Commercial Performance

6. Which customers generate the highest revenue?
7. Which customers place the highest number of orders?
8. How does average order value vary across markets?
9. Which product lines demonstrate the strongest commercial contribution?
10. Where are the largest opportunities for improving sales performance?

---

# Dataset

The project uses an automotive sales transaction dataset containing order-level information.

### Core fields

| Category   | Fields                                                      |
| ---------- | ----------------------------------------------------------- |
| Order      | Order Number, Order Line Number, Order Date, Status         |
| Product    | Product Code, Product Line, MSRP                            |
| Sales      | Quantity Ordered, Price, Sales                              |
| Customer   | Customer Name, Contact First Name, Contact Last Name, Phone |
| Geography  | Address, City, Postal Code, Country                         |
| Commercial | Deal Size                                                   |
| Time       | Order Date, Days Since Last Order                           |

The dataset contains historical transactions across multiple international markets.

---

# Data Preparation

The raw dataset required several preprocessing steps before analysis.

### Data cleaning included:

* Data type validation
* Date normalization
* Handling mixed date representations
* Numerical field validation
* Missing-value assessment
* Duplicate assessment
* Column standardization
* Customer name reconstruction
* Geographic normalization
* Validation of sales and quantity fields

One notable data-quality issue involved the **Order Date** field, where dates appeared in different representations, including conventional date strings and Excel serial date values.

The date field was transformed into a consistent date format before being used in the analytical model.

---

# Data Model

The Power BI model is designed around transactional sales data and supporting dimensions.

### Conceptual structure

```text
                    ┌─────────────────┐
                    │   Dim Date      │
                    └────────┬────────┘
                             │
                             │
┌─────────────────┐   ┌──────▼───────┐   ┌─────────────────┐
│ Dim Customer    │──►│ Fact Sales   │◄──│ Dim Product     │
└─────────────────┘   └──────┬───────┘   └─────────────────┘
                             │
                             │
                    ┌────────▼────────┐
                    │ Dim Geography    │
                    └─────────────────┘
```

The central transactional table contains individual sales records, while analytical dimensions provide additional context for time, products, customers, and geography.

---

# Key Performance Indicators

The dashboard focuses on commercially relevant KPIs.

### Sales KPIs

* **Total Sales**
* **Total Orders**
* **Units Sold**
* **Average Order Value**
* **Average Selling Price**

### Product KPIs

* **Sales by Product Line**
* **Units by Product Line**
* **Sales Contribution %**
* **Top Products by Revenue**

### Customer KPIs

* **Customer Revenue**
* **Orders per Customer**
* **Average Customer Order Value**
* **Top Customers by Sales**

### Market KPIs

* **Sales by Country**
* **Orders by Country**
* **Revenue Contribution by Market**
* **Average Sales per Order by Country**

---

# Dashboard Structure

The Power BI report is organized around two analytical sections.

## Section 1 — Sales & Market Performance

This section focuses on the organization's overall commercial performance.

### Key visuals

* Sales trend over time
* Sales by product line
* Sales by country
* Sales by deal size
* Sales KPI cards
* Geographic sales map
* Product performance analysis

### Business purpose

This section enables management to understand:

> **What is happening across the overall sales operation, products, and markets?**

---

## Section 2 — Customer & Commercial Intelligence

This section focuses on customer contribution and commercial behavior.

### Key visuals

* Top customers by sales
* Customer order volume
* Sales by customer
* Product/customer relationships
* Average order value
* Customer contribution analysis

### Business purpose

This section answers:

> **Which customers and commercial relationships are contributing most to business performance?**

---

# Deal Size Analysis

Deal size provides an additional commercial segmentation of the transaction base.

The dataset contains deal-size categories such as:

* Small
* Medium
* Large

The analysis evaluates how these categories contribute to:

* Total sales
* Order volume
* Units sold
* Customer activity

A doughnut visualization is used to provide a high-level view of **deal-size distribution**.

---

# Geographic Analysis

Geographic analysis evaluates sales performance across international markets.

Countries represented in the dataset include:

* Australia
* Austria
* Belgium
* Canada
* Denmark
* Finland
* France
* Germany
* Ireland
* Italy
* Japan
* Norway
* Philippines
* Singapore
* Spain
* Sweden
* Switzerland
* United Kingdom
* United States

The geographic analysis allows sales performance to be examined at country level and supports identification of differences in market contribution.

---

# Technology Stack

| Technology             | Purpose                                         |
| ---------------------- | ----------------------------------------------- |
| **Microsoft Power BI** | Business intelligence and dashboard development |
| **Power Query**        | Data cleaning and transformation                |
| **DAX**                | KPI calculations and analytical measures        |
| **Excel**              | Source data                                     |
| **Git / GitHub**       | Version control and project documentation       |

---

# Analytical Workflow

```text
Raw Automotive Sales Data
          │
          ▼
   Data Inspection
          │
          ▼
   Data Cleaning
          │
          ▼
 Data Type Validation
          │
          ▼
   Data Transformation
          │
          ▼
     Data Modeling
          │
          ▼
      DAX Measures
          │
          ▼
   Business Analysis
          │
          ▼
   Power BI Dashboard
          │
          ▼
 Commercial Intelligence
```

---

# DAX Measures

The analytical model uses DAX measures to calculate dynamic KPIs.

Examples include:

```DAX
Total Sales =
SUM(Sales[Sales])
```

```DAX
Total Orders =
DISTINCTCOUNT(Sales[Order Number])
```

```DAX
Total Units Sold =
SUM(Sales[Quantity Ordered])
```

```DAX
Average Order Value =
DIVIDE(
    [Total Sales],
    [Total Orders]
)
```

```DAX
Sales Contribution % =
DIVIDE(
    [Total Sales],
    CALCULATE(
        [Total Sales],
        ALL(Sales)
    )
)
```

These measures allow the dashboard to dynamically respond to filters such as:

* Product line
* Country
* Deal size
* Customer
* Order status
* Date

---

# Business Insights Framework

The project is designed to move beyond descriptive reporting.

The analytical framework follows:

```text
What happened?
      ↓
Where did it happen?
      ↓
Which products/customers/markets contributed?
      ↓
How large is the contribution?
      ↓
Where are commercial opportunities or weaknesses?
```

This approach shifts the project from a simple reporting dashboard toward a **sales intelligence system**.

---

# Expected Business Value

The resulting analytical system provides management with a consolidated view of:

### Revenue Performance

Understand how sales are distributed across products, customers, markets, and time.

### Product Strategy

Identify product lines and products with significant commercial contribution.

### Customer Strategy

Identify customers with substantial revenue and purchasing activity.

### Market Strategy

Compare sales contribution across geographic markets.

### Commercial Monitoring

Track changes in sales activity and deal-size composition.

### Decision Support

Provide a structured analytical foundation for commercial planning and resource allocation.

---

# Project Structure

```text
automotive-sales-intelligence/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── powerbi/
│   └── automotive_sales_intelligence.pbix
│
├── documentation/
│   ├── business_problem.md
│   ├── data_dictionary.md
│   └── analytical_framework.md
│
├── screenshots/
│   ├── overview.png
│   ├── sales_market.png
│   └── customer_analysis.png
│
├── README.md
└── .gitignore
```

> Adjust the folder names above to match the final structure of the GitHub repository.

---

# Project Deliverables

The project produces:

* Cleaned automotive sales dataset
* Analytical data model
* DAX KPI framework
* Interactive Power BI dashboard
* Business performance analysis
* Customer intelligence analysis
* Product performance analysis
* Geographic market analysis
* Project documentation

---

# Key Skills Demonstrated

This project demonstrates practical capabilities in:

### Data Analytics

* Exploratory Data Analysis
* Business Analysis
* KPI Development
* Sales Analytics
* Customer Analytics
* Market Analysis

### Data Preparation

* Power Query
* Data Cleaning
* Data Transformation
* Data Type Management
* Data Quality Validation

### Business Intelligence

* Power BI
* DAX
* Interactive Dashboards
* Data Modeling
* Drill-down Analysis
* Dynamic Filtering

### Analytical Thinking

* Translating business problems into analytical questions
* Designing decision-oriented KPIs
* Connecting transactional data to business outcomes
* Converting descriptive statistics into commercial insights

### Version Control

* Git
* GitHub
* Repository documentation
* Reproducible analytical workflow

---

# Project Outcome

The **Automotive Sales Intelligence** project demonstrates how transactional automotive sales data can be transformed into an interactive business intelligence environment for monitoring **sales, products, customers, markets, and commercial performance**.

Rather than treating Power BI as a visualization tool alone, the project uses it as the final analytical layer of a structured workflow:

> **Raw Data → Data Quality → Data Model → KPIs → Business Questions → Intelligence → Decision Support**

---

# Author

**George E. Ejembi**

**Data Analyst | Automation Specialist | Business Intelligence**

### Core Areas

* Data Analytics
* Business Intelligence
* SQL
* Python
* Power BI
* DAX
* Machine Learning
* Decision Intelligence

---

## License

This project is intended for **educational, portfolio, and analytical demonstration purposes**.

Dataset ownership and licensing remain subject to the original dataset provider.
