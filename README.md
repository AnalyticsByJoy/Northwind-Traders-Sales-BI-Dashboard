# Northwind-Traders-Sales-BI-Dashboard
## 🚀 Project Introduction
This project presents a comprehensive Executive Business Intelligence Dashboard for Northwind Traders, a global gourmet food supplier. Built in Power BI, the interactive 3-page dashboard provides leadership with clear visibility into sales performance, product portfolio health, regional dynamics, shipping operations, and salesforce productivity.
The solution analyzes a relational dataset containing 830 orders and approximately 2,155 order detail records spanning from 2013 to mid-2015. Through advanced data modeling, DAX calculations, and thoughtful visualization, the dashboard transforms raw transactional data into actionable strategic insights — highlighting strong revenue growth while uncovering critical risks such as heavy dependence on discontinued products and rising freight costs.
The dashboard directly addresses key business questions around revenue trends, seasonality, category performance, operational efficiency, and discount strategy effectiveness.

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

## Dataset Overview
|Table|Field|Description|
orders	orderID	Unique identifier for each order
orders	customerID	The customer who placed the order
orders	employeeID	The employee who processed the order
orders	orderDate	The date when the order was placed
orders	requiredDate	The date when the customer requested the order to be delivered
orders	shippedDate	The date when the order was shipped
orders	shipperID	The ID of the shipping company used for the order
orders	freight	The shipping cost for the order (USD)
order_details	orderID	The ID of the order this detail belongs to
order_details	productID	The ID of the product being ordered
order_details	unitPrice	The price per unit of the product at the time the order was placed (USD - discount not included)
order_details	quantity	The number of units being ordered
order_details	discount	The discount percentage applied to the price per unit
customers	customerID	Unique identifier for each customer
customers	companyName	The name of the customer's company
customers	contactName	The name of the primary contact for the customer
customers	contactTitle	The job title of the primary contact for the customer
customers	city	The city where the customer is located
customers	country	The country where the customer is located
products	productID	Unique identifier for each product
products	productName	The name of the product
products	quantityPerUnit	The quantity of the product per package
products	unitPrice	The current price per unit of the product (USD)
products	discontinued	Indicates with a 1 if the product has been discontinued
products	categoryID	The ID of the category the product belongs to
categories	categoryID	Unique identifier for each product category
categories	categoryName	The name of the category
categories	description	A description of the category and its products
employees	employeeID	Unique identifier for each employee
employees	employeeName	Full name of the employee
employees	title	The employee's job title
employees	city	The city where the employee works
employees	country	The country where the employee works
employees	reportsTo	The ID of the employee's manager
shippers	shipperID	Unique identifier for each shipper
shippers	companyName	The name of the company that provides shipping services
<img width="1144" height="32766" alt="image" src="https://github.com/user-attachments/assets/6714cbf3-277f-41ed-8e16-53385bd25ec4" />

