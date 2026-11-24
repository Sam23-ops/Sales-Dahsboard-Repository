Sales Dashboard

A simple sales dashboard built on top of customer and order data, using MySQL for storage and Power BI for visualization.

What's in here
schema.sql – creates the customers and orders tables
views.sql – creates the joined view used by the dashboard
dashboard.pbix – the Power BI file
Setup
Run schema.sql in MySQL Workbench. It creates the sales_dashboard database and two tables, customers and orders, linked by Customer_ID (foreign key on orders).
Load the data: saved customers.xlsx and orders.xlsx as CSV, then used Workbench's Table Data Import Wizard to load them into the matching tables (customers first, then orders, since orders depends on customers existing).
Run views.sql to create v_orders_joined — combines every order with its customer's city, segment, etc. via Customer_ID.
Open dashboard.pbix in Power BI Desktop. If it asks to connect, point it at the sales_dashboard MySQL database and hit refresh.
What's on the dashboard
Cards: total net revenue, total orders, unique customers, average order value
Line chart: monthly revenue trend
Bar chart: revenue by product category
Bar chart: revenue by customer segment/city
Bar chart: order count by status
Filters: date range, and category (or segment/city/status)
Assumptions
Revenue is always Net_Amount_INR, nothing else.
Average order value = total net revenue ÷ non-cancelled orders.
Cancelled orders already came in with ₹0 net amount, so no extra cleanup was needed there.
Returned orders are kept in the dataset, not removed, and can be told apart using Order_Status.