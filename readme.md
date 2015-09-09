1.) How many users are there? 50 SELECT COUNT(*) FROM users;

2.) What are the 5 most expensive items? Small Cotton Gloves, Small Wooden Computer, Awesome Granite Pants, Sleek Wooden Hat, Ergonomic Steel Car SELECT title, price FROM items ORDER BY price DESC LIMIT(5);

3.) What's the cheapest book? $1,496 (Does that change for "category is exactly "book" versus "category contains 'book'"?)

sqlite> SELECT title, category, price FROM items WHERE category = 'Books';

4.) Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?

SELECT user_id, street, city, state, zip FROM addresses WHERE street = '6439 Zetta Hills' AND  city = 'Willmouth' AND state = 'WY';

-check headers PRAGMA table_info(table_name);
-id = 40
- SELECT id, first_name, last_name FROM users WHERE id = 40;
- Corrine Little

5.) Correct Virginie Mitchell's address to "New York, NY, 10108"

-locate Virginie Mitchell's id
- userid = 39
- SELECT user_id, street, city, state, zip FROM addresses WHERE user_id = 39;
- UPDATE addresses SET city = "New York", zip = "10108" WHERE user_id = 39 AND street = "12263 Jake Crossing";

6.) How much would it cost to buy one of each tool?
    -locate "Tools" category ($7383)
      - Practical Rubbert Shirt: 1107
      - Incredible Plastic Gloves: 5437
      - Awesome Plastic Shirt: 839
    -locate the word "Tools" associated with other categories
      - SELECT category FROM items ORDER BY category ASC;
      - Tools & Computers
        Tools & Kids
        Tools, Clothing & Toys
        Tools, Garden & Games
        Tools, Garden & Movies
        Tools, Jewelery & Industrial
        Sports & Tools
      - SELECT title, category, price FROM items WHERE category LIKE "%Tools%";
      - SELECT SUM(price) FROM items WHERE category LIKE "%Tools%";
      - total: $46477

7.) How much total items did we sell?
    - SELECT SUM(quantity) FROM orders;
    - total: 2125


8.) How much was spent on books?
    - SELECT SUM(quantity) FROM orders WHERE item_id =
    - SELECT items.id, items.category, items.price, orders.item_id, orders.quantity FROM items INNER JOIN orders ON items.id = orders.item_id;
    SELECT items.id, items.category, SUM(items.price) * SUM(orders.quantity), orders.item_id, orders.quantity FROM items INNER JOIN orders ON items.id = orders.item_id WHERE category LIKE "%Books%";

9.) Simulate buying an item by inserting a User for yourself and an Order for that User.

PRAGMA table_info(addresses);

1|title|varchar|0||0
2|category|varchar|0||0
3|description|text|0||0
4|price|integer|0||0

