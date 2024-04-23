# FIFO_Analysis
This project focuses on FIFO Analysis (First In First Out), Inventory Management, Inventory Analysis, and Inventory Age

I. Database Schema & Test Data
- Table 1: Movement table. This is the most important table. It contains the stock movement history of all warehouses, data including the item SKU, quantity changed, closing inventory balance and date.
- Table 2: Document table. There are 2 types of document, purchase and sales_order. Some document might connected to a customer, but it is optional.
- Table 3: Customer table. It contains customer ID, and Email address.

II. Steps:  
  1. Data Wrangling:
    - Load and read data from path
    - Data preprocessing: Rename, Change data type, fill null cells,...

  2. Answering business questions:
     - Question 1: Customer Leaderboard: Rank customers by quantity they purchased. Include the customer's Email Address (shown as "guest" of not provided) and quantity they purchased in the report
       - Left Join table documents and customers to get full detail information.
       - Fill NA with "guest"
       - Group by "Contact", count "type", and order by 'type' DESC
         
     - Question 2: Write a query to return HK Warehouse's stock of any given time.
       - date: Let user enter date to generate the stock report
       - Filter HK warehouse and 'created_date' <= date
       - Groupby ['warehouse','sku'], sum 'quality' to get the stock report

     - Question 3: Age of Inventory. Show the age of the available stocks of a given time, and group the quantity by age "0-30 days", "31-60 days", "61-90 days", and "90+ days"
     ( Apply the First In First Out rule, meaning oldest stock will be deducted first).
       - date: Let user enter date to generate the stock report
       - Filter HK warehouse and 'created_date' <= date
       - Calculate 'age_of_inventory' = date - 'created_date'
       - Calculate 'age_group'
       - Pivot table: index = 'sku', columns = 'age_group', values = 'quantity', aggfunc = 'sum'
       - Calculate using FIFO method
     

III. Tools:
- Python: Pandas
