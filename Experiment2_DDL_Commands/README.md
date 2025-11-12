# Experiment 2: DDL Commands
## Name: RAGHUL V
## Reg.no:212223060216
## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

*Syntax:*
sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);

### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
sql
ALTER TABLE std ADD (Address CHAR(10));

(b) MODIFY
sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));

(c) DROP
sql
ALTER TABLE relation_name DROP COLUMN field_name;

(d) RENAME
sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;

### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
sql
DROP TABLE relation_name;

### 4. RENAME
Used to rename an existing database object.
sql
RENAME TABLE old_relation_name TO new_relation_name;

### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);

### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);

### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);

### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);

### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);

### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);


*Question 1*

Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.

ALTER TABLE  Student_details ADD COLUMN Email VARCHAR(50);
ALTER TABLE  Student_details ADD COLUMN MARKS DEFAULT '0';

### Output:

![image](https://github.com/user-attachments/assets/a2ad517d-78c6-4489-9474-ae83f64e32ce)


*Question 2*

Create a new table named contacts with the following specifications: contact_id as INTEGER and primary key. first_name as TEXT and not NULL. last_name as TEXT and not NULL. email as TEXT. phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

CREATE TABLE contacts (
contact_id INT PRIMARY KEY,
first_name TEXT  NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT  NOT NULL,
CHECK (LENGTH(phone)>=10)
);

### Output:

![image](https://github.com/user-attachments/assets/4232e1e8-adc2-4bcc-aecc-6cb871978988)


*Question 3*

Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

INSERT INTO Books(ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished 
FROM Out_of_print_books;

### *Output:*

![image](https://github.com/user-attachments/assets/cbec7eb2-d1e6-4204-9486-203ef3c32e2c)


### *Question 4*

Create a table named Departments with the following columns:

DepartmentID as INTEGER DepartmentName as TEXT

CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT);


### *Output:*
![image](https://github.com/user-attachments/assets/3c02ebb4-0350-4b0b-b74a-3611066239c4)

*Question 5*

Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

ALTER TABLE employee ADD COLUMN department_id INTEGER;
ALTER TABLE employee ADD COLUMN manager_id INTEGER DEFAULT NULL;

### Output:
![image](https://github.com/user-attachments/assets/aa64eeea-195a-4162-91ea-0dd7a32aa315)

### *Question 6*

Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

INSERT INTO Customers(CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers;6

### Output:

![image](https://github.com/user-attachments/assets/5ad04860-aab6-4066-9138-47629ff8a49f)

### *Question 7*

 ---Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id -------------+----------------+------------+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002

ALTER TABLE customer  ADD COLUMN discount DECIMAL(5,2);


### Output:

![image](https://github.com/user-attachments/assets/fc9f743c-666b-401b-84c5-983bd21a4926)

### *Question 8*

Create a table named Members with the following columns:

MemberID as INTEGER MemberName as TEXT JoinDate as DATE

create table Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE
);

### *Output:*

![image](https://github.com/user-attachments/assets/0b0a2862-476c-4930-be64-9efc6e273acb)


## *Question 9*

Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

  alter table customer
add column birth_date timestamp;

### Output:

![image](https://github.com/user-attachments/assets/9eb90475-b45d-40ff-aa44-3813174201ba)

### *Question 10*

Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          

Note: The Subject and MARKS columns will use their default values.

insert into Student_details(RollNo,Name,Gender)
values(204,"Samuel Black","M");

### Output:

![image](https://github.com/user-attachments/assets/9d1f9460-2ad8-4479-99d2-7a8a2d5f5797)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
