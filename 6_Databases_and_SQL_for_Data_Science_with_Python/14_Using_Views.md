# Task 1: Create a View

In this exercise, you will create a View and show a selection of data for a given table.

1. Let's create a view called EMPSALARY to display salary along with some basic sensitive data of employees from the HR database. To create the EMPSALARY view from the EMPLOYEES table, Copy the code below and paste it to the textarea of the SQL page. Click Go.

```sql
CREATE VIEW EMPSALARY AS
SELECT EMP_ID, F_NAME, L_NAME, B_DATE, SEX, SALARY
FROM EMPLOYEES;
```

2. Using SELECT, query the EMPSALARY view to retrieve all the records. Use the following statement.

```sql
SELECT * FROM EMPSALARY;
```

# Task 2: Update a View

In this exercise, you will update a View to combine two or more tables in meaningful ways.

1. Assume that the EMPSALARY view we created in Task 1 doesn't contain enough salary information, such as max/min salary and the job title of the employees. For this, we need to get information from other tables in the database. You need all columns from EMPLOYEES table used above, except for SALARY. You also need the columns JOB_TITLE, MIN_SALARY, MAX_SALARY of the JOBS table.
   The command to be used is as follows:

```sql
CREATE OR REPLACE VIEW EMPSALARY AS
SELECT EMP_ID, F_NAME, L_NAME, B_DATE, SEX, JOB_TITLE,
MIN_SALARY, MAX_SALARY
FROM EMPLOYEES, JOBS
WHERE EMPLOYEES.JOB_ID = JOBS.JOB_IDENT;
```

NOTE: The technique used here to combine data from two tables is called implicit inner join. You will learn more about joins later on. For now, just assume you are combining the data of two different tables, EMPLOYEES and JOBS by connecting their respective columns JOB_ID and JOB_IDENT, since both the columns contain common unique data. You can have a look at the database description, shared at the beginning of the lab, to verify this.

Using SELECT, query the updated EMPSALARY view to retrieve all the records. Copy the code below and paste it to the textarea of the SQL page. Click Go.

```sql
SELECT * FROM EMPSALARY;
```
