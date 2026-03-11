# Men's Fashion Dashboard   
## Dashboard link-  https://app.powerbi.com/groups/me/reports/2fb2e1a0-1d67-4ed1-ae57-45614c4b53d7/5375110a49e4969bc09c?experience=power-bi

A *Power BI Data Analytics project* that analyzes fashion product pricing, discounts, and profitability using *SQL, Power Query, and DAX calculations*.
* SQL source (`fashion` database, `dbo.Men+Tshirt`)
* Power Query transformations
* DAX calculated columns
* Data cleaning logic
* Dashboard purpose
* Professional recruiter-friendly sections

---

# 👕 U-Fashion Sales Analytics Dashboard

A **Power BI Data Analytics project** that analyzes fashion product pricing, discounts, and profitability using **SQL, Power Query, and DAX calculations**.

This project demonstrates **end-to-end data analytics skills**, including:

* SQL data sourcing
* Data cleaning and transformation
* Power BI semantic modeling
* DAX calculations
* Interactive dashboard building

---

# 🚀 Project Overview

The **U-Fashion Analytics Dashboard** provides insights into:

* Brand performance
* Product pricing strategy
* Discount analysis
* Profitability estimation
* Retail pricing comparison

The dataset is sourced from a **SQL database (`fashion`)** containing men's T-shirt sales data.

---

# 🧠 Skills Demonstrated

| Skill               | Implementation                                  |
| ------------------- | ----------------------------------------------- |
| SQL Data Extraction | Connected Power BI to MySQL SQL database        |
| Data Cleaning       | Handled missing values and inconsistent pricing |
| Power Query (M)     | Created transformation pipeline                 |
| Data Modeling       | Built Power BI semantic model                   |
| DAX Calculations    | Calculated discount %, cost price, and profit   |
| Business Analysis   | Extracted pricing and margin insights           |

---

# 🏗️ Project Architecture

```
SQL Database (MySQL)
        │
        ▼
Power Query (Data Cleaning & Transformation)
        │
        ▼
Power BI Semantic Model
        │
        ▼
DAX Calculations
        │
        ▼
Interactive Dashboard
```

---

# 🗄️ Data Source

**Database:** `fashion`
**Table:** `dbo.Men+Tshirt`

Key attributes:

| Column         | Description          |
| -------------- | -------------------- |
| Brand          | Brand name           |
| Title          | Product title        |
| Sale_Price     | Actual selling price |
| Original_Price | Marked retail price  |

---

# ⚙️ Data Transformation (Power Query)

Power Query transformations were applied to clean and standardize the dataset.

### 1️⃣ Import Data from SQL Server

```m
Source = Sql.Database("localhost", "fashion")
```

---

### 2️⃣ Extract Men T-Shirt Table

```m
#"dbo_Men+Tshirt" = Source{[Schema="dbo",Item="Men+Tshirt"]}[Data]
```

---

### 3️⃣ Remove Invalid Records

Rows with invalid sales price values were removed.

```m
Table.SelectRows(#"dbo_Men+Tshirt", each ([Sale_Price] <> "NA"))
```

---

### 4️⃣ Handle Missing Original Price

If `Original_Price` was missing (`NA`), a **price factor was applied**.

```m
Factor = if [Original_Price] = "NA" then 1.5 else 0
```

---

### 5️⃣ Estimate Missing Marked Price

```m
Sales*factor = Sale_Price * Factor
```

If original price was missing:

```
Marked Price = Sales Price × Factor
```

Otherwise:

```
Marked Price = Original Price
```

---

### 6️⃣ Data Type Standardization

Converted numeric columns to proper numeric format.

---

### 7️⃣ Final Clean Dataset

Columns retained:

* Brand
* Title
* Sales Price
* Marked Price

---

# 📊 Data Model

The Power BI semantic model contains:

```
Table
 └── Men+Tshirt
```

Columns:

| Column       | Type    |
| ------------ | ------- |
| Brand        | Text    |
| Title        | Text    |
| Sales Price  | Numeric |
| Marked Price | Numeric |
| Discount%    | DAX     |
| Profit%      | DAX     |
| Cost Price   | DAX     |

---

# 🧮 DAX Calculations

### Discount Percentage

```DAX
Discount% =
DIVIDE(
    'Men+Tshirt'[Marked Price] - 'Men+Tshirt'[Sales Price],
    'Men+Tshirt'[Marked Price]
) * 100
```

Shows **how much discount was offered per product**.

---

### Profit Percentage

```DAX
profit% = RANDBETWEEN(2,17)
```

Simulates realistic **profit margins between 2% and 17%**.

---

### Cost Price Calculation

```DAX
cost price =
DIVIDE(
    100 * 'Men+Tshirt'[Sales Price],
    100 + 'Men+Tshirt'[profit%]
)
```

This estimates the **product cost based on sales price and margin**.

---

# 📈 Dashboard Insights


### Pricing Strategy

* How much discount brands are offering
* Difference between marked price and selling price

### Brand Analysis

* Best performing brands
* Pricing differences across brands

### Profitability Insights

* Estimated product cost
* Profit margins

---

# 📷 Dashboard Preview
https://github.com/user-attachments/assets/dab51ce4-81e0-4a1f-8336-dee027ebc5ec

https://github.com/user-attachments/assets/6c2af748-760a-48fa-8c9f-d8327b5ba8d7

---

# 🛠️ Tools used

| Tool        | Purpose               |
| ----------- | --------------------- |
| MySQL       | Data storage          |
| SQL         | Data extraction       |
| Power Query | Data cleaning         |
| Power BI    | Data modeling         |
| DAX         | Business calculations |
| AI model    | Image generation      |
---
