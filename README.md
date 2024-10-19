Coding Skills Assessment

This project is a solution to a coding skills assessment involving three parts:

System Design: Designing an e-commerce system that handles users, products, orders, and payments.
Business Logic Implementation: Developing functions for inventory management that handle order processing and restocking in a warehouse.
Database Query Writing: Writing SQL queries to handle typical scenarios in an online bookstore.



## 1. System design
The system design involves creating Python classes for the core components: User, Product, Order, and Payment. This part of the project doesn't require any setup or installation.

To run the code:

Copy the class definitions into a Python file (e.g., ecommerce.py).
To test, instantiate the classes and simulate orders or payments:
python
Copy code
from ecommerce import User, Product, Order, Payment

user = User(1, "John Doe", "john@example.com")
product1 = Product(1, "Laptop", 999.99)
order = Order(1, user)
order.add_product(product1)
payment = Payment(1, 999.99)
order.set_payment(payment)
## 2. Business Logic Implementation (Inventory Management System)
This part of the project implements two functions: process_orders() and restock_items() in a Warehouse class. These functions manage stock levels based on sales orders and trigger restocks when necessary.

To run the code:

Copy the code for the Warehouse class into a Python file (e.g., inventory.py).
Test the functionality by adding products, processing orders, and restocking items:
python
Copy code
from inventory import Warehouse, Product

warehouse = Warehouse()
laptop = Product(1, "Laptop", 999.99)
warehouse.add_product(laptop, 15)

# Simulate incoming orders
warehouse.process_orders([{laptop: 6}])  # Should reduce stock and alert if low
warehouse.restock_items({laptop: 10})    # Restock items as needed
## 3. Database Query Writing (SQL for Bookstore)
This part involves writing SQL queries to retrieve customer and book sales data.

To run the queries:

Set up a relational database with the following schema:
Customers(customer_id, name, email)
Books(book_id, title, author, price)
Orders(order_id, customer_id, order_date)
OrderDetails(order_id, book_id, quantity)
Run the SQL queries in your preferred SQL editor or database management system.
Example Queries:

Top 5 customers who purchased the most books:
sql
Copy code
SELECT c.customer_id, c.name, SUM(od.quantity) AS total_books
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
JOIN OrderDetails od ON o.order_id = od.order_id
WHERE o.order_date >= DATEADD(YEAR, -1, GETDATE())
GROUP BY c.customer_id, c.name
ORDER BY total_books DESC
LIMIT 5;
## 4. Assumptions
E-Commerce System Design:

The system design assumes that one order can contain multiple products and one payment per order.
It doesn't include specific details for shipping or detailed order tracking but can be extended for real-world use.
Inventory Management:

The threshold for low stock is assumed to be 10 units for all products.
The system does not account for partial shipments or backorders, but it can be extended.
Database Queries:

The queries assume the existence of a relational database with valid and normalized data.
The time period for retrieving top customers is set to the last year using DATEADD() for SQL Server, which can be modified based on the database system.
## 5. Prerequisites
Programming Languages: Python 3.x
Database: Any relational database system (MySQL, PostgreSQL, SQL Server)
Tools:
Python installed on your system.
SQL database management software for testing the SQL queries.
## 6. Code Overview
ecommerce.py: Contains the classes for the e-commerce system design.
inventory.py: Implements the Warehouse class with process_orders() and restock_items() functions.
queries.sql: A separate file for all SQL queries related to the bookstore.
