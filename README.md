# Northwind-Traders-Sales-BI-Dashboard
## 🚀 Project Introduction
This project presents a comprehensive Executive Business Intelligence Dashboard for Northwind Traders, a global gourmet food supplier. Built in Power BI, the interactive 3-page dashboard provides leadership with clear visibility into sales performance, product portfolio health, regional dynamics, shipping operations, and salesforce productivity.
The solution analyzes a relational dataset containing 830 orders and approximately 2,155 order detail records spanning from 2013 to mid-2015. Through advanced data modeling, DAX calculations, and thoughtful visualization, the dashboard transforms raw transactional data into actionable strategic insights — highlighting strong revenue growth while uncovering critical risks such as heavy dependence on discontinued products and rising freight costs.
The dashboard directly addresses key business questions around revenue trends, seasonality, category performance, operational efficiency, and discount strategy effectiveness.

---
## 🔍 Business Objectives:
The business aims on answering these key analytical questions:
#### - Sales Performance
What are the trends in revenue and order volume over time? Are there identifiable seasonal patterns?
#### - Product Intelligence
Which product categories are the top revenue drivers, and how does the discontinued status of products impact potential sales?
#### - Regional Insights
Which countries and cities represent the highest market share, and where are shipping (freight) costs disproportionately high?
#### - Operational Efficiency
How do different shippers compare in terms of cost and speed? Which employees are leading in total sales generated?
#### - Impact of Strategy
How do discounts affect the overall profit margin across different product lines?

### Bonus Questions the Dashboard Also Addresses:
- What is the risk level of the current product portfolio?
- How efficient is the shipping operation relative to revenue growth?
- Which customers and products contribute the most to revenue?
- How is the sales team performing individually and collectively?
---
## Dataset Overview
| Table | Field | Description |
|-------|-------|-------------|
|orders|orderID|Unique identifier for each order|
|orders|customerID|The customer who placed the order|
|orders|employeeID|The employee who processed the order|
|orders|orderDate|The date when the order was placed|
|orders|requiredDate|The date when the customer requested the order to be delivered|
|orders|shippedDate|The date when the order was shipped|
|orders|shipperID|The ID of the shipping company used for the order|
|orders|freight|The shipping cost for the order (USD)|
|order_details|orderID|The ID of the order this detail belongs to|
|order_details|productID|The ID of the product being ordered|
|order_details|unitPrice|The price per unit of the product at the time the order was placed (USD - discount not included)|
|order_details|quantity|The number of units being ordered|
|order_details|discount|The discount percentage applied to the price per unit|
|customers|customerID|Unique identifier for each customer|
|customers|companyName|The name of the customer's company|
|customers|contactName|The name of the primary contact for the customer|
|customers|contactTitle|The job title of the primary contact for the customer|
|customers|city|The city where the customer is located|
|customers|country|The country where the customer is located|
|products|productID|Unique identifier for each product|
|products|productName|The name of the product|
|products|quantityPerUnit|The quantity of the product per package|
|products|unitPrice|The current price per unit of the product (USD)|
|products|discontinued|Indicates with a 1 if the product has been discontinued|
|products|categoryID|The ID of the category the product belongs to|
|categories|categoryID|Unique identifier for each product category|
|categories|categoryName|The name of the category|
|categories|description|A description of the category and its products|
|employees|employeeID|Unique identifier for each employee|
|employees|employeeName|Full name of the employee|
|employees|title|The employee's job title|
|employees|city|The city where the employee works|
|employees|country|The country where the employee works|
|employees|reportsTo|The ID of the employee's manager|
|shippers|shipperID|Unique identifier for each shipper|
|shippers|companyName|The name of the company that provides shipping services|

- Time Period: Mid-2013 to Mid-2015 (~23 months)
- Total Orders: 830
- Total Order Line Items: 2,155
- Unique Customers: 91
- Unique Products: 77 across 8 categories
- Employees: 9 sales representatives
- Shippers: 3 logistics partners
---
## Data Model (Star schema)
<img width="1668" height="675" alt="Screenshot (201)" src="https://github.com/user-attachments/assets/8b14c261-26aa-4df6-89f2-918243ca90fa" />

---
## Data Preparation
Although the Northwind Traders dataset is relatively clean compared to most real-world data, several deliberate preparation steps were taken to ensure accuracy, usability, and optimal performance in the dashboard.
### Data Loading & Type Conversion
- Loaded all 7 CSV tables into Power BI.
- Changed key columns from Text to appropriate data types in Power Query:
   - OrderDate, RequiredDate, and ShippedDate → Date type (critical for time intelligence)
   - UnitPrice, Freight, and Discount → Decimal Number
   - ID fields (OrderID, ProductID, etc.) → Whole Number where appropriate

### Key Data Cleaning & Transformation Steps
- Calendar Table Creation: Built a dynamic Calendar table using DAX (CALENDAR + ADDCOLUMNS) to handle missing months and enable proper time intelligence functions (YoY, seasonality, trends). Marked as a Date Table for full DAX support.
- Employee Hierarchy: Handled blank ReportsTo value for the Vice President of Sales (Andrew Fuller) to maintain a clean organizational structure.
- Readability Enhancements:
  - Created Short Employee Name column (e.g., “Margaret P”, “Janet L”) for better chart visualization.
  - Created Short Month column (“Jan”, “Feb”, etc.) to improve X-axis readability in monthly trend charts.
- Relationship Modeling: Established a clean Star Schema with proper one-to-many relationships between fact tables (Orders, Order Details) and dimension tables.

### Important Analytical Decisions
- Used Order Details[UnitPrice] for all revenue calculations instead of Products[UnitPrice] to reflect historical pricing at the time of each order.
- Retained nulls in ShippedDate (unshipped orders) as they carry business meaning.
- Did not remove any records — all 830 orders were preserved to maintain data integrity.

These preparation steps significantly improved data reliability, visual clarity, and analytical accuracy, preventing common pitfalls such as broken trend lines and incorrect time-based calculations.

---
## Dashboard Design
The final solution is a clean, interactive 3-page Executive Dashboard designed specifically for senior leadership and business stakeholders. The layout prioritizes clarity, usability, and strategic storytelling.
Overall Design Philosophy:
- Executive-Friendly: Minimalist design with clear visual hierarchy, consistent color scheme, and intuitive navigation.
- Interactive Experience: Synchronized slicers across all pages (Year, Country, Category etc) for seamless cross-filtering.
- Storytelling Flow: Each page answers specific business questions while contributing to the bigger picture.

### Page 1
#### Sales & Overview Overview
