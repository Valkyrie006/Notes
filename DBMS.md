# Introduction to DBMS
- ***Data*** is a collection of a distinct small unit of information
- ***Database*** is an organized collection of data, so that it can be easily accessed and manage
- ***Database Management System (DBMS)*** is a software for storing and retrieving users’ data while considering appropriate security measures
- DBMS vs File System
    - In DBMS user not required to write procedure
    - DBMS gives an abstract view of data that hides the details
    - DBMS provides a crash recovery and protection mechanism
    - DBMS Efficient
    - DBMS concurrent access of data is there using locking
- Architecture
    1. Two Tier Architecture
        - Client Application(Presentation layer (application interface) and Application layer (logical operations)) -> Database (Server)
    2. Three Tier Architecture
        - Presentation Layer (Client tier) -> Application Layer (Business(Server) tier) -> Database Layer (Data tier)
- ***Instance*** : Collection of the information stored in the database at that particular moment
- ***Schema*** : Logical Representation/Design of database
- Three Schema Architecture (Data Abstraction)
    1. View Level or External Schema - Tells the application about how the data should be shown to the user
    2. Conceptual Level or Logical Level - Tells how the data is actually stored and structured
    3. Physical Level or Internal Schema - Tells us that where data is actually stored

    ![Three Level Schema](/assets/DBMS/Introduction_3LevelSchema.jpg)

- Data Independence
    - Property of DBMS that helps you to change the Database schema at one level of a database system without requiring to change the schema at the next higher level
    - Types
        1. Logical Data Independence
            - Ability to change the conceptual level without changing view level
        2. Physical Data Independence
            - Modification in the Physical level should not result in any changes in the Logical or View levels

# Relational Database Management Systems (RDBMS)
- Data is stored in terms of rows(Tables) and Relational DBMS as its based on Relational Model

### Keys
- Attribute or a set of attributes that help to uniquely identify a tuple (or row) in a relation (or table)
- Types of Keys
    1. Primary Key
        - Column or group of columns in a table that uniquely identify every row in that table
        - A table cannot have more than one primary key
        - Every row must have a non-NULL primary key
        - Value in a primary key column can never be modified or updated if any foreign key refers to that primary key
    2. Alternate Key
        - Column or group of columns in a table that uniquely identify every row in that table.
        - All the keys which are not primary key are called an Alternate Key
    3. Candidate Key
        - Set of attributes that uniquely identify tuples in a table
    4. Foreign Key 
        - Column that creates a relationship between two tables. It acts as a cross-reference between two tables as it references the primary key of same/another table
        - Referential integrity
            - Rule defines that a foreign key have a matching primary key. Reference from a table to another table should be valid
            - Foreign Key maintains referential integrity 
            - Referenced Table (Primary Key)
                1. Insert - No violation
                2. Delete - May cause violation
                          - We can do On DELETE Cascade (delete from both table)
                3. Update - May cause Violation
            - Referencing Table (Foreign Key)
                1. Insert - Violation
                2. Delete - No violation
                3. Update - May cause violation
    5. Super Key
        - Group of single or multiple keys which identifies rows in a table. A Super key may have additional attributes that are not needed for unique identification
        - All super keys can’t be candidate keys but its reverse is true
        
![Keys Ex1](/assets/DBMS/Keys_Ex1.png)

### ER Diagram
- Used to define the data elements and relationship for a specified system
- Components of ER Diagram
    1. Entity
        - Object or component of data
        - Represented as rectangle in an ER diagram
        - Weak Entity
            - An entity that cannot be uniquely identified by its own attributes and relies on the relationship with other entity
            - Represented by a double rectangle
            - For example – a bank account cannot be uniquely identified without knowing the bank to which the account belongs, so bank account is a weak entity
    2. Attributes
        - Describes the property of an entity
        - Represented as Oval in an ER diagram
        - Types of Attributes
            1. Key attribute
                - Can uniquely identify an entity from an entity set
                - Represented by oval same as other attributes however the text of key attribute is underlined
                - For example, student roll number can uniquely identify a student from a set of students
            2. Composite attribute 
            - An attribute that is a combination of other attributes
            - For example, In student entity, the student address is a composite attribute as an address is composed of other attributes such as pin code, state, country
            3. Multivalued attribute
                - Attribute that can hold multiple values 
                - Represented with double ovals in an ER Diagram
                - For example – A person can have more than one phone numbers so the phone number attribute is multivalued
            4. Derived attribute
                - Attribute is one whose value is dynamic and derived from another attribute
                - Represented by dashed oval in an ER Diagram
                - For example – Person age is a derived attribute as it changes over time and can be derived from another attribute (Date of birth)
    3. Relationship
        - Shows the relationship among entities
        - Represented by diamond shape
        - Types of Relationship
            1. One to One Relationship
                - When a single instance of an entity is associated with a single instance of another entity
                - For example, a person has only one passport and a passport is given to one person
            2. One to Many Relationship
                - When a single instance of an entity is associated with more than one instances of another entity
                - For example – a customer can place many orders but a order cannot be placed by many customers.
            3. Many to One Relationship
                - When more than one instances of an entity is associated with a single instance of another entity
                - For example – many students can study in a single college but a student cannot study in many colleges at the same time

            4. Many to Many Relationship
                - When more than one instances of an entity is associated with more than one instances of another entity
                - For example, a student can be assigned to many projects and a project can be assigned to many students
    
### Normalization
- Database design technique that reduces data redundancy and eliminates undesirable characteristics like Insertion, Update and Deletion Anomalies
- Types of Anomalies
    ![Normalization Anomalies Example](/assets/DBMS/Normalization_Anomalies_Example.png)
    1. Data redundancy
        - When two or more rows or columns have the same value or repetitive value leading to unnecessary utilization of the memory
        - Example - There are two students in the above table, 'James' and 'Ritchie Rich', whose records are repetitive when we enter a new CourseID. Hence it repeats the studRegistration, StudName and address attributes
    2. Insert Anomaly
        - When some attributes or data items are to be inserted into the database without existence of other attributes
        - For example, In the Student table, if we want to insert a new courseID, we need to wait until the student enrolled in a course. In this way, it is difficult to insert new record in the table. Hence, it is called insertion anomalies.
    3. Update Anomalies
        - When duplicate data is updated only in one place and not in all instances. Hence, it makes our data or table inconsistent state. 
        - For example, suppose there is a student 'James' who belongs to Student table. If we want to update the course in the Student, we need to update the same in the course table; otherwise, the data can be inconsistent. And it reflects the changes in a table with updated values where some of them will not.
    4. Delete Anomalies
        - When some records are lost or deleted from the database table due to the deletion of other records
        - For example, if we want to remove Trent Bolt from the Student table, it also removes his address, course and other details from the Student table. Therefore, we can say that deleting some attributes can remove other attributes of the database table
- Functional Dependency 
    - Relationship that exists between two attributes
    -  Left side of FD is known as a determinant, right side of FD is known as a dependent
    - Example: A->B, A is determinant, B is dependent
    - Types of FD
        1. Trivial Functional Dependency
            - X->Y is a trivial functional dependency if Y is a subset of X
            - Example: A->A
        2. Non-Trivial Functional Dependency
            - When A->B holds true where B is not a subset of A
    - Properties of FD
        1. Reflexivity: If Y is a subset of X then, X->Y
        2. Augmentation: If X->Y, then XZ->YZ
        3. Transitive: If X->Y and Y->Z, then X->Z
        4. Union: If X->Y and X->Z, then X->YZ
        5. Decomposition: If X->YZ, then X->Y and X->Z
        6. PseudoTransitivity: If X->Y and WY->Z, then WX->Z
        7. Composition: If X->Y and Z->W, then XZ->YW
- Partial Dependency
    - Non-prime attribute is functionally dependent on part of a candidate key
    - Example: let's start with R{ABCD}, and the functional dependencies AB->CD and A->C. The only candidate key for R is AB. C and D are a non-prime attributes. C is functionally dependent on A. A is part of a candidate key. That's a partial dependency.
- Lossless Decomposition
    - If there natural join results in original relation R
    - No loss of information
- Lossy Decomposition
    - If there natural join does not result in original relation R
- Closure of Attribute Set
    - Set of all those attributes which can be functionally determined from an attribute set
    - Closure of attribute set {X} is denoted as {X}<sup>+</sup>
    - Find closure of attribute set
        1. Add attributes contained in attribute set for which closure is being calculated to result set
        2. Recursively add attributes to result set which can be functionally determined from attributes already contained in result set
    - Example
    ![Closure Example](/assets/DBMS/Normalization_Closure_Example.png)
    - Finding Super Key
        - If closure result of an attribute set contains all attributes of relation, then that attribute set is called as a super key of that relation
        - Example - Closure of attribute A is the entire relation schema. Thus, attribute A is a super key for that relation
    -Finding Candidate Key
        - If there exists no subset of an attribute set whose closure contains all attributes of the relation, then that attribute set is called as a candidate key of that relation
        - Example - No subset of attribute A contains all attributes of the relation. Thus, attribute A is also a candidate key for that relation
    - ***Prime Key***: Attribute which is part of one of candidate key
- Types of Normal Form
    1. First Normal Form (1NF)
        - Table should not contain any multivalued attribute
        - How to get 1NF (Different processes)
            1. Convert 1 table into multiple tables
            2. Change PK to composite key of multiple columns in same table
    2. Second Normal Form (2NF)
        - Rules
            1. Should be in 1NF
            2. All non-prime attributes should be fully functional dependent on candidate key[Remove Partial Dependency](For Partial Dependency - LHS of FD is proper subset of CK AND RHS is non-prime attribute)
        - How to make 2NF (remove Partial Dependency)
            - Increase table by removing that column causing us trouble
        - Example: Prime key attributes are StudentID and ProjectID.Non-prime attributes i.e. StudentName and ProjectName should be functionally dependent on part of a candidate key, to be Partial Dependent.StudentName can be determined by StudentID, which makes relation Partial Dependent. ProjectName can be determined by ProjectID, which makes relation Partial Dependent. Therefore, the <StudentProject> relation violates the 2NF.
        ![2NF Example](/assets/DBMS/Normalization_2NF_Example.png)
    3. Third Normal Form (3NF)
        - Rules
            1. Should be in 2NF
            2. No non-primary key attribute is transitively dependent on primary key(For each FD, LHS must be CK or SK, OR RHS is a prime attribute)
        - Example: There is a transitive dependency between Bank_Code_No and Bank, because Bank_Code_No is not the primary key of this relation. To get to the third normal form (3NF), we have to put the bank name in a separate table together with the clearing number to identify it.
        ![3NF Example](/assets/DBMS/Normalization_Example_3NF.gif)
    4. Boyce-Codd Normal Form (BCNF)
        - Rules
            1. Should be in 3NF
            2. LHS of FD should be candidate key or super key
    5. Fourth Normal Form (4NF)
        - Rules
            1. Should be in BCNF
            2. No multi-valued dependency(For a dependency A → B, if for a single value of A, multiple values of B exists, then relation will be a multi-valued dependency)
    6. Fifth Normal Form (5NF)
        - Rules
            1. Should be in 4NF
            2. Not contains any lossy join dependency and joining should be lossless
        - How to make 5NF
            - Common attribute should be CK or SK of either R1 or R2 or both

### Joins
- Join statement is used to combine data or rows from two or more tables based on a common field between them
- Types of Joins ([Types of Joins](https://www.javatpoint.com/types-of-sql-join))
    1. Cross Join (Cartesian Product/Join)
        - When each row of first table is combined with each row from second table
        - If you add a WHERE clause (if table1 and table2 has a relationship), CROSS JOIN will produce same result as INNER JOIN clause
        - Syntax
            ```SQL
                SELECT * FROM [TABLE1] CROSS JOIN [TABLE2]
            ```
            OR
            ```SQL
                SELECT * FROM [TABLE1], [TABLE2]
            ```
    2. Natural Join
        - Natural Join joins two tables based on same attribute name and data-types. The resulting table will contain all the attributes of both the table but keep only one copy of each common column (Join on common column between two tables only)
        - Syntax
            ```SQL
                SELECT * FROM [TABLE1] NATURAL JOIN [TABLE2]
            ```
        - Example - [Natural Join Example](https://www.w3resource.com/sql/joins/natural-join.php)
    3. Self Join
        - Each row of table is joined with itself and all other rows depending on some conditions
        - Syntax
            ```SQL
                SELECT a.column1, b.column2
                FROM table_name a, table_name b
                WHERE some_condition;
            ```
        - Example - [Self Join Example](https://www.geeksforgeeks.org/sql-join-cartesian-join-self-join/)
    4. Inner Join
        - Used to select all matching rows or columns in both tables or as long as defined condition is valid in SQL
        - Syntax
            ```SQL
                SELECT column_1, column_2 
                FROM table_1 INNER JOIN table_2 
                ON table_1.column = table_2.column; 
            ```
        - Example [Inner Join Example](https://www.javatpoint.com/types-of-sql-join)
    5. Equi Join
        - A special type of join in which we use only an equality operator
        - Syntax
            ```SQL
                SELECT * FROM tblEmp JOIN tblDept 
                ON tblEmp.DeptID = tblDept.DeptID;
            ```
        - Example - [Equi Join Example](https://www.dotnettricks.com/learn/sqlserver/difference-between-inner-join-and-equi-join-and-natural-join)
    6. Left Join (Left Outer Join)
        - Used to retrieve all records from left table (table1) and the matched rows or columns from right table (table2). If both tables do not contain any matched rows or columns, it returns the NULL.
        - Syntax
            ```SQL
                SELECT column_1, column_2, column(s) 
                FROM table_1 LEFT JOIN table_2 
                ON table_1.column_name = table_2.column_name; 
            ```
        - Example - [Left Join Example](https://www.tutorialspoint.com/sql/sql-left-joins.htm)
    7. Right Join (Right Outer Join)
        - Used to retrieve all records from right table (table1) and the matched rows or columns from left table (table2). If both tables do not contain any matched rows or columns, it returns the NULL.
        - Syntax
            ```SQL
                SELECT column_1, column_2, column(s) 
                FROM table_1 RIGHT JOIN table_2 
                ON table_1.column_name = table_2.column_name; 
            ```
        - Example - [Right Join Example](https://www.javatpoint.com/types-of-sql-join#Full)
    8. Full Join (Full Outer Join)
        - It is a combination result set of both LEFT JOIN and RIGHT JOIN. The joined tables return all records from both the tables and if no matches are found in the table, it places NULL.
        - Syntax
            ```SQL
                SELECT column_1, column_2, column(s) 
                FROM table_1 FULL JOIN table_2 
                ON table_1.column_name = table_2.column_name;  
            ```
        - Example - [Full Join Example](https://www.tutorialspoint.com/sql/sql-full-joins.htm)
### Relational Algebra
![Relational Algebra](/assets/DBMS/Relational_Algebra_Operators.png)
1. Projection (π) [vertical partitioning]
    - It displays the columns of a relation or table based on the specified attributes
    - Syntax - π<sub>attribute list</sub>(R)
    - Unique
    - SQL equivalent of SELECT(difference is SELECT allows duplicates while projection does not)
    - Example - [Projection Example](https://www.gatevidyalay.com/projection-operator-relational-algebra-dbms/)
2. Selection (σ) [horizontal partitioning]
    - Chooses the subset of tuples from the relation that satisfies the given condition mentioned in the syntax of selection
    - Syntax - σ<sub>p</sub>(r)
    - Done before projection
    - Example - [Selection Example](https://www.geeksforgeeks.org/select-operation-in-relational-algebra/)
3. Cross/Cartesian Product (✕)
    - On applying CARTESIAN PRODUCT on two relations that is on two sets of tuples, it will take every tuple one by one from the left set(relation) and will pair it up with all the tuples in the right set(relation).
    - Cardinality (number of tuples/rows) = m * n [table1 - m rows, table 2 = n rows]
    - Degree (number of attributes/columns) = a + b [table1 - a columns, table2 - b columns]
    - SQL equivalent CROSS JOIN
    - Example - [Cross Product Example](https://www.geeksforgeeks.org/cartesian-product-operation-in-relational-algebra/)
4. Set Difference (-) [Minus]
    - Syntax - A – S
    - Is a relation that basically includes all the tuples that are present in A but not in S
    - Example - [Set Difference Example](https://www.gatevidyalay.com/set-theory-operators-relational-algebra-dbms/)
5. Union (U)
    - Syntax - A U B
    - Set of all tuples belonging to either R or S or both.
    - Rule
        1. Number of columns in both table are same
        2. Domain(data type) of both table's columns are same 
    - Duplicates are automatically removed.
    - Example - [Union Example](https://www.gatevidyalay.com/set-theory-operators-relational-algebra-dbms/)
6. Division (÷ or /)
    - Syntax - R1 ÷ R2 
    - Tuples of R1 associated with all tuples of R2
    - Example - [Division Example](https://www.tutorialspoint.com/explain-division-operation-in-relational-algebra-dbms)
### Types of SQL commands
![Types of SQL commands](/assets/DBMS/Types_of_SQL_Commands.png)
1. Data Definition Language (DDL)
    - DDL changes the structure of the table like creating a table, deleting a table, altering a table, etc.
    - All the command of DDL are auto-committed that means it permanently save all the changes in the database.
    1. CREATE
        - Used to create new table in DB
        - Syntax
            ```SQL
                CREATE TABLE TABLE_NAME (COLUMN_NAME DATATYPES[,....]);  
            ```
        - Example
            ```SQL
                CREATE TABLE EMPLOYEE(Name VARCHAR2(20), Email VARCHAR2(100), DOB DATE);  
            ```
    2. DROP
        - It is used to delete both the structure and record stored in the table
        - Syntax
            ```SQL
                DROP TABLE table_name;    
            ```
        - Example
            ```SQL
                DROP TABLE EMPLOYEE;
            ```
    3. ALTER
        - It is used to alter the structure of the database. This change could be either to modify the characteristics of an existing attribute or probably to add a new attribute.
        - Used to Add column(ALTER TABLE <tableName> ADD <columnName> <columnDataType>), Remove Column(ALTER TABLE <tableName> DROP column <columnName>), modify data type(ALTER TABLE <tableName> MODIFY <columnName> <newColumnDataType>), modify data type length, add constraints(ALTER TABLE <tableName> ADD PRIMARY KEY (<columnName>)), remove constraints, rename column/table(ALTER TABLE <tableName> RENAME <originalColumnName> TO <newColumnName>)
        - Syntax - Add a new column, Modify existing column
            ```SQL
                ALTER TABLE table_name ADD column_name COLUMN-definition;  
                ALTER TABLE table_name MODIFY(column_definitions....);
            ```
        - Example
            ```SQL
                ALTER TABLE STU_DETAILS ADD(ADDRESS VARCHAR2(20));  
                ALTER TABLE STU_DETAILS MODIFY (NAME VARCHAR2(20));  
            ```
    4. TRUNCATE
        - It is used to delete all the rows from the table and free the space containing the table (Structure remains the same)
        - Same as (DELETE FROM <tableName>) but faster, no rollback allowed
        - Syntax
            ```SQL
                TRUNCATE TABLE table_name;     
            ```
        - Example
            ```SQL
                TRUNCATE TABLE EMPLOYEE;  
            ```
2. Data Manipulation Language (DML)
    - DML commands are used to modify the database. It is responsible for all form of changes in the database.
    - The command of DML is not auto-committed that means it can't permanently save all the changes in the database. They can be rollback.
    1. INSERT
        - Insert data into the row of a table
        - Syntax
            ```SQL
                INSERT INTO TABLE_NAME    
                (col1, col2, col3,.... col N)  
                VALUES (value1, value2, value3, .... valueN);       
            ```
        - Example
            ```SQL
                INSERT INTO javatpoint (Author, Subject) VALUES ("Sonoo", "DBMS");  ;  
            ```
    2. UPDATE
        - Update or modify the value of a column in the table
        - Syntax
            ```SQL
                UPDATE table_name SET [column_name1= value1,...column_nameN = valueN] [WHERE CONDITION]        
            ```
        - Example
            ```SQL
                UPDATE students    
                SET User_Name = 'Sonoo'    
                WHERE Student_Id = '3'   
            ```
    3. DELETE
        - Remove one or more row from a table
        - Syntax
            ```SQL
                DELETE FROM table_name [WHERE condition];       
            ```
        - Example
            ```SQL
                DELETE FROM javatpoint  
                WHERE Author="Sonoo";    
            ```
3. Data Control Language (DCL)
    - Used to grant and take back authority from any database user
    1. GRANT
        - Used to give user access privileges to a database
        - Syntax
            ```SQL
                GRANT privilege_name
                ON object_name
                TO {user_name |PUBLIC |role_name}
                [WITH GRANT OPTION];      
            ```
        - Example
            ```SQL
                GRANT SELECT, UPDATE 
                ON MY_TABLE 
                TO SOME_USER, ANOTHER_USER;    
            ```
    2. REVOKE
        - Used to take back permissions from the user.
        - Example
            ```SQL
                REVOKE SELECT, UPDATE 
                ON MY_TABLE 
                FROM USER1, USER2;    
            ```
4. Transaction Control Language (TCL)
    - Used for transactions.
    - TCL commands can only use with DML commands like INSERT, DELETE and UPDATE only.
    - These operations are automatically committed in the database that's why they cannot be used while creating tables or dropping them.
    1. COMMIT
        - Used to save all the transactions to the database
        - Syntax
            ```SQL
                COMMIT;     
            ```
        - Example
            ```SQL
                DELETE FROM CUSTOMERS  
                WHERE AGE = 25;  
                COMMIT;    
            ```
    2. ROLLBACK
        - Used to undo transactions that have not already been saved to the database
        - Syntax
            ```SQL
                ROLLBACK;      
            ```
        - Example
            ```SQL
                DELETE FROM CUSTOMERS  
                WHERE AGE = 25;  
                ROLLBACK;    
            ```
    3. SAVEPOINT
        - Used to roll the transaction back to a certain point without rolling back the entire transaction.
        - Syntax - Creation of savepoint among all transactions, rollback to undo transaction
            ```SQL
                SAVEPOINT SAVEPOINT_NAME;     
                ROLLBACK TO SAVEPOINT_NAME;
            ```
5. Data Query Language (DQL)
    - Fetch the data from the database
    1. SELECT
        - Used to select the attribute based on the condition described by WHERE clause
        - Syntax
            ```SQL
                SELECT expressions    
                FROM TABLES    
                WHERE conditions;       
            ```
        - Example
            ```SQL
                SELECT emp_name  
                FROM employee  
                WHERE age > 20;    
            ```
6. CONSTRAINTS
    -  Rules that we can apply on the type of data in a table
    - How to specify constraints? 
        - We can specify constraints at the time of creating the table using CREATE TABLE statement. 
        - We can also specify the constraints after creating a table using ALTER TABLE statement.
        - Syntax
            ```SQL
                CREATE TABLE sample_table
                (
                column1 data_type(size) constraint_name,
                column2 data_type(size) constraint_name,
                column3 data_type(size) constraint_name,
                ....
                );
            ``` 
    1. NOT NULL
        - If a column is specified as NOT NULL then we will not be able to store null in this particular column any more.
        - Syntax
            ```SQL
                CREATE TABLE Student
                (
                ID int(6) NOT NULL
                );
            ```
    2. UNIQUE
        - This constraint when specified with a column, tells that all the values in the column must be unique. That is, the values in any row of a column must not be repeated.
        - Syntax
            ```SQL
                CREATE TABLE Student
                (
                ID int(6) NOT NULL UNIQUE
                );
            ```
    3. PRIMARY KEY
        - A primary key is a field which can uniquely identify each row in a table.
        - This is combination of NOT NULL and UNIQUE constraints. 
        - A table can have only one field as primary key.
        - Syntax
            ```SQL
                CREATE TABLE Student
                (
                ID int(6) NOT NULL UNIQUE
                );
            ```
    4. FOREIGN KEY
        - A Foreign key is a field which can uniquely identify each row in a another table.
        - Syntax
            ```SQL
                CREATE TABLE Orders
                (
                O_ID int NOT NULL,
                C_ID int,
                PRIMARY KEY (O_ID),
                FOREIGN KEY (C_ID) REFERENCES Customers(C_ID)
                )
            ```
    5. CHECK
        - This constraint helps to validate the values of a column to meet a particular condition.
        - Syntax
            ```SQL
                CREATE TABLE Student
                (
                AGE int NOT NULL CHECK (AGE >= 18)
                );
            ```
    6. DEFAULT
        - This constraint specifies a default value for the column when no value is specified by the user.
        - Syntax
            ```SQL
                CREATE TABLE Student
                (
                AGE int DEFAULT 18
                );
            ```