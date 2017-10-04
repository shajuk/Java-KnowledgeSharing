#1 Problem Statement: 
 Write a query which returns the number of orders placed by the customers whose name starts with ‘'H’ and display the customer name as well.  
 
Design Rules :  1. Display the customers who have placed at least one order.
2. Return the number of orders with a column name as 'NUMBER_OF_ORDERS'.
3. Do Not Change the name of the column. Please use as per the design rules
4. Order of the output columns: NUMBER_OF_ORDERS, CUST_NAME
5. Sort the output based on the ascending order of cust_name

T_ORDER_PLACEMENT

ORDER_ID CUST_ID 

T_CUSTOMER
CUST_ID CUST_NAME  

Ans 1) select count(o.CUST_ID) as NUMBER_OF_ORDERS, c.CUST_NAME from T_ORDER_PLACEMENT o join T_CUSTOMER c 
on o.CUST_ID=c.CUST_ID and c.CUST_NAME like 'H%' group by c.CUST_NAME order by c.CUST_NAME

#2 Problem Statement: 
 An order line can refer any stock which is represented in t_order_details table. 
 Each stock will have its own defined price which is represented in t_stock_details table. 
 Write a query to calculate the total average discount percentage for all the orders, 
 whose stock price is greater than 200. 

Design Rules:  1. Return the average discount with the column name as 'AVERAGE_DISCOUNT'
2. There should not be any other additional columns in the output.
3. Do Not Change the name of the column.
4. Round the discount to nearest 2 decimals.

select round((sum(DISCOUNT_PERCENTAGE)/count(*)),2) as AVERAGE_DISCOUNT from t_order_details o join t_stock_details s 
on o.STOCK_ID=s.STOCK_ID and s.price > 200;


#3 Problem Statement: 
 Write a query to return the Customer_id, Name, Order_Id for the Customers who have placed  
 more than two items in one order. 

Design Rules: (Do Not Change the name of the column.Please use as per the below design rule) 
 1. The cust_id should be displayed with the column name as CUSTOMER_ID 
 2. Cust_name should be displayed with the column name as NAME 
 3. Order of the output column CUSTOMER_ID,NAME,ORDER_ID 
 4. Sort the output in ascending order based on the customer_id and order_id 




https://stackoverflow.com/questions/46556454/sql-codes-i-tried
