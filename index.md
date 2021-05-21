# SQL Study

## Getting Started
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

## Retrieving Data From a Single Table

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
