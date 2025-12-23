Усі операції виконуються коректно, дані зберігаються та об’єднуються без помилок



усі команди для перевірки роботоздібності:


- SELECT * FROM product;
- SELECT title FROM product WHERE category = 'Electronics';
- SELECT title FROM product WHERE price BETWEEN 500 AND 1200;             -Where                 
- SELECT title FROM product WHERE stock < 10;
------------------------------------------------------------------
-SELECT MAX(price) FROM product;
-SELECT MIN(price) FROM product;                                        -max/min/count
-SELECT COUNT(*) FROM product;
------------------------------------------------------------------
SELECT title, price
FROM product                                                           -subquery
WHERE price > (SELECT AVG(price) FROM product);
------------------------------------------------------------------
- SELECT * FROM cart_item;
- DELETE FROM cart_item WHERE cart_id = 1;                            -DELETE
- SELECT * FROM cart_item;
------------------------------------------------------------------
- SELECT
  c.first_name || ' ' || c.last_name AS customer,
  p.title,
  ci.qty
FROM cart_item ci                                                     -INNER
INNER JOIN cart ca ON ca.cart_id = ci.cart_id
INNER JOIN customer c ON c.customer_id = ca.customer_id
INNER JOIN product p ON p.product_id = ci.product_id;
------------------------------------------------------------------
- SELECT
  c.first_name || ' ' || c.last_name AS customer,
  ca.cart_id                                                          -outer join
FROM customer c
LEFT JOIN cart ca ON ca.customer_id = c.customer_id;
------------------------------------------------------------------
- SELECT username AS name, 'admin' AS role FROM admin_user
UNION                                                                                   -UNION
SELECT first_name || ' ' || last_name AS name, 'customer' AS role FROM customer;
