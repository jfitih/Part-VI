# Part-VI
SQL
SHOW DATABASES;
USE jeffdatabase;

/*
									PART IV
Topics:
• Inserting new records into your database
• Updating existing records
• Deleting records that you no longer want

	4.1 Inserting a new record
*/

/*
	Use INSERT statement with VALUES clause to insert one row at a time.
INSERT INTO table_name (col_1, col_2, col_4)
VALUES (1, 34, ‘Big’),
(2, 33, ‘Small’)
Order of the values in the VALUES list should match with the column list.
*/


/*
	4.2 Inserting default values
Insert a row without specifying any value.
A table can be defined to take default values for specific columns. When we define a table, we can
set this as follows.
CREATE TABLE table_name (col_name INTEGER DEFAULT 0)
Here, a new table called table_name is created with a column named col_name that takes an integer
type input and the default is 0 when no value is specified.
When inserting a new row, you may specify the default value in general or for a specific column
INSERT INTO table_name (col_name) VALUES (DEFAULT)
Or
INSERT INTO table_name VALUES () // when all columns have a default value defined
*/

/*
	4.3 Overriding a default value with NULL
CREATE TABLE table_name (col_1 INTEGER DEFAUL 0, col_2 VARCHAR(10))
INSERT INTO table_name (col_1, col_2) VALUES (null, ‘TSU_TIGERS’)
*/

/*
	4.4 Copying rows from one table into another
Steps: Perform query in one table, take the query result to insert into another table
INSERT INTO table_new (std_id, name, gpa)
//Then
SELECT std_id, name, gpa
FROM table_old
WHERE name IN (‘John’,’Robert’)
*/

/*
	4.5 Copying table definitions (column names), but not the contents (rows)
CREATE TABLE table_name
AS
SELECT *
FROM table_old
WHERE 1 = 0
*/

/*
	4.6 Update records in a table.
Say, you want to increase the salary of all employees who served more than 10 years by 10%.
UPDATE emp_table
SET sal = sal*1.10
WHERE srv_year > 10
*/

/*
	4.7 Update records in a table corresponding to another table
Increase the salary of the employees who appear in another table named Emp_bonus
UPDATE main_table
SET sal = sal* 1.10
WHERE emp_ID IN (SELECT emp_ID FROM Emp_bonus)
*/
/*
	4.8 Deleting specific records
Example, delete all the rows that have dept_no
DELETE FROM emp_table WHERE dept_no = 4
*/

/*
	4.9 Delete records in the main that do not exist in another table
Delete those student records from main_table who do not appear in the new_table.
DELET FROM main_table
WHERE NOT EXISTS (
SELECT * FROM new_table
WHERE new_table.student_ID = main_table.student_ID)
OR
DELET FROM main_table
WHERE student_ID NOT IN (SELECT student_ID from new_table)
*/
/*
	4.10 Delete duplicate records.
DELETE FROM table
WHERE ID NOT IN
(SELECT min (ID) FROM table GROUP BY Origin)
Or
SELECT Origin, min (ID)
 FROM table
GROUP BY Origin
*/

/*
	4.11 Delete records from the main_table of students 
who failed more than or equal to 3 times and
appear in the table named fail_grade
DELETE FROM main_table
WHERE grade IN (SELECT *
FROM fail_grade
GROUP BY student_ID
ID Origin
1 Chicago
2 Chicago
3 Nashville
4 Nashville
5 Nashville
having count(*) >=3)
*/
