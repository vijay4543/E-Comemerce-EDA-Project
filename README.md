# 🛒 E-Commerce Sales Exploratory Data Analysis (EDA)

An end-to-end Python Data Analytics project focused on exploring e-commerce sales, product performance, regional order patterns, sales-channel activity, order status, and delivery behavior.

This project demonstrates practical Data Analyst skills including data inspection, data cleaning, missing-value analysis, duplicate checks, data-type conversion, text standardization, feature engineering, Pandas aggregations, and data visualization using Matplotlib and Seaborn.

## 📌 Project Overview

The **E-Commerce Sales Exploratory Data Analysis (EDA)** project explores an imperfect e-commerce dataset and follows a practical data-analysis workflow: understanding the raw data, identifying quality issues, preparing fields for analysis, calculating a revenue metric, summarizing business patterns, and creating visualizations.

The initial dataset contains **10,000 rows and 15 columns**.

The analysis is intended to help investigate questions such as:

. Which product categories and products appear most frequently in orders?
. How are orders distributed across regions?
. Which sales channels are used most often?
. What does the order-status distribution look like?
. How do delivery days vary across groups?
. How does calculated revenue compare with the revenue field supplied in the dataset?
. Which data-quality issues should be resolved before using the data for business decisions?

The project follows a practical workflow:

**Raw Dataset → Data Inspection → Data Cleaning → Feature Engineering → Exploratory Analysis → Visualization → Findings and Recommendations**

## 🎯 Purpose of the Project

The main purpose is to demonstrate how raw, inconsistent sales data can be inspected and prepared for exploratory business analysis using Python.

### Key objectives

. Understand the structure and quality of the dataset.
. Identify missing values and potential duplicate records.
. Standardize inconsistent text and category values.
. Review and convert data types where needed.
. Handle missing values using appropriate methods.
. Create a calculated revenue field using Pandas `apply()`.
. Analyze product, category, regional, channel, and order-status patterns.
. Explore delivery-day distributions.
. Visualize patterns using Matplotlib and Seaborn.
. Document data-quality limitations before drawing business conclusions.

## 🔄 Project Workflow

```text
E-Commerce CSV Dataset
          ↓
Load Data with Pandas
          ↓
Inspect Shape, Columns, Data Types, and Statistics
          ↓
Explore Unique Values and Value Distributions
          ↓
Identify Missing Values, Inconsistencies, and Duplicates
          ↓
Clean and Standardize Fields
          ↓
Convert Data Types and Handle Missing Values
          ↓
Create Calculated Revenue with apply()
          ↓
Analyze with groupby() and Summary Statistics
          ↓
Visualize with Matplotlib and Seaborn
          ↓
Review Findings, Limitations, and Next Steps
```

## 🧹 Data Cleaning & Preparation

The notebook includes several data-preparation activities.

### 1. Data Inspection

Reviewed the dataset dimensions, column names, data types, descriptive statistics, unique values, and value distributions.

### 2. Missing-Value Analysis

Used Pandas methods such as `isnull().sum()` to inspect missing values.

Missing values were observed in several fields, including:

. `customer_id`
. `product_name`
. `category`
. `region`
. `quantity`
. `unit_price`
. `discount`
. `revenue`
. `payment_method`
. `order_status`
. `delivery_days`
. `customer_rating`

The notebook also encounters missing `order_date` values after date parsing in a later cleaning stage.

### 3. Duplicate Review

Checked for duplicate records and used `order_id` during duplicate handling. In a production analysis, duplicate order IDs should be reviewed carefully because repeated IDs may represent either duplicate records or legitimate multiple rows for an order.

### 4. Data-Type Conversion

Reviewed and worked on converting columns into appropriate formats, including date and numeric fields, to support further analysis.

### 5. Missing-Value Treatment

The notebook uses mode-based imputation for several categorical fields and median/mean-based imputation for numeric fields. The imputation strategy should be selected according to the meaning and distribution of each column.

### 6. Text Standardization

Reviewed category-like columns for inconsistent casing, whitespace, and spelling. Standardizing text helps avoid treating the same category as multiple groups.

### 7. Invalid-Value Review

The dataset contains placeholder or unusual values such as `?`, `unknown`, and blank strings in some fields. These values should be converted or handled consistently before numerical analysis.

### 8. Date Handling

Rows with missing `order_date` values were removed in a later cleaning stage of the notebook. Date parsing and the number of removed records should be documented when presenting final results.

> **Data-quality note:** The notebook still requires additional validation before the dataset can be considered fully analysis-ready. Examples of unusual values include negative or zero quantities, very large quantities, negative prices/revenue, discounts outside the expected range, negative or very large delivery durations, and ratings outside the intended scale. These should be investigated with documented rules rather than automatically treated as valid or invalid without context.

## 🧮 Calculated Analysis & Feature Engineering

### Calculated Revenue

The notebook creates a derived field called `calc_revenue` using Pandas `apply()` to calculate revenue from quantity, unit price, and discount.

Conceptually, the formula is:

```python
calc_revenue = quantity * unit_price * (1 - discount)
```

This formula assumes that `discount` is stored as a fraction—for example, `0.10` means a 10% discount. Check the actual discount format and invalid values before relying on the result.

Comparing `calc_revenue` with the original `revenue` column can help identify discrepancies and investigate data-quality issues. The calculated field should not automatically replace the source revenue field without a clear business rule.

## 📊 Exploratory Data Analysis

The notebook explores several areas using Pandas summaries and groupings.

### 1. Revenue by Product Category

Compares revenue values across product categories to explore how sales value is distributed.

### 2. Best-Selling Products

Examines product order counts to identify products that appear frequently in the dataset.

### 3. Regional Performance

Summarizes order activity across regions to compare geographical distribution.

### 4. Sales-Channel Performance

Explores the distribution of orders across available sales channels.

### 5. Order-Status Analysis

Summarizes order statuses such as delivered, shipped, pending, cancelled, or returned where those labels occur in the data.

### 6. Delivery Performance

Explores delivery-day patterns and variation. Invalid or extreme delivery-day values should be validated before interpreting the results.

### 7. Descriptive Statistics

Uses summary statistics and value distributions to identify potential anomalies and understand numerical fields.

## 📈 Visualizations

The notebook includes or attempts the following visualizations:

. **Category-wise count bar chart:** uses Matplotlib to compare category counts.
. **Regional distribution pie chart:** displays regional distribution; ensure that labels and plotted values correspond to the same categories.
. **Delivery-days box plot by payment method:** uses Seaborn to compare delivery-day distributions across payment methods.

### Recommended visualization improvements

. Use bar charts to compare product categories, products, and regions.
. Use a line chart for monthly revenue trends after validating dates and revenue values.
. Use histograms or box plots to examine delivery days and customer ratings after data validation.
. Use a stacked bar chart to compare order statuses across regions or sales channels.
. Add meaningful chart titles, axis labels, units, and a consistent color palette.
. Add a short written interpretation below each major chart.
. Verify that chart labels match the categories represented by the plotted values.

## 🛠️ Tools & Technologies Used

### Python

Used as the main programming language for data analysis.

### Pandas

Used for data loading, inspection, cleaning, missing-value analysis, transformations, grouping, and summary statistics.

### NumPy

Used for numerical operations and supporting data processing.

### Matplotlib

Used to create and customize charts.

### Seaborn

Used for statistical and categorical visualizations, including box plots.

### Jupyter Notebook

Used to run the analysis step by step and document the workflow.

### Main Pandas methods and concepts

Examples used or relevant to the notebook include:

```python
df.shape
df.info()
df.describe()
df.isnull().sum()
df["column"].value_counts()
df.groupby("column")
df.drop_duplicates()
df.apply()
```

Use the method names above as a quick reference; confirm the final notebook cells when documenting exactly which operations were completed.

## 📂 Dataset

### Dataset information

. **Dataset type:** E-commerce sales data
. **Initial size:** 10,000 rows × 15 columns
. **Local CSV filename used in the notebook:** `uncleaned_ecommerce_sales_analytics_10k.csv`
. **Kaggle dataset URL:** `ADD THE EXACT KAGGLE DATASET URL HERE`

The exact Kaggle page could not be verified from the notebook filename alone. Add the actual source URL you downloaded the dataset from before publishing. If the file was generated for practice or obtained from a different source, describe that source accurately instead of attributing it to Kaggle without verification.

### Dataset columns

| Column | Description |
|---|---|
| `order_id` | Order identifier |
| `order_date` | Order date |
| `customer_id` | Customer identifier |
| `product_name` | Product name |
| `category` | Product category |
| `region` | Sales region |
| `sales_channel` | Channel used to place the order |
| `quantity` | Quantity ordered |
| `unit_price` | Unit price |
| `discount` | Discount value |
| `revenue` | Revenue value supplied in the dataset |
| `payment_method` | Payment method |
| `order_status` | Order status |
| `delivery_days` | Delivery duration in days |
| `customer_rating` | Customer rating |

> **Dataset note:** Check the dataset's license and Kaggle terms before redistributing the CSV. If redistribution is not permitted, include the source link and instructions for downloading the data instead.

## 🧠 Data Analyst Skills Demonstrated

This project showcases foundational, practical skills for an entry-level Data Analyst portfolio.

### Data Cleaning

. Missing-value identification and treatment
. Duplicate review
. Data-type conversion
. Text and category standardization
. Identification of placeholders and unusual values
. Data-quality validation

### Data Transformation

. Creating calculated fields
. Applying a revenue formula with Pandas `apply()`
. Preparing columns for grouping and analysis
. Comparing a calculated metric with a source metric

### Data Analysis

. Aggregation and grouping with `groupby()`
. Category and product analysis
. Regional and sales-channel analysis
. Order-status analysis
. Delivery-time exploration
. Descriptive statistics and anomaly identification

### Data Visualization

. Matplotlib bar charts
. Regional distribution charts
. Seaborn box plots
. Chart interpretation and improvement planning

### Analytical Thinking

. Translating business questions into analysis tasks
. Checking whether data supports a conclusion
. Documenting assumptions and limitations
. Identifying additional validation needed before making recommendations

## 💡 Key Insights to Highlight

When presenting this project, focus on findings supported by the cleaned data and actual chart outputs—not just the charts themselves.

Examples of useful questions to answer:

. Which product categories have the highest order counts or validated revenue?
. Which products appear most frequently?
. Which regions have the largest share of orders?
. Which sales channels are most commonly used?
. What proportion of orders fall into each status?
. How does delivery time vary across payment methods or other relevant groups?
. How many records or values required cleaning?
. How closely does calculated revenue match the source revenue field?

**Important:** Add exact values and conclusions only after calculating and verifying them in your final notebook. This README does not claim specific business results that have not been confirmed.

## 🎥 Project Demonstration

A screen recording can be added to demonstrate the notebook and visualizations.

Suggested recording sequence:

1. Introduce the project objective and dataset.
2. Show the initial dataset and its columns.
3. Demonstrate missing-value and data-quality checks.
4. Show the cleaning and calculated-revenue steps.
5. Walk through the main groupby summaries.
6. Display the charts and explain what each one investigates.
7. Finish with key findings, limitations, and possible next steps.

Add the video to your repository only if its file size is practical. Otherwise, link to a hosted demonstration or include selected screenshots in the README.

## 📁 Suggested Repository Structure

```text
ecommerce-sales-eda/
│
├── README.md
├── notebooks/
│   └── E-Commerce-project.ipynb
├── data/
│   └── README.md
├── images/
│   ├── category_analysis.png
│   ├── regional_analysis.png
│   └── delivery_analysis.png
├── demo/
│   └── ecommerce_eda_demo.mp4
└── requirements.txt
```

The filenames above are suggested examples. Use the actual filenames you add to your repository. Keep the dataset out of the repository if the license or source terms do not permit redistribution.

### Example `requirements.txt`

```text
pandas
numpy
matplotlib
seaborn
jupyter
```

## 🚀 How to Run the Project

1. Clone or download the repository.
2. Download the dataset from the verified source listed in this README.
3. Place the CSV in the folder expected by the notebook, or update the file path.
4. Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

5. Start Jupyter Notebook:

```bash
jupyter notebook
```

6. Open `E-Commerce-project.ipynb` and run the cells from top to bottom.
7. Review the cleaning rules, outputs, and visualizations. Verify that each conclusion is supported by the final results.

**Reproducibility tip:** Replace machine-specific paths such as `D:/...` with a relative path or a clearly documented data location before sharing the notebook.

## 🔮 Future Improvements

This project can be expanded to demonstrate additional Data Analyst tools and techniques.

### Power BI

. Build an interactive sales dashboard.
. Add KPI cards and filters.
. Create monthly sales and regional comparisons.
. Document DAX measures and visuals as a separate project phase.

### SQL

. Load the dataset into MySQL.
. Practice filtering, grouping, joins, subqueries, and window functions.
. Compare SQL aggregation results with Pandas outputs.

### Python

. Add a reproducible before-and-after data-quality report.
. Validate numeric ranges and outliers with documented rules.
. Create monthly and yearly trend analysis.
. Improve chart styling and automate summary exports.

These are possible future extensions; list them as completed skills only after you have implemented them.

## 📌 Portfolio Value

This project demonstrates a core Data Analyst workflow:

**Raw Data → Inspect → Clean → Transform → Analyze → Visualize → Communicate Findings**

It provides practice in Python-based data preparation, exploratory analysis, metric validation, and visualization. It is suitable for an entry-level Data Analyst portfolio when accompanied by a reproducible notebook, clear chart interpretations, and verified findings.

## 👨‍💻 Author

**Gembali Vijay Kumar**

Aspiring Data Analyst

**Skills:** Python · Pandas · NumPy · Matplotlib · Seaborn · Data Cleaning · Exploratory Data Analysis · Data Visualization

. **GitHub:** https://github.com/vijay4543
. **LinkedIn:** https://www.linkedin.com/in/gembali-vijay-kumar-806289352/

## ⭐ Feedback

Suggestions and feedback are welcome. Feel free to explore the notebook, review the analysis workflow, and share ideas for improving the project.
