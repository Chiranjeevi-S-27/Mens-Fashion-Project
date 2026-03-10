# Men's Fashion Dashboard
# Dashboard link - https://app.powerbi.com/groups/me/reports/2fb2e1a0-1d67-4ed1-ae57-45614c4b53d7/5375110a49e4969bc09c?experience=power-bi



This project demonstrates a data preparation and semantic modeling workflow in Power BI for a retail dataset. It showcases data extraction from a local SQL Server database , includes data cleaning using Power Query, and custom business logic using DAX.

Tools

Business Intelligence: Power BI 


Data Transformation: Power Query

Data Modeling: DAX 


Database: SQL Server 

Key Transformations & Features
1. Data Extraction & Cleaning
Connected directly to a local SQL Server database (fashion) to import the dbo.Men+Tshirt table.

Filtered out incomplete records where the Sale_Price was listed as "NA".

Converted necessary fields to numeric data types to ensure accurate calculations.

2. Handling Missing Data
Designed a dynamic solution for missing Original_Price values.

Created a conditional multiplier (Factor) that applies a 1.5x markup to the sales price if the original price was marked "NA".

Merged these conditional logic steps into a clean, finalized Marked Price column.

Optimized the model by removing intermediate calculation columns (Original_Price, Factor, Sales*factor) and standardizing column names (e.g., renaming to Sales Price).

3. DAX Data Modeling
Created several custom columns to extract deeper business insights:


Discount Percentage: Calculated the exact discount rate using DIVIDE('Men+Tshirt'[Marked Price]-'Men+Tshirt'[Sales Price],'Men+Tshirt'[Marked Price])*100.


Profit Simulation: Generated simulated profit margins for analysis using RANDBETWEEN(2,17).


Cost Price Derivation: Calculated the item cost price based on the sales price and simulated profit margin using DIVIDE(100*'Men+Tshirt'[Sales Price],100+'Men+Tshirt'[profit%]).

Portfolio Highlights
This repository highlights practical data analytical skills, specifically the ability to handle messy, real-world data issues like string values "NA" in numeric columns. By mathematically adding missing marked prices, the dataset was preserved for analysis without sacrificing data integrity.

# Dashboard snapshots
https://github.com/user-attachments/assets/dab51ce4-81e0-4a1f-8336-dee027ebc5ec

https://github.com/user-attachments/assets/6c2af748-760a-48fa-8c9f-d8327b5ba8d7
