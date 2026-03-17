 <h1>🍕 Pizzahut_SQL</h1>

    <p>
        This project is a hands-on SQL practice system designed to simulate a real-world 
        E-Commerce database. It helps developers strengthen their SQL skills by working 
        with structured data, relationships, and practical business queries.
    </p>

    <hr>

    <h2>📌 Database Setup</h2>

    <h3>1. Create Database</h3>
    <pre><code>
CREATE DATABASE pizzahut;
USE pizzahut;
    </code></pre>

    <h3>2. Import Existing Tables</h3>
    <pre><code>
SELECT * FROM pizzahut.pizzas;
SELECT * FROM pizzas;
SELECT * FROM pizzahut.pizza_types;
    </code></pre>

    <h3>3. Create Orders Table</h3>
    <pre><code>
CREATE TABLE orders(
    order_id INT NOT NULL,
    order_date DATE NOT NULL,
    order_time TIME NOT NULL,
    PRIMARY KEY(order_id)
);

SELECT * FROM orders;
    </code></pre>

    <h3>Create Order Details Table</h3>
    <pre><code>
CREATE TABLE order_details(
    order_details_id INT NOT NULL,
    order_id INT NOT NULL,
    pizza_id TEXT NOT NULL,
    quantity INT NOT NULL,
    PRIMARY KEY(order_details_id)
);

SELECT * FROM order_details;
    </code></pre>

    <hr>

    <h2>🧪 Assignments & Queries</h2>

    <h3>1. Retrieve Total Number of Orders</h3>
    <pre><code>
SELECT COUNT(order_id) AS total_order FROM orders;
-- Answer: 21350
    </code></pre>

    <h3>2. Calculate Total Revenue</h3>
    <pre><code>
SELECT
ROUND(SUM(order_details.quantity * pizzas.price), 2) AS total_sales
FROM order_details
JOIN pizzas ON pizzas.pizza_id = order_details.pizza_id;
    </code></pre>

    <h3>3. Maximum Price of Pizza</h3>
    <pre><code>
SELECT MAX(price) AS max_price_of_pizza FROM pizzas;

-- OR

SELECT
pizza_types.name, pizzas.price
FROM pizza_types
JOIN pizzas ON pizza_types.pizza_type_id = pizzas.pizza_type_id
ORDER BY pizzas.price DESC
LIMIT 1;
    </code></pre>

    <hr>

    <h2>🚀 Conclusion</h2>
    <p>
        This project provides a practical environment to learn and master SQL concepts 
        including joins, aggregations, and real-world data analysis.
    </p>
