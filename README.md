# PMT-Company-Sales-Analysis-and-Performance-Overview
## Objective
The project aimed to develop a comprehensive sales dashboard that provides insights into company sales performance using various data sources. The goal was to facilitate decision-making by offering visual insights into revenue, costs, profit margins, and trends across different dimensions such as geography, product categories, and sales representatives.
## Scope 
The scope included gathering data from various files, performing data transformations, building a data model, creating custom calculations using DAX, and designing an insightful dashboard to visualize the findings.

## Data Sources
Data was gathered from multiple sources in various formats, including:

- **Sales:** Folder organized by year
- **Categories:** Excel file [Categories]
- **Geography:** Excel file
- **Product:** CSV / Database
- **SalesRep:** Excel file
- **SubCategories:** Excel file
  
### Task 1.1: 
Develop a mechanism to load all the files from the sales folder into a single Sales fact table. The mechanism is resilient, ensuring:
- Removal of any file from the folder does not cause errors.
- New yearly sales files are automatically loaded upon refresh.

## 2. Data Modeling

### Task 2.1:  
Transform the Sales fact table by:
- Splitting the "Location" field into Country and City fields.
- Formatting the Date field to ensure proper setup for time-based analysis.

### Task 2.2:  
Create a unique key (`GeoKey`) to link the Sales and Geography tables.

### Task 2.3:  
Clean the SalesRep and SubCategories queries by removing the prefix "ID - " from their respective ID columns. A reusable function was created to automate this cleanup process.

### Task 2.4:  
Create a comprehensive data model that connects all tables (Sales, Geography, Product, SalesRep, etc.) and utilize an existing Calendar table for time-based analysis.

## 3. DAX Calculations

### Task 3.1:  
Calculate **Total Revenue** by multiplying the product’s retail price by the units sold.

### Task 3.2:  
Calculate **Total Cost** by multiplying the product’s standard cost by the units sold.

### Task 3.3:  
Calculate **Gross Profit** by subtracting Total Cost from Total Revenue.

### Task 3.4:  
Develop a measure for **Gross Profit Month-over-Month (MoM) Growth Percentage** to assist in tracking profit trends.

### Task 3.5:  
Create a measure for **Average Sales Per Day** based on the actual sales dates.

### Task 3.7:  
- Conduct a **Breakdown Analysis** by Product to determine performance drops or increases.
- Implement time measures such as **Quarter-over-Quarter (QoQ) Growth** for Quarterly Business Reviews (QBR).

## 4. Dashboard Development

Using the measures and calculations, the final step was to build a one-page Power BI dashboard that visualizes sales insights. The dashboard includes:
- Visualizations to represent sales trends, product performance, and regional breakdowns.
- Chronologically sorted months (Jan-Dec) on the x-axis for time-based analysis.

## Conclusion

The project delivers an insightful sales performance dashboard, integrating multiple data sources and advanced calculations in Power BI. This helps the company make informed decisions based on detailed visual insights.
