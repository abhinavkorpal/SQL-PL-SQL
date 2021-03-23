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

![](https://github.com/abhinavkorpal/SQL-PL-SQL/blob/master/images/oracle_engine.png)
## Working with the Oracle Engine

![](https://github.com/abhinavkorpal/SQL-PL-SQL/blob/master/images/oracle_client_oracle_engine.png)
## Interaction between Oracle Clients - Oracle Engine and the server hard disk drive with data on it.

![](https://github.com/abhinavkorpal/SQL-PL-SQL/blob/master/images/oracle_tool_oracle_engine.png)
## Various Oracle tools connected to the oracle engine

#### SQL used for

- SQL can create and maintain data manipulation objects such as tables, views, sequences etc.

- Data manipulation Objects will be create and stored on the server's hard disk drive, in a tabelspace, to which the user has been assigned.

- Once these data manipulation objects created, they are used extensively in commerical applications.

#### DML, DCL, DDL

- SQL sentences that are used to create these objects are called **DDL's** or **Data Definition Language.**

- SQL sentences that are used to manipulate data within these objects are called **DML's** or **Data Manipulation Language.**

- SQL sentences that are used to control the behavior of these objects are called **DCl's** or **Data Control Language.**

#### THE CREATE TABLE COMMAND:
```
Syntax:
        CREATE TABLE tablename(columnname datatype(size), columnname datatype(size));
```        
        
#### INSERTION OF DATA INTO TABLES
```
Synatx: 
        INSERT INTO tablename(columnname, columnname) VALUES (expression, expression);
```
#### VIEWING DATA IN THE TABLES

All Rows and All Column:

To View Global Table Data the syntax is:

Global data extract:
```
I) Syntax:
        SELECT (columname1... ...columname n) FROM tablename;
II) Syntax:
        SELECT * FROM tablename;
```
#### FILTERING TABLE DATA:
way of filtering table data will be:
- Selected columns and all rows
- Selected rows and all columnns
- Selected columns and Selected rows

Selected Columns and All Rows:
```
Syntax: 
        SELECT columname, columname FROM tablename;
```
Selected rows and all columnns
```
Syntax: 
        SELECT * FROM tablename WHERE search condition;
```
Selected columns and Selected rows
```
Syntax:
        SELECT columname, columnname FROM tablename WHERE search condition;
        
```

#### SQL Performance Tuning





