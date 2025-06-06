# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi and age below 30

Sample table: CUSTOMERS
```
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1          Ramesh        32          Ahmedabad     2000
2          Khilan        25          Delhi         1500
3          Kaushik       23          Kota          2000
4          Chaitali      25          Mumbai        6500
5          Hardik        27          Bhopal        8500
6          Komal         22          Hyderabad     4500
7          Muffy         24          Indore        10000
```

```sql
SELECT * FROM CUSTOMERS
WHERE ADDRESS = 'Delhi'
AND AGE < 30
ORDER BY ID;
```

**Output:**

![image](https://github.com/user-attachments/assets/c5597554-93fd-488c-bcb5-eb15c2ff6de0)

**Question 2**
---
From the following tables, write a SQL query to find all orders generated by the salespeople who may work for customers whose id is 3007. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Table Name: orders
```
name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```

```sql
SELECT 
   ord_no,
   purch_amt,
   ord_date, 
   customer_id,
   salesman_id
FROM orders
WHERE salesman_id = (
SELECT salesman_id 
FROM orders
WHERE customer_id = 3007
);
```

**Output:**

![image](https://github.com/user-attachments/assets/b03461fd-3718-4d15-9c36-b78f5fbbf4ca)

**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS
```
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1          Ramesh       32           Ahmedabad    2000
2          Khilan       25           Delhi        1500
3          Kaushik      23           Kota         2000
4          Chaitali     25           Mumbai       6500
5          Hardik       27           Bhopal       8500
6          Komal        22           Hyderabad    4500
7          Muffy        24           Indore       10000
```

```sql
SELECT * FROM CUSTOMERS
WHERE SALARY < 2500;
```

**Output:**

![image](https://github.com/user-attachments/assets/29ccc0ac-1277-4dd7-b4fd-290f7d75e9ae)

**Question 4**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS
```
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1          Ramesh       32           Ahmedabad     2000
2          Khilan       25           Delhi         1500
3          Kaushik      23           Kota          2000
4          Chaitali     25           Mumbai        6500
5          Hardik       27           Bhopal        8500
6          Komal        22           Hyderabad     4500
7          Muffy        24           Indore        10000
```

```sql
SELECT * FROM CUSTOMERS
WHERE AGE < 30;
```

**Output:**

![image](https://github.com/user-attachments/assets/3f9ed719-6898-48cd-83d4-96cd0d8ffac5)

**Question 5**
---
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)
![image](https://github.com/user-attachments/assets/10d2b5fc-8e2b-442d-a5ae-d075d398b132)

```sql
SELECT 
   medication_id AS medic,
   medication_name,
   dosage
FROM Medications
WHERE dosage = (
SELECT MAX(dosage)
FROM Medications
);
```

**Output:**

![image](https://github.com/user-attachments/assets/6e7437b7-e6e8-433b-a5bc-f585cf28eee0)

**Question 6**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS
```
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh       32           Ahmedabad     2000
2          Khilan       25           Delhi         1500
3          Kaushik      23           Kota          2000
4          Chaitali     25           Mumbai        6500
5          Hardik       27           Bhopal        8500
6          Komal        22           Hyderabad     4500
7          Muffy        24           Indore        10000
```

```sql
SELECT * FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```

**Output:**

![image](https://github.com/user-attachments/assets/7290e87d-6f9a-4e8c-b7ff-b8722d40c3d6)

**Question 7**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

Employee Table
```
name             type
------------   ---------------
id                INTEGER
name              TEXT
age               INTEGER
city              TEXT
income            INTEGER
```

```sql
SELECT * FROM Employee
WHERE age < (
SELECT AVG(age)
FROM Employee
WHERE income > 1000000
);
```

**Output:**

![image](https://github.com/user-attachments/assets/657e1f2a-5be3-43a3-9d83-d77b7f0b4b8e)

**Question 8**
---
From the following tables write a SQL query to find all orders generated by London-based salespeople. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

salesman table
```
name             type
---------------  ---------------
salesman_id      numeric(5)
name             varchar(30)
city             varchar(15)
commission       decimal(5,2)
```
orders table
```
name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```

```sql
SELECT 
   ord_no,
   purch_amt,
   ord_date,
   customer_id,
   salesman_id
FROM orders
WHERE salesman_id IN (
SELECT salesman_id 
FROM salesman 
WHERE city = 'London'
);
```

**Output:**

![image](https://github.com/user-attachments/assets/2cfe6a4b-37b2-40f2-823d-d0cd8cf0568d)

**Question 9**
---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

salesman table
```
name                 type
---------------   ---------------
salesman_id       numeric(5)
name              varchar(30)
city              varchar(15)
commission        decimal(5,2)
```
customer table
```
name              type
-----------       ----------
customer_id      int
cust_name        text
city             text
grade            int
salesman_id      int
```

```sql
SELECT
   salesman_id,
   name
FROM salesman
WHERE salesman_id IN (
SELECT salesman_id
FROM customer
GROUP BY salesman_id
HAVING COUNT(salesman_id )> 1
);

```

**Output:**

![image](https://github.com/user-attachments/assets/8c437f30-3f3b-41ae-a4cb-d7cc60661bd3)

**Question 10**
---
From the following tables, write a SQL query to determine the commission of the salespeople in Paris. Return commission.

salesman table
```
name             type
---------------  ---------------
salesman_id      numeric(5)
name             varchar(30)
city             varchar(15)
commission       decimal(5,2)
```
customer table
```
name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int
```

```sql
SELECT commission
FROM salesman 
WHERE salesman_id IN (
SELECT salesman_id 
FROM customer 
WHERE city = 'Paris'
);
```

**Output:**

![image](https://github.com/user-attachments/assets/3a48d1ed-d615-419f-a7ba-bd66a1cea5d9)

**Grade:**

![image](https://github.com/user-attachments/assets/fd53902a-752f-480d-8c38-fd5987324553)

## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
