# Data Cleaning Log

## Project Overview

This project involved cleaning, validating, and preparing retail order data for business reporting and analysis. The objective was to create an analysis-ready dataset, document all data quality issues, and generate summary reports for business review.

---

# 1. Issues Found

The following data quality issues were identified in the raw dataset:

### Text Field Issues

* Leading and trailing spaces in text fields.
* Inconsistent capitalization and formatting.
* Missing values in Region and Ship Mode fields.
* Inconsistent category and sub-category naming.

### Date Issues

* Multiple date formats were present (DD-MMM-YYYY, MM/DD/YYYY, DD-MM-YYYY, YYYY-MM-DD).
* Missing date values.
* Ship dates occurring before order dates.
* Date values stored as text.

### Duplicate Issues

* Exact duplicate records.
* Duplicate Order IDs.
* Duplicate Order IDs containing conflicting information.

### Discount Issues

* Missing discount values.
* Negative discount values.
* Discount values above the allowed range.

### Order and Payment Issues

* Cancelled orders.
* Failed payments.
* Refunded orders requiring separate reporting.

### Calculation Issues

* Potential sales and profit calculation mismatches.
* Missing or inconsistent financial values.

---

# 2. Cleaning Actions Performed

### Text Cleaning

* Removed extra spaces using TRIM.
* Standardized capitalization and text formatting.
* Corrected inconsistent category and sub-category values.
* Replaced missing Region values with "Unknown".
* Replaced missing Ship Mode values with "Unknown".

### Date Cleaning

* Converted all dates into a consistent dd-mmm-yyyy format.
* Converted text-based dates into valid Excel date values.
* Validated order and ship dates.
* Calculated shipping_delay_days.

### Duplicate Handling

* Identified exact duplicate records.
* Removed exact duplicate rows.
* Reviewed duplicate Order IDs.
* Retained conflicting duplicate records and flagged them for review.

### Discount Validation

* Replaced missing discounts with 0 when supporting sales fields were valid.
* Flagged negative discounts as invalid.
* Flagged discounts greater than 100% as invalid.

### Calculated Fields Created

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

---

# 3. Business Rules Applied

### Missing Region

* Missing Region values were replaced with "Unknown".

### Missing Ship Mode

* Missing Ship Mode values were replaced with "Unknown".

### Missing Discount

* Missing discounts were replaced with 0 when other sales-related fields were valid.

### Negative Discount

* Negative discounts were flagged as invalid.

### Discount Above Allowed Range

* Discounts greater than 100% were flagged as invalid.

### Cancelled Orders

* Retained in dataset.
* Excluded from completed sales summaries.

### Failed Payments

* Retained in dataset.
* Excluded from completed sales summaries.

### Refunded Orders

* Retained in dataset.
* Summarized separately in reporting outputs.

### Ship Date Before Order Date

* Flagged as Invalid Shipping Record.

---

# 4. Assumptions Made

* Slash-formatted dates were interpreted as MM/DD/YYYY because values such as 08/31/2024 confirmed U.S. date formatting.
* Dates were standardized to dd-mmm-yyyy format.
* Maximum valid discount was assumed to be 50%.
* Missing Region and Ship Mode values were replaced with "Unknown".
* Cancelled, Failed, and Refunded records were retained for audit and reporting purposes.

---

# 5. Records Removed

* Exact duplicate rows were removed from the cleaned dataset.
* Duplicate records containing identical information were consolidated.

Records Removed: 20

---

# 6. Records Flagged

The following records were flagged for review:

* Duplicate Order IDs with conflicting information.
* Negative discount records.
* Discount values above 100%.
* Invalid shipping records.
* Missing critical fields.
* Date validation issues.



---

# 7. Limitations

* Ambiguous date values where both day and month were less than or equal to 12 required assumptions regarding source date format.
* Duplicate records with conflicting information could not be automatically resolved without business confirmation.
* Data quality validation was performed using available fields only.
* Some business assumptions were necessary due to the absence of source system documentation.

---

# Final Outcome

The dataset was cleaned, validated, and transformed into an analysis-ready format. Data quality reports, pivot summaries, calculated fields, and validation checks were created to support business reporting and decision-making.
