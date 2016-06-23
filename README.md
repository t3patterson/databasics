#Answers

##Explorer
####1. number of users
50

####2. 5 most expensive items
| id    |   title   |
|----  | ---------   |
| 25 | Small Cotton Gloves(9984) | 
| 83 | SmallWoodenComput  |
| 100 | Awesome Granite Pan |
| 40  |  Sleek Wooden Hat |
| 60 | Ergonomic Steel Car |

####3. most expensive book :
```sql
SELECT *,MAX(items.price) FROM items WHERE category = 'Books';
```
| id       | title             | category  | Price   | 
| -------- |---------------       | ----------| --- |
| 4        | Fantastic Steel Chair | Books  | 9246  |          


####4.  Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?
 
```sql
SELECT user_id,  FROM addresses INNER JOIN users ON addresses.user_id = users.id WHERE street='6439 Zetta Hills' AND  city='Willmouth' AND state='WY';
```
| user_id |     first_name |  last_name| 
| ---------- |  ---------- |  ----------|
| 40 |          Corrine |     Little|   

####5. Correct Virginie Mills Address to *New York, NY, 10108*

####6. How much to buy one of each item?
```sql
SELECT SUM(items.price) FROM items;
```
467488

####7. How many total items were sold?
```sql
SELECT SUM(orders.quantity) FROM orders ;
```

####8. How much was spent on books?

```sql
 SELECT SUM(orders.quantity*items.price) FROM orders
    INNER JOIN items
    ON orders.item_id = items.id;
```
10045128                        

####9. Simulate buying an item by inserting a User for yourself and an Order for that User.
```sql

```

##Adventurer
####10. What item was ordered most often?
```sql
SELECT item_id, MAX(total) from (SELECT orders.item_id,SUM(orders.quantity) AS total FROM orders GROUP BY orders.item_id);
```
(to check the max)

```sql
SELECT item_id, MAX(total) from (SELECT orders.item_id,SUM(orders.quantity) AS total FROM orders GROUP BY orders.item_id);
```

|id    |    title   |     category |    description  |     price |     
|-----| -----      |   ----  |   ------  | -----|
|65  |   Incredible Granite Car  | Music, Sports & Clothing | Virtual bi-directional alliance | 7295 |

####11. What item grossed the most money?
```sql
SELECT items.title,orders.quantity,items.price,items.price*orders.quantity FROM items INNER JOIN orders ON items.id = orders.item_id GROUP BY items.id;
```

|title            |  quantity  |  price   |  items.price*orders.quantity |
|-----------------|  ----------|  ----------  | ------------------|
|Fantastic Granite Pants|  1         |  1151    |  1151 |                      
|Fantastic Wooden Chair |  6         |  6215    |  37290 |                     
|Intelligent Concrete Co | 10        |  7815    |  78150 |                            

####12. What user spent the most?

####13. What were the top 3 highest grossing categories?