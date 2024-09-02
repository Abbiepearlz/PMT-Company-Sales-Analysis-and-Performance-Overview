# PMT-Company-Sales-Analysis-and-Performance-Overview
## Objective
The project aimed to develop a comprehensive sales dashboard that provides insights into company sales performance using various data sources. The goal was to facilitate decision-making by offering visual insights into revenue, costs, profit margins, and trends across different dimensions such as geography, product categories, and sales representatives.
## Scope 
The scope included gathering data from various files, performing data transformations, building a data model, creating custom calculations using DAX, and designing an insightful dashboard to visualize the findings.

## Data Sources
Data was gathered from multiple sources in various formats, including:

- **Sales:** Folder organized by year [Sales 2014.csv](https://github.com/user-attachments/files/16840203/Sales.2014.csv)
- **Categories:**[Categories.xlsx](https://github.com/user-attachments/files/16840163/Categories.xlsx)
- **Geography:** [Geography.xlsx](https://github.com/user-attachments/files/16840166/Geography.xlsx)
- **Product:** CSV [Product.csv](https://github.com/user-attachments/files/16840185/Product.csv)
- **SalesRep:** [SalesRep.xlsx](https://github.com/user-attachments/files/16840174/SalesRep.xlsx)
- **SubCategories:** [SubCategories.xlsx](https://github.com/user-attachments/files/16840176/SubCategories.xlsx)

  
### Task 1.1: 
Developed a mechanism to load all the files from the sales folder into a single Sales fact table. The mechanism is resilient, ensuring:
- Removal of any file from the folder does not cause errors.
- New yearly sales files are automatically loaded upon refresh.

## 2. Data Modeling

### Task 2.1:  
Transform the Sales fact table by:
- Splitting the "Location" field into Country and Town.
- Formatting the Date field to ensure proper setup for time-based analysis.
![geography](https://github.com/user-attachments/assets/9f975ae2-f1a4-4648-991c-b54f3a1c759c)

### Task 2.2:  
Create a unique key (`GeoKey`) to link the Sales and Geography tables.
![Youtube Data Project 7_31_2024 6_41_18 PM](https://github.com/user-attachments/assets/2d1a8baa-a650-4c6d-bc96-bba61d86afa5)


### Task 2.3:  
Clean the SalesRep and SubCategories queries by removing the prefix "ID - " from their respective ID columns. A reusable function was created to automate this cleanup process.

![Sales rep ID](https://github.com/user-attachments/assets/2144eed9-485b-404b-b275-1721a4191d7b)


### Task 2.4:  
Create a comprehensive data model that connects all tables (Sales, Geography, Product, SalesRep, etc.) and utilize an existing Calendar table for time-based analysis.
![Data model](https://github.com/user-attachments/assets/da6c1933-76b8-4050-83eb-762a39ef8b21)

## 3. DAX Calculations

### Task 3.1:  
Calculate **Total Revenue** by multiplying the product’s retail price by the units sold.
```PowerBi
Total Revenue = Sales[Units] * RELATED('Product'[RetailPrice])
```

### Task 3.2:  
Calculate **Total Cost** by multiplying the product’s standard cost by the units sold.
```PowerBi
Total Cost = Sales[Units]*RELATED('Product'[StandardCost])
```

### Task 3.3:  
Calculate **Gross Profit** by subtracting Total Cost from Total Revenue.
```PowerBi
Gross Profit = Sales[Total Revenue]-Sales[Total Cost]
```

### Task 3.4:  
Develop a measure for **Gross Profit Month-over-Month (MoM) Growth Percentage** to assist in tracking profit trends.
```PowerBi
MOM % = DIVIDE([Profit MOM],[Previous Month],0)
```

### Task 3.5:  
Create a measure for **Average Sales Per Day** based on the actual sales dates.
```PowerBi
AVERAGE SALES PER DAY = DIVIDE([Total Revenue (m)],COUNTROWS(VALUES('Date Table'[Date])))
```
![Avg Sales per day](https://github.com/user-attachments/assets/07f54bf5-608a-4aab-b4a8-4fa91c69316b)


### Task 3.7:  
- Conducted a **Breakdown Analysis** by Product to determine performance drops or increases.
- Implement time measures such as **Quarter-over-Quarter (QoQ) Growth** for Quarterly Business Reviews (QBR).
 ```PowerBi
QMOM = [Total Gross Profit (m)]-[Previous Quater]
```


## 4. Dashboard Development

Used the measures and calculations, the final step was to build a one-page Power BI dashboard that visualizes sales insights. The dashboard includes:
- Visualizations to represent sales trends, product performance, and regional breakdowns.
- Chronologically sorted months (Jan-Dec) for time-based analysis.
  
![pmt dashboard ](https://github.com/user-attachments/assets/c9769c71-bdd0-43fa-9d3e-646bc3b6fa87)

## Conclusion

The project delivers an insightful sales performance dashboard, integrating multiple data sources and advanced calculations in Power BI. This helps the company make informed decisions based on detailed visual insights.
