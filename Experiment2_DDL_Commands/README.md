# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
-- Insert all products from Discontinued_products into Products.
Table attributes are ProductID, ProductName, Price, Stock

```sql
-- insert into Products(ProductID,ProductName,Price,Stock) 
select * from Discontinued_products;
```

**Output:**

![image](https://github.com/user-attachments/assets/dcd0cea9-3c5f-4374-b04d-528eae4a73c1)


**Question 2**
---
-- Create a table named Members with the following columns:
MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
-- create table Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE);
```

**Output:**

![image](https://github.com/user-attachments/assets/e65726c6-57ea-4c6f-b8a2-6f8267297706)


**Question 3**
---
-- Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
-- Create table Shipments(
ShipmentID INTEGER primary key,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
foreign key (SupplierID) References Suppliers(SupplierID),
foreign key (OrderID) references Orders(OrderID));
```

**Output:**

![image](https://github.com/user-attachments/assets/ea627ae5-c54a-4850-aac0-b483417b98e2)


**Question 4**
---
-- Insert the following students into the Student_details table:
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
202            Ella King         F           Chemistry   87
203            James Bond   M          Literature    78

```sql
-- insert into Student_details(RollNo,Name,Gender,Subject,MARKS)
values(202,'Ella King','F','Chemistry',87),
(203,'James Bond','M','Literature',78);
```

**Output:**

![image](https://github.com/user-attachments/assets/37624fb3-aedb-442f-9809-07b40f7d7642)


**Question 5**
---
-- Write a SQL query to Rename the "city" column to "location" in the "customer" table.
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
-- alter table customer
rename city to location;
```

**Output:**

![image](https://github.com/user-attachments/assets/406cd0ee-a1d2-43cb-ad20-312793d1582b)


**Question 6**
---
-- Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
-- create table Products(
ProductID integer primary key,
ProductName text unique not null,
Price REAL check(Price>0),
StockQuantity Integer check(StockQuantity>0));
```

**Output:**

![image](https://github.com/user-attachments/assets/bb0ec5c3-a35b-4789-bbbd-07d98deed48b)


**Question 7**
---
-- Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
-- Pcreate table item(
item_id text primary key,
item_desc text not null,
rate integer not null,
icom_id text(4),
foreign key (icom_id) references company(com_id)
on update cascade
on delete cascade);
```

**Output:**

![image](https://github.com/user-attachments/assets/e1af43c6-c39d-4bce-ab0a-9be2abae032e)


**Question 8**
---
-- Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
-- insert into Employee
values(001,'Sarah Parker','Manager','HR',60000);
```

**Output:**

![image](https://github.com/user-attachments/assets/896079b3-1992-411c-a571-49ce0734adc6)


**Question 9**
---
-- Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
-- alter table customer
add column discount DECIMAL(5,2);
```

**Output:**

![image](https://github.com/user-attachments/assets/ffc8bf2f-80ba-4b81-8e7d-d26f5c7c0263)


**Question 10**
---
-- Create a table named Tasks with the following columns:
TaskID as INTEGER
TaskName as TEXT
DueDate as DATE

```sql
-- create table Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE);
```

**Output:**

![image](https://github.com/user-attachments/assets/abd98bcc-a396-4ae7-8455-0c88b8937eca)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
