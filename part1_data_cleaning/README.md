# Business Data Cleaning, Validation & Excel Reporting

## Problem Summary

This project focuses on cleaning, validating, and preparing a retail sales dataset for business analysis. The raw dataset contained inconsistent text formatting, missing values, duplicate records, invalid discounts, date inconsistencies, and calculation mismatches. The objective was to transform the raw data into a clean, analysis-ready dataset and generate business reports to support decision-making.

## Dataset Description

The dataset contains order-level retail sales information, including customer details, product information, order dates, shipping information, sales, discounts, costs, profits, payment status, and order status.

### Key Fields

* Order ID
* Order Date
* Ship Date
* Customer Name
* Customer Segment
* Region
* State
* City
* Category
* Sub Category
* Ship Mode
* Quantity
* Unit Price
* Discount
* Sales
* Cost
* Profit
* Payment Status
* Order Status

## Tools Used

* Microsoft Excel
* Excel Functions (TRIM, SUBSTITUTE, IF, IFERROR, ROUND, YEAR, MONTH, DATEDIF)
* Find & Replace
* Flash Fill
* Conditional Formatting
* Pivot Tables
* Data Validation

## Cleaning Steps Performed

### 1. Raw Data Preservation

* Preserved the original dataset as `raw_orders.xlsx`.
* Performed all cleaning activities in `cleaned_orders.xlsx`.

### 2. Text Cleaning

Standardized the following columns:

* Customer Name
* Segment
* Region
* State
* City
* Category
* Sub Category
* Ship Mode
* Payment Status
* Order Status

Cleaning included:

* Removing leading and trailing spaces
* Eliminating extra spaces
* Correcting inconsistent capitalization
* Standardizing category names
* Removing unwanted special characters where applicable

### 3. Date Validation

Validated and standardized:

* Order Date
* Ship Date

Performed the following checks:

* Missing dates
* Invalid date values
* Ship dates earlier than order dates
* Non-date text values

Created a new calculated column:

* Shipping Delay Days

### 4. Duplicate Validation

Identified:

* Exact duplicate rows
* Duplicate Order IDs
* Duplicate records with conflicting information

### 5. Business Rule Validation

Applied business validation rules for:

* Missing Region
* Missing Ship Mode
* Missing Discount
* Negative Discount
* Discount above valid range
* Cancelled Orders
* Failed Payments
* Refunded Orders
* Invalid Shipping Dates

### 6. Calculated Columns

Created the following calculated fields:

* Cleaned Discount
* Calculated Sales
* Calculated Profit
* Profit Margin
* Shipping Delay Days
* Order Month
* Order Year
* Data Quality Flag

## Business rules applied

1. Missing `region` values were filled as `Unknown` and flagged in `cleaning_flags`.
2. Missing `ship_mode` values were filled as `Unknown` and flagged in `cleaning_flags`.
3. Missing `discount` values were treated as `0` only when `sales`, `cost`, `profit`, `unit_price`, and `quantity` were all present and valid.
4. Negative discount values were flagged invalid.
5. Discount values above the allowed range (> 1.0) were flagged invalid.
6. Cancelled orders were excluded from completed sales summary.
7. Failed payment orders were excluded from completed sales summary.
8. Refunded orders were marked for separate refund summary.
9. Ship dates before order dates were flagged as invalid shipping records.

## Data Quality Issues Identified

The dataset was analyzed for the following quality issues:

* Missing values
* Duplicate records
* Duplicate Order IDs
* Invalid discounts
* Date inconsistencies
* Shipping date errors
* Sales calculation mismatches
* Profit calculation mismatches
* Order status inconsistencies
* Payment status inconsistencies

A complete summary is available in:

`outputs/data_quality_report.xlsx`

## Pivot Reports Created

The following business summaries were created using Pivot Tables:

* Sales and Profit by Region
* Sales and Profit by Category
* Order Count by Ship Mode
* Profit Margin by Customer Segment
* Refunded, Cancelled, and Failed Orders by Region
* Monthly Sales Trend

## Key Business Insights

* Regional sales performance can be compared to identify high-performing markets.
* Product category analysis highlights the most profitable categories and sub-categories.
* Shipping mode analysis helps evaluate operational efficiency.
* Customer segment analysis identifies the most profitable customer groups.
* Monthly sales trends reveal seasonal business patterns.
* Refunds, cancellations, and failed payments provide visibility into operational and financial risks.

## Assumptions and Limitations

### Assumptions

* Missing discounts were treated as zero only when related sales information was valid.
* Missing Region and Ship Mode values were replaced with "Unknown".
* Conflicting duplicate records were retained and flagged for manual review.
* Business calculations were based on the cleaned dataset only.

### Limitations

* Invalid source data requiring business confirmation could not be corrected automatically.
* Some inconsistent records require manual verification.
* Cleaning decisions were made according to the assignment requirements and available data.

## Repository Structure

```
part1_data_cleaning/
│
├── data/
│   ├── raw_orders.xlsx
│   └── cleaned_orders.xlsx
│
├── outputs/
│   ├── data_quality_report.xlsx
│   ├── pivot_summary.xlsx
│   └── cleaning_log.md
│
├── screenshots/
│   ├── raw_data_preview.png
│   ├── cleaned_data_preview.png
│   ├── pivot_summary_1.png
│   └── pivot_summary_2.png
│
└── README.md
```

## Screenshots Included

The repository includes screenshots of:

* Raw dataset preview
* Cleaned dataset preview
* Pivot Summary Report 1
* Pivot Summary Report 2

These screenshots provide a visual overview of the cleaning process and final analytical reports.
