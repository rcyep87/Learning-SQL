1.) How many users are there? 50 SELECT COUNT(*) FROM users;

2.) What are the 5 most expensive items? Small Cotton Gloves, Small Wooden Computer, Awesome Granite Pants, Sleek Wooden Hat, Ergonomic Steel Car SELECT title, price FROM items ORDER BY price DESC LIMIT(5);

3.) What's the cheapest book? $1,496 (Does that change for "category is exactly "book" versus "category contains 'book'"?)

sqlite> SELECT title, category, price FROM items WHERE category = 'Books';

4.) Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?

SELECT id, street, city, state, zip FROM addresses WHERE street = '6439 Zetta Hills' AND  city = 'Willmouth' AND state = 'WY';

-check headers PRAGMA table_info(table_name);
-id = 43
- SELECT id, first_name, last_name FROM users WHERE id = 43;
- Kyral Kilback

5.) Correct Virginie Mitchell's address to "New York, NY, 10108"

-locate Virginie Mitchell's id
- userid = 39
- SELECT user_id, street, city, state, zip FROM addresses WHERE user_id = 39;
- UPDATE addresses SET city = "New York", zip = "10108" WHERE user_id = 39 AND street = "12263 Jake Crossing";

6.) How much would it cost to buy one of each tool?


7.) How much total items did we sell?


8.) How much was spent on books?


9.) Simulate buying an item by inserting a User for yourself and an Order for that User.

PRAGMA table_info(addresses);
