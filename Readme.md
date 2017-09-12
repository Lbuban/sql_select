PROBLEM #1:Create a list of students showing first and last names only.
mysql> SELECT first_name, last_name
    -> FROM student;
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| Eric       | Ephram    |
| Greg       | Gould     |
| Adam       | Ant       |
| Howard     | Hess      |
| Charles    | Caldwell  |
| James      | Joyce     |
| Doug       | Dumas     |
| Kevin      | Kraft     |
| Frank      | Fountain  |
| Brian      | Biggs     |
+------------+-----------+
10 rows in set (0.00 sec)

PROBLEM #2:Create a list of students with all the columns but only if the student has less than 8 years experience
mysql> SELECT * FROM student
    -> WHERE years_of_experience < 8;
+------------+------------+-----------+---------------------+------------+
| student_id | first_name | last_name | years_of_experience | start_date |
+------------+------------+-----------+---------------------+------------+
|          1 | Eric       | Ephram    |                   2 | 2016-03-31 |
|          2 | Greg       | Gould     |                   6 | 2016-09-30 |
|          3 | Adam       | Ant       |                   5 | 2016-06-02 |
|          4 | Howard     | Hess      |                   1 | 2016-02-28 |
|          5 | Charles    | Caldwell  |                   7 | 2016-05-07 |
|          8 | Kevin      | Kraft     |                   3 | 2016-04-15 |
|         10 | Brian      | Biggs     |                   4 | 2015-12-25 |
+------------+------------+-----------+---------------------+------------+
7 rows in set (0.00 sec)

PROBLEM #3: Create a list of students showing the lastname, startdate, and id columns only and sorted by last_name in ascending sequence
mysql> SELECT last_name, start_date, student_id
    -> FROM student
    -> ORDER BY last_name ASC;
+-----------+------------+------------+
| last_name | start_date | student_id |
+-----------+------------+------------+
| Ant       | 2016-06-02 |          3 |
| Biggs     | 2015-12-25 |         10 |
| Caldwell  | 2016-05-07 |          5 |
| Dumas     | 2016-07-04 |          7 |
| Ephram    | 2016-03-31 |          1 |
| Fountain  | 2016-01-31 |          9 |
| Gould     | 2016-09-30 |          2 |
| Hess      | 2016-02-28 |          4 |
| Joyce     | 2016-08-27 |          6 |
| Kraft     | 2016-04-15 |          8 |
+-----------+------------+------------+
10 rows in set (0.00 sec)

PROBLEM #4: Create a list of students showing all columns but only if the student first name is Adam, James, or Frank and sort them in last_name descending sequence.
mysql> SELECT *
    -> FROM student
    -> WHERE first_name IN ("Adam", "James", "Frank")
    -> ORDER BY last_name DESC;
+------------+------------+-----------+---------------------+------------+
| student_id | first_name | last_name | years_of_experience | start_date |
+------------+------------+-----------+---------------------+------------+
|          6 | James      | Joyce     |                   9 | 2016-08-27 |
|          9 | Frank      | Fountain  |                   8 | 2016-01-31 |
|          3 | Adam       | Ant       |                   5 | 2016-06-02 |
+------------+------------+-----------+---------------------+------------+
3 rows in set (0.00 sec)

PROBLEM #5: Create a list of students showing firstname, lastname and startdate where the startdate is between Jan 1, 2016 and June 30, 2016 and order the list by descending start_date sequence.
mysql> SELECT first_name, last_name, start_date
    -> FROM student
    -> WHERE start_date BETWEEN "2016-01-01" AND "2016-06-30"
    -> ORDER BY start_date DESC;
+------------+-----------+------------+
| first_name | last_name | start_date |
+------------+-----------+------------+
| Adam       | Ant       | 2016-06-02 |
| Charles    | Caldwell  | 2016-05-07 |
| Kevin      | Kraft     | 2016-04-15 |
| Eric       | Ephram    | 2016-03-31 |
| Howard     | Hess      | 2016-02-28 |
| Frank      | Fountain  | 2016-01-31 |
+------------+-----------+------------+
6 rows in set (0.00 sec)


*****MEDIUM******

mysql> explain assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   |     | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| grade_id       | int(11)          | YES  | MUL | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> select * from assignment;
+---------------+------------+----------------+----------+----------+
| assignment_id | student_id | assignment_nbr | class_id | grade_id |
+---------------+------------+----------------+----------+----------+
|             1 |          3 |              4 |        5 |        5 |
|             2 |          2 |              3 |        4 |        4 |
|             3 |          1 |              2 |        4 |        5 |
|             4 |          7 |              3 |        6 |        1 |
|             5 |          4 |              5 |        6 |        2 |
+---------------+------------+----------------+----------+----------+
5 rows in set (0.00 sec)

mysql> explain grade;
+-------------+-------------+------+-----+---------+----------------+
| Field       | Type        | Null | Key | Default | Extra          |
+-------------+-------------+------+-----+---------+----------------+
| grade_id    | int(11)     | NO   | PRI | NULL    | auto_increment |
| grade_value | varchar(50) | YES  |     | NULL    |                |
+-------------+-------------+------+-----+---------+----------------+
2 rows in set (0.00 sec)

mysql> select * from grade;
+----------+-----------------------------+
| grade_id | grade_value                 |
+----------+-----------------------------+
|        1 | incomplete                  |
|        2 | complete and unsatisfactory |
|        3 | complete and satisfactory   |
|        4 | exceeds expectations        |
|        5 | not graded                  |
+----------+-----------------------------+
5 rows in set (0.00 sec)

*****HARD******

mysql> explain assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11) unsigned | YES  | MUL | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| grade_id       | int(11)          | YES  | MUL | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)
