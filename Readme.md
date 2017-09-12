Instruction 0
    mysql> select * from student;
    +------------+------------+-----------+---------------------+------------+
    | student_id | first_name | last_name | years_of_experience | start_date |
    +------------+------------+-----------+---------------------+------------+
    |          1 | Eric       | Ephram    |                   2 | 2016-03-31 |
    |          2 | Greg       | Gould     |                   6 | 2016-09-30 |
    |          3 | Adam       | Ant       |                   5 | 2016-06-02 |
    |          4 | Howard     | Hess      |                   1 | 2016-02-28 |
    |          5 | Charles    | Caldwell  |                   7 | 2016-05-07 |
    |          6 | James      | Joyce     |                   9 | 2016-08-27 |
    |          7 | Doug       | Dumas     |                  13 | 2016-07-04 |
    |          8 | Kevin      | Kraft     |                   3 | 2016-04-15 |
    |          9 | Frank      | Fountain  |                   8 | 2016-01-31 |
    |         10 | Brian      | Biggs     |                   4 | 2015-12-25 |
    +------------+------------+-----------+---------------------+------------+
    10 rows in set (0.00 sec)

Instruction 1
    mysql> select first_name, last_name from student
        -> ;
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


Instruction 2
    mysql> select * from student where years_of_experience < 8;
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
    7 rows in set (0.01 sec)


Instruction 3
    mysql> select last_name, start_date, student_id from student order by last_name asc;
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


Instruction 4
    mysql> select * from student where first_name in ('Adam', 'James', 'Frank') order by last_name desc;
    +------------+------------+-----------+---------------------+------------+
    | student_id | first_name | last_name | years_of_experience | start_date |
    +------------+------------+-----------+---------------------+------------+
    |          6 | James      | Joyce     |                   9 | 2016-08-27 |
    |          9 | Frank      | Fountain  |                   8 | 2016-01-31 |
    |          3 | Adam       | Ant       |                   5 | 2016-06-02 |
    +------------+------------+-----------+---------------------+------------+
    3 rows in set (0.00 sec)


Instruction 5
    mysql> select first_name, last_name, start_date from student where start_date between '2016-01-01' and '2016-06-30'
        -> order by start_date desc;
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



Changing the GRADE field in Assignment

        mysql> CREATE TABLE `assignment` (
            ->   `assignment_id` int(11) unsigned NOT NULL AUTO_INCREMENT,
            ->   `student_id` int(11) NOT NULL,
            ->   `assignment_nbr` int(11) NOT NULL,
            ->   `grade` varchar(30) DEFAULT NULL,
            ->   `class_id` int(11) DEFAULT NULL,
            ->   PRIMARY KEY (`assignment_id`)
            -> ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
        Query OK, 0 rows affected (0.02 sec)

        mysql> alter table assignment drop column grade;
        Query OK, 0 rows affected (0.02 sec)
        Records: 0  Duplicates: 0  Warnings: 0

        mysql> alter table assignment add column grade_id int;
        Query OK, 0 rows affected (0.01 sec)
        Records: 0  Duplicates: 0  Warnings: 0

        mysql> select * from assignment;
        Empty set (0.00 sec)

        mysql> explain assignment;
        +----------------+------------------+------+-----+---------+----------------+
        | Field          | Type             | Null | Key | Default | Extra          |
        +----------------+------------------+------+-----+---------+----------------+
        | assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
        | student_id     | int(11)          | NO   |     | NULL    |                |
        | assignment_nbr | int(11)          | NO   |     | NULL    |                |
        | class_id       | int(11)          | YES  |     | NULL    |                |
        | grade_id       | int(11)          | YES  |     | NULL    |                |
        +----------------+------------------+------+-----+---------+----------------+
        5 rows in set (0.00 sec)

        mysql>


Medium challenge:

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
        |             1 |          2 |              5 |        4 |        1 |
        |             2 |          4 |              6 |        4 |        2 |
        |             3 |          5 |              5 |        3 |        3 |
        |             4 |          7 |              6 |        4 |        4 |
        |             5 |          8 |              7 |        2 |        5 |
        |             6 |          9 |              7 |        3 |        1 |
        |             7 |          7 |              5 |        4 |        4 |
        +---------------+------------+----------------+----------+----------+
        7 rows in set (0.00 sec)

        mysql>

        mysql> explain grade;
        +-------------------+-------------+------+-----+---------+----------------+
        | Field             | Type        | Null | Key | Default | Extra          |
        +-------------------+-------------+------+-----+---------+----------------+
        | grade_id          | int(11)     | NO   | PRI | NULL    | auto_increment |
        | grade_description | varchar(30) | YES  |     | NULL    |                |
        +-------------------+-------------+------+-----+---------+----------------+
        2 rows in set (0.00 sec)

        mysql> select * from grade;
        +----------+-----------------------------+
        | grade_id | grade_description           |
        +----------+-----------------------------+
        |        1 | Incomplete                  |
        |        2 | Complete and unsatisfactory |
        |        3 | Complete and satisfactory   |
        |        4 | Exceeds expectations        |
        |        5 | Not graded                  |
        +----------+-----------------------------+
        5 rows in set (0.00 sec)

        mysql>




Hard mode:

        mysql> CREATE INDEX idx_student_id
            -> on assignment(student_id);
        Query OK, 0 rows affected (0.02 sec)
        Records: 0  Duplicates: 0  Warnings: 0

        mysql> alter table assignment
            -> add constraint fk_student_id
            -> foreign key (student_id)  references student(student_id);
        ERROR 1215 (HY000): Cannot add foreign key constraint
        mysql> alter table assignment modify column student_id int unsigned not null;
        Query OK, 7 rows affected (0.03 sec)
        Records: 7  Duplicates: 0  Warnings: 0

        mysql> alter table assignment
            -> add constraint fk_student_id
            -> foreign key (student_id)  references student(student_id);
        Query OK, 7 rows affected (0.02 sec)
        Records: 7  Duplicates: 0  Warnings: 0

        mysql> explain assignment
            -> ;
        +----------------+------------------+------+-----+---------+----------------+
        | Field          | Type             | Null | Key | Default | Extra          |
        +----------------+------------------+------+-----+---------+----------------+
        | assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
        | student_id     | int(10) unsigned | NO   | MUL | NULL    |                |
        | assignment_nbr | int(11)          | NO   |     | NULL    |                |
        | class_id       | int(11)          | YES  |     | NULL    |                |
        | grade_id       | int(11)          | YES  | MUL | NULL    |                |
        +----------------+------------------+------+-----+---------+----------------+
        5 rows in set (0.00 sec)

        mysql> insert assignment (assignment_id, student_id, assignment_nbr, class_id, grade_id) value ('11', '15', '4', '6', '4');
        ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`tiy`.`assignment`, CONSTRAINT `fk_student_id` FOREIGN KEY (`student_id`) REFERENCES `student` (`student_id`))
        mysql>
