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

#4 Problem Statement: 
 Write a query to return both ordered and unordered Stock details. If a stock is ordered, then the order status must be displayed as ‘ORDERED’. If a stock is unordered, then the status must be displayed as  ‘UNORDERED’. 

Design Rules: 
 1.  Sort the output in ascending order based on the stock id, order_status 
 2. Order of the output column should be as STOCK_ID, STOCK_NAME, ORDER_STATUS, PRICE 
 3. Do Not Change the name of the column. Please code as per the below design rules 

#5 Problem Statement: 
 Write a query to update the shipment status based on the below logic. For orders with: • No zip code or NULL zip code, shipment status should be set to 0
• Valid zip code, shipment status should be set to 1
• Invalid zip code, shipment status should be set to 2
Design Rules: 
 Valid zip code refers to a zip code with 5 digits 

#6 Problem Statement:  

 The company exposes, the customer and order data to a third party system which takes care of packing and shipping the orders. Hence, create a view to display the information about customers and Orders. 

Design Rules : 1. The view name should be as ORDER_INFO
2. Retrieve the customer details who have placed at least one order.
3. Sort the output based on the ascending of the cust_id,order_id,order_date,shipment_date.
4. The columns in the view should be displayed in the below order
5. CUST_ID, CUST_NAME, CUST_ADDRESS, CUST_CITY, CUST_STATE, CUST_ZIP_CODE, CUST_MAIL, ORDER_ID, ORDER_DATE, SHIPMENT_DATE
6. Do Not Change the name of the columns. Please code as per the design rules

#7 Problem Statement: 
 Create a procedure which takes customer id as input and returns the details of the customer. 

 The customer details should be returned as a SYS_REFCURSOR. The details must include the following: 
customer_id, customer_name, order_id, stock_name, quantity, total_cost    

 Use the skeleton file, to develop the stored procedure. 

Procedure name:    get_customer_details 
Input parameter :    Customer_id 
Output parameter:  customer details with data type as SYS_REFCURSOR 

 Design rules: 

 1.    Procedure NAME or IN OUT parameters / types/names MUST NOT be changed 
 2.   The REF CURSOR record MUST contain the output in the following ORDER only: 
 customer_id, customer_name, order_id, stock_name, quantity, total_cost    
 3.   Please DO NOT FETCH the SYS_REFCURSOR inside the Stored Procedure 
 4.   Please ensure that you have ONLY the PROC while doing the last save. Other queries you use for executing the Stored Procedure MUST NOT be available while doing the last save. 


#8 Problem Statment: 

 Please go through the below package spec: 

 CREATE OR REPLACE PACKAGE order_reconcile AS 
 PROCEDURE update_stock_balance(input_order_date IN DATE, input_stock_id IN NUMBER); 
 FUNCTION cancel_order(input_order_id t_order_placement.order_id%type) RETURN NUMBER; 
 END order_reconcile; 
 / 

This package SPEC is already created in the backend database, and is available for you to work on. 

Create the below PL/SQL sub programs in the package body: 

(a) Procedure:   
 A stored procedure must be created that will accept the order date and the stock id as input. Based on this input, the proc must calculate the balance quantity in hand, on a given order date and update the balance quantity in the T_stock_details table. 

Use the skeleton file, to develop the stored procedure. Both the procedure and function should be defined under the same package body. You can independently code function and procedure and try executing your code. While finish, make sure that you attempted both the procedure and function in the package. 

Procedure name : update_stock_balance , 
 Input parameter : input_order_date(date), input_stock_id(Number) 
Output Parameter: None 

Design rules: 
 1. The structure of the procedure / IN or OUT parameters must not be altered 


Logic for the procedure : Calculate the sum of quantity based on the given inputs. Then update STOCK_BALANCE_QTY as per the below formula: 

 STOCK_BALANCE_QTY = STOCK_BALANCE_QTY - (sum of quantity) 

(b) Function:  
 Modify the given function to handle "No data found" error scenario. The expected behavior of the function is to remove the order details from the tables, t_order_placement and t_order_details table, for a given order_id. 

Current design: 
 The given function will work fine when the input order_id is available in the back-end tables. The unction throws unhandled exception when order_id is not found in the tables.  This is something to fixed upon. 

Proposed requirement: 
 Modify the function provided in the skeleton, to add customized exception with error message "ERROR" that should be thrown when order_id is not found. 

Design rules: 
 1. The business logic or the structure of the function / return types / return values / error messages must not be altered 
 2. Both the procedure and function should be defined under the same package body. 

Function name : cancel_order,  
Input Parameter : input_order_id(t_order_placement.order_id%type) , 
Output Parameter : A VARIABLE WITH NUMBER TYPE 
Exception scenario: When order_id is not found to cancel / delete in database 
Error message :  -20000, 'ERROR' 

Note: DO NOT CHANGE the given error code or error message description in your solution. 


https://stackoverflow.com/questions/46556454/sql-codes-i-tried
