<h1 align="center">🍕 Pizzahut_SQL</h1>

<p align="center">
This project is a hands-on SQL practice system designed to simulate a real-world 
E-Commerce database. It helps developers strengthen their SQL skills by working 
with structured data, relationships, and practical business queries.
</p>

---

## 📌 Database Setup

### 1. Create Database
```sql
CREATE DATABASE pizzahut;
USE pizzahut;
```

### 2. Import Existing Tables
```sql
SELECT * FROM pizzahut.pizzas;
SELECT * FROM pizzas;
SELECT * FROM pizzahut.pizza_types;
```

### 3. Create Orders Table
```sql
CREATE TABLE orders(
    order_id INT NOT NULL,
    order_date DATE NOT NULL,
    order_time TIME NOT NULL,
    PRIMARY KEY(order_id)
);

SELECT * FROM orders;
```

### 4. Create Order Details Table
```sql
CREATE TABLE order_details(
    order_details_id INT NOT NULL,
    order_id INT NOT NULL,
    pizza_id TEXT NOT NULL,
    quantity INT NOT NULL,
    PRIMARY KEY(order_details_id)
);

SELECT * FROM order_details;
```

---

## 🧪 Assignments & Queries

### 1. Retrieve Total Number of Orders
```sql
SELECT COUNT(order_id) AS total_order FROM orders;
-- Answer: 21350
```

### 2. Calculate Total Revenue
```sql
SELECT
ROUND(SUM(order_details.quantity * pizzas.price), 2) AS total_sales
FROM order_details
JOIN pizzas ON pizzas.pizza_id = order_details.pizza_id;
```

### 3. Maximum Price of Pizza
```sql
SELECT MAX(price) AS max_price_of_pizza FROM pizzas;

-- OR

SELECT
pizza_types.name, pizzas.price
FROM pizza_types
JOIN pizzas ON pizza_types.pizza_type_id = pizzas.pizza_type_id
ORDER BY pizzas.price DESC
LIMIT 1;
```

### 4. Create a table that show most commonly quantity ordered
```sql
select
quantity, count(order_details_id)
from order_details group by (quantity);
```

### 5. Most common pizza size ordered
```sql
select 
pizzas.size, count(order_details.order_details_id)
from pizzas join order_details
on pizzas.pizza_id = order_details.pizza_id
group by pizzas.size;
```

### 6. List the top 5 most pizzas type ordered along ordered quantity
```sql
select 
pizzas.pizza_id, count(order_details.quantity) as total_orders_quantity
from pizzas join order_details
on pizzas.pizza_id = order_details.pizza_id
group by pizzas.pizza_id
order by total_orders_quantity desc limit 5;
```

### 7. Join the table to find total quantity of each pizza category ordered.
```sql
select
pizza_types.category, sum(order_details.quantity) as quantity
from pizza_types join pizzas
on pizza_types.pizza_type_id = pizzas.pizza_type_id
join order_details on order_details.pizza_id = pizzas.pizza_id
group by pizza_types.category order by quantity desc;
```

### 8. Determine the distribution of order by hour of the day
```sql
select hour(order_time) as hours, count(order_id) as order_count
from orders
group by(hours)
order by(hours);
```

### 9. Give the relevant table to find the category-wise distribution of pizzas
```sql
select hour(order_time) as hours, count(order_id) as order_count
from orders
group by(hours)
order by(hours);
```

---

## 🚀 Conclusion
This project provides a practical environment to learn and master SQL concepts including:
- Joins  
- Aggregations  
- Real-world data analysis  

---

## ⭐ Author
**Apurava Anand**
