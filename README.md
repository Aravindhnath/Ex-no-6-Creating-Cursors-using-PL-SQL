# Ex. No: 6 Creating Cursors using PL/SQL

### AIM: To create a cursor using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create a cursor named as employee_cursor
3. Using cursor read each record and display the result
4. Close the cursor

### Program:
```sql
SQL> CREATE TABLE emp(empid number, empname varchar(10), dept varchar(10),salary number);
Table created.

-- Insert the values in the employee table
INSERT INTO emp(empid, empname, dept, salary)
values(1,'Krishna','Agri',70000);
INSERT INTO emp(empid, empname, dept, salary)
values(2,'Radha','Cyber',80000);
INSERT INTO emp(empid, empname, dept, salary)
values(3,'Balram','IT',50000);
```
### Create employee table

![Output](/exp6_DBMS-1.png)

### PLSQL Cursor code
```sql
SQL> SET SERVEROUTPUT ON;
SQL> DECLARE
  2  CURSOR employee_cursor IS
  3  SELECT empid, empname, dept, salary
  4  FROM emp;
  5  empid number;
  6  empname varchar(10);
  7  empdept varchar(10);
  8  salary number;
  9  BEGIN
 10     OPEN employee_cursor;
 11     LOOP
 12             FETCH employee_cursor INTO empid, empname, empdept, salary;
 13             EXIT WHEN employee_cursor%NOTFOUND;
 14             DBMS_OUTPUT.PUT_LINE('**********************');
 15             DBMS_OUTPUT.PUT_LINE('EMPLOYEE ID: ' || empid);
 16             DBMS_OUTPUT.PUT_LINE('EMPLOYEE NAME: ' || empname);
 17             DBMS_OUTPUT.PUT_LINE('DEPARTMENT: ' || empdept);
 18             DBMS_OUTPUT.PUT_LINE('SALARY: ' || salary);
 19             DBMS_OUTPUT.PUT_LINE('**********************');
 20     END LOOP;
 21     CLOSE employee_cursor;
 22  END;
 23  /
```
### Output:

![Output](/exp6_DBMS-2.png)

### Result:
The program has been successfully implemented.
