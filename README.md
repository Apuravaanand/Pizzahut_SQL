# Pizzahut_SQL
This project is a hands-on SQL practice system designed to simulate a real-world E-Commerce database. It helps developers strengthen their SQL skills by working with structured data, relationships, and practical business queries.

-- 1. create databse 
CREATE DATABASE pizzahut;
USE pizzahut;

-- 2. importing  pizza_type and pizzas table
SELECT * FROM pizzahut.pizzas;
SELECT * FROM pizzas;
SELECT * FROM pizzahut.pizza_types;

-- 3. Creating order table and import existing data 
CREATE TABLE orders(
order_id INT NOT NULL,
order_date DATE NOT NULL,
order_time TIME NOT NULL,
PRIMARY KEY(order_id)
);
SELECT * FROM orders;

CREATE TABLE order_details(
order_details_id INT NOT NULL,
order_id INT NOT NULL,
pizza_id TEXT NOT NULL,
quantity INT NOT NULL,
PRIMARY KEY(order_details_id)
);
SELECT * FROM order_details;

-- Assignments
-- 1. Retrive the total no. of order placed from table order.
select count(order_id) as total_order from orders;
-- ans. 21350

-- 2. Calculate the total revenue generated from pizza sales.
select
round(sum(order_details.quantity * pizzas.price ),2) as total_sales
from order_details join pizzas
on pizzas.pizza_id = order_details.pizza_id; 

-- 3. Max price of all pizzas 
select max(price) as max_price_of_pizza from pizzas;
-- or
select
pizza_types.name , pizzas.price
from pizza_types join pizzas
on pizza_types.pizza_type_id = pizzas.pizza_type_id
order by pizzas.price desc limit 1; 
