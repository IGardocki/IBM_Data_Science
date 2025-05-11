# Final Project: Advanced SQL Techniques

Estimated time needed: 60 minutes

## Scenario

You have to analyse the following datasets for the city of Chicago, as available on the Chicago City data portal.

- Socioeconomic indicators in Chicago
- Chicago public schools
- Chicago crime data

Based on the information available in the different tables, you have to run specific queries using Advanced SQL techniques that generate the required result sets.

The lab will be followed by a graded quiz that will have questions on all problems in this lab. Hence, remember to take screenshots of your SQL queries and their outputs for reference.

## Objectives

After completing this lab, you will be able to:

1. Use joins to query data from multiple tables
2. Create and query views
3. Write and run stored procedures
4. Use transactions

# Exercise 1: Using Joins

You have been asked to produce some reports about the communities and crimes in the Chicago area. You will need to use SQL join queries to access the data stored across multiple tables.

1. Write and execute a SQL query to list the school names, community names and average attendance for communities with a hardship index of 98.

```sql
SELECT S.NAME_OF_SCHOOL, S.COMMUNITY_AREA_NAME, S.AVERAGE_STUDENT_ATTENDANCE, C.HARDSHIP_INDEX
FROM chicago_public_schools S
INNER JOIN chicago_socioeconomic_data C
ON S.COMMUNITY_AREA_NAME = C.COMMUNITY_AREA_NAME
AND C.HARDSHIP_INDEX = 98;
```

2. Write and execute a SQL query to list all crimes that took place at a school. Include case number, crime type and community name.

```sql
SELECT C.CASE_NUMBER, C.PRIMARY_TYPE, C.COMMUNITY_AREA_NUMBER, CSD.COMMUNITY_AREA_NUMBER, CSD.COMMUNITY_AREA_NAME
FROM chicago_crime C
OUTER LEFT JOIN chicago_socioeconomic_data CSD
ON C.COMMUNITY_AREA_NUMBER = CSD.COMMUNITY_AREA_NUMBER
WHERE C.LOCATION_DESCRIPTION LIKE '%SCHOOL%'
```

# Exercise 2: Creating a View

For privacy reasons, you have been asked to create a view that enables users to select just the school name and the icon fields from the CHICAGO_PUBLIC_SCHOOLS table. By providing a view, you can ensure that users cannot see the actual scores given to a school, just the icon associated with their score. You should define new names for the view columns to obscure the use of scores and icons in the original table.

## Question 1

- Write and execute a SQL statement to create a view showing the columns listed in the following table, with new column names as shown in the second column.

```sql
CREATE OR REPLACE VIEW PRIVACY_VIEW(School_Name, Safety_Rating, Family_Rating, Environment_Rating, Instruction_Rating, Leaders_Rating, Teachers_Rating) AS
SELECT NAME_OF_SCHOOL, Safety_Icon, Family_Involvement_Icon, Environment_Icon, Instruction_Icon, Leaders_Icon, Teachers_Icon
FROM chicago_public_schools;
```

- Write and execute a SQL statement that returns all of the columns from the view.

```sql
SELECT * FROM PRIVACY_VIEW;
```

- Write and execute a SQL statement that returns just the school name and leaders rating from the view.

```sql
SELECT SCHOOL_NAME, LEADERS_RATING FROM PRIVACY_VIEW;
```

# Exercise 3: Creating a Stored Procedure

The icon fields are calculated based on the value in the corresponding score field. You need to make sure that when a score field is updated, the icon field is updated too. To do this, you will write a stored procedure that receives the school id and a leaders score as input parameters, calculates the icon setting and updates the fields appropriately.

1. Write the structure of a query to create or replace a stored procedure called UPDATE_LEADERS_SCORE that takes a in_School_ID parameter as an integer and a in_Leader_Score parameter as an integer.

```sql
CREATE OR REPLACE PROCEDURE UPDATE_LEADERS_SCORE (
    IN in_School_ID INT,
    IN in_Leader_Score INT
)
BEGIN
-- logic here
END;
```

2. Inside your stored procedure, write a SQL statement to update the Leaders_Score field in the CHICAGO_PUBLIC_SCHOOLS table for the school identified by in_School_ID to the value in the in_Leader_Score parameter.
```sql
DELIMITER //

CREATE PROCEDURE UPDATE_LEADERS_SCORE (
    IN in_School_ID INT,
    IN in_Leader_Score INT
)
BEGIN
    UPDATE CHICAGO_PUBLIC_SCHOOLS
    SET Leaders_Score = in_Leader_Score
    WHERE School_ID = in_School_ID;
END //

DELIMITER ;
```
