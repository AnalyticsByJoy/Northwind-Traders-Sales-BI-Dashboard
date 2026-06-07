# Northwind-Traders-Sales-BI-Dashboard

### Table Of Contents
[Project Introduction](#project-introduction)

[Business Objectives](#business-objectives)

[Dataset Overview](#dataset-overview)

[Data Model (Star schema)](#data-model-star-schema)

[Data Preparation](#data-preparation)

[Tools Used](#tools-used)

[Dashboard Design](#dashboard-design)

[Page 1](#page-1)

[Page 2](#page-2)

[Page 3](#page-3)

[Challenges & Business Limitations](#challenges-&-business-limitations)

[Business Recommendations](#business-recommendations)

## Project Introduction
This project presents a comprehensive Executive Business Intelligence Dashboard for Northwind Traders, a global gourmet food supplier. Built in Power BI, the interactive 3-page dashboard provides leadership with clear visibility into sales performance, product portfolio health, regional dynamics, shipping operations, and salesforce productivity.
The solution analyzes a relational dataset containing 830 orders and approximately 2,155 order detail records spanning from 2013 to mid-2015. Through advanced data modeling, DAX calculations, and thoughtful visualization, the dashboard transforms raw transactional data into actionable strategic insights — highlighting strong revenue growth while uncovering critical risks such as heavy dependence on discontinued products and rising freight costs.
The dashboard directly addresses key business questions around revenue trends, seasonality, category performance, operational efficiency, and discount strategy effectiveness.

---
## Business Objectives:
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

- **Time Period**: Mid-2013 to Mid-2015 (~23 months)
- **Total Orders**: 830
- **Total Order Line Items**: 2,155
- **Unique Customers**: 91
- **Unique Products**: 77 across 8 categories
- **Employees**: 9 sales representatives
- **Shippers**: 3 logistics partners
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
- **Calendar Table Creation**: Built a dynamic Calendar table using DAX (CALENDAR + ADDCOLUMNS) to handle missing months and enable proper time intelligence functions (YoY, seasonality, trends). Marked as a Date Table for full DAX support.
- **Employee Hierarchy**: Handled blank ReportsTo value for the Vice President of Sales (Andrew Fuller) to maintain a clean organizational structure.
- **Readability Enhancements**:
  - Created Short Employee Name column (e.g., “Margaret P”, “Janet L”) for better chart visualization.
  - Created Short Month column (“Jan”, “Feb”, etc.) to improve X-axis readability in monthly trend charts.
- **Relationship Modeling**: Established a clean Star Schema with proper one-to-many relationships between fact tables (Orders, Order Details) and dimension tables.

### Important Analytical Decisions
- Used Order Details[UnitPrice] for all revenue calculations instead of Products[UnitPrice] to reflect historical pricing at the time of each order.
- Retained nulls in ShippedDate (unshipped orders) as they carry business meaning.
- Did not remove any records — all 830 orders were preserved to maintain data integrity.

These preparation steps significantly improved data reliability, visual clarity, and analytical accuracy, preventing common pitfalls such as broken trend lines and incorrect time-based calculations.

---
## Tools Used
| Tool | Purpose |
|------|---------|
|Power BI Desktop|Primary tool for data modeling, DAX calculations, visualization, and dashboard development.|
|Power Query Editor|Used for data loading, type conversion, cleaning, and creating calculated columns (e.g., Short Employee Name, Short Month).|
|DAX (Data Analysis Expressions)|Developed all key measures including Revenue, YoY%, Discount Rate, Freight Efficiency, Average Days to Ship, and conditional formatting logic.|
|GitHub|For project documentation, version control, and showcasing the complete analytics project.|

#### Additional Techincal Stack
| Tool | Purpose |
|------|---------|
|Star Schema Design|Implemented best practices for optimal performance and maintainability.|
|Dynamic Calendar Table|Built using DAX for robust time intelligence.|
|Conditional Formatting & Advanced Visuals|Applied for executive-friendly insights (Green/Red indicators).|

---
## Dashboard Design
The final solution is a clean, interactive 3-page Executive Dashboard designed specifically for senior leadership and business stakeholders. The layout prioritizes clarity, usability, and strategic storytelling.
Overall Design Philosophy:
- **Executive-Friendly**: Minimalist design with clear visual hierarchy, consistent color scheme, and intuitive navigation.
- **Interactive Experience**: Synchronized slicers across all pages (Year, Country, Category etc) for seamless cross-filtering.
- **Storytelling Flow**: Each page answers specific business questions while contributing to the bigger picture.

### Page 1
#### Sales & Overview Overview
<img width="1182" height="684" alt="Northwind traders page 1" src="https://github.com/user-attachments/assets/7586e822-818c-40f9-b233-462a145f2360" />

##### Key KPIs Displayed

| KPI | Overall | 2013 | 2014 | 2015 | YoY% Trend |Insight |
|-----|---------|------|------|------|------------|--------|
|Total Revenue|$1.27M|$208K|$617K|$441K|+179.31%|Strong growth, peaked in 2014|
|Total Orders|830|152|408|270|+170.36%|Significant volume increase|
|Average Order Value|$1,530|$1,370|$1,510|$1,630|+3.31%|Steady improvement in order quality|
|Discount Rate|6.55%|8.05%|6.27%|6.20%|-4.93%|Positive trend (improving)|
|Total Customers|91|91|91|91|0.00%|Stagnant customer base|

##### Key Observations from KPIs
- **Revenue & Orders** 2013 had a slow growth but between 2014 and 2015 showed explosive growth, indicating successful market expansion.
- **Average Order Value** improved consistently, suggesting the company is selling more effectively per transaction.
- **Discount Rate** declined over the period — a positive sign of better pricing control and improved profitability.
- **Customer Base** remained flat at 91 unique customers throughout the three years. This highlights a potential risk of over-reliance on a limited number of clients.
- 
##### This page directly addresses the core question:
“What are the trends in revenue and order volume over time? Are there identifiable seasonal patterns?”
Main Insights Delivered:
- Revenue showed modest growth in 2013 with November and December as the strongest months. 2014 had significant growth led by December, October, and January, followed by an Explosive early-year performance in 2015 with April recording the highest monthly revenue of the entire period, followed by March and February. However, May 2015 was the weakest month across all three years.

Clear seasonality patterns were identified:
- October, November, and December consistently perform well, particularly in 2013 and 2014.
- December is the highest-performing month in 2014, suggesting strong holiday or year-end purchasing activity.
- Revenue tends to be weaker during some mid-year months, such as June.
- The strong growth observed in the first three months of 2015 suggests the business entered 2015 with significant momentum following the strong performance in late 2014.
- However, because the dataset contains only partial data for 2013 and 2015, the observed pattern should be treated as an indication rather than definitive proof of seasonality. Additional years of historical data would be required to build reliable seasonal forecasts.

### Page 2
#### Product & Category Intelligence
<img width="1188" height="681" alt="Northwind traders page 2" src="https://github.com/user-attachments/assets/5a1e13a4-d0a2-4cf6-83ff-519742c3319b" />

##### Key KPIs Displayed

| KPI | Overall | 2013 | 2014 | 2015 | YoY% Trend |Insight |
|-----|---------|------|------|------|------------|--------|
|Total Products|Sold|77|74|77|76|Stable|Near maximum product utilization|
|Total Discount Amount|$88.7K|$18.2K|$41.3K|$29.1K|+118.5% overall|Increased significantly with growth|
|Active Revenue|$185K|$32K|$91K|$62K|+181.25% overall|Growing but still very low|
|Discontinued Revenue|$1.08M|$176K|$526K|$379K|+179.5% overall|Dominates total revenue|

##### Key Observations from KPIs
- The number of **Products Sold** remained relatively stable (74–77).
- **Total Discount Amount** increased in line with revenue growth, peaking in 2014, but the overall Discount Rate showed a slight increase.
- **Active Revenue** remains critically low at only $185K (15% of total).
- **Discontinued Products** generated $1.08 Million, accounting for approximately 85% of total revenue across the three years.

##### This page directly addresses the core questions:
"**Product Intelligence**: Which product categories are the top revenue drivers,and how does the discontinued status of products impact potential sales?, **Impact Of Strategy**: How do discounts affect the overall profit margin across different product lines?" and **bonus questions** "What is the risk level of the current product portfolio?, Which  products contribute the most to revenue?"

1. **Product Intelligence**
Which product categories are the top revenue drivers, and how does the discontinued status of products impact potential sales?

- **Top Revenue Drivers**: Beverages and Dairy Products consistently ranked as the strongest categories across all three years.
- **Star Product**: Côte de Blaye was the highest revenue-generating product every single year.
- **Critical Finding**: Discontinued products generated $1.08 Million (approximately 85% of total revenue), while active products contributed only $185K. This reveals an extremely high dependency on products that are no longer in active production.
  
2. **Impact of Strategy**
How do discounts affect the overall profit margin across different product lines?

- The overall Discount Rate averaged 6.55%, trending downward (positive sign).
- Discounts were strategically applied more heavily in high-revenue categories such as Beverages, Meat & Poultry, and Dairy Products.
- While discounts appear to support volume in competitive categories, the high reliance on discontinued products raises questions about long-term margin sustainability.

#### Bonus Questions Answered
3. **What is the risk level of the current product portfolio?**
- High Risk. The business is heavily dependent on discontinued inventory. If stock of key discontinued products (especially Côte de Blaye) runs out, revenue could drop significantly.

4. **Which customers and products contribute the most to revenue?**
- QUICK-Stop, Ernst Handel, Save-a-lot were the overall dominating.
- Côte de Blaye dominated revenue every year.
- Other consistent top performers included Thüringer Rostbratwurst, Raclette Courdavault, and Camembert Pierrot.
- A small number of products (Top 10) drive the majority of total revenue.


#### Additional Insights
- Some categories showed an interesting pattern: high order quantity but relatively low revenue (and vice versa), suggesting differences in average unit price and product mix strategy.
- Grains & Cereals and Produce stood out for achieving both high quantity and strong revenue contribution.

This page shifts the conversation from “how much we sold” to “what we sold” and “how sustainable is our product strategy?”

### Page 3
#### Regional, Operational & People Performance
<img width="1187" height="684" alt="Northwind traders page 3" src="https://github.com/user-attachments/assets/b06627da-1176-4caf-9f28-4e5d3505ede9" />

##### Key KPIs Displayed

| KPI | Overall | 2013 | 2014 | 2015 | YoY% Trend |Insight |
|-----|---------|------|------|------|------------|--------|
|Total Freight|$64.9K|$10.3K|$32.5K|$22.2K|+189.80%|Growing faster than revenue|
|Average Freight per Order|$78.24|$67.63|$79.58|$82.20|+7.19%|Rising cost per order|
|Freight % of Revenue|5.13%|4.94%|5.26%|5.04%|+3.76%|Declining efficiency|
|Average Days to Ship|8.5 days|8.1 days|8.9 days|8.0 days|-1.70%|Slight improvement|

##### Key Observations from KPIs
- Revenue continued its strong upward trajectory, but **Total Freight** grew even faster (+189.80% YoY), signaling increasing pressure on margins.
- *8Freight % of Revenue** rose from 4.94% in 2013 to 5.26% in 2014 before slightly improving in 2015. This indicates that shipping costs are becoming less efficient relative to revenue growth.
- **Average Days to Ship** remained relatively stable (around 8–9 days), with a modest improvement in 2015 (-12.19% YoY), showing operational consistency in delivery performance.
- The gap between revenue growth and freight cost growth is one of the most important red flags highlighted on this page.

##### This page directly addresses the core questions:
"**Regional Insights**: Which countries/cities represent the highest market share, and where are shipping (freight) costs disproportionately high?, **Operational Efficiency**How do different shippers compare in terms of cost and speed?,Which employees are leading in total sales generated? and **bonus questions** How efficient is the shipping operation relative to revenue growth?,How is the sales team performing individually and collectively?"

1. **Regional Insights**
Which countries/cities represent the highest market share, and where are shipping (freight) costs disproportionately high?

- **Top Performing Markets**: The USA and Germany were the strongest countries throughout the period.
- **Key Cities**: Cunewalde (Germany), Graz (Austria), and Boise (USA) consistently ranked among the top revenue-generating cities.
- **Freight Cost Hotspots**: Countries such as Norway, Poland, Argentina, Portugal, and Ireland showed disproportionately high freight costs as a percentage of revenue.

2. **Operational Efficiency**
How do different shippers compare in terms of cost and speed?

- **United Package**: Handled the highest volume but had higher average freight costs and slower delivery times in some years.
- **Speedy Express**: Generally the most cost-efficient shipper with lower average freight per order.
- **Federal Shipping**: Offered a balanced performance with competitive speeds (especially in 2015).

3. **Salesforce Productivity**
Which employees are leading in total sales generated?

- **Top Performers**:Margaret Peacock and Janet Leverling were the standout sales representatives across the three years.
Nancy Davolio also delivered consistently strong results.
- The sales team showed clear performance tiers, with a few individuals driving a significant portion of total revenue.

#### Bonus Questions Answered
4. **How efficient is the shipping operation relative to revenue growth?
Concerning Trend. While revenue grew by 179%, total freight costs grew faster at 189.8%. Freight as a percentage of revenue increased from 4.94% in 2013 to 5.13% overall, indicating declining shipping efficiency and rising pressure on profitability.

5. **How is the sales team performing individually and collectively?**
The sales team delivered strong collective growth, but performance was highly concentrated. Top performers (Margaret Peacock, Janet Leverling) significantly outperformed others, highlighting both the strength of key individuals and the risk of over-reliance on a few star salespeople.
---

## Challenges & Business Limitations
While the dashboard provides strong insights, several important limitations and challenges were encountered:

- **Limited Time Span**: The dataset only covers approximately 23 months (July 2013 – May 2015), making long-term trend analysis difficult and YoY comparisons less robust.
- **Stagnant Customer Base**: Only 91 unique customers across three years with no meaningful growth. This indicates heavy reliance on a small number of clients.
- **Product Portfolio Risk*8: 85% of revenue comes from discontinued products. This represents a significant supply chain and revenue sustainability risk.
- **Data Gaps**: Some months have incomplete data, and there is no Cost of Goods Sold (COGS) information, limiting true profitability analysis.
- **Freight Cost Pressure**: Shipping costs grew faster than revenue, but without carrier contract details or distance data, root causes are difficult to pinpoint.
- **Customer & Product Concentration**: A few customers (QUICK-Stop, Ernst Handel, Save-a-lot Markets) and products (especially Côte de Blaye) dominate revenue.

These limitations highlight that while top-line growth looks impressive, the underlying business model has structural vulnerabilities.

---
## Business Recommendations
Based on the analysis, here are prioritized recommendations for Northwind Traders leadership:
### High Priority
1. **Product Portfolio Transformation**
Develop a clear roadmap to reduce dependency on discontinued products. Focus on scaling active products in high-performing categories (Beverages and Dairy).
2. **Freight Cost Optimization**
Conduct a detailed review of shipping partners. Shift more volume to cost-efficient shippers (e.g., Speedy Express) and negotiate better rates with high-volume partners.
3. **Customer Acquisition Strategy**
Reduce concentration risk by targeting new customers, especially in high-potential markets like Germany and the USA.

### Medium Priority
4. **Seasonal Planning**
Leverage the strong April and Q4 peaks. Prepare targeted promotions and inventory for these periods, while running campaigns to lift performance in the weak May–September window.
5. **Sales Team Development**
Study and replicate best practices from top performers (Margaret Peacock and Janet Leverling) across the rest of the team.
6. **Discount Strategy Review**
Continue monitoring discount rates in high-volume categories to ensure they drive profitable volume rather than just revenue.

## Author
Ndu Joy Ifesinachi - Data Analyst

LinkedIn www.linkedin.com/in/joy-ndu-1b1783333
