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
--![image](https://github.com/user-attachments/assets/89dcf6c3-6c68-47b5-b44a-79e047c96a56)

```insert into Employee(EmployeeID,Name,Position,Department,Salary) values (2,'John Smith','Developer','IT',75000),(3,'Anna Bell','Designer','Marketing',68000);
```

**Output:**

![image](https://github.com/user-attachments/assets/47a8cd23-b85d-48f6-923f-de4961fc1e62)

**Question 2**
---
-- ![image](https://github.com/user-attachments/assets/a00a3708-5697-400f-af87-4d6efea46f63)

```
--create table Employees(
EmployeeID primary key,
FirstName NOT NULL,
LastName NOT NULL,
Email unique,
Salary not null CHECK(Salary>0),
DepartmentID int,
foreign key(DepartmentID) references Departments(DepartmentID)
);

```

**Output:**

![image](https://github.com/user-attachments/assets/d00e3896-2660-48fd-a797-09e99af4e5db)

**Question 3**
---
-- ![image](https://github.com/user-attachments/assets/8e2e7cf2-bd43-4ba2-bbe0-df045b934cf9)

```
-- insert into Books(ISBN,Title,Author,Publisher,YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM Out_of_print_books;
```

**Output:**
![image](https://github.com/user-attachments/assets/fdcfe071-bfe7-4562-bc3a-36f74db82268)

**Question 4**
---
-- ![image](https://github.com/user-attachments/assets/658806dd-7493-449c-a61d-a4ce04d14e0c)

```sql
-- alter table Companies
RENAME COLUMN name TO VARCHAR(50);
alter table Companies
ADD column DOB Date;

```

**Output:**

![image](https://github.com/user-attachments/assets/69359801-ebd3-4497-b399-883db0a23e9c)


**Question 5**
---
-- ![image](https://github.com/user-attachments/assets/78925fbf-e6d4-4cc7-8214-804e5b76963e)

```sql
-- create table Products(
ProductID primary key,
ProductName NOT NULL,
Price real check(Price>0),
Stock int check(Stock>=0)
);
```

**Output:**
![image](https://github.com/user-attachments/assets/c1cf0e49-bff9-452c-9451-215c609ba194)

**Question 6**
---
-- ![image](https://github.com/user-attachments/assets/a51ee06f-8c11-4745-ae1b-1c54242701d4)

```sql
-- ALTER TABLE Student_details
Add column Country TEXT;
```

**Output:**

![image](https://github.com/user-attachments/assets/20270e2c-8623-4068-9f82-cd892916460b)

**Question 7**
---
-- ![image](https://github.com/user-attachments/assets/70792827-a3f5-4617-ba60-3db972265a2c)

```sql
--create table ProjectAssignments(
AssignmentID INTEGER primary key,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
foreign key(EmployeeID)references Employees(EmployeeID),
foreign key(ProjectID)references Projects(ProjectID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/4715f8cc-820d-4968-ade9-b630f482faa2)

**Question 8**
---
-- ![image](https://github.com/user-attachments/assets/fc06e08a-f238-47fa-99ed-5ea19e465c9c)

```sql
--create table Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
);
```

**Output:**

![image](https://github.com/user-attachments/assets/dbb17674-11e9-412c-9d3a-538655426b6b)

**Question 9**
---
-- ![image](https://github.com/user-attachments/assets/09e150c8-4053-4655-aa3e-03f752f58fa1)

```sql
-- insert into Books(ISBN,Title,Author,Publisher,Year) values ('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**

![image](https://github.com/user-attachments/assets/e2c7071a-fc23-491e-af0e-e3409512a990)

**Question 10**
---
--![image](https://github.com/user-attachments/assets/da112e00-a9eb-4bed-b1b7-a9191b1238cd)


```sql
-- create table Attendance(
AttendanceID INTEGER primary key,
EmployeeID INTEGER,
AttendanceDate DATE NOT NULL,
Status TEXT CHECK(STATUS IN('Present','Absent','Leave')),
foreign key(EmployeeID)references Employees(EmployeeID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/e3947bc4-a1e5-445b-971a-192f15f01f4a)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
