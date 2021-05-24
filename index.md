# SQL Study

## **Getting Started**
after installing MySQL log in via the terminal is not possible unless it MySQL is added to the PATH....

### if using bash:
* `nano ~/.bash_profile`
* add the line `export PATH=$PATH:/usr/local/mysql/bin/` 
* save and exit
* back in the terminal enter `source ~/.bash_profile`

### if using zsh:
* `nano ~/.zshrc`
* add the line `export PATH=$PATH:/usr/local/mysql/bin/` 
* save and exit
* back in the terminal enter `source ~/.zshrc`

## **Retrieving Data From a Single Table**

### SELECT Clause:
Selected values appear in the order specified in the query. A last name, first name list can be created simply by querying  
`SELECT last_name, first_name FROM users`

Arithmetic expressions can be added to the `SELECT` clause. For example...    
`SELECT last_name, first_name, points * 0.15 as Discount FROM Customers`

### WHERE Clause:
`WHERE` is used, in combination with logical operators, to specify that only certain members of a selected group should be displayed  
for example...  
`SELECT * FROM patients WHERE birth_date <= '1970-02-24'`  
(Note as well the SQL syntax for dates yyyy-mm-dd)

### AND, OR, NOT Operators
These operators are used after a `WHERE` clause to refine a search.  
Logical operators in addition to `AND`,`OR` and `NOT` can produce statements such as...  

`SELECT * FROM customers`    
`WHERE birth_date > 1990-01-01`   
`  OR bonus_points > 1000 and state = 'PA';`
  
(Note that logical operators have an order of operations as well in which `AND` comes first)

### IN Operator
Simplifying queries can be accomplished using the `IN` Operator. For example,  
`SELECT * FROM customers`\
`WHERE state = 'PA' OR state = 'DE' OR state = 'TX';`  
can be simplified to...  
`SELECT * FROM customers`\
`WHERE state IN ('PA', 'DE', 'TX';`  

### BETWEEN Operator
The `BETWEEN` operator is another mechanism for simplifying queries
`SELECT * FROM customers`<br>
`WHERE points >= 1000 AND <= 3000`<br>
can be ismplified to...  
`SELECT * FROM customers`<br>
  `WHERE points BETWEEN 1000 AND 3000`<br>
  
(Note that `BETWEEN` is inclusive)
 
### LIKE Operator
The `LIKE` Operator is a non case sensitive operator used in queries to identify entries based on character patterns.  
`SELECT * FROM customers`<br>
`WHERE last_name LIKE b%`<br>

`_` and `%` are used along with `LIKE` to create queries. With `_` meaning one character and `%` representing any number of characters.  
So, `_b%` means a word with the second letter as b and ony number of characters there after.  

(Note that `LIKE` is somewhat out dated. Regex can do anything `LIKE` can. )

### REGEX
`^` beginning of a string.
`&` end of a string.
`|` or
`[git]` or `[g-t]` specific characters or a range of characters

`WHERE last_name REGEXP 'field'` - last name contains field
`WHERE last_name REGEXP '^field'` - last name begins with field
`WHERE last_name REGEXP 'field&'` - last name ends with field
`WHERE last_name REGEXP '^field|mac|key'` - last name begins with field or contains mac or key
`WHERE last_name REGEXP 'b[ru]'` - last name contains a 'b' that is followed by an 'r' or 'u'

### IS NULL
Find all orders that have not been shipped<br>
`SELECT * FROM orders`<br>
`WHERE ship_date IS NULL`<br>

or, find non null values...
Find all customers with a phone number in their records  
`SELECT * FROM customers`<br>
`WHERE phone_number IS NOT NULL`<br>

### ORDER BY
The default ordering of a query is via the primary key. This can be overridden with `ORDER BY`

Order by last name desceneding
`SELECT * FROM customers`<br>
`ORDER BY last_name DESC`

Order by state in desceneding order then by first name
`SELECT * FROM customers`<br>
`ORDER BY state DESC, first_name`

These `ORDER BY` commands do not need to columns in the table. They can be aliases or arithmetic expressions.  
For example, find all items with an order number of 2 sorted total price (highest first)

`SELECT *, quantity * unit_prince AS total_price FROM orders`<br>
`WHERE order_number = 2`<br>
`ORDER BY total_price DESC`<br>

### LIMIT
Used to create a query that displays only a portion of the applicable results.  
Retun the first three customers  
`SELECT * FROM customers LIMIT 3`

Return customers 7 - 9  
`SELECT * FROM customers LIMIT 6, 3`

-or-

Select the top three customers based on loyalty points  
`SELECT * FROM customers ORDER BY points LIMIT 3`

## 
