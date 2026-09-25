# Automotive Sales Intelligence — Data Dictionary

## 1. Dataset Overview

The dataset contains historical automotive sales transactions at order-line level.

Each record represents a sales transaction associated with a customer, product, order, geographic market, pricing information, and commercial classification.

The dataset supports analysis across four primary dimensions:

* **Orders**
* **Products**
* **Customers**
* **Geography**

Additional commercial attributes such as deal size and order status support segmentation and performance analysis.

---

# 2. Data Dictionary

## Order Fields

| Field             | Description                                                  | Analytical Role            |
| ----------------- | ------------------------------------------------------------ | --------------------------- |
| `ORDERNUMBER`     | Unique identifier for a customer order                       | Order identification       |
| `ORDERLINENUMBER` | Sequential identifier for an individual line within an order | Transaction-level analysis |
| `ORDERDATE`       | Date on which the order was placed                           | Time-series analysis       |
| `STATUS`          | Current or recorded status of the order                      | Order-status analysis      |

---

## Product Fields

| Field         | Description                           | Analytical Role        |
| ------------- | -------------------------------------- | ----------------------- |
| `PRODUCTCODE` | Unique identifier for the product     | Product identification |
| `PRODUCTLINE` | Product category or product family    | Product-line analysis  |
| `MSRP`        | Manufacturer's suggested retail price | Pricing reference      |

---

## Sales Fields

| Field             | Description                                               | Analytical Role  |
| ----------------- | ----------------------------------------------------------- | ------------------ |
| `QUANTITYORDERED` | Number of units included in the transaction               | Volume analysis  |
| `PRICEEACH`       | Selling price per unit                                    | Pricing analysis |
| `SALES`           | Total monetary value associated with the transaction line | Revenue analysis |

### Sales Calculation

At transaction level, sales can generally be represented as:

```text
Sales ≈ Quantity Ordered × Price Each
```

The `SALES` field is treated as the primary revenue measure for the analytical model.

---

## Customer Fields

| Field              | Description                       | Analytical Role         |
| ------------------ | ---------------------------------- | ------------------------- |
| `CUSTOMERNAME`     | Name of the customer or account   | Customer analysis       |
| `CONTACTLASTNAME`  | Customer contact's last name      | Customer identification |
| `CONTACTFIRSTNAME` | Customer contact's first name     | Customer identification |
| `PHONE`            | Customer contact telephone number | Customer reference      |

A consolidated customer/contact name can be derived where required.

---

## Geographic Fields

| Field          | Description                                   | Analytical Role      |
| -------------- | ----------------------------------------------- | ----------------------- |
| `ADDRESSLINE1` | Primary customer address                      | Geographic reference |
| `ADDRESSLINE2` | Secondary address information where available | Geographic reference |
| `CITY`         | Customer city                                 | Geographic analysis  |
| `STATE`        | Customer state or region where available      | Geographic analysis  |
| `POSTALCODE`   | Customer postal/ZIP code                      | Geographic analysis  |
| `COUNTRY`      | Customer country                              | Market analysis      |

The `COUNTRY` field is the primary geographic dimension used in the dashboard.

---

## Commercial Fields

| Field      | Description                                        | Analytical Role   |
| ---------- | ----------------------------------------------------- | -------------------- |
| `DEALSIZE` | Commercial classification of the transaction/order | Deal segmentation |

Deal-size categories are used to compare sales contribution and transaction distribution across different commercial segments.

---

## Customer Activity Field

| Field                  | Description                                        | Analytical Role            |
| ----------------------- | ----------------------------------------------------- | ----------------------------- |
| `DAYS_SINCE_LASTORDER` | Number of days since the customer's previous order | Customer activity analysis |

This field can provide additional context when evaluating customer purchasing behavior.

---

# 3. Data Types

The analytical model should assign appropriate data types to each field.

| Field Category        | Recommended Type       |
| ----------------------- | ------------------------- |
| Order Number          | Integer / Whole Number |
| Order Line Number     | Integer / Whole Number |
| Order Date            | Date                    |
| Quantity Ordered      | Integer / Whole Number |
| Price Each            | Decimal Number          |
| Sales                 | Decimal Number          |
| MSRP                  | Decimal Number          |
| Days Since Last Order | Integer / Whole Number |
| Product Code          | Text                     |
| Product Line          | Text                     |
| Customer Name         | Text                     |
| Country               | Text                     |
| Deal Size             | Text                     |
| Status                | Text                     |

---

# 4. Data Quality Considerations

## Order Date

The original order-date field contained mixed representations, including standard date values and Excel serial date values.

The field was standardized into a consistent date format before analytical use.

This transformation is important because inconsistent date types can cause:

* Incorrect sorting.
* Failed date calculations.
* Incorrect time-series aggregation.
* Power BI type-conversion errors.

---

## Customer Names

Customer identification is primarily based on `CUSTOMERNAME`.

Contact first and last names are separate attributes and can be combined where a full contact name is required.

---

## Geographic Values

Country values should be standardized before geographic visualization.

Potential issues include:

* Inconsistent country naming.
* Country-name recognition by Power BI.
* Ambiguous geographic values.

Where required, country codes can be introduced as an additional geographic attribute.

---

## Numerical Fields

The following fields should be validated as numeric:

* `QUANTITYORDERED`
* `PRICEEACH`
* `SALES`
* `MSRP`
* `DAYS_SINCE_LASTORDER`

Numeric validation ensures that aggregations and DAX calculations operate correctly.

---

# 5. Analytical Grain

The primary analytical grain is the **order-line transaction**.

Therefore:

```text
1 Row = 1 Order Line
```

An order can contain multiple order lines.

Consequently:

```text
Distinct Orders ≠ Number of Rows
```

This distinction is important when calculating order-level KPIs.

For example:

```DAX
Total Orders =
DISTINCTCOUNT(Sales[ORDERNUMBER])
```

rather than:

```DAX
COUNTROWS(Sales)
```

---

# 6. Important Analytical Distinctions

### Revenue vs. Orders

`SALES` measures monetary contribution, while `ORDERNUMBER` identifies orders.

### Orders vs. Order Lines

One order may contain multiple products, resulting in multiple order-line records.

### Quantity vs. Revenue

A product can have high unit volume without generating the highest revenue.

### MSRP vs. Actual Selling Price

`MSRP` represents the manufacturer's suggested retail price, while `PRICEEACH` represents the transaction selling price.

These fields should therefore not be treated as interchangeable.

---

# 7. Derived Metrics

The following metrics can be derived from the source fields.

### Total Sales

```text
SUM(SALES)
```

### Total Units

```text
SUM(QUANTITYORDERED)
```

### Total Orders

```text
DISTINCT COUNT of ORDERNUMBER
```

### Average Order Value

```text
Total Sales / Total Orders
```

### Average Selling Price

```text
Total Sales / Total Units
```

### Sales Contribution %

```text
Segment Sales / Total Sales
```

These derived metrics form the basis of the Power BI analytical layer.

---

# 8. Data Limitations

The dataset primarily supports historical descriptive and diagnostic analysis.

Potential limitations include:

* Historical data may not represent current market conditions.
* No explicit cost data is available for true profitability analysis.
* No inventory data is available for supply-side analysis.
* No customer demographic information is available.
* No marketing attribution data is available.
* No competitor pricing data is available.
* Historical sales relationships should not automatically be interpreted as causal relationships.

Therefore, analytical conclusions should remain within the scope supported by the available data.
