<!-- PROJECT LOGO -->
<br />
<p align="center">
  <h1 align="center">SQL-PL-SQL ✨</h1>

  <p align="center">
    <br />
    ·
    <a href="https://github.com/abhinavkorpal/SQL-PL-SQL/issues">Report Bug</a>
    ·
    <a href="https://github.com/abhinavkorpal/SQL-PL-SQL/issues">Request Feature</a>
  </p>
</p>

* [Working with the Oracle Engine](#working-with-the-oracle-engine)
* [Various Oracle tools connected to the oracle engine](#various-oracle-tools-connected-to-the-oracle-engine)
* [Interaction between Oracle Clients and Oracle Engine and the server hard disk drive with data on it](#interaction-between-oracle-clients-and-oracle-engine-and-the-server-hard-disk-drive-with-data-on-it)
* [SQL](#sql)
* [SQL used for](#sql-used-for)
* [DML DCL DDL](#dml-dcl-ddl)

- [THE CREATE TABLE COMMAND](#the-create-table-command)
- [INSERTION OF DATA INTO TABLES](#insertion-of-data-into-tables)
- [VIEWING DATA IN THE TABLES](#viewing-data-in-the-tables)
- [SQL Specific Questions](#sql-specific-questions)

##### Working with the Oracle Engine
![](https://github.com/abhinavkorpal/SQL-PL-SQL/blob/master/images/oracle_engine.png)

##### Interaction between Oracle Clients and Oracle Engine and the server hard disk drive with data on it.
![](https://github.com/abhinavkorpal/SQL-PL-SQL/blob/master/images/oracle_client_oracle_engine.png)

##### Various Oracle tools connected to the oracle engine
![](https://github.com/abhinavkorpal/SQL-PL-SQL/blob/master/images/oracle_tool_oracle_engine.png)

##### SQL

<details>
<summary>What does SQL stand for?</summary><br><b>

Structured Query Language

</b></details>

<details>
<summary>How is SQL Different from NoSQL</summary><br><b>

The main difference is that SQL databases are structured (data is stored in the form of
tables with rows and columns - like an excel spreadsheet table) while NoSQL is
unstructured, and the data storage can vary depending on how the NoSQL DB is set up, such
as key-value pair, document-oriented, etc.
</b></details>

<details>
<summary>What does it mean when a database is ACID compliant?</summary><br>

ACID stands for Atomicity, Consistency, Isolation, Durability. In order to be ACID compliant, the database much meet each of the four criteria

**Atomicity** - When a change occurs to the database, it should either succeed or fail as a whole.

For example, if you were to update a table, the update should completely execute. If it only partially executes, the
update is considered failed as a whole, and will not go through - the DB will revert back to it's original
state before the update occurred. It should also be mentioned that Atomicity ensures that each
transaction is completed as it's own stand alone "unit" - if any part fails, the whole statement fails.

**Consistency** - any change made to the database should bring it from one valid state into the next.

For example, if you make a change to the DB, it shouldn't corrupt it. Consistency is upheld by checks and constraints that
are pre-defined in the DB. For example, if you tried to change a value from a string to an int when the column
should be of datatype string, a consistent DB would not allow this transaction to go through, and the action would
not be executed

**Isolation** - this ensures that a database will never be seen "mid-update" - as multiple transactions are running at
the same time, it should still leave the DB in the same state as if the transactions were being run sequentially.

For example, let's say that 20 other people were making changes to the database at the same time. At the
time you executed your query, 15 of the 20 changes had gone through, but 5 were still in progress. You should
only see the 15 changes that had completed - you wouldn't see the database mid-update as the change goes through.

**Durability** - Once a change is committed, it will remain committed regardless of what happens
(power failure, system crash, etc.). This means that all completed transactions
must be recorded in non-volatile memory.

Note that SQL is by nature ACID compliant. Certain NoSQL DB's can be ACID compliant depending on
how they operate, but as a general rule of thumb, NoSQL DB's are not considered ACID compliant
</details>

<details>
<summary>When is it best to use SQL? NoSQL?</summary><br><b>

SQL - Best used when data integrity is crucial. SQL is typically implemented with many
businesses and areas within the finance field due to it's ACID compliance.

NoSQL - Great if you need to scale things quickly. NoSQL was designed with web applications
in mind, so it works great if you need to quickly spread the same information around to
multiple servers

Additionally, since NoSQL does not adhere to the strict table with columns and rows structure
that Relational Databases require, you can store different data types together.
</b></details>

<details>
<summary>What is a Cartesian Product?</summary><br>

A Cartesian product is when all rows from the first table are joined to all rows in the second
table. This can be done implicitly by not defining a key to join, or explicitly by
calling a CROSS JOIN on two tables, such as below:

Select * from customers **CROSS JOIN** orders;

Note that a Cartesian product can also be a bad thing - when performing a join
on two tables in which both do not have unique keys, this could cause the returned information
to be incorrect.
</details>

##### SQL used for

- SQL can create and maintain data manipulation objects such as tables, views, sequences etc.

- Data manipulation Objects will be create and stored on the server's hard disk drive, in a tabelspace, to which the user has been assigned.

- Once these data manipulation objects created, they are used extensively in commerical applications.

##### DML DCL DDL

- SQL sentences that are used to create these objects are called **DDL's** or **Data Definition Language.**

- SQL sentences that are used to manipulate data within these objects are called **DML's** or **Data Manipulation Language.**

- SQL sentences that are used to control the behavior of these objects are called **DCl's** or **Data Control Language.**

##### THE CREATE TABLE COMMAND

```sql
Syntax:
        CREATE TABLE tablename(columnname datatype(size), columnname datatype(size));
```

CREATE TABLE syntax, the SQL statement starts with 'CREATE' i.e. a verb, followed by 'TABLE' i.e. a noun and '<tablename>' i.e. adjective.
  
**Example:** ***Create a client_master table who structure is***:

Column Name | Data Type | Size
------------ | ------------- | -------------
client_no | varchar2 | 6
name | varchar2 | 20
address1 | varchar2 | 30
address2 | varchar2 | 30
city | varchar2 | 15
state | varchar2 | 15
pincode | number | 6
remarks | varchar2 | 60
bal_due | number | 10,2

```sql
CREATE TABLE client_master (client_no varchar2(20), name varchar2(30), address1 varchar2(30), 
  address2 varchar2(30), city varchar2(15), state varchar2(15), 
  pincode number(6), remarks varchar2(60), bal_due number(10,2));
```
        
##### INSERTION OF DATA INTO TABLES

```sql
Synatx: 
        INSERT INTO tablename(columnname, columnname) VALUES (expression, expression);
```
  
**Example:** ***Insert the following values into the client_master table***:
  
Column Name | Values
------------ | -------------
client_no | C02000,
name | Abhinav Korpal
address1 | HSR Layout
address2 | Outer Ring
city | Bangalore
state | Karantaka
pincode | 560001

```sql
INSERT INTO client_master 
  (client_no, name, address1, address2, city, state, pincode)
  VALUES('C02000', 'Abhinav Korpal', 'HSR Layout', 'Outer Ring', 'Bangalore', 'Karantaka', 560001);
```

 ##### VIEWING DATA IN THE TABLES

All Rows and All Column:

To View Global Table Data the syntax is:

Global data extract:

```sql
I) Syntax:
        SELECT (columname1... ...columname n) FROM tablename;
II) Syntax:
        SELECT * FROM tablename;
```
Example:
  
1. Retrieve the names of the employees and their salaries from the table emp_master;
```sql
SELECT name, salary FROM tablename;
```
2. Retrieve all records from tabel client_master;
```sql
SELECT * FROM client_master;
```

#### FILTERING TABLE DATA:

The way of filtering table data will be
- Selected columns and all rows
- Selected rows and all columnns
- Selected columns and Selected rows

Selected Columns and All Rows:

```sql
Syntax: 
        SELECT columname, columname FROM tablename;
```

Selected rows and all columnns:

```sql
Syntax: 
        SELECT * FROM tablename WHERE search condition;
```
Selected Columns and Selected Rows:

```sql
Syntax:
        SELECT columname, columnname FROM tablename WHERE search condition;
        
```

#### SQL Performance Tuning

###### USING ROWNUM IN SQL STATEMENTS

```sql
Syntax: 
      SELECT ROWNUM, client_no, name
      FROM client_master
      WHERE ROWNUM < 8;
```

###### SEQUENCES

```sql
Syntax:
      CREATE SEQUENCES sequence_name 
      [INCREMENT BY integervalue 
      START WITH integervalue 
      MAXVALUE integervalue / NOMAXVALUE integervalue 
      MINVALUE integervalue / NOMINVALUE integervalue 
      CYCLE / NOCYCLE CACHE integervalue / NOCACHE 
      ORDER / NOORDER]
```

###### Dropping A Sequence

```sql
Syntax: 
       DROP SEQUENCE sequence_name;
```

#### Security Management Using SQL

###### Granting Privileges using the Grant statement

```sql
Syntax: 
        GRANT {object privileges}
        ON objectname
        TO username
        [WITH GRANT OPTION];
```
###### Revoking permissions using the REVOKE statement

```sql
Synatx: 
       REVOKE { object privileges }
       ON objectname
       FROM username;
```

#### PL/SQL

#### SQL*PLUS
                       
##### SQL Specific Questions

For these questions, we will be using the Customers and Orders tables shown below:

**Customers**

Customer_ID | Customer_Name | Items_in_cart | Cash_spent_to_Date
------------ | ------------- | ------------- | -------------
100204 | John Smith | 0 | 20.00
100205 | Jane Smith | 3 | 40.00
100206 | Bobby Frank | 1 | 100.20

**ORDERS**

Customer_ID | Order_ID | Item | Price | Date_sold
------------ | ------------- | ------------- | ------------- | -------------
100206 | A123 | Rubber Ducky | 2.20 | 2019-09-18
100206 | A123 | Bubble Bath | 8.00 | 2019-09-18
100206 | Q987 | 80-Pack TP | 90.00 | 2019-09-20
100205 | Z001 | Cat Food - Tuna Fish | 10.00 | 2019-08-05
100205 | Z001 | Cat Food - Chicken | 10.00 | 2019-08-05
100205 | Z001 | Cat Food - Beef | 10.00 | 2019-08-05
100205 | Z001 | Cat Food - Kitty quesadilla | 10.00 | 2019-08-05
100204 | X202 | Coffee | 20.00 | 2019-04-29

<details>
<summary>How would I select all fields from this table?</summary><br><b>

Select * <br>
From Customers;
</b></details>

<details>
<summary>How many items are in John's cart?</summary><br><b>

Select Items_in_cart <br>
From Customers <br>
Where Customer_Name = "John Smith";
</b></details>

<details>
<summary>What is the sum of all the cash spent across all customers?</summary><br><b>

Select SUM(Cash_spent_to_Date) as SUM_CASH <br>
From Customers;
</b></details>

<details>
<summary>How many people have items in their cart?</summary><br><b>

Select count(1) as Number_of_People_w_items <br>
From Customers <br>
where Items_in_cart > 0;
</b></details>

<details>
<summary>How would you join the customer table to the order table?</summary><br><b>

You would join them on the unique key. In this case, the unique key is Customer_ID in
both the Customers table and Orders table
</b></details>

<details>
<summary>How would you show which customer ordered which items?</summary><br><b>

Select c.Customer_Name, o.Item <br>
From Customers c <br>
Left Join Orders o <br>
  On c.Customer_ID = o.Customer_ID;

</b></details>

<details>
<summary>Using a with statement, how would you show who ordered cat food, and the total amount of money spent?</summary><br><b>

with cat_food as ( <br>
Select Customer_ID, SUM(Price) as TOTAL_PRICE <br>
From Orders <br>
Where Item like "%Cat Food%" <br>
Group by Customer_ID <br>
) <br>
Select Customer_name, TOTAL_PRICE <br>
From Customers c <br>
Inner JOIN cat_food f <br>
  ON c.Customer_ID = f.Customer_ID <br>
where c.Customer_ID in (Select Customer_ID from cat_food);

Although this was a simple statement, the "with" clause really shines when
a complex query needs to be run on a table before joining to another. With statements are nice,
because you create a pseudo temp when running your query, instead of creating a whole new table.

The Sum of all the purchases of cat food weren't readily available, so we used a with statement to create
the pseudo table to retrieve the sum of the prices spent by each customer, then join the table normally.
</b></details>











